---
title: "Help with Hard disk recovery!"
date: 2008-07-13
forum: General Help
---

### Post by Wishtar on 2008-07-13
Hi all!
I have a Windows XP system, which works fine. I was running messengers, 1 firefox window and a couple of MS Word (07) windows, when I seemed to be having trouble with the Word. so I tried to shut everything down and suddenly, everything was dead slow, then it hung. I shut my PC down from the mains and now it won't restart!!
I get the startup options window (Safe, normal, best config, etc). and the process takes me as far as the windows logo and then I get a bluescreen for 1 nanosecond (so I don't know what it says) after which it starts the entire reboot process all over!!!! :(

Thankfully, I can log on and even access the internet using an Ubuntu LiveCD I have, but the problem is that I cannot access my hard drives (3 partitions, 1 hard drive)!!! I get the message: Error: Cannot mount the hard drives.

These have some important information and I don't have backups for all of it..
Any help will be greatly appreciated

Thanks a lot,
WIshtar

Edit: I've attached a screenshot of what the error message looks like. Thanks!!!

---

### Post by coffeecat on 2008-07-13
I'll tell you what I'd do, but you might want to wait and see if anyone has a better idea.

I'd consider that my data is more important than either the Windows installation or the hardware. Also, I'd bear in mind that although this appears to be a software issue in Windows, there could be a hardware problem in that machine - possibly a failing PSU, possibly anything.

So - I'd take the hard drive out and put it in a USB casing. Then I'd plug it into **another** machine (there might be a hardware fault in yours) running Windows, Linux or even a Mac. Macs can read NTFS Windows partitions, but not write to them, and all you want to do is copy off. Then I'd copy all my data onto backup media.

Only then would I put the drive back into the machine and investigate whether this was a software or hardware issue.

**Edit** - I've now seen your edit. The journal on the NTFS partition(s) needs repairing. If you put the HD into a USB casing you might be able to repair it from another Windows machine or from Linux with ntfsprogs installed. Does the Live CD come with ntfsprogs already installed? I don't know. You might want to look into this. Or, if you have a proper Windows install CD (not a manufacturer's image disk) you *might* be able to repair the filesystem with the recovery console.

---

### Post by tech0007 on 2008-07-13
Better call your PC vendor coz it's definitely a windoze issue (the BSOD, i mean). Linux ntfs support is still premature, and can damage your windoze install.  Unless you're willing to take the risk.

---

### Post by Herman on 2008-07-13
:) Hello Wishtar,
You probably just need to run a file system check in the partitions in your hard disk.
The best way to run a file system check in a Windows partition is to use a Microsoft Windows 'Installation Disk'  and boot it to a console and run 'CHKDSK /R'.
If you don't have your own Windows 'Installation CD', maybe you can borrow one from a friend.
Here's a link which contains more links about how to run a file system check in Windows, [NTFS and FAT32 file system repair and maintenance]("http://users.bigpond.net.au/hermanzone/p10.htm#NTFS_File_Fystem_Repair_and_Maintenance") - Windows CHDSK - Linux ntfsfix.
I hope some of that info will help you.
Regards, Herman :)

---

### Post by coffeecat on 2008-07-13
> **tech0007 said:**
> Linux ntfs support is still premature, and can damage your windoze install.

Have you anything to back up that claim? At least something recent.

---

### Post by Wishtar on 2008-07-14
Thanks Coffeecat. I have a windows CD which I can use to run a system recovery with. I'm going to do that tonight and get back on this.

Thanks for all the responses. I hope this works, though. If not, I'll try the other options provided here.

Wishtar

---

### Post by Rhubarb on 2008-07-14
A friend of mine had exactly this problem a few months ago.  It's easily fixed too.

Open up a terminal Applications --> Accessories --> Terminal
Then enter this in:
```
sudo fdisk -l
```
This will give you a list of all the partitions you have available on your hard drive.
This should tell you which partition is your ntfs windows partition that's locked.  Take a note of it (it should be something like **/dev/sda1**)
Then to let Ubuntu unlock the drive, in a terminal, type this in (make sure to use **/dev/sdaX** where **X** is the number of your problematic locked ntfs windows partition):-
```
sudo mount -t ntfs-3g **/dev/sdaX** /media/disk-1 -o force
```

You are then able to browse the partition and backup your data easily.

---

### Post by Wishtar on 2008-07-14
Thank you, coffeecat, tech0007, Herman, and Rhubarb.
My comp had crashed on me last night at around 930 PM. I had it fixed before 9 PM today, i.e. within 24 h of the issue!
What I did was (1) prayed really hard all night to ensure my comp gets functional ASAP
(2) Immediately load Ubuntu and use the network connecivity to post on this forum for help
(3) Tried to access my drives and identified what was wrong (and posted a screenshot here).

What happened was:
1. I got a lot of responses: a) all the responses here b) friends who knew linux and supported ubuntu c) friends who knew to fix Windows errors.
2. I took printouts of all the posts and used Rhubarb's suggestion for trying to mount. I managed to get C:/ mounted and IMMEDIATELY backed up ALL THE IMP stuff there. This didn't work for the other 3 partitions.
3. I used coffeecat's suggestion about the system recovery by using Windows and 
Voila!
I'm here, I lost nothing,
And I'm eternally grateful to all your support.

Thank you, all!

Wishtar.

---

