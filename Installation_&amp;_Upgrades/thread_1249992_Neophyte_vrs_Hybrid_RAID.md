---
title: "Neophyte vrs Hybrid RAID"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by Harry Voyager on 2009-08-26
So, I'm completely new to Linux, and I'm attempting to install a copy of Ubuntu 9.04 as the 2nd operating system for an XP-Linux dual boot. Unfortunately, it turns out that I have a problematic hardware.
 
The current system is a Core 2 Duo, in a Gigabyte GA-EP45-UD3P. The video card is an EVGA GeForce 880 GTX ([http://www.newegg.com/Product/Product.aspx?Item=N82E16814130072](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130072)). XP is installed on a Hybrid RAID 0 on the ICH10R controller. I want to install 64 bit Ubuntu on a third sata hard drive currently plugged into the Gigabyte RAID controller, which is currently in ACHI mode in the BIOS, without nuking my XP, and preferably with some degree of mutual access between both.
 
Any suggestions on how I go about doing this?
 
Harry Voyager

---

### Post by ronparent on 2009-08-26
You don't say if the third disk you plugged in is incorporated into a raid array thru bios. If it is, you probably have to use the alternate cd since the standard live cd does not automatically have raid support. If the sata port you plugged into is not configured as a raid then you would be able to do a normal (non raid) install.

Be aware that raid drives will show up as unallocated space if you try to install from the live cd. If you do not install software ubuntu requires to recognize the raid you can easily wipe out the raid0 array and all its data. The raid you are using incidently is commonly refered to a 'fakeraid' within the ubuntu community. The following reference tells you how you can deal with it to install to raid: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Harry Voyager on 2009-08-26
The third drive, that I want to install Linux on, is not in the array.  I believe it's actually on a separate SATA controller entirely.  As I understand it, this motherboard has two SATA controllers, one in the ICH10R southbridge, and a second, (I think made by JMicron, possibly the JMB363?) that's called the Gigabyte SATA2 (which also appears to control the P-ATA as well, badly.)
 
Thanks for linking me to that HowTo.  I think that may be what I need; I'll try that when I can bring my work laptop home, and see what happens.
 
On the RAID naming convention, it wouldn't seem to me that FakeRAID implies the level of hardware dependence that this type of RAID has.  Is SoftRAID hardware indepented?  Can you take a SoftRAID array and plug it into a new controller without destorying the array?  Basically, I'm wondering if this is just an implimentation of software raid where the software is split between the SATA controller and the OS, or if this is actually a fully distinct type of RAID.
 
Take care,
 
Harry Voyager

---

### Post by ronparent on 2009-08-26
Your issue will be that you will be dual booting with XP. The software raid is totally incompatible with windows. If you want to access data drives created on the raid from a linux based system you are basically stuck with the MB fakeraid implementation. Ubuntu doesn't use drivers per se as would windows, but uses software called dmraid. Once ubuntu is installed on your non-raid drive you will have to install dmraid to access the raid drives from ubuntu. But one thing at a time. I recommend changing the boot order in bios so that you boot from the 3rd drive and then install ubuntu to it from the live cd. This installation process will install a grub bootloader to that third drive and write the instructions to allow dual boot to windows/ubuntu. I have used such an approach myself and in a pinch was able to always access windows by reverting the boot order.

Once you get ubuntu up and running on the 3rd drive, I can instruct you how to mount the raid partitions so you can access them, if you so wish.

---

### Post by Harry Voyager on 2009-08-30
[LEFT]Sorry about the delay. Took me this long to get my work machine home. It's been an interesting week.[/LEFT]
 
[LEFT]So I started following the FakeRaid How To you link me too, and after some extraneous detours I got to activating dmraid, which promptly announced that my raid array has some problems. To quote:[/LEFT]
 
```

ERROR: isw device for volume "Vista" broken on /dev/sdb in RAID set "isw_bafbghgea_Vista"
[LEFT]ERROR: isw: wrong # of devices in RAID set "isw_bafbghgea_Vista" [1/2] on /dev/sdb
ERROR: isw device for volume "Vagabond" broken on /dev/sda in RAID set "isw_eajhaehdeh_Vagabond"

ERROR: isw: wrong # of devices in RAID set "isw_eajhaehdeh_Vagabond" [1/2] on /dev/sda
[LEFT]RAID set "isw_bafbghgea_Vista" was not activated
RAID set "isw_eajhaehdeh_Vagabond" was not activated[/LEFT]
[/LEFT]


```
[LEFT]

 [LEFT]I think I know what happened, but I'm not sure how to fix it, short of rebuilding the array from scratch (which would be un-fun).[/LEFT]
[/LEFT]

 
[LEFT]I'll have to check this when I reboot into XP, but I believe "Vista" is the name of the drive that was built on the my Raid array previously. I believe "Vagabond" is the drive that was built onto that array after Vista (the OS, not the array) died. While that required a full reformat, I didn't rebuild the array, so it is possible that some parts of it still exist.[/LEFT]
 
The other possibility that springs to mind is that this is remnants of the original XP/Vista64 install when I managed to end up with two copies of Vista in the boot menu, one of which booted Vista, the other of which didn't...
 
Any ideas on how I could fix this? Would rebuilding the array even fix it?
 
Thank you,
 
Harry Voyager
 
 
[LEFT]Addendum: All right. Rebooted in the XP, and checked the devices on this end. This OS and the controller are identifying the array as "Vista", which probably means that "Vagabond" was the original array that I managed to break in the original XP/Vista install, which means this is the phantom OS that's been with my machine since the beginning, not an artifact of the recent reinstall. This likely means that rebuilding isn't going to fix this, but will instead leave another ghost boot on the system, given that's pretty much how I got the first one.[/LEFT]

---

### Post by ronparent on 2009-08-31
Harry: You are now delving into strange territory. If I were to venture a wild guess, it appears like the meta data on the disks is corrupted. If xp is happy with the current situation it seems dangerous to try to correct the situation with dmraid - xp could be left inoperable. Although dmraid could delete the vagabond meta data there is no way to predict how that would affect xp? If you have the means available, you should probably try to examine and correct any partition errors on those drives within xp. You ultimately have to be able to activate the _Vista array to be able to mount it. Incidently is it a raid0 or raid1?

---

