---
title: "[SOLVED] I need to mount my DVD as UDF"
date: 2008-07-21
forum: General Help
---

### Post by greenco on 2008-07-21
I am running Ubuntu 8.04 on a PC, that used to have Win XP on it. I am new to both Ubuntu and X-Plane, so I need some help. With my X-Plane DVD disk 1 in the DVD drive, I start the simulator and during the loading process I get a message that tells me that it found the disk, but it should be mounted as "UDF". I can not find anything that explains how to do this, in layman's terms, so I can fix it. I have run some sudo commands from the terminal, so that is not new to me. I saw several links that talked about running a "mount" command, but it did not say how to do it. 

The warning message says that I should do this:

unmount/dev/dvd && mkdir -p /mnt/dvd && mount -t udf/dev/dvd/mnt/dvd

I have no idea of what I need to do to carry this out. Is there another way and prehaps an easier method to accomplish this?
Thanks

---

### Post by Elfy on 2008-07-21
I assume that you typed rather than pasted that message - because I don't think iut would work as it is.

Try

```
umount /dev/dvd
mount -t udf /dev/dvd /media/dvd
```

That assumes that your dvd normally mounts as /media/dvd I think

---

### Post by damis648 on 2008-07-21
Try in terminal (Applications>Acessories>Terminal):
```
sudo umount /dev/dvd
#If that doesn't work, try:
sudo umount /dev/cdrom
sudo mkdir /media/dvd
sudo mount -t udf /dev/dvd /media/dvd
#And if that doesn't work, try:
sudo mount -t udf /dev/cdrom /media/dvd
```

---

### Post by greenco on 2008-07-21
Yes, frostpixie I copied that from a piece of paper so it is probably wrong. Here is a copy of my fstab for you to look at. I am not sure if I should use "CD" or "DVD" in the sudo statements.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0c03895c-cad9-44b1-9aed-813e4ef8e006 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1d5a822c-413b-48e2-a689-420433a0c246 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Thanks

The cdrom0 is for my cd r/w drive
The cdrom1 is for my DVD r/w drive

---

### Post by greenco on 2008-07-21
coleman@My-desktop:~$ sudo umount /dev/dvd
[sudo] password for coleman: 
damis648

This is the result I got when I tried your info.


coleman@My-desktop:~$ sudo mkdir /media/dvd
coleman@My-desktop:~$ sudo mount -t udf /dev/dvd /media/dvd
mount: block device /dev/scd1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

coleman@My-desktop:~$ sudo mount -t udf /dev/cdrom /media/dvd
mount: block device /dev/scd1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

coleman@My-desktop:~$

---

### Post by damis648 on 2008-07-21
> **greenco said:**
> coleman@My-desktop:~$ sudo umount /dev/dvd
[sudo] password for coleman: 
damis648

This is the result I got when I tried your info.


coleman@My-desktop:~$ sudo mkdir /media/dvd
coleman@My-desktop:~$ sudo mount -t udf /dev/dvd /media/dvd
mount: block device /dev/scd1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

coleman@My-desktop:~$ sudo mount -t udf /dev/cdrom /media/dvd
mount: block device /dev/scd1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

coleman@My-desktop:~$

Interesting.. try mounting with a capital UDF instead of lowercase udf.

---

### Post by Elfy on 2008-07-21
Try
```
sudo mount -t udf -o loop /dev/scd1 /media/cdrom1
```

---

### Post by mc4man on 2008-07-21
You might want to ck. your /dev links, many times /dev/dvd links to /dev/scd1 and /dev/dvd1 links to /dev/scd0

You might consider changing fstab as such
> /dev/scd0      /media/cdrom0   iso9660 user,noauto,exec,utf8 0       0
/dev/scd1      /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by greenco on 2008-07-21
frostpixie, here is the results of trying your new idea.

coleman@My-desktop:~$ sudo mount -t udf -o loop /dev/scd1 /media/cdrom1
[sudo] password for coleman: 
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

coleman@My-desktop:~$ 

I sure appreciate everyone's help.

mc4man, The properties for the DVD drive show it as cdrom1. I am a newbe and don't understand all of this code.

---

### Post by mc4man on 2008-07-21
Didn't notice you had a cdrw drive also
Try editing this line in fstab
/> dev/scd1 /media/cdrom1 iso9660 user,noauto,exec,utf8 0 0
to look like this
> /dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

```
gksudo gedit /etc/fstab
```

you might also run and post this to d. check something
```
sudo lshw -C disk
```

---

### Post by Vivaldi Gloria on 2008-07-21
I suggest you also try this. Press Alt+F2 and start

```
gksudo gedit /etc/fstab
```

and change the line

```
dev/scd1 /media/cdrom1 iso9660 user,noauto,exec,utf8 0 0
```

to

```
/dev/scd1 /media/cdrom1 auto user,noauto,exec,utf8 0 0 
```

Now save the file and restart your computer.

---

### Post by greenco on 2008-07-21
mc4man, here is what I got when I ran it.

