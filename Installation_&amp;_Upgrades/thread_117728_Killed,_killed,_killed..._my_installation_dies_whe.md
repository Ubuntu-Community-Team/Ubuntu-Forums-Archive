---
title: "Killed, killed, killed... my installation dies when partitioning: why ?"
date: 2006-01-15
forum: Installation &amp; Upgrades
---

### Post by sebbone on 2006-01-15
First of all: I did't find a real answer to this problem in the forum: there were just two guys suggesting 
a) to try another version of ubuntu 
b) to "kill some processes" 
while I was looking for an explanation of the problem, more than a solution (and of course would like to install the latest ubuntu 5.10).

So this is the problem:

While installing KUbuntu 5.10 from CD, after network and DHCP settings, while starting the partitioning app I get the black background on the screen and:

[I]Killed
Killed
Killed[/I]

as a loop and the whole screen. My installation dies here.

With CTRL+ALT+F3 I get a lot of stuff, last 3 rows are:

[I]insmod /lib/modules/2.6.12-9-386/kernel/drivers/cdrom/crdom.ko
insmod /lib/modules/2.6.12-9-386/kernel/drivers/ide/ide-cd.ko
insmod /lib/modules/2.6.12-9-386/kernel/fs/isofs/isofs.ko[/I]

With CTRL+ALT+F4 i get: 
[I]
Jul 7 11:15:53 init: ^Mprocess '/sbin/debian-installer' (pid 23267) exited. Scheduling it for restart.
Jul 7 11:15:53 init: ^MStarting 23202, console /dev/vc/1: '/sbin/debian-installer'[/I]

as a loop. just the numbers (and the hour, of course) change: the one following ^Mstarting becomes the one after "pid" in the next row, etc etc...

My PC is a Celeron 433, 64 MB RAM, HD 6GB, CD burner Plextor 8/4/32. 
HD and CD drive look perfect, on the HD Win98 runs without problems, recognizing the drive.

The Kubuntu CD itself looks perfect under Win98: "Kubuntu 510 i386",  671.580.160 byte (640 MB).

Who can help me to definitely trash Win, format the HD, and start my new (and first!) linux experience ?

Thanks in advance

---

### Post by sebbone on 2006-01-15
Just downloaded another ISO (the ubuntu 5.10, not the kubuntu one), burned it at 10x, and still getting the "Killed" error.
But now the word does appear only in the bottom left corner of the screen, "jumps" fast on top and then again on bottom left, and loops.
And with CTRL+ALT+F4 I get one more row:

Date hour *main-menu[*xxxxx*]: DEBUG: Executing /lib/main-menu.d/10casper*

What the hell is going on ?

---

### Post by peterscj on 2006-01-26
I'm getting the same problem trying to do a minimum install on an old laptop.  I would really like to get it to run Ubuntu Lite but for some reason I can't even get the minimum install of Ubuntu to work.

Any thoughts or suggestions?

---

### Post by RavenOfOdin on 2006-01-26
You can always try obtaining a CD that isn't burned. . .have you tried md5sum?

---

### Post by markcaetano@gmail.com on 2006-01-26
i dont know if this will help but u can get up to 100
official ubuntu cd's for x86,mac and 64-bit pc free from [HERE]("https://shipit.ubuntu.com/")

hope this will help

---

### Post by GTvulse on 2006-01-26
[QUOTE=sebbone]Just downloaded another ISO (the ubuntu 5.10, not the kubuntu one), burned it at 10x, and still getting the "Killed" error.
But now the word does appear only in the bottom left corner of the screen, "jumps" fast on top and then again on bottom left, and loops.
And with CTRL+ALT+F4 I get one more row:

Date hour *main-menu[*xxxxx*]: DEBUG: Executing /lib/main-menu.d/10casper*

What the hell is going on ?[/QUOTE]
Try burning the CDs at no more than 4x. The internal filesystem structure of the ubuntu installation CDs is so complex that a CD/DVD writer will have trouble placing the laser accurately on the disc die if you try to use a faster speed.

---

### Post by yugotpinky on 2006-03-12
that doesn't explain the error though.  

the issue is that the partitioner doesn't run... there's no CD info reading at the time.

---

### Post by Mustard on 2006-03-14
From what I can ascertain, this is a problem with systems with low RAM ie 64mb.

When you set up your partitions with the installer are you setting up a swap partitions as well?

-edit-

Just reading over the thread again and I realise that the partitioner is not working.  I wonder if it's possible for you to get a live CD and manually partition your drives.

Basically the only clue I have been able to find on this issue is that its related to people who are installing on systems with 64mb of RAM.

---

