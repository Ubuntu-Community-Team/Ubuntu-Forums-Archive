---
title: "CD-ROM problems with kernel updates"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by Reducer on 2005-07-05
Being using Ubuntu since the beginning of the year, and I have a recurring problem.  I'm not sure exactly where the problem lies, so I'm sorry if this is a bit vague.  Please let me know what more information you need.

I have a Pioneer DVD-RW A104 drive.  When I updated from Warty to Hoary it worked fine.  When the first kernel update came out, it stopped working.  When the second kernel update came out, it started working again.  When the latest kernel update came out (last week or the week before) it's stopped working again.

When I say stopped working, I mean that when I put a CD in the drive, it doesn't pop-up on my desktop.  Gnome doesn't launch any blank CD dialog boxes when I put a blank CD in.  When I put an audio CD in to tip using Grip, I get an "Can't initialize device /dev/hda" error.

Any ideas?

Thanks.

Jason

---

### Post by petehall on 2005-07-05
Is the drive really at /dev/hda? Normally the first hard disk drive is there.

If you go into the Device Manager (System > Administration) you should be able to hunt down the drive and find out where it is. If it's not /dev/hda then try updating the CD-ROM device field in Grip and ripping again.

If it IS at /dev/hda then try ```
eject /dev/hda
``` and let us know if the tray pops out.

---

### Post by Reducer on 2005-07-05
/dev/hda is the CD drive.  I have /dev/sda for my hard disk.  Typing 'eject /dev/hda' does eject the drive.

---

### Post by petehall on 2005-07-06
Is there anything suspicious in the device manager? Are you able to mount the cd from the command line?

---

### Post by Reducer on 2005-07-06
Everything looks fine in Device Manager.  I *can* mount stuff manually, then the icon *cdrom0* shows up on the desktop, instead of the CD label.

Thanks for your help in trying to figure this out.

Jason

---

### Post by moment on 2005-07-06
can you give the output of the dmesg right after you load a cd? something like:
[PHP]dmesg | tail -10[/PHP]

---

