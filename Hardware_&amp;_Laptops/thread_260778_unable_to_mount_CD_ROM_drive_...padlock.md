---
title: "unable to mount CD ROM drive ...padlock ??"
date: 2006-09-19
forum: Hardware &amp; Laptops
---

### Post by alanmzifa on 2006-09-19
Hi, as the title says I can't mount my laptop's external CD ROM drive (it's an old Dell Latitude). 

I've just purchased the CD ROM and it's proprietary lead and presume it's working OK but it's not possible to connect it to anything else to find out. A CD icon shows up under My Computer but I can click through to see files and properties says it has no data.

I've tried to search the forums for something to help me but haven't found much and what I've found I've tried.

I've dragged the CD ROM icon to desktop just to make it easier to work with and a padlock shows beside the icon which must have some significance.

Here is the terminal output of the mount instruction...


> joyce@joyce-desktop:~$ sudo mount /media/cdrom0
Password:
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

would someone like to give me a hand to get things up and running please?

thanks

---

### Post by jd65pl on 2006-09-19
It may seem trivial but you will need a cd in the drive in order to mount it.

Do you have a cd in the drive?

---

### Post by alanmzifa on 2006-09-19
yeah, currently I have an audio CD in the drawer. Funnily when I checked and closed the drawer sound juicer window came up and listed the tracks but it won't play or allow me to browse the folder. 

A separate "Audio CD" icon has appeared on the desktop now. But still no joy.

---

### Post by alanmzifa on 2006-09-20
polite bump

---

### Post by jd65pl on 2006-09-20
Is the cd drive listed in the folder /media?

What happens when you try to open the "audio cd" folder?

J

---

### Post by alanmzifa on 2006-09-20
Got rid of the padlock....permissions. Won't have to ask that one again.
[B]
Screenshots below.[/B]

> 
Is the cd drive listed in the folder /media?

yes, I have cdrom and cdrom0 listed. (I have only 1 cdrom, external)

> What happens when you try to open the "audio cd" folder?


When I click on the desktop icon for audio cd - nothing.

When I open and close the cd drawer sound-juicer opens and lists the tracks but I can't get anything to play and I have to force-close sound-juicer.

I've tried data cdrws too. Show no data.

---

### Post by alanmzifa on 2006-09-21
polite *laptop-forum-like* bump

---

### Post by nathanbriggs on 2006-09-22
cdrom0 is the device, cdrom should just be a sym link to it.

can you ls the directory /dev/cdrom?
have you tried a data disk?
are you sudo the mount command?
what does your line in /etc/fstab look like that contains
/dev/cdrom0?
Will try and get it working for you

---

### Post by alanmzifa on 2006-09-23
thanks for your offer of help.

I'm not sure if I understand everything you asked, jargon's all still quite new to me.
[I]
can you ls the directory /dev/cdrom?[/I]

> joyce@joyce-desktop:~$ ls /dev/cdrom
/dev/cdrom

*have you tried a data disk?*
> 
yes, doesn't seem to read anything at all from a data disc
[I]
are you sudo the mount command?[/I]

> yes.here's the output.

joyce@joyce-desktop:~$ sudo mount /media/cdrom0
mount: No medium found
joyce@joyce-desktop:~$ sudo mount /media/cdrom0
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

joyce@joyce-desktop:~$

what does your line in /etc/fstab look like that contains
/dev/cdrom0?

> this is all of the text of that file...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0





Did I understand the instructions correctly and do the answers point to anything obvious?

thanks

---

### Post by ty13 on 2006-09-23
Try to chmod it, if it doesn't work, chroot to your username.

|sudo chmod /dev/hdc 777|
|sudo chroot /dev/hdc yourusername|

---

### Post by alanmzifa on 2006-09-24
I've tried this...and here is the output.

What does chmod do anyway?


> joyce@joyce-desktop:~$ | sudo chmod /dev/hdc 777|
bash: syntax error near unexpected token `|'
joyce@joyce-desktop:~$ |sudo chroot/dev/hdc joyce
bash: syntax error near unexpected token `|'
joyce@joyce-desktop:~$


Perhaps there's a space or something missing or does this spell bad news?

---

### Post by alanmzifa on 2006-09-25
polite bump

---

