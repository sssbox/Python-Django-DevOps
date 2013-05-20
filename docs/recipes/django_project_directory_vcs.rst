############################################################
Using version control for your Django your project directory
############################################################

Your Django project directory needs to be treated with as much care as your
applications. If you ever need to set up a new instance of the project (for
example to set up a new development environment) you'll want the process as
to:

* be as easy and quick as as possible
* replicate your live project precisely

One way of doing this is to manage your project using version control, so that
it can be cloned, branched, rolled back and otherwise managed in the same way
as any other material you use version control to look after.

Required expertise
==================

* basic use of version control software

How to do it
============

Create a new repository on your version control repository hosting service
(GitHub, BitBucket, or whatever you like best) for the project. If you have an
account that will allow you to create private repositories, use that.

Initialise the project directory for version control. In Git, for example::

    git init

Configure the version control system so that it ignores the file paths and
types that you don't want include. In Git, this involves entering some
patterns into a ``.gitignore`` file at the root of the repository, for
example::

    *.pyc
    secret_settings.py
    processed_thumbnail_files
    temporary_uploads

So, in this example we are excluding all compiled Python files, a file called
``secret_settings.py`` (if you don't have a private repository, you don't want
to put secrets in it), a directory of rendered rather than source files, and a
directory of files that don't need to be kept anyway.

You will need to spend some time carefully setting up this aspect of
configuration, to make sure unnecessary and worse - sensitive - files do not
end up in a public repository.
                                
.. DANGER::
    Your ``settings.py`` file **contains sensitive** information such as
    database passwords. You absolutely do not want to publish this
    information.

One solution to the problem of sensitive information in your settings is to go
through your settings file, carefully, and move that sensitive information
into a file called for example ``secret_settings.py``, and then, in
``settings.py``::

    import secret_settings.py
    
You'll have to keep the secret_settings safe somewhere else.