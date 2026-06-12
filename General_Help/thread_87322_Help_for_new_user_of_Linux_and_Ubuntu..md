---
title: "Help for new user of Linux and Ubuntu."
date: 2005-11-07
forum: General Help
---

### Post by mad_hatter on 2005-11-07
First I am going to ask a strange question, bear with it's stupidity. Is it possible to dual boot Windows XP and Ubutu off of the same HDD? Second I am going to ask a more complicated question. What is the meaning of this:

ALERT! /dev/hdb1 does not exist. Dropping to a shell!

BusyBox v1.0-pre10 (Debian 20040623-1ubuntu22) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off.

This is the message I get when I try to boot Ubuntu. I have my 160gig HDD partitioned into two sectors, one is a 120gig and the other a 40gig. With Ubuntu installed on the smaller one.

My System Specs:
Motherboard- ECS nForce4-A939
CPU- AMD Athlon 64 3000 Socket 939 Venice Core
GPU- Nvidia G-Force FX 5500 PCI
PSU- Ultra Xconnect
RAM- Ultra 512 DDR
HDD- Maxtor 160gig IDE (OEM)
DVD Drive- LiteOn DVD+/-R/RW

Thanks in advance for the help, and just ask if there is more information needed.

---

### Post by jaddison on 2005-11-07
> **mad_hatter]First I am going to ask a strange question, bear with it's stupidity. Is it possible to dual boot Windows XP and Ubutu off of the same HDD?[/QUOTE]

Yes, it is.  You'll just need to configure Grub appropriately.  If you don't know what Grub is, then you'll definitely need to do some more reading!   said:**
> http://ubuntuforums.org/showthread.php?t=84373&highlight=grub+dual+boot[/url]

[quote]Second I am going to ask a more complicated question. What is the meaning of this:

ALERT! /dev/hdb1 does not exist. Dropping to a shell!

BusyBox v1.0-pre10 (Debian 20040623-1ubuntu22) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off.

This is the message I get when I try to boot Ubuntu. I have my 160gig HDD partitioned into two sectors, one is a 120gig and the other a 40gig. With Ubuntu installed on the smaller one.

I am assuming that you only have the one physical hard drive that you've partitioned into two logical drives.  If you have only one hard drive, then your partitions will most likely be /dev/hda1 and /dev/hda2, although that depends on your setup.  What I'm saying is, if you have only one hard drive, you won't have /dev/hdb1 or /dev/hdb<anything>, unless it's an IDE CD/DVD drive.

I hope I've helped - and not confused you too much.  Keep asking questions - you'll get your answers.  ;)

---

### Post by Zwack on 2005-11-07
[QUOTE=mad_hatter]First I am going to ask a strange question, bear with it's stupidity. Is it possible to dual boot Windows XP and Ubutu off of the same HDD? 
[/Quote]

Yes, it is, but never having done it I'm not going to be able to tell you how to do it...

[QUOTE=mad_hatter]
Second I am going to ask a more complicated question. What is the meaning of this:

ALERT! /dev/hdb1 does not exist. Dropping to a shell!
[/QUOTE]

Given the specification you gave you have one hard drive, which would normally be an IDE Master drive on the first channel.  If that is the case then it is /dev/hda not /dev/hdb  (a = master, primary channel, b = slave, primary channel, c = master, secondary channel...., I have hda (hard drive) and hdc (cdrw) and I suspect your set up is similar)...

You should be able to boot by giving grub the option root=/dev/hdaX where X is the hard drive partition (probably 2) you installed ubuntu on...

I hope that this helps,
Z.

---

### Post by Kapre on 2005-11-07
[QUOTE=mad_hatter]First I am going to ask a strange question, bear with it's stupidity. Is it possible to dual boot Windows XP and Ubutu off of the same HDD? [/quote]
Yes. Lots of users here is doing that (I myself had this one time)

> Second I am going to ask a more complicated question. What is the meaning of this:

