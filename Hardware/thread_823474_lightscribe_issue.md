---
title: "lightscribe issue"
date: 2008-06-09
forum: Hardware
---

### Post by mo.reina on 2008-06-09
hi,

i'm running xubuntu 8.04, and i've tried installing the lightscribe drivers and the 4l and simple labeler programs.  

i followed this guide:
[http://howtopenguin.blogspot.com/2008/05/how-to-install-lightscribe-software-on.html]("http://howtopenguin.blogspot.com/2008/05/how-to-install-lightscribe-software-on.html")

this is the output i get when i run 4L-cli enumerate:

```
mo@mo-laptop:~$ 4L-cli enumerate
Using /etc/lightscribe.rc
mo@mo-laptop:~$ 

```

this is the output of dpkg -s lightscribe:

```
mo@mo-laptop:~$ dpkg -s lightscribe
Package: lightscribe
Status: install ok installed
Maintainer: Hewlett-Packard Company
Architecture: i386
Version: 1.12.37.1
Description: LightScribe System Software
 Copyright: 2005 by Hewlett-Packard Company, All Rights Reserved.
 LightScribe System Software
mo@mo-laptop:~$ 

```

my laptop is an asus f8SR, lightscribe enabled, or so it says in the specs anyway.

any help on this?

---

### Post by mo.reina on 2008-06-09
dmesg outputs this:

```
mo@mo-laptop:/dev$ dmesg | grep -e sr0
[   18.290001] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   18.290050] sr 3:0:0:0: Attached scsi CD-ROM sr0

```

---

### Post by The Cosmic Hobo on 2008-06-09
Are you expecting to see something other than the output you get? If I remember correctly, HP created the Lightscribe technology and I think they're responsible for the software or at least the licence on it.

Does your drive work as you expect it to? What's the exact nature of the problem you're experiencing?

---

### Post by mo.reina on 2008-06-10
the labeling software, both lacie and simple labeler, cannot see the lightscribe drive.

from other posts, the expected output of the command 4L-cli enumerate is supposed to look something like this:

```
[joao@localhost dev]$ 4L-cli enumerate
Using /etc/lightscribe.rc
Drive path: /dev/sr0
Usable: 1
Full name: TSSTcorp - CD/DVDW SH-S162L - LC01
Model: CD/DVDW SH-S162L
Manufacturer: TSSTcorp
Capabilities: monochrome
Drive inner radius: 21700
Drive outer radius: 59000

```

instead of just:
```
[joao@localhost dev]$ 4L-cli enumerate
Using /etc/lightscribe.rc
[joao@localhost dev]$
```

---

### Post by The Cosmic Hobo on 2008-06-10
Is there anything in the documentation about telling it which path the lightscribe drive is mounted on?

---

### Post by mo.reina on 2008-06-10
from [http://www.linux.com/feature/118705]("http://www.linux.com/feature/118705")

> If, as I did, you have trouble with either piece of software recognizing your LightScribe-capable drive, try adding the following lines to the end of the configuration file /etc/lightscribe.rc:

DriveEnumeration=false;
CDROMDevicePath=drivepath;

however even when i added that, it didn't make a difference.  the path to my drive is /dev/scd0, or there is /dev/sr0, which is a link to /dev/scd0.  not quite sure what to do anymore.

---

### Post by The Cosmic Hobo on 2008-06-10
Sorry, we've exhausted my technical know-how, too. Hope someone else comes along who knows more, as I'm planning on putting a Lightscribe drive in my new PC.

---

### Post by cha-os on 2008-08-05
Hi,

this is exactly my problem!!! Is there any solution out there?? Please help us...

@mo.reina: Did you solved the problem? I don't what to do anymore:confused:

---

### Post by reylafo on 2008-09-17
Burned my first label after trying all sugestions, just;

Run the program as super user.
sudo
gksudo

This works for "simplelabeler" and "4L-gui"

---

