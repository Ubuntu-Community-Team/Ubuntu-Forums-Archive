---
title: "Partitioning Confusion"
date: 2006-01-01
forum: Installation &amp; Upgrades
---

### Post by DoctorLes on 2006-01-01
:confused: Hi,

I burned an ISO install disk for Ubuntu 5.1 after downloading the file a couple of days ago.  It boots up nicely to the installation assistant and finds all my hardware and such.  But I get confused when it runs the partition app.

It shows my two physical drives, both 40 Gigs.  They are hooked-up in an unusual relationship, using a toggle switch I mounted on my case cover.  One position has Win '98 on it and the other has Fedora Core 3.  I can boot either Win '98 or FC3 by throwing the toggle switch, so long as it's before hitting the power button. 

OK, now the partitioner seems to identify both of my drives, even though I thought the toggle switch might prevent that--apparently not.  As best I can recall, the toggle switch uses an old jumper with leads attached, salvaged from some dead 486 box years ago.  I believe it shorts the master/slave option, but I may be wrong; haven't been able to find the schematic for the hack that I used.  

Anyway, I'm showing about 109 MB in the primary of one of the HD's, according to the partitioner.  

I want to keep Win '98 on the one, seperate, physical hard drive, so I can still toggle it on during those rare occasions I want to run Win '98 (I would have wiped it, but I'm afraid I have some old apps, or files on it that I don't want to lose, including passwords and activation keys and such). 

But I do want to divide the other hard drive, the one that already has FC3 on it, so I can dual boot either FC3 or Ubuntu. I am not particular otherwise, and am OK with dividing whatever space there is right down the middle.  Of course, I don't want to lose a byte of my data from my FC3 installation either ;)

So, given the options I visualize on the partitioner window, which should I choose to meet my goal?  Would you mind walking through each step?

Thanks very much for your time.

And Happy New Year!

---

### Post by Herman on 2006-01-01
DoctorLes, I have a website in my signature link underneath this text, and it shows illustrated examples of three slightly different styles of Ubuntu install, dual boot with Windows.
I am not sure about your arrangement with the hard drives. I have no first hand experience yet with more than one hard disk per machine. Adding in the interesting arrangement you describe makes me feel a little nervous. I might not be experienced enough to help you with this all the way. I might need to sleep soon too.
Nevertheless, the 'sig link' website might help to guide you, and you should be able to achieve your goal, but I can't predict whether it will be simple or not. We might be lucky, or we might have to work a little for it. You could have complications with the boot loader, (GRUB).
I would recommend making yourself a GAG boot CD, or, have a 'System Rescue CD' handy, (which has GAG on it), as that will be able to boot Windows 98 for you in the event your new GRUB boot loader needs manual configuring to get it working properly. 
All will be clearer when you click on the 'sig link' and have a look around. I think you will likely want the 'Ubuntu+FAT32 flavour for your install, since you have Windows 98, which will have the FAT32 file system for Windows. 
You will also find a page on how to make a GAG boot floppy, among other things. :D (Herman)
Oh, and 'Happy New Year' back.

---

