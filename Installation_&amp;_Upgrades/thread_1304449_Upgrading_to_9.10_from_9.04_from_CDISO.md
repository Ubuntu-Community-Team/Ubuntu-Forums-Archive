---
title: "Upgrading to 9.10 from 9.04 from CD/ISO"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by battlecyborg on 2009-10-29
I just downloaded the 9.10 desktop ISO, burned it on disk.  It was my impression there is a method I can upgrade from disk instead of using the update manager since it is not ready for download yet.  Ubuntu did not detect that the disk is an upgrade disk or anything like that, is there a command I can invoke to get it started from the shell?

---

### Post by phillw on 2009-10-29
> **battlecyborg said:**
> I just downloaded the 9.10 desktop ISO, burned it on disk.  It was my impression there is a method I can upgrade from disk instead of using the update manager since it is not ready for download yet.  Ubuntu did not detect that the disk is an upgrade disk or anything like that, is there a command I can invoke to get it started from the shell?


Hi ...

[http://www.ubuntugeek.com/upgrade-ubuntu-9-04-jaunty-jackalope-to-ubuntu-9-10-karmic-koala-beta.html](http://www.ubuntugeek.com/upgrade-ubuntu-9-04-jaunty-jackalope-to-ubuntu-9-10-karmic-koala-beta.html)

Regards,

Phill.

---

### Post by battlecyborg on 2009-10-29
Thanks, I thought that was just for download method.  The update manager detects the CD!

---

### Post by battlecyborg on 2009-10-29
Actually, now after I hit upgrade its actually not doing what I initially assumed.  Still getting data off the network instead... ugh.  At least its available now.

---

### Post by UNIXnewbie on 2009-10-29
Hi battlecyborg :)

Since you already upgraded, this is just FYI:

To upgrade from the CD, we need to use the Alternate copy; ref [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) => Upgrading Using the Alternate CD/DVD

I would download the alternate version from here [http://mirrors.kernel.org/ubuntu-releases/9.10/](http://mirrors.kernel.org/ubuntu-releases/9.10/)

---

### Post by battlecyborg on 2009-10-29
Thank You for the link. I've downloaded the alternate disk for the other hosts I need to convert. Thanks!

---

### Post by sheetzam on 2009-10-29
having a similar problem.  Using the alternate install cd, and it still wants to connect to the net.
Here's exactly what I've done:
sheetzam@geekbox-linux:~/Desktop$ sudo mount -o loop /home/sheetzam/Desktop/kubuntu-9.10-alternate-amd64.iso /media/cdrom0
sheetzam@geekbox-linux:~/Desktop$ gksu "sh /cdrom/cdromupgrade"

gets through over 1300 packages, then wants to download from the net.

---

### Post by alfu on 2010-01-01
When after booting from the alternate 9.10 CD, per instructions from [http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading"), I type: 

**Alt+F2** then  **gksu "sh /cdrom/cdromupgrade"**

I get the reply: "-/bin/sh: gksu: not found"

If I type **sh /cdrom/cdromupgrade**

it seems to recognize it a bit better, then I only get a 

"Could not find the upgrade application in the archive, exiting" error.

Is this fun or what?  :confused:

---

