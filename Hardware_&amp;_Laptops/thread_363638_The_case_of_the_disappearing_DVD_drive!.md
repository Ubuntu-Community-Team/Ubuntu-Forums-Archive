---
title: "The case of the disappearing DVD drive!"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by akajonesy on 2007-02-17
Having some weird problems with my dvd drive I need help with. It keeps disappearing on me.
Essentially, it won't mount. No idea why. It worked fine on first install, then a few weeks ago Ubuntu stopped seeing the drive, and just as suddenly started seeing it again. (original post here: [http://www.ubuntuforums.org/showthread.php?t=348729](http://www.ubuntuforums.org/showthread.php?t=348729))
Now it's gone again.
I am almost possitive it is related to updates, since this last dissappearance occured right after updating the latest kernel release.
At any rate, I can't use my DVD at all right now so I need help desperately.

fdisk -l gives this
> Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2433    19543041    7  HPFS/NTFS

Disk /dev/hdb: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2392    19213708+  83  Linux
/dev/hdb2            2393        2498      851445    5  Extended
/dev/hdb5            2393        2498      851413+  82  Linux swap / Solaris


my fstab reads: > # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=55dbb9b3-ed0a-43a2-93fd-9e5b5c757932 /               ext3    defaults,erro$
# /dev/hdb5
UUID=3ebf61e3-dba6-424b-a308-37c5f64ee69f none            swap    sw           $
/dev/hda1    /media/windows    ntfs-3g    defaults,locale=en_US.utf8    0    0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


mtab reads:> /dev/hdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-11-generic/volatile tmpfs rw 0 0
/dev/hda1 /media/windows fuse rw,nosuid,nodev,noatime,allow_other 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0


Can anyone help? I can't do the switch until I figure out how to keep this from happening again.
Thanks

---

### Post by Stemp on 2007-02-17
Show us the result of these commands :

```
ls /dev/hd* -l

ls /media/cd* -l
```

---

### Post by akajonesy on 2007-02-17
Hey Stemp. Thanks for helping me again. :D

/dev/hd* -l:
> brw-rw---- 1 root disk  3,  0 2007-02-17 02:49 /dev/hda
brw-rw---- 1 root disk  3,  1 2007-02-17 08:00 /dev/hda1
brw-rw---- 1 root disk  3, 64 2007-02-17 02:49 /dev/hdb
brw-rw---- 1 root disk  3, 65 2007-02-17 07:55 /dev/hdb1
brw-rw---- 1 root disk  3, 66 2007-02-17 02:49 /dev/hdb2
brw-rw---- 1 root disk  3, 69 2007-02-17 02:49 /dev/hdb5
brw-rw---- 1 root root 22,  0 2007-02-17 02:51 /dev/hdc


/media/cd* -l
> lrwxrwxrwx 1 root root    6 2007-01-21 16:20 /media/cdrom -> cdrom0


---

### Post by Stemp on 2007-02-17
> Hey Stemp. Thanks for helping me again. 

Hey akajonesy, I'm not helping again, it's the same problem :-P 

Your line : ***brw-rw---- 1 root root 22, 0 2007-02-17 02:51 /dev/hdc*** is strange, it should be root cdrom (user root, group cdrom)

So try :
```
sudo chown root:cdrom /dev/hdc
```

Then reboot to see if a /media/cdrom0 is created, if not edit you /etc/fstab and change cdrom0 to cdrom :
```
/dev/hdc **/media/cdrom** udf,iso9660 user,noauto 0 0
```

---

### Post by akajonesy on 2007-02-17
Hey Stemp:

All right, did both things, no change.

If I open up nautilus I can see an icon for the cdrw dvd drive in the main window (NOT in the 'places' window, only in the main (right-hand) window), along with the icon for the WINDOWS drive and the FILESYSTEM drive.
This is not new as it did it before (sometimes), but if I double click it doesn't do anything beyond a window telling me it's opening the CDR. This window remains until I click 'cancel' but nothing happens.

I will now throw out a bunch of stuff that may or may not be relevant (just in case).

I think it may be relevant, but if there happens to be a disc in the drive when I boot it hangs. Just stops dead. It eventually boots, but it takes a very long time. If I take the disc out it immediately continues to boot (accordingly if I boot without a disc it boots at normal speed). 

I loaded into Nautilus under GKSUDO a couple times to see if I could change settings on cdrom0 and I got the following error message 
> (nautilus:4942): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

Then it opened Nautilus (seemed to work fine).

---

### Post by Stemp on 2007-02-18
Check this post : [http://ubuntuforums.org/showthread.php?t=349325](http://ubuntuforums.org/showthread.php?t=349325)

---

### Post by akajonesy on 2007-02-18
ok, Tried changing permissions but I'm not really sure what I'm doing. I copied his entries but still no dice.
Any links to documentation on how permissions work? (What do I need to have set to what?) 
The "Help" file wasn't very detailed.
I tried logging into nautilus under sudo and changing permissions there, but I'm uncertain as to what I'm supposed to change them TO.

---

### Post by Stemp on 2007-02-20
> I tried logging into nautilus under sudo and changing permissions there, but I'm uncertain as to what I'm supposed to change them TO.

Just do : 

```
sudo chmod 4755 /bin/mount
```

And sorry I don't know a tutorial in English concerning the permissions.

---

### Post by akajonesy on 2007-02-20
Yah tried that. Ah well. The hell with it. Ill just reinstall, maybe use the new Feisty Herd RC. Maybe that will work. If not... oh well.

Thanks for your time and help though. It was greatly appreciated. :D

---

