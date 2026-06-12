---
title: "External Hard Drive Not Working"
date: 2010-04-23
forum: Hardware
---

### Post by dave2001 on 2010-04-23
I'm starting a thread here because I haven't been able to find a good solution on the forums/web, and because this seems to be an issue for a lot of people with external usb hard drives.

I have this issue in both my desktop running ubuntu 8.04 and my laptop running xubuntu 8.04.

I have an external USB hard drive, it shows up fine when connected, but when mounted, I have no write permission for the the main linux ext3 partition. The permissions tab on properties says the owner and group are root.  I tried using "storage device manager" and editing fstab manually to change ownership, but then when attempting to mount afterward I get "only root can mount ...." error message.  The drive also does not "eject" properly. I get an error when using the context menu command. Strangely, using the command line:
~$ sudo eject /dev/sdb
will properly eject all partitions on the drive. The vfat partion on the drive mounts fine with default settings. but it also has the eject issue.

I have the same eject error on my sansa fuze and it's SDHC card

The external USB hard drive is a WD 250GB, which I use for backups. I formatted this drive to have three primary partitions. The first is an NTFS partition for backing up my windows comp(I don't want to access this partition). The second is an EXT3 partition for backing up my two ubuntu comps. The third is a smaller vfat partition for data transfer between operating systems.  The drive was partioned using gparted.

I can post any diagnostics if someone will tell me what might be useful to them. Thanks for any advice.

---

### Post by deges on 2010-04-23
i confirm the same problem. here is the output of mount:

 /dev/sdb1 on /media/vdata type ext3 (rw,nosuid,nodev,uhelper=hal) 
/dev/sdb2 on /media/vencrypted type ext3 (rw,nosuid,nodev,uhelper=hal)  

fresh formated external usb hdd via gparted, ubuntu 8.10

---

### Post by srs5694 on 2010-04-23
Try:

```

sudo chmod 0777 /mount/point

```

where /mount/point is wherever the drive is mounted. If the disk already contains subdirectories, you may need to do the same to them, or do:

```

sudo chown -R yourusername: /mount/point

```

where yourusername is your Linux username.

---

### Post by dave2001 on 2010-04-24
srs5694, thanks for the suggestion. My hard drive is partially working now. Combining your advice with some other things helped.
 
I stumbled across something which helped immensely with problems on the laptop (xubuntu). There are two mount managers running with the Xcfe desktop. The Thunar file manager, and gnome-mount.  Apparently Thunar has bugs in this area and also doesn't play nice with gnome-mount. I disabled this feature of Thunar in by unchecking "volume management" in Applications-->Settings-->Settings Manager-->File Manager-->Advanced Tab.

 To resolve my permission my issues, I did the following, with the drive disconnected. I deleted the following: all /etc/fstab entries pertaining to the drive, a folder in /media which was the mount point of one of the partions on the drive, and some left-over information in the /media/.mtab file. (back up anything your changing).  This got rid of all the changes I made with the PySDM "storage device manager" attempting to resolve issues. Btw, this program just screwed things up even worse.  Then I reconnected my drive and used the command from srs5694 (with a -R added to make it recursive and avoid needing to manually change every folder on the partition).
```
sudo chmod -R 0777 /mount/point 
```
Almost there!

---

### Post by dave2001 on 2010-04-24
Forgot to mention what my remaining problem is.

The drive still does not eject properly from the laptop. Clicking eject in the context menu does not do everything it should. I get an "unable to eject" error message. Using this command gives no error message, but the problem below still occurs.```
sudo eject <device>
```
does not work without using sudo.

After clicking eject, or using command, the file system is "unmounted" from the media directory, but the icons for the drive re-appear on the desktop, the drive heads do not park, and the drive remains spinning. This causes me some concern about unplugging the drive. Before the previous fixes, the drive was remounted completely after eject, now it seems it is only partially remounted. I found this problem listed as a bug on launchpad, but no solution. I am still somewhat new to Ubuntu, forgive me if some of my terminology isn't technically correct.

---

### Post by dave2001 on 2010-04-25
Havn't figured out anything yet. If no one has a solution...Does anyone else have this problem? Perhaps if we look for similarities in our setup we can isolate a problem

---

