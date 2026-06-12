---
title: "External HD &amp; Ubuntu"
date: 2005-08-08
forum: Hardware &amp; Laptops
---

### Post by tekwerx on 2005-08-08
I have a 20GB external HD that I am wanting to use as a backup source for Linux.  It also houses about 10GB of Windows garbage I need to keep, as well.  It is formatted FAT32, and I would like to be able to WRITE to the drive under Ubuntu, and not just read.  How do I go about doing this?  Thanks in advance.

---

### Post by drummer on 2005-08-08
Just plug it in and go. It should mount automatically and you can then read and write to it. Linux can read and write to fat and fat32, it's only NTFS that can't be safely written to.

---

### Post by tekwerx on 2005-08-08
Really?  Every time Ive tried to write to it, its said that "You do not have permission to write to this folder."

Is there something Im missing?

---

### Post by wellery on 2005-08-08
[QUOTE=tekwerx]Really?  Every time Ive tried to write to it, its said that "You do not have permission to write to this folder."

Is there something Im missing?[/QUOTE]

It may not be giving access to the user you are using. By using sudo you probably can write to it.

Try this and see if it works

[http://www.ubuntuguide.org/#mountunmountfat](http://www.ubuntuguide.org/#mountunmountfat)

you can use this to work out the device eg /dev/hda

```
sudo fdisk -l
```

---

### Post by tekwerx on 2005-08-08
Says its already mounted...hm.  I also tried to unmount and said there wasnt anything to unmount.  I'll try rebooting...again...and see what happens.

---

### Post by tekwerx on 2005-08-08
Nothin.  Ive rebooted and still I get the error...hrm...anyone have any ideas?

---

### Post by wellery on 2005-08-09
are there any errors reported by dmesg?

---

### Post by tekwerx on 2005-08-09
Sorry, dont know what dmesg is...I can find out if I know.  :P

---

### Post by drummer on 2005-08-09
[QUOTE=tekwerx]Sorry, dont know what dmesg is...I can find out if I know.  :P[/QUOTE]
 turn on your external hdd then open a terminal (applications > system tools > Terminal) and type dmesg and enter. A long list of messages will come up, but you will probably only need to look at the stuff at the end, anything that refers to 'usb', 'your hard drive' and the like. and post any errors/suspect looking messages relating to them.

also, type 'man dmesg' for a description of dmesg.

---

