.. _summary_sharelocal:

Summary
-------

Together with your room mate you have just discovered how
to share and update a DataLad dataset on a shared filesystem.
Thus, you have glimpsed into the principles and advantages of
sharing a dataset with a simple example.

* To obtain a dataset, one has to ``datalad install`` this
  dataset. Note that this requires the appropriate permissions
  in real-world examples.
  Note further that subdatasets will not be installed by default --
  you will have to do a plain ``datalad install PATH/TO/SUBDATASET``,
  or specify the ``-r``/``--recursive`` option in the install command:
  ``datalad install -s ../DataLad-101 -r`` with a decent
  ``recursion-limit`` choice.

* On a common or share file system, ``datalad install`` takes a path
  as the ``-s``/``--source`` option.

* The configuration of the original dataset determines which types
  of files will have their content available right after installation
  of the dataset, and which types of files need to be retrieved via
  ``datalad get``: Any file content stored in :term:`Git` will be available
  right away, while all file content that is ``annexed`` only has
  small meta data about its availability attached to it. The original
  ``DataLad-101`` dataset used the ``text2git`` configuration template
  to store text files such as ``notes.txt`` and ``code/list_titles.py``
  in Git -- these files' content is therefore available right after
  installation.

* Annexed content can be retrieved via ``datalad get`` from the
  file content sources.

* ``git annex whereis PATH`` will list all locations known to contain file
  content for a particular file. This location is where :term:`Git-annex`
  will attempt to retrieve file content from, and it is described with the
  ``--description`` provided during a ``datalad create``. It is a very
  helpful command to find out where file content resides, and how many
  locations with copies exist.

* A shared copy of a dataset includes the datasets history. If well made,
  ``datalad run`` commands can then easily be ``rerun``.

* Because an installed dataset knows its origin -- the place it was
  originally installed from -- it can be kept up-to-date with the
  ``datalad update`` command. This command will query the origin of the
  dataset for updates, and a ``datalad update --merge`` will integrate
  these changes into the dataset copy.

* Thus, using DataLad, data can be easily shared and kept up to date
  with only two commands: ``datalad install`` and ``datalad update``.

Now what I can do with that?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Most importantly, you have experienced the first way of sharing
and updating a dataset.
Thgit e example here may strike you as too simplistic, but in later parts of
the book you will see examples in which datasets are shared on the same
file system in surprisingly useful ways.

Simultaneously, you have observed dataset properties you already knew
(for example how annexed files need to be retrieved via ``datalad get``),
but you have also seen novel aspects of a dataset -- for example that
subdatasets are not automatically installed by default, how
``git annex whereis`` can help you find out where file content might be stored,
or how a shared dataset can be updated to reflect changes that were made
to the original dataset.

Also, you have successfully demonstrated a large number of DataLad dataset
principles to your room mate: How content stored in Git is present right
away and how annexed content first needs to be retrieved, how easy a
``datalad rerun`` is if the original ``datalad run`` command was well
specified, how a datasets history is shared and not only its data.
Therefore, these last few sections have hopefully been a good review
of what you already knew, but also a big knowledge gain.
