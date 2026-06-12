---
title: "yet anther newbie boot problem :("
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by georgec32 on 2009-06-02
i've been reading all the 'boot' threads & googling like crazy, but I can't quite find an answer to my problem (or perhaps I can't quite -recognize- the answer to my problem)

I have a two HD Windoze XP desktop w/ Windows XP SP3 on the C: drive.  I installed Ubuntu 8.10 on the D: (a 500Mb drive), using manual partition & setting up ~27Gb ext mounted at /, and a 4Gb swap space.  Everything seemed to install just fine, but when I re-booted, it went straight to windows.  I checked my D: properties and it indeed shows around 32 Gb missing (the stuff I partitioned for Ubuntu).  I booted from the Ubuntu live CD and ran GParted and I could see my ubuntu partition just fine, with the boot flag enabled.  I DID partition the ubuntu part at the end of the drive instead of the beginning ..

ANy ideas how to get my bootloader to recognize the Ubuntu boot option?

thanks in advance.

georgec32

---

### Post by kruegger on 2009-06-02
You could have done a deeper goggling ;)
[This might be it]("http://ubuntuforums.org/showthread.php?t=224351")

4 gb swap space looks like a waste to me.

See you.

---

### Post by georgec32 on 2009-06-02
> **kruegger said:**
> You could have done a deeper goggling ;)
[This might be it]("http://ubuntuforums.org/showthread.php?t=224351")

4 gb swap space looks like a waste to me.

See you.

Thank you for the URL pointer (and also the swap space advice!).  I followed the instructions listed on the URL (doing the grub commands from the Live CD) but still get no boot option.  I'll google deeper & see if I can find anyone who's had the same problem.

Have a great day & thanks again for the help!  It's always appreciated.

georgec32

---

### Post by wpshooter on 2009-06-02
Do you actually have 2 physical hard drives or 1 hard drive divided into logical C & D drives ?

---

### Post by rEgonicS on 2009-06-02
Try checking the boot menu when you first start up your comp. The loading page with your computer manufacturer (i.e... Dell). It should tell you what key to press in order to get to the boot menu. Usually one of the function keys. (ie... f3, f5, f12) It should show your available OS.

---

### Post by georgec32 on 2009-06-02
I have 2 physical drives, my second (D: drive) is a WD 500Gb drive just recently added.  

I've tried the boot menu but it doesn't show the D: drive .. I looked for it in the BIOS but perhaps I was so tired I overlooked it .. I can look again.

BTW, I found a thread stating a way to do a 2-drive dual boot, recommending making the ubuntu drive the master & the windows drive the slave.  I'll try that a bit later (after checking the BIOS).  The thread is at [http://ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings).

georgec32

---

### Post by wpshooter on 2009-06-02
I "think" the way you have installed (windows on 1st drive and Ubuntu on 2nd drive) that you will need to go into BIOS and change boot device order, so that you can boot Ubuntu.

I think things would be much easier if you had both of your O/Ss installed on the same drive.  

If it were me I would make the newer larger/faster hard drive my primary drive and place both O/Ss on that same drive by first installing windows O/S and then second installing Ubuntu and at that point Ubuntu would put both choices of windows & Ubuntu on the Grub menu.  I would demote the old drive to a secondary/slave drive to be used for extra storage or perhaps I would remove it from the system altogether to make things less complicated and since it is an older drive, its performance is probably out of synch with the newer drive.

---

### Post by rEgonicS on 2009-06-02
I have my windows and ubuntu installed on two seperate drives but they seem to work fine :o'

---

### Post by raymondh on 2009-06-02
> **georgec32 said:**
> I have 2 physical drives, my second (D: drive) is a WD 500Gb drive just recently added.  

I've tried the boot menu but it doesn't show the D: drive .. I looked for it in the BIOS but perhaps I was so tired I overlooked it .. I can look again.

BTW, I found a thread stating a way to do a 2-drive dual boot, recommending making the ubuntu drive the master & the windows drive the slave.  I'll try that a bit later (after checking the BIOS).  The thread is at [http://ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings).

georgec32

Hi Georgec32,

If you have 2 physical drives, you are on the right track with regards to which is primary master and which is primary slave.  Also, in CMOS, try to set both to auto and see if that'll help your issue.

Good luck and pls. do post back results.

Regards,

---

### Post by georgec32 on 2009-06-03
> **raymondhenson said:**
> Hi Georgec32,

If you have 2 physical drives, you are on the right track with regards to which is primary master and which is primary slave.  Also, in CMOS, try to set both to auto and see if that'll help your issue.

Good luck and pls. do post back results.

Regards,

well .. I have to admit I wimped out & just installed via wubi on the same HD as windows.  At any rate, it's up & working fine right now.  Maybe after a bit of a break from the installation woes, I'll try  doing it on the other drive again, just for the learning experience :)

george c

---

### Post by raymondh on 2009-06-03
> **georgec32 said:**
> well .. I have to admit I wimped out & just installed via wubi on the same HD as windows.  At any rate, it's up & working fine right now.  Maybe after a bit of a break from the installation woes, I'll try  doing it on the other drive again, just for the learning experience :)

george c

Hi George,

For as long as you have a working OS ... you're good to go :)  Congratulations !

Regards,

---

### Post by kwalters on 2009-06-03
I have a solution to the problem, but it involves using a bootable Linux rescue CD I downloaded (free) some time ago.  Whether you can do the same thing with the live CD, I don't know.

It enables to you boot up into the Linux partition by using

(First step)  Press F2
(Second step) type <rescuehd root=/dev/sda3 (or wherever your linux partition is.)  That will start your Ubuntu as loaded on your hard disk


Get a terminal window and type grub [enter]

at the new grub> prompt, type the following in turn

root (hd0,2)  [that is the equivalent of /dev/sda3 in grub notation}

setup (hd0,0) that will put the grub bootloader on the first hard disk.

Grub will find your windows entries by itself and offer a choice at boot up, together with a (default) choice of the Ubuntu partition

KW

---

