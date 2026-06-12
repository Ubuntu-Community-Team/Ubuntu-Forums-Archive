---
title: "Is there a max file size in a .deb package"
date: 2008-11-18
forum: General Help
---

### Post by zakiwi on 2008-11-18
Hi there,

I'm trying to create a debian package for deployment of standard services to our production systems.

It's all been working reasonably well until I added a 9GB database file to a package.  The file is a database file of sorts, and compresses really well.  The package goes down to about 220MB, and the build process ([FONT="Courier New"]sudo dpkg-deb -b my-package Packages/my-package.deb[/FONT]) seems to work without error, but on installation, I get the following errors:

[FONT="Courier New"]# sudo dpkg -i my-package.deb 
Selecting previously deselected package my-package.
(Reading database ... 167258 files and directories currently installed.)
Unpacking my-package (from my-package.deb) ...
dpkg: error processing my-package.deb (--install):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 my-package.deb[/FONT]

I can manually extract the contents of my-package.deb file with File Roller, and everything looks fine.  I checked all the files with md5sum and they all appear to be fine.  If I compress the database file with gzip and then build the package, then there's not a problem.  It installs fine, but we'd prefer not to have to do that if we can.

Any help would be highly appreciated.

Kind regards

Zakiwi

---

### Post by SunnyRabbiera on 2008-11-18
There really isnt a max file size with .deb to my knowledge, but you may wish to break your stuff down to several installers...
that way apt doesnt get overloaded

---

### Post by zakiwi on 2008-11-18
Thanks for your reply.

I'm afraid this .deb package that I'm referring to only has the one file in it, so it can't really be split.

What we have found is that by gzipping the database file and including a postinst script and gunzip'ing the database file from there works fine ... but it's a bit slow.

I wonder if it's a 4gb thing.

Cheers

Zakiwi

---

