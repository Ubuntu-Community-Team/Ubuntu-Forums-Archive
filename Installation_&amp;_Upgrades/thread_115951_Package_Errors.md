---
title: "Package Errors"
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by Raven-sb on 2006-01-11
Hi All,

I recently installed Breezy and after downloading Gnomebaker apt-get/Synaptic decided that they wouldn't work for me.  I have updates to apply to my ubuntu box, however whenever I try to get them the following errors occur.


Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://nz.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Bad header line
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://nz.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

and

E: The package index files are corrupted. No Filename: field for package adduser.

E: Unable to lock the download directory

Any help to resolve these errors would be warmly appreciated.

Raven

---

### Post by aysiu on 2006-01-11
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by Raven-sb on 2006-01-12
Thanks aysiu,

unfortunately now I get a whole lot of different errors.  Btw I followed the sites instructions as to what to do in case of a checksum error.  Unfortunately it didn't help.

Here is the output I'm receiving.

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


Any other ideas?

Regards,

Raven

---

