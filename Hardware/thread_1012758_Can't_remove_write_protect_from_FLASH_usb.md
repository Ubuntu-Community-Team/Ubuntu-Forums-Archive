---
title: "Can't remove write protect from FLASH usb"
date: 2008-12-16
forum: Hardware
---

### Post by tazza on 2008-12-16
hi there
i'm having problems with a usb device that was read-write but somehow has become read only. If I try to remove a file in the USB I get:
```

rm: cannot remove 'x.c': Read-only file system

```

It doesn't have any external switch or anything like that and hasn't gone back to being writable at any time.
 
I think that somehow it internally changed to read only. Is there any way to change it back?  Or is it internal and nothing can be done?

Here is the relevant output from dmesg:
```


[ 2902.781714] usb-storage: device found at 3
[ 2902.781722] usb-storage: waiting for device to settle before scanning
[ 2907.780229] usb-storage: device scan complete
[ 2907.781086] scsi 6:0:0:0: Direct-Access     FLASH    Drive AU_USB20   8.07 PQ: 0 ANSI: 2
[ 2907.810847] sd 6:0:0:0: [sdc] 4016128 512-byte hardware sectors (2056 MB)
[ 2907.811701] sd 6:0:0:0: [sdc] Write Protect is on
[ 2907.811708] sd 6:0:0:0: [sdc] Mode Sense: 03 00 80 00
[ 2907.811711] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 2907.815530] sd 6:0:0:0: [sdc] 4016128 512-byte hardware sectors (2056 MB)
[ 2907.816289] sd 6:0:0:0: [sdc] Write Protect is on
[ 2907.816295] sd 6:0:0:0: [sdc] Mode Sense: 03 00 80 00
[ 2907.816298] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 2907.816662]  sdc:
[ 2907.992254] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[ 2907.992523] sd 6:0:0:0: Attached scsi generic sg3 type 0

```

And this is its line in /etc/mtab:
```

/dev/sdc /media/disk vfat ro,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

```

I also tried writing similar things in fstab too to mount automatically with rw but this didn't work.

I tried remounting it a few times 
```

$ mount -o remount,rw /media/disk
$ mount -w -t vfat -o remount,rw /dev/sdc /media/disk

```

which gave this:
```

mount: block device /dev/sdc is write-protected, mounting read-only
mount: block device /dev/sdc is write-protected but explicit '-w' flag given


```

but still no change at all. 
Is this a problem I can fix? This happens on linux/mac/windows and I can't reformat it in windows.

Does anyone think that they can help?

---

### Post by pastalavista on 2008-12-16
I had that problem once and never learned why. I fixed my problem by reformatting the drive with gparted. I copied all the information off of it easily enough before I did though. If you don't have gparted (it comes included with a live CD) you can download it from add/remove programs (Gnome Partition Editor) or from the terminal ```
sudo apt-get install gparted
```

---

### Post by tazza on 2008-12-17
hey pastalavista thanks for the reply.
Unfortunately this still can't seem to make the USB device read-write:
```

sudo gparted /dev/sdc
...
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.

```

I'm wondering is it even possible to change the write permissions.
chmod and chown on /media/disk don't work either.

Does anyone have ANY idea of ANYTHING that might help?

---

### Post by bgerlich on 2008-12-17
Have you tried unmounting the volume with "sudo umount /dev/sdc1" afterwards "sudo gparted /dev/sdc"?

---

### Post by sharan01 on 2011-07-19
hi i have the same problem gparted is showing read only 
please help
[IMG]http://i.imgur.com/Nv0XP.png[/IMG]

---

### Post by MorrisseyJ on 2011-12-02
Hi, 

I was having the same problem until i realised that the USB device was simply locked - i.e. the hold switch was turned to 'on'.

Changed that and now i can manipulate the drive.

---

### Post by nothingspecial on 2011-12-02
Old thread.

Closed.

---

