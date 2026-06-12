---
title: "[SOLVED] Deleted Ubuntu partition, can't boot Vista"
date: 2008-07-18
forum: General Help
---

### Post by simonsimon on 2008-07-18
Hi all

In order to free up HD space on my laptop I deleted the partition with Ubuntu on it.  I now know that deleting the partition first was not the right way to go about it.

Now I can't boot into Vista and I'm getting a Grub Error 17.

I tried [fixing from an ubuntu live disk]("http://ubuntuforums.org/showthread.php?t=825222&highlight=mbr.bin") and got the error message that mbr.bin doesn't exist.

I tried [this vista recovery disk]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and startup repair did nothing.  

I've wasted most of a day on this.  Can anyone help me?

boot is sda1  NTFS

Thanks in advance.

---

### Post by WRDN on 2008-07-18
You could use [Super Grub Disk](www.supergrubdisk.org)  to replace the Windows Master Boot Record (MBR).

---

### Post by SunnyRabbiera on 2008-07-18
How much room do you have on that HD by the way?
And why dump ubuntu, any issues?

---

### Post by simonsimon on 2008-07-18
> **WRDN said:**
> You could use [Super Grub Disk](www.supergrubdisk.org)  to replace the Windows Master Boot Record (MBR).

Is there anyway you can point me in the right direction and help me throught this website?  Where do I start?  What do I download?  It looks like it was written by a highly caffeinated 12 yr old with a disdain for all things linear.

For example here is a solution to the problem I'm having (according to the website):

Quick solution 
WIN => MBR & !WIN! :((((((((((((((((( 
SGD fixes Windows automagically for you and boots Windows again. 


That means nothing to me.  Any help would be greatly appreciated.

---

### Post by WRDN on 2008-07-18
From the documentation, it appears you choose "!WIN!" to only boot Windows, and "WIN => MBR and !WIN!" to write the master boot record for Windows, so it will boot normally again.

Ive never used the disk before, but I know multiple people on these forums have done so, with success often.

---

### Post by simonsimon on 2008-07-18
> **WRDN said:**
> From the documentation, it appears you choose "!WIN!" to only boot Windows, and "WIN => MBR and !WIN!" to write the master boot record for Windows, so it will boot normally again.

Ive never used the disk before, but I know multiple people on these forums have done so, with success often.

SOLVED.

Thanks WRDN.  That was quick + painless.

:)

Simon

---

### Post by jimv on 2008-07-18
See:

[http://members.rushmore.com/~jsky/id39.html](http://members.rushmore.com/~jsky/id39.html)

---

### Post by simonsimon on 2008-07-18
> **SunnyRabbiera said:**
> How much room do you have on that HD by the way?
And why dump ubuntu, any issues?

I'm not dumping ubuntu.  Just removing it from my laptop.  I needed the space for work and can't run crappy proprietary manufacturing software on Ubuntu.

---

### Post by owoito on 2008-07-18
I am not an expert but i recently did encounter the same problem that you are having.
Insert the window vista DVD or CD, and then restart your system. Do not select the repair option, because it won't find anything to repair but rather select the command prompt option, and type in the terminal Bootrec.exe /FixMbr and then press enter.
Windows will start again.

---

### Post by adrian15 on 2008-08-22
> **simonsimon said:**
> Is there anyway you can point me in the right direction and help me throught this website?  Where do I start?  What do I download?  It looks like it was written by a highly caffeinated 12 yr old with a disdain for all things linear.

I am sorry but I wasn't born in a English-speaking country. My English is quite well but not perfect.

Everyone in the ubuntuforums.org is welcome to get a [Super Grub Disk wiki account](http://www.supergrubdisk.org/w/index.php?title=Special:Userlogin&type=signup) and start improving it so that everyone can understand it.

You know when you develop a program everything is funny but when you ask help for documentation is not evident.

adrian15

---

