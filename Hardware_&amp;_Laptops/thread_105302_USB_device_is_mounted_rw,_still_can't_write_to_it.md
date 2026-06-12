---
title: "USB device is mounted rw, still can't write to it"
date: 2005-12-18
forum: Hardware &amp; Laptops
---

### Post by ubuntuuser on 2005-12-18
Hi. I am using an USB card reader for my SD and multimedia cards (MMC). When I plug the reader on my USb hub, ubuntu autmatically mounts the drive and I can read the data.
When I type mount at the terminal I get
```
/dev/sda1 on /media/usbdisk type vfat (**[COLOR="Red"]rw[/COLOR]**,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)

```
Even if I do a ```
sudo cp file /media/usbdisk
``` I only get an error saying the file system is read-only.

How can I get write access to it. I know it worked a while ago, but not anymore. Furthermore, How and where can I specify the default mount options ubuntu uses, like uid and gid?

---

### Post by aysiu on 2005-12-18
Can you try this?
Plug in your media card.
Then type these exact commands in the terminal:
```
sudo umount /media/usbdisk
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Then see if there's a line with /dev/sda1 in it. If so, replace it with this one ```
/dev/sda1 /media/usbdisk vfat umask=000  0  0
``` Save (control-x), confirm (y), and exit (Enter). ```
sudo mount -a
``` Then go to /media/usbdisk and see if it's read/write.

---

### Post by ubuntuuser on 2005-12-18
Thanks for the tip. I tried it, but it didn't work. And anyway, I am using a lot of different devices and switch them regularly. Ubuntu assigns each of them a different folder under /media, which I find quite convenient. With this line, every sda1 would be mounted to /media/usbdisk.
By the way, my external firewire hdd, which is sdb at the moment, is writeable, I just tried it.

---

### Post by greenway on 2005-12-18
Hi there, 

I'm experiencing the same trouble with a friends USB thumbstick. I checked the file system and it turned out to be FAT16. What about your SD/MMC cards? Is the filesystem FAT16 or FAT32?

Does anybody know if it's normal for FAT16 to give problems with Linux?

---

### Post by ubuntuuser on 2005-12-18
The FS on the card is FAT32. I just plugged in another USB stick and I was able to write on it. I'll check the SD card, maybe it's damaged or the filesystem is corrupted somehow. although it works perfectly in my Pocket PC.

---

### Post by jliedeka on 2005-12-19
Can you give us the output of ls -l for your device? E.g. ls -l /media/usbdrive

---

### Post by ubuntumaneh on 2005-12-19
I have a similar problem today (maybe it is something with stars ;)) ). I plug in a mp3 player from a cousin which I was willing to use as a pendisk to carry some files. It was mounted ok, but I could not write anything, only read. When I typed ls -l (or ll ), instead of my name in permitions it was written root root. Bad sign.

---

### Post by ubuntumaneh on 2005-12-19
I solved my problem. I tried different filesystems type. At first, it was automatically mounted as usbfs, and even so it was saying it was rw, I could't get it work for writing. I umounted it and tried it with others. For my luck it worked with vfat. It did't with fat. ANyway Im not expert with this usb sticks and mp3 players. But It brand mount them in different filesystems.

---

### Post by ubuntuuser on 2005-12-20
I did a scandisk and defrag under Windows after fsck found errors but didn't correct them. Now the card mounts rw and is indeed writable.

---

### Post by Domie on 2005-12-20
[QUOTE=ubuntuuser]Hi. I am using an USB card reader for my SD and multimedia cards (MMC). When I plug the reader on my USb hub, ubuntu autmatically mounts the drive and I can read the data.
When I type mount at the terminal I get
```
/dev/sda1 on /media/usbdisk type vfat (**[COLOR="Red"]rw[/COLOR]**,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)

```
Even if I do a ```
sudo cp file /media/usbdisk
``` I only get an error saying the file system is read-only.

How can I get write access to it. I know it worked a while ago, but not anymore. Furthermore, How and where can I specify the default mount options ubuntu uses, like uid and gid?[/QUOTE]

Try to change the setting to umask=0000

---

### Post by ubuntuuser on 2005-12-20
[QUOTE=Domie]Try to change the setting to umask=0000[/QUOTE]
Well, that just leads to my second, still unanswered question:

As ubuntu sets these values, like umask, to some default settings, where can I change these defaults? I indeed would like to set umask to 000, but I don't know where since 077 is set automatically. Does anybody here know where to change this?

---

### Post by jliedeka on 2005-12-20
/etc/profile sets the umask to 022 on my machine.   I don't know where your 077 is coming from.

---

### Post by ubuntuuser on 2005-12-21
[QUOTE=jliedeka][COLOR="Red"]/etc/profile[/COLOR] sets the umask to 022 on my machine.   I don't know where your 077 is coming from.[/QUOTE]
I must admit I don't understand what this file is for, but it here sets a umask to 022, too. So I just guess this is not the file I'm looking for.

---

### Post by jliedeka on 2005-12-21
I forgot about the umask=077 in your fstab.  Since you were using uid=1000 and gid=1000, that shouldn't matter.  That is, if you are trying to write to the usb device as the first user you created at install time.

Also, if the file system is read/write, root should always be able to write to it.  If not, something is wrong.  Try mounting the device and doing a:

cat /etc/mtab

That should show you what is mounted and with what options.  You can at least verify that the device is being mounted the way it is supposed to.

---

### Post by ubuntuuser on 2005-12-22
[QUOTE=jliedeka]I forgot about the umask=077 in your fstab.  Since you were using uid=1000 and gid=1000, that shouldn't matter.  That is, if you are trying to write to the usb device as the first user you created at install time.

Also, if the file system is read/write, root should always be able to write to it.  If not, something is wrong.  Try mounting the device and doing a:

cat /etc/mtab

That should show you what is mounted and with what options.  You can at least verify that the device is being mounted the way it is supposed to.[/QUOTE]
The  device is writable again, must have been a corrupt filesystem, but scandisk fixed it (fsck wouldn't correct it, see also my last post on page 1). Also, root wasn't allowed to write.
Anyway. the uid and gid were set by ubuntu, I don't have a standard entry in my fstab for this device. I think the device discovery is handled by the hal daemon, right? Where can I set the defualt values (uid, gid, rw/ro etc.) for removable devices like the card reader or my external hdds? There must be a config file somewhere, but I wasn't able to find it.

---

