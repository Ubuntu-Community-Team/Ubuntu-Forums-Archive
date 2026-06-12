---
title: "Kubuntu: Problem with HAL or pmount or ntfs-3g"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by json684 on 2007-04-27
I have looked through the ubuntu forums and kubuntu forums and have found problems that are close to the same but not quite. So I have decided to start a new thread and hope it helps.

The Problem: In Kubuntu Feisty clean install my USB LaCie 160GB HD is not automounted, nor can a regular user mount it with ntfs-3g. I have install ntfs-3g and ntfs-config. I set both internal and external drives to be writeable. My WinXP partition mounts with ntfs-3g fine and dandy using fstab.

More Symptoms: Once plugged in a window pops up asking if I wish to open the folder or what not. I can try any of the options and the window goes away but the disk is not mounted. So I can then go into konqueror and to the Services tab on the side. I can click on the USB disk that shows up under Storage Media. I can click on it and I receive:
(Window Title: Error - Konqueror)
```
hal-storage-removable-mount-all-options refused uid 1000
```
If I try instead to right click on the drive and click mount I receive:
(Window Title: Error - kio_media_mounthelper)
```
hal-storage-removable-mount-all-options refused uid 1000
```

Next I tried using pmount-hal:
```
pmount-hal /dev/sdb1
```
and get this spit out:
```
libhal-storage.c 1401 : INFO: called LIBHAL_FREE_DBUS_ERROR but dbusError was no                     t set.
process 9726: Applications must not close shared connections - see dbus_connecti                     on_close() docs. This is a bug in the application.
```
And I have read access but not write access. A glance at mtab reveals (last two lines):
```
/dev/disk/by-uuid/04F8E5B6F8E5A5E0 /media/winXP fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sdb1 /media/Arrowboxed ntfs rw,noexec,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
```
Here the first line is my internal WinXP partition and the second line is my external HD. And it looks like the filesystem for my XP partition is fuseblk, and ntfs for the USB HD. So the next idea is to use the -t option in pmount to specify I want to use ntfs-3g. And I use:
```
pmount-hal /dev/sdb1 -t ntfs-3g
```
And this results in:
```
libhal-storage.c 1401 : INFO: called LIBHAL_FREE_DBUS_ERROR but dbusError was not set.
process 9811: Applications must not close shared connections - see dbus_connection_close() docs. This is a bug in the application.
Error: invalid file system name 'ntfs-3g'
Error: could not execute pmount
```
And indeed it does not mount. So I figure okay, lets try just mount:
```
sudo mount /dev/sdb1 /media/sdb1
```
And it is mounted with read access only for root only. And again mtab has:
```
/dev/disk/by-uuid/04F8E5B6F8E5A5E0 /media/winXP fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sdb1 /media/sdb1 ntfs rw 0 0
```
Which appears to mean that it is mounted with the old ntfs driver. So it's back to unmounting and trying to specify ntfs-3g with mount:
```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
```
And the HD is now mounted with read and write for everyone. And mtab reads:
```
/dev/disk/by-uuid/04F8E5B6F8E5A5E0 /media/winXP fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sdb1 /media/sdb1 fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
```
And now we have both the internal and external using fuseblk. So in my limited knowledge it seems that maybe hal isn't recognizing the drive as ntfs-3g when I try to use pmount. I opened up kde-hal-device-manager and navigate to the external HD and under the advanced tab I see it has the property
```
volume.fstype       strlist      ntfs-3g
```
The property was checked while the device was unmounted so I don't think it was dependent on me mounting it as ntfs-3g. And now we are at the end of my skillset. It seems that some part is broken in how the drive is automounted. I have no idea what though. And assuming kubuntu uses pmount to automount usb devices it seems, to me at least, that something is not configured right with it. As a final note when I plug in my ipod it mounts fine, but it is formatted in fat32 and uses vfat to mount it according to kde-hal-device-manager and mtab. So please help me out if you can. I don't know what else to do. I do understand that I could add a line to fstab, but I am plugging and unplugging the drive quite often. And I think it is important to try to track down what is actually wrong, not just avoid the problem.

---

### Post by capdog on 2007-04-27
I have the same problem. The Kubuntu window pops up with the list of actions (open in new window, etc) but nothing happens when I choose an option.

I have to mount my external USB drive manually. It is an NTFS drive, 300 gigs, Maxtor OneTouch II.

My IPODs also seem to hotplug / automount perfectly!

I hope someone in the know can resolve this! :(

---

### Post by EyeOfRa on 2007-04-28
I'm having the exact same problem with my Seagate 250GB drive.  I previously tried the last test release of Ubuntu and Gnome automounted just fine.  But I really want KDE.

---

### Post by axl55aa on 2007-04-28
the previous version of Kubuntu worked fine with post-installed ntfs-3g from deb ..  so it's problably a glitch that will soon be fixed ...
Anyway, you can always make an entry in /etc/fstab and mount as root

---

### Post by mattyp1 on 2007-04-29
Same problem here with KDE Feisty. Works very well in Gnome, with the exception of having to "eject" manually. For now I will continue to mount manually. The problem is people like my parents can't be bothered with the manual work around. Hopefully someone will find a fix soon, maybe it's a KDE thing (not K ubuntu).

---

### Post by d3athp3nguin on 2007-06-03
Same problems here- it must be an NTFS thing, because all my usb sticks work fine and dandy...

What also puzzles me is that the windows ntfs partition on my hard drive automounts no problem.  This only seems to impede access to my external hard drive, which (I dont think) is using any kind of new NTFS format...

---

### Post by json684 on 2007-06-03
I fixed my problem by choosing looking at the properties of the drive and unchecking "mount as user". Sorry for not putting it in this thread, added it to another, but failed to update this thread. Not sure why this works, but it does.

---

### Post by KhaaL on 2007-09-13
Whoa, unchecking that does indeed fix the problem... thanks for providing a solution to this annoying problem! :)

---

### Post by asiersanmi on 2007-10-19
Thanks for all, I'm new in this world, I've installed Kubuntu for first today and i have the same problem.

Regards

---

### Post by mikyt on 2007-10-31
Unchecking "mount as user" works for me too.
However this obviously is not the right behaviour.
Did anyone file a bug report to launchpad? I think it should be done...

---

### Post by dinji on 2007-11-06
um... setting Konqueror to "mount as user" was actually sort of sane from the linux permissions methodology, NTFS is just not very linux like in its permissions use. Still i have had to remember this stupid option in three different installs so far, spaced many months apart, so i definately understand the frustration... maybe the gui(konqueror) should allow the mount program to set default for "mount as"?

---

### Post by pollux71 on 2007-11-17
I found a solution that works fine for me with all my USB Harddisk with NTFS partitions.
Just delete two line the the following file:
```
/usr/share/hal/fdi/policy/10osvendor/20-storage-methods.fdi
```
Open this file as root, then delete the following two lines (line #219, 220):
```

	  <append key="volume.mount.valid_options" type="strlist">uid=</append>
	  <append key="volume.mount.valid_options" type="strlist">gid=</append>

```

Hope it will work for you as well.
Greetings from China :)

Pollux71

---

### Post by tachikoma1 on 2007-11-18
> **json684 said:**
> I fixed my problem by choosing looking at the properties of the drive and unchecking "mount as user". Sorry for not putting it in this thread, added it to another, but failed to update this thread. Not sure why this works, but it does.

Many thanks! I'm a relative newbie to Ubuntu and a *real* newbie to Kubuntu...but I like KDE! Was frustrating not to be able to mount my external NTFS volume with all my music on it, and now I can ~ Thanks Again!

---

