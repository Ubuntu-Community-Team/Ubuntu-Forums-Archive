---
title: "Upgrade to 8.10 from 7.10 Advice"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by AlistairH on 2009-02-27
Hi,

I'm looking for confirmation before I launch into this.

My understanding is that I cannot upgrade from 7.10 to 8.10 without first upgrading to 8.04 first.

I'm happy to do a completely fresh installation, overwriting my 7.10 installation in the process, however I do have an important issue that I need answered before I do so.

Last year I purchased a Java based application which was downloaded and installed over the Internet. That company is now defunct and the application is no longer available so it is important that the installation of 8.10 does NOT wipe this.

My understanding is that this application is installed in my home directory. Specifically, /home/alistair/.java/deployment/cache/6.0/58/64b5e8ba-7a9338a4

As my home directory is on its own partition, I presume that I can install 8.10 on the partition where the 7.10 system files are stored and leave my home partition intact. Obviously I'd backup the home partition anyway.

My question is therefore, if I do a clean install of 8.10 on partition /dev/sda1 (where 7.10 currently resides) and point the home folder to /dev/sda3 (where my home folder currently resides) will this preserve the Java application that I need and use everyday?

Are there any issues that I should be aware of before hand? Would it be better if I simply waited for 9.04 to be released?

Many thanks

---

### Post by wpshooter on 2009-02-27
I "hope" I am wrong but I would not have the utmost confidence that your appplication is still going to run correctly after changing from one version of Ubuntu to another !!!

---

### Post by mozkill on 2009-02-27
Just do a CloneZilla backup of the whole drive first and THEN upgrade it.  If it breaks you can easily go back to where you were before.  Problem solved.

---

### Post by AlistairH on 2009-03-02
> **wpshooter said:**
> I "hope" I am wrong but I would not have the utmost confidence that your appplication is still going to run correctly after changing from one version of Ubuntu to another !!!

The application is Java based so there shouldn't be a problem. Famous last words of course.

If got the application installed on my daughter's 7.10 box so I'll try it there first, though the home and system folders are on the same partition.

---

