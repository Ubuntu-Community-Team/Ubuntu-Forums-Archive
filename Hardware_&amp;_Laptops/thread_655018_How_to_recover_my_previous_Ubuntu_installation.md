---
title: "How to recover my previous Ubuntu installation?"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by eku on 2007-12-31
I had Ubuntu 6.x running as my server, on a 30GB (or a 20GB disk, don't remember which), and decided to install 7.10 to a new 160GB disk. So, now I have Ubuntu running on 160GB disk, and two other disks (20GB and 30GB) which other had my previous installation.
I tried to mount each one separetly now, using my 160GB Ubuntu installation, but all I get is 2GB sized /boot/ partition, and just some "disk" partition, which is too only 2GB. Other, 18 to 28 GB is unallocated (or something like that, with exclamation marks), according to Partition Editor.

So, I try the old setup, but on the boot I get "no operating system found". It worked (almost) fine before (booting took forever, or sometimes it would have just crash on some other error, but when up and running, nothing wasn't broke (well, kind of every other program, but that was due to bad setup etc.)).

Is there a way to "force mount" the disks or anything? Otherwise I lost over three years of irc logs and other moderatively important files.

Oh yeah, when I installed 7.10, it did had some errors when I tried to format or something the 160GB disk on installation. And I'm quite sure I didn't touch the other disks in anyway during that.

edit: Oh yeah, the content of the /boot/ disk is lost+found folder, and some other stuff (abi 2.7... or something, Abiword?), and other isn't accesable.

L

---

### Post by Sef on 2007-12-31
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

---

