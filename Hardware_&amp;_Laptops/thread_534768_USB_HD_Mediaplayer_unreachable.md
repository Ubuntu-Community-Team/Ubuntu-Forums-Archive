---
title: "USB HD Mediaplayer unreachable"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by loza on 2007-08-25
Hi All

I've done something really dumb! :confused:

I plugged in a USB mediaplayer which has a IDE harddisk which automounted and I was able to read the contents of the drive.

I noticed I could not write to the drive so from the desktop I selected 'properties' and selected 'volume' and  entered the following in mount point 'media-player', file system 'ntfs' and in mount options I put gid=0.

Now I cannot access or read the drive. I know its the gid=0 stopping me but I do not know how to get rid of this option as I cannot see the 'volume' tab.

My mtab looks like this:

/dev/sdb1 /media/media-player ntfs rw,noexec,nosuid,nodev,gid=0 0 0

I had a look in mtab and tried deleting the entry for the mediaplayer but when I reboot and plug the mediaplayer back into the computer, the system recognizes the device and puts the same line back into mtab.

Any help would be very appreciated!
Thanks in advance
loza

---

### Post by loza on 2007-08-25
I have just sussed it! I have just come across the 'configuration editor' and I have just deleted the key with gid=0 and everything is now working! Linux rocks! :guitar:

---

### Post by Gary.M on 2007-08-25
Also it is the file /etc/fstab that you need to edit if you want to affect the mounting of drives at boot. Search the forums for info on ntfs-3g if you want read-write access too. Your fstab entry would have ntfs-3g in it then to replace the ntfs. You need to use synaptic or whatever to install ntfs-3g first though.

---

### Post by loza on 2007-08-25
Thank you for the pointers GaryM!

I'm going to give that a go tomorrow after I have recovered from the excitement of today!

I wonder if I can treat my usb pendrive the same and edit the fstab to allow read/write access to that too!

loza

---

