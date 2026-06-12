---
title: "Zip100 Drives and Floppy Disks in Gnome"
date: 2007-02-16
forum: Hardware &amp; Laptops
---

### Post by jourdanritchey on 2007-02-16
Ubuntu Edgy i386 flava installed:
Gnome Disk Mounter applet shows two Floppy Drives and one Zip (100) Drive
Machine actually has only one Floppy Drive and one Zip Drive

Solution 1: Deleted floppy entry in /etc/fstab

Now Gnome Disk Mounter applet shows one Floppy Drive and one Zip Drive (correct)
Interaction with applet to mount/unmount Floppy successful and as expected
Interaction with applet to mount/unmount Zip unsuccessful

Error Msg: "/dev/hdd4 does not exist"

Solution 2: Edit UDEV rules and add the line:
```
KERNEL=="hdd", SYMLINK+="hdd4"
```

Now Gnome Disk Mounter applet successfully mounts/unmounts Zip Drive

HOWEVER:
Click on icon for Zip Drive, select "mount"
Zip disk is mounted
A second Zip Drive icon appears in the Gnome Disk Mounter applet
Interaction with this second Zip icon mounts/unmounts the Zip disk
Interaction with the first Zip icon ejects the disk
Confusion strikes...

By this time I'm hacking away again at udev rules trying to figure out how to turn off detection of the Zip drive so that I can make a clean entry in fstab, which the gnome applet reads properly, but I'm thinking this might have to be done in the kernel (?).

If you've had any experience with this, please post something (I'm on a tangent  - keep me going).  Thanks!

---

### Post by jourdanritchey on 2007-02-16
Unsolved, it seems:
[https://launchpad.net/ubuntu/+source/nautilus/+bug/53251](https://launchpad.net/ubuntu/+source/nautilus/+bug/53251)

But if we find a way to turn off HAL's detection of the Zip Drive, a simple line in fstab would fix it nice.

---

### Post by jourdanritchey on 2007-02-16
in /etc/fstab:
```
/dev/hdd      /media/zip0         auto    rw,user,noauto,sync 0       0
```

works beautifully, except we now have three icons for one drive.  Ha ha.

---

### Post by jourdanritchey on 2007-02-16
OK, now I wait to hear from some of you in the Ubuntu community.

As stated, after my UDEV addition, the second icon for Zip Drive provides facility to open/unmount, while the first icon provides facility to mount and eject.  Both icons operate on the same drive.

NOTES:
Using the first icon to mount the Zip drive after it's already been mounted (using this same icon) produces an error.  Ejecting the Zip disk using this same first icon will successfully unmount and eject the disk.  Clicking 'Eject' again will actually attempt to eject it again.

The second Zip icon, which appears only after mounting the Zip disk using the first Zip icon, provides options to 'Open' (in Nautilus) and 'Unmount', both of which the applet performs successfully.

And finally, when I select 'Places > Computer' in Nautilus, I see the same two icons for the same one Zip drive.

ciao

---

### Post by beast2k on 2007-03-07
Has anyone found a solution to this "bug" both my floppy and zip drives are not working (they never did in 604 or 610). This is basic hardware and no distro should be having floppy drive and zip drive access problems these days.
Edit, update, myfloppy drive does work, it's just so slow to mount it (almost 4 min) that it seems like it doesn't work.

---

### Post by jourdanritchey on 2007-03-09
I've had no luck in Gnome as yet.  Outside of Gnome, UDEV rules and AutoFS work well.

---

