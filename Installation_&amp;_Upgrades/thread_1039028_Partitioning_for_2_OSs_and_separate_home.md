---
title: "Partitioning for 2 OSs and separate /home"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by matt_feliks on 2009-01-14
Hi all,

I've been using Ubuntu solely for months now, but I need to put windows back on my machine.

I don't mind formatting then installing windows, then ubuntu.

However, how should I set the partitions up to do this? Whenever I've tried to shrink Vista's partition it complains about a corrupted HD.

Also, I'd like /home to sit in a separate partition - how should I do this from the Ubuntu installation?

Additionally, I don't want to create a swap partition this time around - I have 2GB of RAM and don't need one for Ubuntu.

Any help much appreciated - I'm not sure where to start.

---

### Post by Partyboi2 on 2009-01-14
> Additionally, I don't want to create a swap partition this time around - I have 2GB of RAM and don't need one for Ubuntu. I would recommend creating one if you plan to use hibernate/suspend

If vista is complaining of a corrupt hard drive the maybe you should test your hard drive. Most of the hard drive manufactures have a program that you can use to test your hard drive.

You don't have to install windows first if you don't want to. All it means is that if you install windows after installing ubuntu you will need to restore grub using a live cd. See [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351")

Edit: If you are wanting a /home partition, you will need to select "manual" at the partitioning stage of the install and create a ext3 partition for home and set the mount point to /home.
You will also need to create another ext3 partition with the mount point / for the system files.
Also recommend  creating a  /swap (3gig)

---

