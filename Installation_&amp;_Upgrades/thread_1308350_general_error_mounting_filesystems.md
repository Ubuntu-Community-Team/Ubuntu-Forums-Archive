---
title: "general error mounting filesystems"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by blisteringsyko on 2009-10-31
i just recently got rid of vista home premium x64 from my pc and decided to go with ubuntu .. ubuntu worked fine with wubi in vista but the live disk i had was 8.10   64bit  the update to 9.4 worked but after i updated to 9.10 when it tries to start up i get 

init : mountall main process (488) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and retry.
root@chris-desktop:~#
ubuntu 9.10 chris-desktop ttyl

chris-desktop login: _


when this screen apears every thing blinks very rapidly ,the display, leds on key board typing in my username is hard, it seems that the power is just flickering... password is just not gona happen.    no maintenance shell ever starts... i tried loading a different one by hitting esc but they do justa bout the same thing, using the recovery options did nothing, nothing to update nothing to be repaired so it says. Some times when i try to boot it says 

Boot from (hd0,0) ext3   a7c85936-011b-44b7bo5d-a547ff549457
Ubuntu 9.10 chris-desktop ttyl

chris-desktop login : _

screen still flashing



idk if i should just wipe my drive and reinstall and only update until 9.4 and wait for a hotfix, from what i understand people are having simillar issues so idk if there will be a patch of some sort or not

---

### Post by schwitzer on 2009-11-01
Exact same problem here.

I installed Ubuntu 9.10 on a fresh 320GB SATA Drive (Samsung).

I get the exact same behaviour.
First the error message "General error mounting filesystems" followed by the following errors:

"Buffer I/O error on device sr0"
"I/O resource nForce2_smbus conflicts with ACPI region SM00"
"Error probing SMB2"

And then the screen starts flickering. There is no possibility to get a graphical login.

I have an ASUS M3N78 mainboard. The live system works fine, everything okay without any problems. Only after I installed the system I got above problem.

---

### Post by Duke Togo on 2009-11-02
same issue here, after upgrade to 9.10

general error mounting filesystems
A maintenance shell will now be started
CONTROL-D will terminate this shell and re-try
root@richard-laptop:~#

ant ideas?

---

### Post by Duke Togo on 2009-11-02
ant ideas!
sorry
any ideas?

---

### Post by Duke Togo on 2009-11-02
if I press esc when grub is loading I get the menu options screen for 8.04
I had already upgraded to 8.10 so whats happened?

---

### Post by blisteringsyko on 2009-11-05
well i decided to just wipe my drive and install the 32bit version i386 or what ever its called.. seems my 64bit computer doesnt like 64bit ubuntu  so what ever no big deal. i never really did get any advantage out of a 64bit system so yea what ever...

---

### Post by DandyAndy on 2009-11-10
+1 Don't know where to go from here. When it WAS working the first 2 days after install it complained about something like the install disc having a lot of bad sectors. It's an old disc - but it seems a bit strange that it breaks down at just that time. Also i can see the files during "recovery shell mode"
 Ubuntu also pointed out that my other driver had the same problems.

---

### Post by anthonywith on 2009-11-12
General error mounting filesystems
A maintenance shell...