ALERT! /dev/hdb1 does not exist. Dropping to a shell!

This means that 2nd drive is not formatted to any system (that's why it says does not exist - maybe dead). If you have Ubuntu on this partition before, it was deleted (or system corruption)

K

---

### Post by steve.horsley on 2005-11-08
[QUOTE=mad_hatter]First I am going to ask a strange question, bear with it's stupidity. Is it possible to dual boot Windows XP and Ubutu off of the same HDD? [/QUOTE]

It certainly is. I do it every day.

[QUOTE=mad_hatter]Second I am going to ask a more complicated question. What is the meaning of this:

ALERT! /dev/hdb1 does not exist. Dropping to a shell!

BusyBox v1.0-pre10 (Debian 20040623-1ubuntu22) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off.

This is the message I get when I try to boot Ubuntu. I have my 160gig HDD partitioned into two sectors, one is a 120gig and the other a 40gig. With Ubuntu installed on the smaller one.[/QUOTE]

That looks bad. It looks as though Linux is configured to run from the second hard disk (hdb), but finding that it is in fact on a different disk (probably hda, judging by your text). You might be able to fix it by editing /etc/fstab from a rescue CD, but I'm not sure. Also, you shouldn't have just one partition for Linux, there should also be a swap partition. 

I suggest that you delete the Linux partition, leaving just empty space. Then re-install Ubuntu, choosing the option to use the empty space on the disk - the installer will then create the partitions it feels it needs.

Steve

---

### Post by Roobert on 2005-11-08
[QUOTE=mad_hatter] Is it possible to dual boot Windows XP and Ubutu off of the same HDD?[/QUOTE]

Yes, I did this yesterday, successfully at that...I'm a noob, too. 

[QUOTE=mad_hatter]Second I am going to ask a more complicated question. What is the meaning of this:

ALERT! /dev/hdb1 does not exist. Dropping to a shell![/QUOTE]

I believe the experts have answered this one pretty adequately. I had the same error message, too! My solution? I threw the WIndows XP boot CD in the drive and re-formatted, and did a fresh install.

I found that you can get into a lot of trouble mucking around with the Ubuntu disk partitioner if you're using it for the first time...creating LMV's, creating partitions everywhere - so here's what I did: I started with a freshly re-formatted NTFS partition which occupied 100% of my hard drive. I had XP running on this partition. Boot from the Ubuntu install CD, and when you get to the disk partitioner, I believe there is an option to change the size of the NTFS partition. Once NTFS was resized, I created an ext3 primary partition to install Ubuntu on (the boot partition). Make sure you give this drive boot privileges! I then made another ext3 for housing Ubuntu data and files. It's mounted under /home; a 1.5 GB swap partition (you'll want one of these too); and a FAT32 partition to exchange data with Windows. After you write all these changes to disk, Ubuntu will typically report that it has detected a Windows XP install on your NTFS partition, and that it will install the bootloader Grub to ask you which OS you want to use at start-up.

One thing I did not realize at first when using the Ubuntu disk partitioner is that you change pretty much every parameter on the screen by pressing Enter when the line is highlighted. 

That's about it...my setup has been painless after that...Ubuntu works fine, but Windows can't auto-detect my ethernet driver while Ubuntu can. I hate windows, ugh..........;) 

~ Roobert.

---

### Post by eyebrowman92 on 2005-11-08
boot on the install cd or the live cd?

---

### Post by Roobert on 2005-11-09
[QUOTE=eyebrowman92]boot on the install cd or the live cd?[/QUOTE]
...er, boot from the Install CD.

---

### Post by mad_hatter on 2005-11-09
Well I tried what Roobert said, and was able to succesfully boot Ubuntu. Once. I shut down so I could boot into Windows for some F.E.A.R. action, and after a while rebooted up Ubuntu. Same problem occured, though it says hdc1, I think, it might have always said that I have a little dislexia problem :) Anyway, thanks for the help. Any input would be helpful.

---

