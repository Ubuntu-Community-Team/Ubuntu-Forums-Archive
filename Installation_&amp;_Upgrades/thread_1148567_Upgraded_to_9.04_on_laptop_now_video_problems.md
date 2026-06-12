---
title: "Upgraded to 9.04 on laptop now video problems"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by Steve Meynell on 2009-05-04
Hi All, I don't know why I don't learn from the past but once again my upgrades have gone for a crap.

I was on the LST version and I decided that a lot of the programs that I was using had newer versions that were not in the APT updates so I thought, hey everything is going far to well... lets upgrade.

So I upgraded through 8.10 and then on to 9.04.  Now my system will not boot completely.  It gets through the splash screen but then gets all pixilated and then just freezes to which I have to do a hard reset.  I can get to the recovery boot.  I have tried all of the options including xfix the video, check for broken packages and nothing helps.  

I found some help here with numerous suggestions to which they either don't work or I haven't implemented them correctly.( I am a bit new to having to manually edit files and such, I am getting much better though with each upgrade. )

I do believe this to be a video driver issue but in lies my issue.  I have this installed on an Averatec 6100 Laptop.  It has an integrated video card which is a ATI Radeon 9600 card.  The driver at ATI is the 9.3 version which I have read here is not supported by 9.04.  I cannot seem to find the 9.4 version.  But is also seems that I need a GUI to install it from what the docs look like anyway.  So changing video cards is also out of the question.

I would be willing to go back to 8.10 if that will work better but I don't know how to go backwards without loosing everything and I really don't want to loose everything if I don't have to (That is just too much like Windows for me.)  :)

Oh yeah and the other dough-headed thing I didn't learn from before was, no backup... I know... I'm such an IDIOT!!

Please any help would be greatly appreciated.

Thank You,
Steve

---

### Post by Topsiho on 2009-05-06
We are all idiots time and time again. Hope this helps :)

There are two possibilities: you have your /home in a separate partition, and then there is no problem at all, when reinstalling the previous Ubuntu, which worked OK, or trying to install Jaunty (9.04) (instead of upgrading): just DOn'T FORMAT the partition in which your /home sits (you have to make sure which partition that is, of course, hopefully you made notes when you partitioned your hard disk).

And second: if you don't have a separate partition for your /home, then the only hole I can see that you can creep out of is that you can boot into recovery mode. If you can get into a terminal, you are there as root, and possibly you can copy all the files that you want to keep into another place: an external disk or a USB-stick.

Ah: maybe there is another one, I don't know, if you can boot into the Live CD and operate from there, copying the relevant files to another computer, or external hard disk or USB-stick, or burn it on a CD- or DVD Rom.

And in next installs create a /home partition :)

Hope I have helped here.

Topsiho

---

### Post by Mark Phelps on 2009-05-07
There is no Catalyst 9.4 version that will work with your card, and the 9.3 version will not work in Ubuntu 9.04.  So, like so many of us, you're stuck using the open source video drivers.

Take a look at the link below for instructions for removing the fglrx driver and replacing it with the open source driver:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

