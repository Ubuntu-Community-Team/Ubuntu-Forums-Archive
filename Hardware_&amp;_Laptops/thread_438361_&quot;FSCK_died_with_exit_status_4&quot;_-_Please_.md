---
title: "&quot;FSCK died with exit status 4&quot; - Please help!"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by amosharper on 2007-05-09
===============RESOLVED===============

Hi all,

I'm dual-booting Ubuntu Feisty and Windows XP. I booted into XP because I needed a certain program, copied an .xls across to my Linux desktop (I'm using an extension which allows me to access the ext3 sector and read/write within Windows, hasn;t caused a problem before). I then shut down and booted into Ubuntu, only to have the loading bar reach about 1/3 way across, then throw the error:

```

* Activating swap...
* Checking root file system...
fsck 1.40-WIP (14 Nov 2006)
Ubuntu 7.04 contains a file system with errors, check forced.
Ubuntu 7.04:
Inodes that were part of a corrupted orphan linked list found.

Ubuntu 7.04: UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY.
(i.e. without -a or -p options)
fsck died with exit status 4
[RIGHT][fail][/RIGHT]
* An automatic file system check (fsck) of the root file system failed.
A normal fsck must be performed, then the system restarted.
The fsck should be performed in maintenence mode with the
root file system mounted in read-only mode.
* The root file system is currently mounted in read-only mode.
A maintenence shell will now be started.
After performing system maintenence, press CONTROL-D
to terminate the maintenence shell and restart the system.
Give root password for maintenence
(or type CONTROL-D to continue): _
```

As the root password is random, there's not a lot I can do on that front, is there?

What *can* I do?

Thanks very much in advance;

- Amos

---

### Post by amosharper on 2007-05-10
24 hours and not a single suggestion - does this mean no-one knows?

Please help! Thanks.

---

### Post by kjaggu on 2007-05-12
Having the same problem here :(

Please help!!!

---

### Post by amosharper on 2007-05-12
Update - and this may help you, Kjaggu:

Opened in Recovery Mode (from the GRUB menu), got through and logged in, then changed root password by opening the terminal and typing 'sudo passwd root'.

[COLOR="Silver"]Unfortunately for me, mine now just gets into a cycle where it starts, fails, reboots in 5 seconds (rinse and repeat).[/COLOR]
Actually, no, after I opened in recovery mode, it's now fine. No problems.

Kjaggu, how's yours looking?

- Amos

---

### Post by euphonic05 on 2007-07-03
Hey! I have the same problem. But i can't get through recovery mode either. It follows the same pattern as the normal mode. Do you think I should just re install?

---

### Post by ceomoses on 2007-07-07
I was getting the same error code on a separate partition of mine.  What I did to fix was to just type "sudo fsck /dev/sdb1", but the command might be slightly different for you (sda1, etc).  fsck then went through some diagnostic modes, found some errors, I clicked yes on everything it found, restarted and everything was fine.  Lemme know if that helps you.

---

### Post by bats999 on 2007-07-08
A few comments.

I got the same error message.  I looked in /etc/fstab and found that my swap partition was listed twice, once (in UUID lingo) as "swap", and once again (in traditional /dev) as "ext3".  I deleted the offending line and now Ubuntu boots fine.  I think the install program dropped the ball.  But this is my first Ubuntu install, so I can't say what the problem was.

Also, it seems that the maintenance shell that comes up will not respond to a "control-D" until you've entered a command (anything really, like 'ls').  After the control-D, boot proceeds normally. 

Has anyone else seen anything like this in their /etc/fstab?

---

### Post by drachenchen on 2007-12-17
Howdy.  Running Feisty on an old Athlon, roughly P3-era, 1GB CPU, 756MB RAM, which maxes-out the POS MoBo.  Dual boot with XP, recent upgrade from CD to Feisty, preserving Home directory.

    I had the same error message on boot-up, but the maintenance shell wouldn't recognise many common bash commands.  Figured I was excommunicated from the box.   I tried ceomoses' suggestion to type "sudo fsck /dev/<device in question>, but the shell wouldn't recognise the "sudo" command.  I tried simply "fsck /dev/<device in question>, and got a series of questions about various inodes.  I'm somewhat of a newbie, and wouldn't know an inode from my posterior on the pavement,  but the program seemed to have some strong opinions on what needed to be done.   I  answered "no" to all of the questions, just to be cautious, and it looked like it really wanted to "fix" a lot of details.  So, I tried the whole exercise again, answering "yes" to everything, and my problem appears to be over.  Boots fine with the latest kernel, desktop comes up, etc.   I suspect that the OS just walked me through the Masonic version of what Bats999 was alluding to, and deleted a spare swap space without actually telling me in English what the Hel it was doing.  Good luck to one and all.

---

