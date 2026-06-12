---
title: "Reboot from within linux to bootable ISO file?"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Defrector on 2009-11-06
Is there any possibility of invoking a reboot off of a bootable ISO file from within ubuntu? I know it's a bit of a stretch...

I am trying to re-install ubuntu to a partition of the boot drive on a machine which has no CD-ROM drive, but it has an ISO installer image file on one of the other partitions and a ubuntu-server install which is not detecting the network device properly on another partition.

Ideally it would be nice to invoke a reboot from ubuntu-server, pointing to the ISO file and reinstalling with the ISO. I am explicitly avoiding virtualization for this.

---

### Post by MikeSho on 2009-11-06
I'm not sure if this would be of any help. Try install 'Gmount' Synaptic Package Manager. With this, you can upload the ISO image and it would appear as a CD-ROM drive, from which you can do the install. Good Luck Mate. :D

---

### Post by Defrector on 2009-11-06
Thanks! I caved and found an optical drive to connect.

found a related thread:
[http://ubuntuforums.org/showthread.php?t=774539](http://ubuntuforums.org/showthread.php?t=774539)

---