I had this message after upgrading from JJ to KK on a dualboot system with XP this morning and was lucky enough to find the answer (after hours on other problems with SuperGrubDisk I wasn't keen on anything too time-consuming)

All I had to do was edit and save the menu.list file to point to the latest kernel - 2.6.31-14 worked for me.  I replaced it in each line of the first Linux option given (and changed the version number to 9.10 for good measure).  Careful with the spacing and punctuation.  There was another menu.list file with a ~ next to it so I edited and saved that one too - just in case.

The XP part of my dual boot was working and I had installed the Ext2 Installable File System from [www.fs-driver.org](www.fs-driver.org) which gives read and write access to the Linux partitions;  I used ZTree to locate and edit the menu.list file, but Explorer and Notepad should do as well.

Rebooted and Karmic Koala loaded and ran as expected.  Hope this helps.

---

### Post by GO%)$@*1 on 2009-11-12
I am having the exact same problem. Any ideas?

---

### Post by joijo on 2009-11-16
Same problem here....

---

### Post by Kjeldgaard on 2009-11-20
> **anthonywith said:**
> General error mounting filesystems
A maintenance shell...

I had this message after upgrading from JJ to KK on a dualboot system with XP this morning and was lucky enough to find the answer (after hours on other problems with SuperGrubDisk I wasn't keen on anything too time-consuming)

All I had to do was edit and save the menu.list file to point to the latest kernel - 2.6.31-14 worked for me.  I replaced it in each line of the first Linux option given (and changed the version number to 9.10 for good measure).  Careful with the spacing and punctuation.  There was another menu.list file with a ~ next to it so I edited and saved that one too - just in case.

The XP part of my dual boot was working and I had installed the Ext2 Installable File System from [www.fs-driver.org]("http://www.fs-driver.org") which gives read and write access to the Linux partitions;  I used ZTree to locate and edit the menu.list file, but Explorer and Notepad should do as well.

Rebooted and Karmic Koala loaded and ran as expected.  Hope this helps.

Can you elaborate on this solution. Where do you find the menu.lst file? I thought it was located at /boot/grub/ but I can't locate it.

---

### Post by qneill on 2009-12-14
> **Kjeldgaard said:**
> Can you elaborate on this solution. Where do you find the menu.lst file? I thought it was located at /boot/grub/ but I can't locate it.

Sometimes it is in /grub, depending on how you partitioned your disk - see [http://tr.im/HAqu](http://tr.im/HAqu)

If you can get a shell running with Live CD booted or busybox, you can use this brute force command to find it:
```
find / -name menu.lst

```
Or you can just use "cd" and "ls" to find it yourself.

-- 
Quentin

---

### Post by Anhedonia on 2010-02-24
I was having this problem as well on a text only server install of 9.10 on my hp notebook. (1330ap)

When i looked at fstab i saw it was attempting to mount the other linux installs swap parititon.

When i tried to edit, the error of course happened as soon as i pressed a bloody directional key.

I had assumed it was the ext4 file system i was using however i am now reinstalling the server as the main and only partitions in the hope this is successful.

So much for text only mode being more reliable! =D

---

### Post by Anhedonia on 2010-02-24
I reinstalled as ext3 , and as the only partiton on the drive. Still the exact same error.

i had 2gb swap, and 40gb for the /

I don't understand why there is not more information regarding this as so many people seem to be having the problem.

---

### Post by trinetra on 2010-03-19
> **blisteringsyko said:**
> 

init : mountall main process (488) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and retry.
root@chris-desktop:~#
ubuntu 9.10 chris-desktop ttyl

Boot from (hd0,0) ext3   a7c85936-011b-44b7bo5d-a547ff549457
Ubuntu 9.10 chris-desktop ttyl

chris-desktop login : _

screen still flashing





Any updates on this issue. Just now I had formatted my Windows (came along with my notebook) and installed 9.10. Everything worked fine but when I restarted the machine I am getting the flashing screen from there I couldn't do any thing. I am really struck somebody please help.

I even tried to change the grub option pointing to Linux 2.5.31-14-generic, even then the problem is not solved and still have the flashing screen. 

One more thing (may be useful), I had installed Netbook remix 9.10 on my netbook some three months back till now I don't have any problem with that.

---

### Post by trinetra on 2010-03-21
For those who had faced problems like me, please follow the following steps to solve the problem. (You need to have Internet connection).

At the time of grub loading please select the recovery mode and then after some time you will be asked with different options, out of which select fix the broken packages and automatically Ubuntu downloads latest Kernel (2.6.31-20-generic) along with some packages. So after the update just reboot your machine, thats it **problem solved**.

Hope this will help somebody.

---

### Post by Swerve1000 on 2010-03-26
> **trinetra said:**
> 

Hope this will help somebody.

Thanks for posting this.

I've had this same issue a few times on my 9.10 Server install on a dual boot (XP is the other OS) Samsung NC10 netbook.

For me this is occurring when I use Nano. I try to edit a file as sudo, then the cursor keys stop working, and I end up with the text in the text editor screen in a right mess all over the screen and end up having to do a hard reset.

Every time it's happened it been a virtually brand new fresh and updated installation.

So far the solution kindly posted by trinetra seems to have fixed the issue and when I use Nano as sudo, the cursor keys are working and text is displayed correctly.

Hope it doesn't mess up again after afew days, which has been the problem so far.


EDIT - This time when I had the problem I to recevied:

> 
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and retry.


after nano started displaying text all over the display.

---

### Post by a7garg on 2010-03-27
two ways to recover this problem 

1. Format your pc 

2. go through the manually it will take a help alot:popcorn:

---

