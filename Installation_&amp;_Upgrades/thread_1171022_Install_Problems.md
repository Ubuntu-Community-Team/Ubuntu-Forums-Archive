---
title: "Install Problems"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by netbook on 2009-05-26
ok, i just purchased a acer aspire one netbook yesterday with 160 gig and 1 gig of ram, I really want to install ubuntu on my netbook but since i have NEVER used linux i have many doubts and want to keep a dual boot system, at least for now. 
I have downloaded the netbook remix version and written it to a usb i believe (it shows a ubuntu logo when i look at it in my computer) and checked the md5 sum. 
now i have the problem i understand that to have a dual boot i must partition my hard drive but i do not know how to do so at all and much less without uninstalling my current os. 
after i do partition what is the next step any help greatly appreciated

netbook

---

### Post by lindsay7 on 2009-05-27
Down load Gparted from their web site. It will be an ISO image so need a burner that will burn ISO files. Onece you do that you can boot your computer with the Gparted disk and do all the partitioning you want The web site has really great support docs.

---

### Post by donato roque on 2009-05-27
Hi
I understand partitioning can be a bit hairy.
The easiest way to partition your hard drive in preparation for a
dual boot with another OS is to let the live CD of Ubuntu partition it
for you (meaning accept the default partitioning suggested when installing
Ubuntu).
If you don't have the live Ubuntu CD, you can download the iso from their
website.  Then burn it.  
If you already have the ubuntu netbook remix UNR in your flash drive and md5 sum it then you're ready to install. 
The earlier suggestion of using Gparted (an open source partition manager)
is also great.  Please take a look at this documentation which is a great help for me when I was doing this a few ubuntu versions back.  Don't worry it's been updated since.  
      [https://help.ubuntu.com/community/forum/installation/Partitioning]("https://help.ubuntu.com/community/forum/installation/Partitioning")

---

### Post by dandnsmith on 2009-05-27
You can avoid a lot of the problems using CD (since you don't have a drive built in) by consulting pendrivelinux.com where you can find methods for installing ubuntu desktop to a USB stick.

You'll then be able to boot this, as if using a live CD, and be able to perform the wubi operation to install ubuntu under Windows (if you want to further than just liveCD trials). The netbook remix doesn't (in my view) offer a lot of advantage, and you can always add the different desktop look later.

---

### Post by Davestom on 2009-05-27
Some of you guys just need to remember, that AA1 (Acer Aspire 1) has no CD/DVD driver..

Im in the same prob as this guy, but I will try to make boot from USB with UNR on it, and then install it on a free partion.. Hope it will work.. anyone who know any easier methods, then PM me.. :)
The ones mentioned above seem hard, since the file is an .img and not iso.. :S

---

### Post by lindsay7 on 2009-05-27
Ok, I did know about the cd drive problem.  This is what I would do if I had trhis computer.  I would use Unetbootin and set up an usb with Puppy Linux on it. It is small in size and easy to work with. I would boot from it and use the Gparted program that is on it to partition the hard drive on the cumputer. It is easy to unmount the hard drive from the desktop of Puppy Linux so it will be ready to be work on when Gparted is started up.

---

### Post by dandnsmith on 2009-05-27
> **Davestom said:**
> Some of you guys just need to remember, that AA1 (Acer Aspire 1) has no CD/DVD driver..

Im in the same prob as this guy, but I will try to make boot from USB with UNR on it, and then install it on a free partion.. Hope it will work.. anyone who know any easier methods, then PM me.. :)
The ones mentioned above seem hard, since the file is an .img and not iso.. :S

OK - so have a look at [this thread](http://ubuntuforums.org/showthread.php?t=1171203) which will take you to the installation of the img file method(s)

---

### Post by netbook on 2009-05-27
ok i can boot the unr from my usb, my question is if when i click install on the boot screen will it let me make a new partition or will i have to have my partition already available when i get to that step.

thanks for all the help

---

### Post by netbook on 2009-05-27
up?

---

### Post by lindsay7 on 2009-05-27
I a word yes, but it may not be what is best for you. You did not say, do you have windows on this system? If so you could just install Ubuntu using Wubi and do it from the internet. That way you would have a dual boot system but Ubuntu would be installed under windows and you can uninstall it in the control panel if you do want it.

I would set up a new partition first if it was me. You can do it using the live cd. The Partition tool is Gparted and you will find it under system/administration/partition editor. Right click on you laptop partition and unmount it first in order to shrink the current partition and them use the unallocated space to set up a new partition. Then install Ubuntu to that partition. 10 gigs is enough if you are not going to store a lot of data on it.

---

