---
title: "Grub Hangs"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by linuxuser21 on 2009-04-15
I've installed Jaunty and it installed Grub 1.5.  It says that it installed successfully and I restart it.  Grub comes up and it says "Grub loading
please wait..."
That's as far as it gets.
I've reinstalled the entire thing, I've ran a Disk integrity & it says that the disk is without errors.  I've also tried to refresh the Grub from the live CD with:
```
sudo bash
mount /dev/sda1 /mnt
grub-install /dev/sda --root-directory=/mnt --recheck
```
Still no go though.

---

### Post by Herman on 2009-04-15
I suggest downloading a copy of [Super Grub Disk]("http://www.supergrubdisk.org/") and using that to boot with.

It's very strange that you're only getting as far as  "Grub loading
please wait...". 
There are three stages of GRUB, and I think the message you're being left with is from the stage1_5 before it loads stage2. 
Your stage2 of GRUB doesn't seem to be working. That could be caused by a corrupt stage2 file.  
What you have done already was the best logical solution and that should have fixed it.

When you use Super Grub Disk, you'll need to find the option 'Boot Gnu/Linux Directly', somewhere in Super Grub Disk's menus.
If you try a configfile boot or a chainloader boot, you'll only get a repeat of the same error message, because you'll still be trying to boot through your own stage2 of GRUB.

If you don't mind using the command line (recommended), you could do a 'direct boot' manually. Press your 'C' key from any menu in Super Grub Disk for [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")  and do a [Direct (kernel) Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.").

---

### Post by Herman on 2009-04-15
Is there anything unusual about your hard disk or about your installation that you can think of?
Some flash memory drives pause for a while in the early stages of booting, but they should continue to boot up. Some SSD drives might too, I'm not sure. It might have something to do with the wear levelling method used in some types of flash memory.
What file system did you install Ubuntu in?

---

### Post by linuxuser21 on 2009-04-15
> **Herman said:**
> I suggest downloading a copy of [Super Grub Disk]("http://www.supergrubdisk.org/") and using that to boot with.

It's very strange that you're only getting as far as  "Grub loading
please wait...". 
There are three stages of GRUB, and I think the message you're being left with is from the stage1_5 before it loads stage2. 
Your stage2 of GRUB doesn't seem to be working. That could be caused by a corrupt stage2 file.  
What you have done already was the best logical solution and that should have fixed it.

When you use Super Grub Disk, you'll need to find the option 'Boot Gnu/Linux Directly', somewhere in Super Grub Disk's menus.
If you try a configfile boot or a chainloader boot, you'll only get a repeat of the same error message, because you'll still be trying to boot through your own stage2 of GRUB.

If you don't mind using the command line (recommended), you could do a 'direct boot' manually. Press your 'C' key from any menu in Super Grub Disk for [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")  and do a [Direct (kernel) Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.").

Thanks, I'm going to try the USB version.

---

### Post by linuxuser21 on 2009-04-15
> **Herman said:**
> Is there anything unusual about your hard disk or about your installation that you can think of?
Some flash memory drives pause for a while in the early stages of booting, but they should continue to boot up. Some SSD drives might too, I'm not sure. It might have something to do with the wear levelling method used in some types of flash memory.
What file system did you install Ubuntu in?

Oh yeah, It's really different.  3 RAID hard drives (only 2 work though) & one IDE one.  I installed it onto the RAID drives.  The IDE hard drive had 8.10 on it because it came out of my previous computer.  It worked with a 8.10 installation though.

---

### Post by Herman on 2009-04-15
> Oh yeah, It's really different. 3 RAID hard drives (only 2 work though) & one IDE one. I installed it onto the RAID drives. The IDE hard drive had 8.10 on it because it came out of my previous computer. The installation worked with a 8.10 installation though.Aha! There's your problem then. 
I'm sorry, but I don't know very much about how to boot a RAID array. 
I know that GRUB does support RAID, but I think there are some extra tricks you need to get it working. 
I think probably one thing you may need is a separate /boot partition. I'm not sure because I also know there are a lot of different kinds of RAID, which made it seem like too much work for anyone hoping to learn how to help people with it. I did begin trying to learn all about RAID at one time, but gave up. 
Hardware RAID, software RAID, mirrored RAID, striped RAID . . . all the different brands of hardware RAID, - it's too much.

I hope at least you might be able to boot it with Super Grub Disk for now.

It's a shame that no other RAID users seem to want to hang around and give GRUB help.

There is an excellent video how-to available from [**Ubuntu Screencasts.com**]("http://screencasts.ubuntu.com/") called   [Installing Ubuntu Part2]("http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2") and that shows how to set up software RAID with the Ubuntu 'Alternate' CD. That might help you, (depending on what kind of RAID you have or want).
If you already have Ubuntu installed, I doubt if you want to install it again except as a last resort though.

What kind of RAID do you have exactly, I could try looking in my links or see if I can sniff out something for you through some searches of  the official GRUB site, the Ubuntu Community Docs or Ubuntu Wiki or Google.

