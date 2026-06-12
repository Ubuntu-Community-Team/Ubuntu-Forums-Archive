---
title: "Ubuntu Won't Install"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by LinuxPenguin007 on 2009-07-10
I am trying to install Ubuntu 8.10 using the Live CD on my desktop. It won't work for some reason (it works fine on my laptop).
When it loads from the CD, I can choose whether to Try Ubuntu without any change.. install Ubuntu.. etc. 
But when I choose to install it (or just try Ubuntu without any change) it will bring up a black screen while showing up all of these errors. 

Buffer I/O error on device sdb1, logical block 128 
Buffer I/O error on device sdb1, logical block 129
etc.. 

After about 5 minutes of that and some random numbers and such, it will end up with 

Setting preliminary keymap... [OK]
Preparing restricted drivers... [OK]
Setting the system clock [OK]
Starting basic networking... [OK]
Starting kernel event manager... [OK]
Loading hardware drivers... 

Then it just gets stuck there. 

Core 2 Quad Q6600
Nvidia 8800 GT
4 GB RAM 
2 Hard drives (750GB + 250GB) 

If I unhook one of the hard drives (250GB) , then the installation will continue and it will freeze right before it loads (it will freeze before it gets to the third bar) 

Any suggestions / help is greatly appreciated !

---

### Post by tommcd on 2009-07-10
The first thing you should do when the Ubuntu CD boots up is choose the option: "Check CD for defects". Let that run. It can take a couple minutes to finish. If it reports no errors, then the disc is ok. If it reports errors, burn a new CD at the slowest possible speed and retry.

What chipset does your motherboard use? If it is a fairly new chipset you may be be better off with the newest version of Ubuntu, which is 9.04. I would use 9.04 anyway, since it is an improvement over 8.10 imo, and it has newer programs and features.

EDIT: If you are burning from Windows, use Infra Recorder:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

And welcome to the Ubuntu forums!

---

### Post by LinuxPenguin007 on 2009-07-10
I checked the CD for defects, and nothing was wrong with it. I just tried to install 9.04 right now, and the same thing happened... :(

---

### Post by tommcd on 2009-07-11
So at least we ruled out a bad CD as the source of the problem.

Again, what **chipset** does your motherboard use? In your first post you said it gets stuck after:
> 
Loading hardware drivers...
Then it just gets stuck there. 

That would seem to indicate that Ubuntu is having trouble recognizing your hardware.

---

