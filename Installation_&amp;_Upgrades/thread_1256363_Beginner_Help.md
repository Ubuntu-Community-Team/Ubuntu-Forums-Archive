---
title: "Beginner Help"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by nickf8 on 2009-09-02
I know nothing about Linux, or Ubuntu.  I just got the Ubuntu install disk in the mail and I wanted to try and play around with a desktop that I don't really use.  

I put the install disk in the drive and everything goes fine until step 4 of the installation.  After it checks the partitions nothing comes up in the menu and then when I try to click forward it tells me that no root file system is defined.

What do I do?

---

### Post by jerrrys on 2009-09-02
this may help

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by ronparent on 2009-09-02
The install cd you received is also known as the live cd. That means that you can boot to it with no changes to your machine. Doing that will allow you to play with it for a while before you try to install it. That also allows to to figure out an installation strategy - ie decide where to put it and how big you want the partition or install to the whole disk and in effect wipe everything else.

The install step you are stopped on, is that you have to pick one of the drop down boxes after checking the box to format the installation partition to tell it to install to /. After that the installation should go fine. Have fun.

---

### Post by nickf8 on 2009-09-02
I know for sure that I want to clear the full disk and wipe everything out. 

As far as the dropdown boxes, I don't know where these boxes are that you are talking about.  Also, I tried selecting the first option to run Ubuntu from the CD and it just goes to a black screen and won't run.  

If you have any more specifics on where I can find the drop down boxes that would help, thanks!

---

### Post by jerrrys on 2009-09-02
did you get a good burn (cd that is)?  did you burn at low speed?  did you do a check cd after the burn?

also how much ram do you have and what kind of video card?

---

### Post by nickf8 on 2009-09-02
i got the "official" cd from the website mailed to me, so I'm pretty sure it's good

I have 512 mb ram (old computer lol) and video card i have no idea

---

### Post by QIII on 2009-09-02
-- OOF!  Edit:  just saw

> goes to a black screen and won't run

When that happens on the LiveCD, it often indicates hardware incompatibility issues.  How old is the machine?  What graphics chipset?

Need to figure that out before going to install, since you'll probably get that behavior after install, which would be a tad frustrating.


The OP said he got it in the mail...

nickf8 -- if you are new, don't want to do anything snazzy, are using an old machine, don't mind just goofing around with Ubuntu and want to wipe the existing disk anyway ...

Just select Use Entire Disk at the partitioning step.

You can do something different later after you've gained some experience -- usually we all get that by hard knocks.

---

### Post by jerrrys on 2009-09-02
also stated

> **nickf8 said:**
> Also, I tried selecting the first option to run Ubuntu from the CD and it just goes to a black screen and won't run.  

not all video cards work with 9.04.  what make and model of computer do you have?

now its a double OOF

---

### Post by nickf8 on 2009-09-03
I have an older Dell Dimension 2400.  It's definitely possible that I don't have the video card to run it.  Any other version I can run?

---

### Post by presence1960 on 2009-09-03
when the below screen appears when you boot the CD hit F4 then choose safe graphics mode. You should be able to continue with the install.

---

### Post by nickf8 on 2009-09-03
LOL Alright, so I got Ubuntu to run on the computer, but it still stops at the partitioning step during the installation.  All of the options are grayed out or else I would just create a new partition.  Even in Ubuntu, when I go to GParted, the options are all grayed out and it says "no devices detected".

Thoughts, guys?

I certainly appreciate all the help here.  You've taken me farther than I ever would have gone myself.

---

### Post by presence1960 on 2009-09-03
> **nickf8 said:**
> LOL Alright, so I got Ubuntu to run on the computer, but it still stops at the partitioning step during the installation.  All of the options are grayed out or else I would just create a new partition.  Even in Ubuntu, when I go to GParted, the options are all grayed out and it says "no devices detected".

Thoughts, guys?

I certainly appreciate all the help here.  You've taken me farther than I ever would have gone myself.
 Download the alternate text based installer from [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"), burn it to CD and try that to install Ubuntu.

---

### Post by krisarnold on 2009-09-03
I'm no expert, but is it possible that ur hard-drive is fried?

---

### Post by nickf8 on 2009-09-03
I don't think it's fried, I just ran windows xp on it before trying to install Ubuntu.  I don't know why it's not reading any of the disk drives.

---

