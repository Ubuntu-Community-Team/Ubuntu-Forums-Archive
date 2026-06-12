---
title: "USB hard drive no longer recognized (jaunty)"
date: 2009-04-26
forum: Hardware
---

### Post by jswhite on 2009-04-26
I have a terabyte external drive (WD "My Book") that I've been using for a few months successfully with Intrepid. I've backed up a bunch of important files to it. Previously, I could just plug it in and it'd be automagically recognized, mounted, and a new nautilus window would open up for me at its location.

After a few weeks of not using it for anything, I tried to plug it in again today and it's suddenly not being recognized anymore. In the interim, I did upgrade to Jaunty, but I'm not actually convinced that's the problem. It could be a hardware issue (ugh), but I wanted to seek out help first in the hopes that it may be software related and I could fix it myself.

Here's the facts of what I've done and what I've observed so far:

1. I've been [here]("http://ubuntuforums.org/showthread.php?t=1128849&highlight=external+hard+drive") already, which suggested adding "usb_storage" to /etc/modules. Did that, no change.

2. "sudo fdisk -l" does not list anything for my terabyte drive after I plug it in to the computer.

3. I have a PNG 2.0 gig flash drive that works just fine, exactly the way it always has. I just tested right after my terabyte drive had problems, and it was recognized with no problems. This is what makes me suspect it's not a Jaunty-specific issue. "sudo fdisk -l" shows an entry for the flash drive at /dev/sdb when it's plugged in.

4. The earlier thread suggested powercycling the hard drive and trying again. I did; still nothing.

5. Tried rebooting with it plugged in the entire time; nada.

6. When I plug in the USB cable, the lights on the front of the terabyte drive come on just like they did before, so there's obviously some kind of communication going on between it and my computer. I can also hear the hard drive inside of it spinning up, so there shouldn't have been any kind of catastrophic hardware failure.

7. I believe it's formatted as a FAT32 drive. Whatever it's supposed to be out of the box; I didn't reformat it when I got it.

That's all I can think of. Any help would be greatly appreciated.

---

### Post by VastOne on 2009-04-27
> **jswhite said:**
> I have a terabyte external drive (WD "My Book") that I've been using for a few months successfully with Intrepid. I've backed up a bunch of important files to it. Previously, I could just plug it in and it'd be automagically recognized, mounted, and a new nautilus window would open up for me at its location.

After a few weeks of not using it for anything, I tried to plug it in again today and it's suddenly not being recognized anymore. In the interim, I did upgrade to Jaunty, but I'm not actually convinced that's the problem. It could be a hardware issue (ugh), but I wanted to seek out help first in the hopes that it may be software related and I could fix it myself.

Here's the facts of what I've done and what I've observed so far:

1. I've been [here]("http://ubuntuforums.org/showthread.php?t=1128849&highlight=external+hard+drive") already, which suggested adding "usb_storage" to /etc/modules. Did that, no change.

2. "sudo fdisk -l" does not list anything for my terabyte drive after I plug it in to the computer.

3. I have a PNG 2.0 gig flash drive that works just fine, exactly the way it always has. I just tested right after my terabyte drive had problems, and it was recognized with no problems. This is what makes me suspect it's not a Jaunty-specific issue. "sudo fdisk -l" shows an entry for the flash drive at /dev/sdb when it's plugged in.

4. The earlier thread suggested powercycling the hard drive and trying again. I did; still nothing.

5. Tried rebooting with it plugged in the entire time; nada.

6. When I plug in the USB cable, the lights on the front of the terabyte drive come on just like they did before, so there's obviously some kind of communication going on between it and my computer. I can also hear the hard drive inside of it spinning up, so there shouldn't have been any kind of catastrophic hardware failure.

7. I believe it's formatted as a FAT32 drive. Whatever it's supposed to be out of the box; I didn't reformat it when I got it.

That's all I can think of. Any help would be greatly appreciated.

