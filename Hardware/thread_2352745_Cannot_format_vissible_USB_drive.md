---
title: "Cannot format vissible USB drive"
date: 2017-02-15
forum: Hardware
---

### Post by superdude2 on 2017-02-15
Good Morning,
I have a problem with my Kingston DataTraveler 100 G3 64GB usb flash drive. I wanted to format it and backup my files from PC but cant delete anything at all. I see all files but its like they're somehow protected. I've tried many ways in terminal from google  but doesn't work . I don't think it has any switch for blocking data. I've also tried on Win10 with regedit but still nothing works. 
My OS is Xubuntu 16.04. 
That's why i'm asking You for help.

I look forward to hearing from you soon.

edit: something like that happened to me earlier but this one is the biggest so i don't want it to be dead so fast...

---

### Post by yancek on 2017-02-15
You should be able to format your usb drive with gparted, the partition manager.  It's not installed by default on an installed  Xubuntu but it should be on the installation DVD/flash drive.  In order to do this, you will need root privileges which means preceding any command with sudo.  The link below is to the GParted Manual which explains in detail how to do anything with partitions.

  [http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

Not knowing what you tried, it is difficult to advise.

---

### Post by superdude2 on 2017-02-15
Thanks you for answering.
I've tried gparted but it says > cant write to /dev/sdb, because it is opened read-only

I've also tried ddrescue and another soulutions from these sites:
[HTML]https://askubuntu.com/questions/101637/usb-turn-write-protection-off#138051[/HTML]
[HTML]http://www.makeuseof.com/tag/how-to-fix-write-protection-errors-on-a-usb-stick/[/HTML]
[HTML]http://www.pcadvisor.co.uk/how-to/storage/how-erase-write-protected-usb-drive-or-sd-card-summary-3633096/[/HTML]

---

### Post by sudodus on 2017-02-15
Have you checked if there is a microswitch, and if this switch is 'lock on' or something similar?

I suggest that you try also with ***mkusb*** - if the USB flash drive is healthy (electronically), but there is some confusing data in the partitiion table or bootloader area, you can wipe the first megabyte, and after that use any tool to create partitions again - or use mkusb itself to restore it to a standard storage device.

See these links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

If this does not work, you can try in another USB port, in another computer, and with another operating system. If still no luck, I am afraid that the USB flash drive is 'gridlocked', which is the first stage of failing. See the following link

[Pendrive lifetime](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

---

### Post by superdude2 on 2017-02-15
Thanks you for responding.

I said in my first post that i don't see any switch. Its [COLOR=#000000]Kingston DataTraveler 100 G3 64GB. [/COLOR]Maybe i'm wrong but i even searched Kingston site and couldn't find any info.
I installed mkusb but i don't think it worked. It can see my usb drive but says:
> dd: failed to open '/dev/sdb': Read-only file system  
0
# failed

I'm now unable to get some other PC and check if it works. Although on my TV(some samsung) i can browse and use all files like music, videos and pictures but same things work on my computer...

I'm now confused because i can browse all data previously sent to this device but cant delete nor send new ones.

---

### Post by sudodus on 2017-02-15
I suspect that the USB flash drive is gridlocked. It means that it is read-only, and cannot be made read-write again, at least not with tools available to regular users like you and me.

See [this link to a post by DuckHook](http://ubuntuforums.org/showthread.php?t=2178075&p=12805426#post12805426) describing what can happen, when the internal management of a USB flash drive gets 'so bogged down trying to free up old blocks that it just gives up the ghost'.

-o-

But don't give up yet, keep the USB flash drive and try later in another computer.

---

### Post by superdude2 on 2017-02-15
Thank you for replying.

I think that's the case. Is this damage in terms of warranty? I can't find receipt but i suspect that it's still on warranty. 
And are there any companies that specialize in that kind of problems and can fix it?

---

### Post by sudodus on 2017-02-15
If you can find the receipt, you can try to get the drive replaced.

Special services are very expensive, and only worthwhile in order to recover very valuable data. In this case you can still read the drive, so save what needs to be saved before it will be completely dead.

---

### Post by yancek on 2017-02-15
What was on the flash drive and is there any data you want to save?  Was it a Live system.  If no data, have you tried creating a new partition table for the device from the 'Device' tab at the top of the GParted window?  If you do this, make absolutely certain you have the correct device.  Other than what is suggested above, I don't know what else the problem would be.

---

