---
title: "Please HELP partition table lost"
date: 2007-03-19
forum: Hardware &amp; Laptops
---

### Post by T31 on 2007-03-19
Hi all,

I just bought ,yesterday :( an Fujitsu siemens amilo pi 1505.

It is a great laptop I am very happy with it, everything works right out of the box

So my problem is installing Feisty I have lost my partition table, Ubuntu can see the hard disk but windows can not, I cant install any windows because tells me there is no hard disk at all. ](*,) 

And the point is that ubuntu sees the hard disk and I can work with it normally

For work and wife reasons I need to have windows running on this machine

Anyone can help me? pleeeeeeeeeeeeeeease I am really desperate  [-o< 

everything I have seen in google is or for windows or to restore a mbr from a back up.

Thanks in advance,

edit: I have tried already to make fat32 partitions but still windows doesnt see them and in the bios everything looks ok :(

---

### Post by Scunizi on 2007-03-19
I need you to help clarify something.  Did this laptop come with windows installed? Did it come with rescue CD's or a normal windows installation cd?  When you installed Ubuntu did you wipe out the original windows install?

---

### Post by T31 on 2007-03-19
Yup It came with Vista basic installed and with a recovery dvd, and when I tried to run the recovery dvd, it can not see the hard drive and the system just freeze.

At least in the case of Windows XP tells me that doesnt see the hard drive.

Thats when I tried just cleaning whole drive and leaving only one fat32 partition.

It didnt help :/

And hey thanks for the quick reply I really appreciate

---

### Post by Scunizi on 2007-03-19
No problem.  You might want to download the iso for gparted from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) and burn it.  It's a live cd so you can boot to it.  Then use gparted to delete all your partitions.  Don't create any new ones and don't format it.  Shutdown and then put your xp or vista disk in and see if it can see it.  If it can't see the drive still, you might have to go into the bios of the machine and check the settings, although I don't think that is your issue.  Report back what happens.

---

### Post by T31 on 2007-03-19
Right now I am still at work but I will check it out as soon as I get home.

There is one more possibility from Saint Google :) it is possible that Windows XP is not seeing the hard drive because is SATA. But again, then why Vista recovery dvd freezes?

As well a friend told me about this site [ http://www.hiren.info/pages/bootcd]("http://www.hiren.info/pages/bootcd")

In any case I will let you know, thanks indeed for your help :D

---

### Post by T31 on 2007-03-20
ok fixed :D (I hope)

that was the issue, windows xp cant recognize a SATA hard disk without an additional driver, that you only can give him with a floppy (exactly that thing that my laptop is missing)

It seems that definitely I really messed up the whole partition table because last 2 times I tried to start the computer ubuntu freezes trying to check it.

So what I did is what you suggested use gparted, I had an old copy of dapper so I used to delete everything and then I tried the recovery dvd and reinstalled Vista.

It seems up to google that Vista has his own tool for partitioning so I am going to use it to free as much space as I can for GNU/Linux

Thanks a lot for your help, I was really desperate, a brand new laptop :P thanks again

---