---

### Post by linuxuser21 on 2009-04-15
I didn't know that there was so much to it.  I'm defienetely going to have to do some reading.  Well, I will study these links that you gave me.  Hopefully I can figure something out.  Thank you much!

---

### Post by Herman on 2009-04-15
Well , I guess 'Hardware RAID' is something you get as a feature when you buy a new computer or motherboard, or maybe a special hardware RAID card, which fits in a slot in your motherboard, I'm not sure. Anyway, here's a link I saved about that, [RAID Optimization Guide]("http://www.adriansrojakpot.com/Speed_Demonz/IDE_RAID/RAID_01.htm") - by Ken NG.

This link though, from the Ubuntu Community Docs, says that a lot of 'Hardware RAID' is not real RAID, but 'Fake RAID', so the document is titled, '[FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")' - Ubuntu Community Docs.

'Software RAID' is a feature in the Ubuntu installer and you don't need any special hardware. That's the kind you'll see explained in the above-linked video how-to.

Here's a link from the GNU-GRUB Wiki, '[LVM and RAID]("http://grub.enbug.org/LVMandRAID")'. I think they're talking about GRUB2 there, but they do mention that GRUB has supported RAID since 0.95.
Here's another GNU-GRUB Wiki link, [Setting up GRUB to boot from both disks of mirrored RAID]("http://grub.enbug.org/MirroringRAID").

Here are a couple of old Ubuntu Web Forum threads, I can't remember why I bookmarked them now, I must have found something interesting in them, [Does ANYONE have a working Feisty fakeraid installation?]("http://ubuntuforums.org/showthread.php?t=421405&highlight=grub")  and [Install with Raid 0]("http://ubuntuforums.org/showthread.php?t=413647&highlight=grub").

I hope those links will be least a little bit of help to you. Sorry I can't give you more direct help.

Let us know how you go,
Regards, Herman :)

---

### Post by linuxuser21 on 2009-04-15
I've got a HP ProLiant ML350 G4.  It came with 3 Raid hard drives and a PCI Smart Array controller to run them.  I'm glad you have some links that I can find some information on this.  This computer is originally a server, so if you are working on one, chances are is that you are probably doing it for a business.  Which means you've got a degree and you're supposed to know what you are doing with it; so there is not much documentation on it.  Lol.

---

### Post by ronparent on 2009-04-15
Just a suggestion. Since you have 8.10 installed on a non-raid ide, why not reset your bios to use this ide disk as boot. You can then install and run dmraid to that 8.10 install which will map out your raid array. In computerese gobbly-gook this will create a sybolic link to your array in /dev/mapper. This link can direct you step by step in setting up and accessing the raid array for installs:

[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

Fake Raid is the termenolgy used to describe a motherboard implemented raid. Although there is usually a raid bios that can be accessed on boot to configure the raid, you actually need a driver or software link installed to allow you to use the raid array. Dmraid is that link.

---

### Post by linuxuser21 on 2009-04-15
> **ronparent said:**
> Just a suggestion. Since you have 8.10 installed on a non-raid ide, why not reset your bios to use this ide disk as boot. You can then install and run dmraid to that 8.10 install which will map out your raid array. In computerese gobbly-gook this will create a sybolic link to your array in /dev/mapper. This link can direct you step by step in setting up and accessing the raid array for installs:

[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

Fake Raid is the termenolgy used to describe a motherboard implemented raid. Although there is usually a raid bios that can be accessed on boot to configure the raid, you actually need a driver or software link installed to allow you to use the raid array. Dmraid is that link.

Like I've mentioned before, it was made to be a server and so, I'm no quite sure if the BIOS has an option to boot off a IDE hard drive.  If there is, I don't know where it would be at.  It does, however have an IDE CD/DVD drive option in the boot order.  So, it might.

---

### Post by ronparent on 2009-04-15
Generally a system that uses both SATA and IDE can be configured in bios to select a boot order regardless of how the drive is connected. The fist boot screen will tell you what key to press to access the bios. You then have to search thru the bios screens for where all the hard drives are listed. That screen should tell you how to move the hard disk in boot order.

---

### Post by linuxuser21 on 2009-04-16
Okay, I did a number of new things.  I reinstalled it with a separate boot partition on the RAID drive and that didn't work.  Then, I've tried it with a separate boot partition on the IDE drive and now I get "Error: 15".  So, I did get somewhere I guess.  Lol.

---

### Post by ronparent on 2009-04-16
Error 15 suggests either a spelling error or incorrect syntax in menu.lst for the kernel you are trying to boot. Lets see a post of just the menu section of the grub menu.lst. If that's the case it might be easy to correct???

---

### Post by linuxuser21 on 2009-04-16
Well, this is solved.  Upon looking at devices.map in the grub folder, I realized that I didn't have the IDE hard drive in when I installed 8.10.  So, I took it out, installed 9.04 and it works now.  Thanks everyone for your help!

---