I am having the same issue with a USB printer that has worked flawlessly even after the upgrade/new install to Jaunty.  During a routine update via Update Manager, it no longer works and I get several errors of device descriptor read/64, error -110 until I unplug the printer.  I have switched out everything imaginable and every thing else works on these USB's but not the printer.  In reading a million posts regarding the device descriptor read/64, error -110 errors, I have come across several with the exact same issues as your issues with the external USB drive(s).  I think this is a kernel issue and am patiently waiting for some insight to it.

---

### Post by jswhite on 2009-04-28
Well, I guess at least the good news is that you're getting an error message of some kind. Mine just does nothing. It looks like it should be working, but it doesn't.

Anybody got any suggestions?

---

### Post by mariusthart on 2009-05-04
I have the same issue with several USB hard-drives and several USB sticks. The problem is there on several machines upgraded from Intrepid to Jaunty, but not on two fresh installs.

This is what dmesg says when I plug in my USB stick:

```
[334539.164043] usb 1-3: new high speed USB device using ehci_hcd and address 7
[334539.306424] usb 1-3: configuration #1 chosen from 1 choice
[334539.306733] scsi10 : SCSI emulation for USB Mass Storage devices
[334539.306839] usb-storage: device found at 7
[334539.306842] usb-storage: waiting for device to settle before scanning
[334544.304540] usb-storage: device scan complete
[334544.305522] scsi 10:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[334544.506133] sd 10:0:0:0: [sdc] 15638528 512-byte hardware sectors: (8.00 GB/7.45 GiB)
[334544.506623] sd 10:0:0:0: [sdc] Write Protect is off
[334544.506627] sd 10:0:0:0: [sdc] Mode Sense: 23 00 00 00
[334544.506630] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[334544.508249] sd 10:0:0:0: [sdc] 15638528 512-byte hardware sectors: (8.00 GB/7.45 GiB)
[334544.509632] sd 10:0:0:0: [sdc] Write Protect is off
[334544.509636] sd 10:0:0:0: [sdc] Mode Sense: 23 00 00 00
[334544.509640] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[334544.509647]  sdc: sdc1
[334544.510378] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[334544.510449] sd 10:0:0:0: Attached scsi generic sg3 type 0

```

Looks like there should be devices on /dev/sdc, let's take a look at what fdisk knows about that:

```
marius@pc:~$ sudo fdisk -l /dev/sdc
marius@pc:~$ 
```

That's not a lot. The Device Manager also doesn't show the drives anywhere in the USB section. Trying to mount it anyway also has no succes.

After upgrading, I tracked some dependency issues to gvfs and fuse (especially the components for mounting ntfs drives, there is one package in the library that's not on the servers: libntfs-3g28 ), so I reinstalled most or all of that. I also tried adding usb_storage to /etc/modules and the module is inserted for sure, but it didn't help.

I'll try a fresh install to save time, but I don't like it.

---

### Post by mariusthart on 2009-05-04
Seems related to this [bug]("https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/88746").

---

### Post by mariusthart on 2009-05-04
For some reason it works again after a reboot, although I don't see any changes in loaded modules and such.

---

### Post by jswhite on 2009-05-07
Mine does not appear to be related to that bug. The bug post says the problem is related to the module ehci_hcd, which is "loaded on every boot." I did "modprobe ehci_hcd", and it says there is no such module running on my computer.

This keeps getting stranger.

---

### Post by kdib on 2009-05-08
Hi all,

I may have a somewhat similar issue happening under 8.10. Please see my post here:
[http://ubuntuforums.org/showthread.php?t=1152376](http://ubuntuforums.org/showthread.php?t=1152376)

I'm relatively new to nix but could this by chance be caused by an update we've all applied?

When you reboot your machine; does the POST screen hang (much) longer than normal like mine?

Has anyone removed the drive from the external enclosure (voiding their warranty) and attached inside the PC on SATA/PATA? I haven't tried it yet as I don't really want to do anything that may worsen my situation; before getting advice from someone more knowledgeable than myself.

woe is me!

---