coleman@My-desktop:~$ sudo lshw -C disk
  *-cdrom:0               
       description: CD-R/CD-RW writer
       product: CD-RW  CRX217E
       vendor: SONY
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1DS1
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: DVD writer
       product: DVD+-RW DVD8701
       vendor: PHILIPS
       physical id: 0.1.0
       bus info: scsi@4:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       logical name: /media/cdrom1
       version: 5D24
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom1
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted
  *-disk
       description: ATA Disk
       product: WDC WD2500JS-75M
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 03.0
       serial: WD-WMANK1077644
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=d0f4738c
  *-disk:0
       description: SCSI Disk
       product: CF Card       CF
       vendor: Samsung
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb
       version: 1.6E
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdb
  *-disk:1
       description: SCSI Disk
       product: MS Card       MS
       vendor: Samsung
       physical id: 0.0.1
       bus info: scsi@6:0.0.1
       logical name: /dev/sdc
       version: 1.6E
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdc
  *-disk:2
       description: SCSI Disk
       product: SD Card   MMC/SD
       vendor: Samsung
       physical id: 0.0.2
       bus info: scsi@6:0.0.2
       logical name: /dev/sdd
       version: 1.6E
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdd
  *-disk:3
       description: SCSI Disk
       product: SM/XD Card    SM
       vendor: Samsung
       physical id: 0.0.3
       bus info: scsi@6:0.0.3
       logical name: /dev/sde
       version: 1.6E
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sde
coleman@My-desktop:~$

---

### Post by greenco on 2008-07-21
Sorry vivaldi, but that did not help. I still get the same message when I start the program

---

### Post by Vivaldi Gloria on 2008-07-21
> **greenco said:**
> Sorry vivaldi, but that did not help. I still get the same message when I start the program

When you put the dvd in does a dvd icon appear on the desktop? Can you double click and see its contents?

---

### Post by greenco on 2008-07-21
In hopes that this will help I have placed a jpg file on my storage space, that shows the message I am getting. If you would copy this url and paste it in your browser you should be able to read it. What commands would I need to run, to do what it suggests. Would this be done using Terminal? 

[http://home.comcast.net/~flt-simmer/Mount-udf.jpg](http://home.comcast.net/~flt-simmer/Mount-udf.jpg)

Thanks

---

### Post by greenco on 2008-07-21
Yes Vivalda I can read it and the flight sim also finds it and runs for 20 or 30 minutes and then it stops and throws the message back at me. Look at the post I just did.

---

### Post by Vivaldi Gloria on 2008-07-21
> **greenco said:**
> Yes Vivalda I can read it and the flight sim also finds it and runs for 20 or 30 minutes and then it stops and throws the message back at me. Look at the post I just did.

First of all, keep the fstab as I told in the post #11. Restart your computer if you change it.

Put the dvd in. Wait the desktop icon to appear. Start a terminal & give the following sequence of commands. Only then start X-Plane.

```
sudo umount /dev/scd1
sudo mkdir -p /media/dvd
sudo mount -t udf /dev/scd1 /media/dvd
```

If this doesn't work then close X-Plane and take out the dvd. Put back the dvd in. Wait the icon to appear. Start a terminal & give the following set of commands. Then start X-Plane.

```
sudo umount /dev/scd1
sudo mkdir -p /mnt/dvd
sudo mount -t udf /dev/scd1 /mnt/dvd
```

If you get errors then copy and paste them here.

---

### Post by greenco on 2008-07-21
vivaldi, I got an error on both of the tests.
Here they are, the top one was from your first example and the second one was from your second one. It seems like something is write protected.

coleman@My-desktop:~$ sudo umount /dev/scd1
[sudo] password for coleman: 
coleman@My-desktop:~$ sudo mkdir -p /media/dvd
coleman@My-desktop:~$ sudo mount -t udf /dev/scd1 /media/dvd
mount: block device /dev/scd1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

coleman@My-desktop:~$ 

************************************

coleman@My-desktop:~$ sudo umount /dev/scd1
coleman@My-desktop:~$ 
coleman@My-desktop:~$ sudo mkdir -p /mnt/dvd
coleman@My-desktop:~$ sudo mount -t udf /dev/scd1 /mnt/dvd
mount: block device /dev/scd1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

coleman@My-desktop:~$

---

### Post by Vivaldi Gloria on 2008-07-21
> **greenco said:**
> vivaldi, I got an error on both of the tests.
Here they are, the top one was from your first example and the second one was from your second one. It seems like something is write protected.

It's write protected because it's a dvd. That's not a problem. The problem is here:

```
mount: wrong fs type, bad option, bad superblock on /dev/scd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I seached a bit and it seems that this is a common problem:

[http://ubuntuforums.org/showthread.php?t=650697](http://ubuntuforums.org/showthread.php?t=650697)

I don't know what you can do about it. There is a solution here:

[http://ubuntuforums.org/showthread.php?t=718744](http://ubuntuforums.org/showthread.php?t=718744)

But I don't know anything about it so I cannot comment on it.

---

### Post by greenco on 2008-07-21
Thank a lot for you help, vivaldi!

I will fire off an email to the Linux people at the X-Plane company and hope that they can help me.I can use the program like it is, but it is a pain in the bottom to keep the warning message.

---

### Post by zerothis on 2008-11-01
I had this problem, turned out to be a toasted CD-R. Bad disk. Tried another disk and it worked fine. So if any one else has this problem, this is one more solution that might help.

---

