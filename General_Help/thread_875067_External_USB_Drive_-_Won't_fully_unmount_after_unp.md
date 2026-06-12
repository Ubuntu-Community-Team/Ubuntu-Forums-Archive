---
title: "External USB Drive - Won't fully unmount after unplugged"
date: 2008-07-30
forum: General Help
---

### Post by rperrine on 2008-07-30
I Have an External USB Drive (NTFS),

When I unplug the drive it removes the folder icon from "/media" however if i do

/media# ls
ls: cannot access DRIVE 8: Input/output error
DRIVE 8

if i do a fdisk -l it reports the drive is gone...

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       47888   384660328+  83  Linux
/dev/sda2           47889       48641     6048472+   5  Extended
/dev/sda5           47889       48641     6048441   82  Linux swap / Solaris

if i try to remove the directory:
/media# rmdir *
rmdir: failed to remove `DRIVE 8': Device or resource busy

I check processes:
#ps -ax
7340 ?        Ss     1:26 /sbin/mount.ntfs-3g /dev/sdf1 /media/FOX DRIVE 8 -o rw,nosuid,nodev,uhelper=hal,locale=en_US.UTF-

Why is this being held in process? Why is it not being removed automatically?

Where is this being held in at? I have a script which runs and checks /media for content, its holding the script up. It only seems to happen to this BIG 400 Gig NTFS drive, my small USB thumb drives (4gb) work perfectly and remove themselves completely...

Please help! Urgent!

---

### Post by PGScooter on 2008-07-30
hi rperrine,

I am not sure if you know (I couldn't tell by your post), but unmounting should be done BEFORE unplugging. To unmount the device, use the following command: ```
umount
```

---

### Post by ajgreeny on 2008-07-30
I have the disk mounter applet on my panel, which adds a quick way to mount and unmount all hard disks and usb devices, including cameras, card readers, flash drives etc etc. with a single click.  It makes life very easy and is much more convenient than using the terminal and *umount* commands.
Give it a try.

---

### Post by ajgreeny on 2008-07-30
I have the Disk Mounter applet on my panel, which adds a quick way to mount and unmount all hard disks and usb devices, including cameras, card readers, flash drives etc etc. with a single click.  It makes life very easy and is much more convenient than using the terminal and *umount* commands.
Give it a try.

Sorry, a clone appeared after I tried to stop the previous post.  Please remove this second version.

---

### Post by rperrine on 2008-07-30
I've added "umount" to my script to auto-unmount the drive after it performs its functions. We'll see how that works after it finishes this run.

BUT - Where do you get that Disk Mounter program? - Actually is it "Disk Management" - get the error "user mount tool" - There are no filesystems which you are allowed to mount or unmount, contact your administrator.

---

### Post by ajgreeny on 2008-07-30
Right click in the panel and choose "Add to Panel" then Disk Mounter is in the list.

---

