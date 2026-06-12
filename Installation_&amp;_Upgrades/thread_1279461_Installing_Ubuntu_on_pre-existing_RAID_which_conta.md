---
title: "Installing Ubuntu on pre-existing RAID which contains Gentoo."
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2009-09-30
Hi,

I have this hardware:
Intel i7 920
6g RAM
Asus P6T motherboard. (SATA/"hardware" RAID)
4x WD 750G 10000 rpm drives.

It is configured as RAID + LVM2, it boots and works fine, mostly.  Here are the partitions:
/dev/md1:  /boot 128M, RAID1 * 4
/dev/sd*2: swap 6G
/dev/md3:  / 25G, Gentoo
/dev/md5:  / 25G, empty for Ubuntu
/dev/md6:  LVM2.

I want to put Ubuntu on md5.  I would like to set up LV's to handle a few other partitions, and share things like /home and /opt and /tmp.

What I'm worried about is trashing my existing disks.

I couldn't figure out how to make Ubuntu work like this.  It wants to go straight into formatting the disk and doesn't recognize the RAID or LVM.

I downloaded Kubuntu's alternate CD, and I'm staring at it now.  It recognizes the LV's and everything, but it wants to scribble on my partition table.  I don't want it to.

Has anyone else done this?  I have a huge amount of time invested in the Gentoo installation.  Those of you who have used it know exactly what I mean.

What I would like to have is Ubuntu, not Kubuntu.  I will live with KDE if I have to, to get the job done.  If I go that route, I'll probably configure gnome on it anyway, it'll just be a bit dirtier.

---

### Post by Nostalos on 2009-10-01
The Ubuntu Alternate Installer will detect your RAID/LVM as well.  Just not the Live CD. 

There is a couple methods to do this, and since you are a Gentoo user I am going to assume that you are not the average user. 

1.  On the install as long as you do not set the existing partitions to be formatted they will be safe (still recommend backing it up of course).  Ubuntu will of course replace Grub and you will need to add your Gentoo Kernel configs.

2.  If you want just the Ubuntu System without changing from Gentoo's Grub install you can follow this walk through on encrypted filesystem install.  Most of it is not relevant but the use of debootstrap is what you are concerned with.     If you have another ubuntu system you can create a directory that contains the base bootstrap image or you can boot from a Live CD and install the required components and manually configure the system to be able to see the RAID/LVM from there.

Debootstrap info
[https://help.ubuntu.com/community/EncryptedFilesystemHowto4](https://help.ubuntu.com/community/EncryptedFilesystemHowto4)

FakeRaid Howto
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

LVM Howto
[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

---

### Post by 1clue on 2009-10-01
Awesome!

I've been running Linux of one distro or another for over a decade now -- since before it started getting all that attention.  I have used it exclusively on my desktop for more than half of that time.  I've done several Gentoo installs, but never RAID or LVM, and I can remember that I dual-booted in the early days but that was lilo and even that has changed dramatically since then.

My Achilles' heel is that I tend to want to do things in the shell, rather than with a GUI when I learn it.  So I set up RAID and LVM in Gentoo after a couple false starts with Ubuntu.

One thing, I have been sticking with lilo until very recently, since I knew that.  The Gentoo install is on grub, since I know Ubuntu uses grub.  But I really don't know what I'm doing there.

The /boot directory, there are no name collisions in /boot, but lots of them in /boot/grub.  I'll have a backup of all of /boot in a common filesystem, and I can reference that if I have to, but I'm afraid of trashing the whole works.

I wouldn't describe myself as an uptime junkie anymore, but I used to be one.  Had one of my systems stay up for 523 days, and actually that was the one that convinced me that huge uptimes were not really that beneficial.  It was a wreck by the time I was done, and wouldn't boot for all the configuration changes.  But as a result of all that, I have a sort of fear of booting after manual changes to the initialization code.

Thanks for the help.

---

### Post by Nostalos on 2009-10-01
Glad to be of help.  Let me know how it goes.  I've done the later when switching out my servers from Gentoo to Ubuntu.

---

### Post by 1clue on 2009-10-02
So far, it seems to have gone quite well.  Haven't booted into Gentoo again yet, but the partitions are still there and they contain data.

Thanks again.

---

