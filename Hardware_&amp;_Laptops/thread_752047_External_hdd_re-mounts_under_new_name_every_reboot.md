---
title: "External hdd re-mounts under new name every reboot"
date: 2008-04-11
forum: Hardware &amp; Laptops
---

### Post by lebear on 2008-04-11
I'm having a problem that started after a kernel upgrade, when I rebooted the loading screen stuck and my external USB hdd seemed to be the problem, så I unplugged it and Ubuntu started.

Now, every time I reboot there's a new folder under /media, like this:

[X]External_
[X]External__
[X]External___
[   ]External____

with the X indicating that the old folder is undreadable, the last one works fine but this is annoying.

Anyone help would be appreciated

---

### Post by bobhenz on 2008-04-12
Your /etc/fstab is what controls where your HDDs mount at boot up.

It would probably be useful if you posted the contents of your /etc/fstab to this forum...

---

### Post by lebear on 2008-04-12
Alright, here's what it says:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=acee46fe-a69b-42aa-b267-f817ac790922 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=ef4926d2-7491-48d7-af3b-4c03544346ad /boot           ext2    defaults        0       2
# /dev/sda1
UUID=0E4E-05CE  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=09C5-770E  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=100CFB790CFB57E4 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=06511b8e-05a4-440e-ab72-7b11313a7ea7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

I'm quite new to Linux, but I guess the problem is "errors=remount-ro 0 " ?

---

### Post by lebear on 2008-04-12
Problem resovled! There was no line for my external drive in fstab, so I added one and removed all the empty folders. It seems to work fine now.

---

### Post by edm1 on 2008-04-12
Can you post an example of the line you put in fstab and mark the thread as solved (under 'Thread Tools').

Also, this is fixed automatically in Hardy.

---

