---
title: "[SOLVED] Can't automount USB (UUID=0000-0000)"
date: 2007-09-07
forum: Hardware &amp; Laptops
---

### Post by ruberad on 2007-09-07
Hi, I'm trying to get Gutsy Tribe 4 (I had to go beyond Fiesty to recognize my new motherboard (Intel DG33BU)) to recognize and automount devices plugged into USB.

My .mp3 player, my thumb drive, and my digital camera all have the same problem -- they don't auto-mount when I plug them in.  System>Removable Drives and Media>Storage has all the boxes checked.

I have created an fstab entry for my .mp3 player:

LABEL=RCA_LYRA /media/mp3 vfat user,owner 0 2

so I can mount/umount it manually from the command-line, but it doesn't happen automagically like the internets tell me I should expect.  (And even when it is mounted, Gpodder doesn't think it's mounted)

I have run blkid, and for all three of the USB devices, it lists what appears to be a pathological UUID of "0000-0000" (which is why I put the LABEL in the fstab instead of UUID).  

When I plug in the mp3 player, here is what dmesg says:

[ 3726.543220] usb 8-5: new high speed USB device using ehci_hcd and address 6
[ 3726.676421] usb 8-5: configuration #1 chosen from 1 choice
[ 3726.676892] scsi11 : SCSI emulation for USB Mass Storage devices
[ 3726.676963] usb-storage: device found at 6
[ 3726.676965] usb-storage: waiting for device to settle before scanning
[ 3731.665498] usb-storage: device scan complete
[ 3731.666001] scsi 11:0:0:0: Direct-Access     Thomson  Lyra_MPR2452_US  0100 PQ: 0 ANSI: 4
[ 3731.667349] sd 11:0:0:0: [sdc] 2039552 512-byte hardware sectors (1044 MB)
[ 3731.667963] sd 11:0:0:0: [sdc] Write Protect is off
[ 3731.667968] sd 11:0:0:0: [sdc] Mode Sense: 38 00 00 00
[ 3731.667971] sd 11:0:0:0: [sdc] Assuming drive cache: write through
[ 3731.669961] sd 11:0:0:0: [sdc] 2039552 512-byte hardware sectors (1044 MB)
[ 3731.670586] sd 11:0:0:0: [sdc] Write Protect is off
[ 3731.670590] sd 11:0:0:0: [sdc] Mode Sense: 38 00 00 00
[ 3731.670593] sd 11:0:0:0: [sdc] Assuming drive cache: write through
[ 3731.670597]  sdc: sdc1
[ 3731.678652] sd 11:0:0:0: [sdc] Attached SCSI removable disk
[ 3731.678704] sd 11:0:0:0: Attached scsi generic sg3 type 0

I just today (9/7/2007) did an overall update, which took quite a long time, so it must have been doing something!  Still no joy, though.

Any help?  Is Ubuntu supposed to recognize and automount and open (in Nautilus, or gnome-volume-manager-gthumb) out-of-the-box, or is more stuff needed to automount USB devices?

thx,

r

---

### Post by ruberad on 2007-09-08
BTW, I hot-plugged my .mp3 player and flash drive into my old computer, which is running Fiesty, and  both of them worked great, automounting (with no entries in fstab), appearing on the desktop, and raising an app (Rhythmbox or Nautilus).   However, on my old computer, "blkid" revealed that my .mp3 player still reports a UUID of "0000-0000".

So the problem is not with my USB devices, but either with Gutsy, or with my new computer...

---

### Post by Peterix on 2007-09-10
Try deleting /usr/share/hal/fdi/policy/gparted-disable-automount.fdi
(I found that in [[COLOR="DarkOrange"]_this thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=531953").)
It seems to be some kind of lock file created when using gparted that isn't automatically removed when it crashes.

---

### Post by ruberad on 2007-09-13
Thx so much!  Deleting that file did the trick!  I have marked this thread as solved.

---

### Post by devliljohn on 2007-10-14
auto mounting ins't working for me either but i don't have the file /usr/share/hal/fdi/policy/gparted-disable-automount.fdi any ideas?

---

