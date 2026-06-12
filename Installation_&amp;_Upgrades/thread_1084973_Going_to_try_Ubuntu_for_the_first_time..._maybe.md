---
title: "Going to try Ubuntu for the first time... maybe"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by mattj7 on 2009-03-02
Ok, I'm really interested in Ubuntu, but I'm not ready to give up windows.  Not because I like windows as an operating system, but because I like the third party media available on windows as apposed to linux and mac.  Therefore I've decided to try to set up a "dual boot".  From what I understand, I have to create a seperate partition on my hard drive, then install ubuntu onto that and set up some sort of thing that will let me choose between operating systems when I turn my laptop (coimpaq presario c500, 1.5gb ddr2, 1.6 ghz intel celerom, 80bg hard drive, Windows Vista Basic, no dedicated graphics card) on.  I have no idea how to do this, and am starting from square one.  i want to know the risks, and I have no experience with the terminal or writing code.  I need alot of help, but if you guys can convert me, I'll certainly do alot of good for linux; help out on these forums, post my own thoughts\praises\ideas\questions, and tell people how awesome it is.  So, guide me through it

p.s. in order to get some sort of experience, i tried install ubuntu unto my moms old piece of crap desktop.  She'd be pissed if i gave her a different operating system, so i took her hard drive out and put in a spare one.  Then i burned the Ubuntu 8.10 desktop to a cd.  I turned it on and pressed a bunch of f keys, since i didnt know which one.  Then the Ubuntu loading screen and Language screen came on, but i could not interact with the language screen.  Then a black screen with plain white text went on endlessly saying something about status[drdy] logical block at 13513 ect.

---

### Post by taurus on 2009-03-02
Maybe this line, [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall), would answer some of your questions.  Again, do a _backup_ of your files in windows first just in case.

---

### Post by jerrrys on 2009-03-02
here's some reading material

[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

---

### Post by Riba1122 on 2009-03-02
Maybe I, as a "green" Ubuntu user, can give you some useful tips.
(and if anyone sees any mistake in my post, please, correct me)

Ubuntu (Linux) uses different types of partitions then Windows.
You'll need to create them.
My friend told me, that I have to create a SWAP partition (I got the feel it's something like pagefile.sys in Windows), it should be about the size of your RAM (1.5GB in your case) and you'll need something like /ext2.
That is where you're going to install Ubuntu (and also where it's going to be your desktop).
I agree with the backup, even tho I didn't created it, because I had nothing to lose.


About the booting problem... when you will have Windows and Ubuntu installed, soon after you boot your computer, you will be asked which OS you would like to run (this closes after 10 seconds if you don't press any button; it can be adjusted).

Hope it helped.

---

### Post by Deddly on 2009-03-02
> **mattj7 said:**
> I need alot of help, but if you guys can convert me...

Matt, I'm also pretty new to Ubuntu. All I can say is you won't regret it if you try it out. First download/burn the cd and try it out as a live CD (reboot with the cd in the drive and your computer can boot from it into Ubuntu without making any changes to your hard drive). Click on the "install" icon and it talks you through the whole process, no need to do the partitioning or anything else yourself. 

I still can't get over how impressed I am with the ease of it all.

---

### Post by avtolle on 2009-03-02
One thing, though; before installing, defrag your HDD (>once), then make some space on the HDD (at least 15 GB) for the install by shrinking your partition by using the Vista tool for this task. Leave this space unallocated, and let the installer do its thing.

---

