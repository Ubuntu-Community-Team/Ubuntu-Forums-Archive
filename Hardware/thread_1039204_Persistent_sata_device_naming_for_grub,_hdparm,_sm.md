---
title: "Persistent sata device naming for grub, hdparm, smartctl, etc?"
date: 2009-01-14
forum: Hardware
---

### Post by matt_garman on 2009-01-14
I have Ubuntu Server 8.04 installed on a machine with nine total hard drives.  Eight are SATA and one is PATA/IDE.  The IDE drive is the system drive (i.e. from which I boot, where the OS is installed, etc).  The other eight drives are grouped into two 4-disk md (linux software raid) arrays.

On boot, all devices get named /dev/sd?.  The problem is, the device names always get shuffled around on each boot.  E.g., the system drive is /dev/sda today, but on the next boot, might show up as /dev/sde.  I saw that [this post]("http://ubuntuforums.org/showthread.php?t=911182") talks about using UUIDs instead of device names.  That works fine for /etc/fstab, but other programs, namely hdparm and smartctl, don't use UUIDs.  And I have scripts that I want to run on the raid drives, but not on the system drive.  (Granted, my script could, for example parse /proc/mdstat to determine the RAID drives, but it would be much easier just to have persistent device names.)

Another, but related problem: I just built another server using Ubuntu Server 8.04.  When I installed the OS, I only had one drive in the system.  After install, I booted into the system to verify that everything works.

Now the tricky part: this machine has a number of hot swap bays, and I intend to swap drives in and out on a regular basis.  So the first thing I did was plug in a number of hard drives.  I went into the BIOS to make sure the original drive was searched first for booting the operating system.  When it booted, I got a GRUB Error 15.

I found [this blog post](http://www.mohawksoft.org/?q=node/26) which talks about a workaround for the GRUB problem.  And in other posts I've seen suggestions to hack my udev rules to get persistent device naming... but I'm just wondering if there's an easier way?  My gentoo box is using udev and doesn't shuffle device names around or require non-trivial workarounds.  So is this behavior specific to Ubuntu?  And is there anyway to make it behave a little more sanely?

Thanks,
Matt

---

### Post by Belfry on 2010-11-23
Just an answer to an old post in case anyone needs it.   If your drive names come up inconsistently, try the /dev/disk/by-id identifier.  List long to find the symlink for your disk and use it in /etc/hdparm.conf or elsewhere.
```
ls -l /dev/disk/by-id
```

---

### Post by teeedubb on 2010-12-19
Thanks for the tip!

---

