---
title: "Hard drive failure, cannot mount partitions from Live CD"
date: 2016-02-13
forum: Hardware
---

### Post by Steve Mosen on 2016-02-13
I know this is a long-shot, but thought I'd try.

My hard drive failed 2 days ago.  It is a Dell desktop (Vostro 260) and the Dell diagnostic test came back with "DST long test unsuccessful" and error code 2000-0142.

All my important stuff is backed up, but I think there may be some photos that I didn't get around to saving off to my NAS.

Booting with a live CD of GPARTED, I can see the partitions (/dev/sdaX, where X=1 to 7), but not do anything with them.  GPARTED tells me "No file systems found on /dev/sda".

Booting with a live CD of Ubuntu 12.04 lets me run the machine, but not do anything with the hard drive.  Some of the hardware commands show the partitions and some don't.  I would like to mount the data partition to see if there is anything there I want.  

Trying to mount a partition gives me a "can't read superblock" message [http://pastebin.com/RrqWqEvY](http://pastebin.com/RrqWqEvY)

I have been Googling this over the past couple of days and got nowhere so far, any help would be appreciated.  I am a novice at this so any instructions will have to be explicit ;)

I've seen many requests for the output from lshw - you can see it at [http://pastebin.com/cyxzqAcD](http://pastebin.com/cyxzqAcD)

Thanks in advance,
Steve

---

### Post by sudodus on 2016-02-13
Welcome to the Ubuntu Forums :-)

Is it clear from the Dell diagnostic test if it is a hardware problem (bad sectors on the disk surface) or a software problem (damaged file system)?

If a hardware problem and very important to save files, you should stop using the failing drive, except that you should try to clone it (or the parts of it that can still be read).

ddrescue is a tool to do that. After cloning you should use other tools to repair the file system(s) and recover the files you want.

Otherwise you don't want to spend that much effort, and you can try to repair the file system(s) and recover the files (photos in this case) directly from the failing drive.

What file system was there on the partition where you kept the photos?

See this link for more details, and ask if you need more help.

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

### Post by weatherman2 on 2016-02-13
Gparted isn't the right tool for this.  You aren't trying to edit partitions.

I would first install GSmartControl - a tool that lets you check S.M.A.R.T. Attributes and run tests.  There may be Linux live boot discs that already included GSmartControl, but if not it's easy to install on an Ubuntu live boot if you have an internet connection.  But first, start up Ubuntu Software, and edit the "sources" of software to add the "Universe" repository (check the box that is unchecked and Apply, then wait until the update completes).  Then search for "GSmartControl in Software Center and install it.

(There is an older version of the Parted Magic Linux CD that is still free - on Major Geeks - that includes GSmartControl, should work fine on older systems.  That might be easier for you than installing GSmartControl as above - not sure.  GSmartControl is called "Disk Health" on the Parted Magic desktop.)

Then start GSmartControl and check the Attributes of your drive.  Just see what condition it is in or even if the drive's health can be read at all.  If you have thousands of bad sectors, or if the drive simply can't be recognized there, you should probably give up.  If you have only a few bad sectors, you can try one of the other solutions like testdisk or ddrescue to try to recover files.  But be aware that ddrescue is not a simple tool for novices to use.  Testdisk might be able to fix a corrupted file system and allow you to mount it just to get some files off pretty easily.

---

### Post by Steve Mosen on 2016-02-13
Hi sudodus, thanks for taking the time to respond.

The Dell error code indicates a hardware failure.  I bought the computer in 2012, so that is spot on for the average 4 year lifespan.

The data partition is NTFS.  I was dual booting Windows 10 and Ubuntu 14.04.

I'll read through the link about repairing and post any updates tomorrow.

---

### Post by Steve Mosen on 2016-02-13
Hi Weatherman2, thanks for the comments.

I was only using Gparted to check the partition attributes.

I installed GSmartControl, but unfortunately the drive is coming up as "Unknown model" and SMART status is unsupported.

---

### Post by weatherman2 on 2016-02-13
You may need to go into BIOS setup (restart the computer then hit F2) to enable S.M.A.R.T. on that drive.   Or - the drive may just be completely dead.

---

### Post by sudodus on 2016-02-13
> **weatherman2 said:**
> You may need to go into BIOS setup (restart the computer then hit F2) to enable S.M.A.R.T. on that drive.   Or - the drive may just be completely dead.

+1

---

### Post by Steve Mosen on 2016-02-14
There doesn't appear to be an option for SMART.

F2 gets me into "Aptio Setup Utility".  I can only see HDDs mentioned under **Main** and **Boot**.  **Main** just shows drives under "Device Information" but I can only change the system date/time and **Boot** just lets me change boot order.

---

### Post by sudodus on 2016-02-14
Are you still able to 'see' the hard disk drive as a mass storage device /dev/sdx, where x is the drive letter (a for the first one). In that case you can try according to post #2.

A shortcut is to use ***photorec*** to recover photos directly from the drive. See this link (and links from it), [https://www.cgsecurity.org/](https://www.cgsecurity.org/)

If it is not possible, the drive is probably so damaged, that you cannot get any data from it with 'our free' methods. A specialist company can still get data from it, but it costs [a lot of] money.

---

### Post by Steve Mosen on 2016-02-14
Yes, the HD appears in lshw output as /dev/sda1 (see pastebin from post #1), but the partitions do not.

I've downloaded PhotoRec on to USB, but can't get it to run under Live CD.  I have tried following the instructions from [http://askubuntu.com/questions/23108/trying-to-make-file-executable-on-usb-but-the-permission-doesnt-stick](http://askubuntu.com/questions/23108/trying-to-make-file-executable-on-usb-but-the-permission-doesnt-stick) and [http://askubuntu.com/questions/22778/how-can-i-run-an-executable-from-a-cd-when-it-doesnt-have-the-executable-bit-se](http://askubuntu.com/questions/22778/how-can-i-run-an-executable-from-a-cd-when-it-doesnt-have-the-executable-bit-se) but get an "Operation not permitted" error ([http://pastebin.com/PQUVeSHW](http://pastebin.com/PQUVeSHW)).

Also, e2fsck didn't like my /dev/sda1 ([http://pastebin.com/wwVaSGxW](http://pastebin.com/wwVaSGxW)).

I know it's not looking good.  Is it time to give up?

---

### Post by Steve Mosen on 2016-02-14
An update.

I found instructions about formatting an ext file system on a USB would allow executable files, so I did that and got TestDisk running.  Initially it couldn't find a partition and a "Quick Search" resulted in countless read errors...

PhotoRec doesn't appear to recognise the data partitions, it sees /dev/sda and gives me an unknown partition to select, then a filesystem choice of either ext2/ext3/ext4 or other (being FAT, NTFS etc).  However both selections just result in a listing of the USB contents...

---

### Post by sudodus on 2016-02-14
It does not look good. I'm afraid that your HDD is dead.

---

### Post by Steve Mosen on 2016-02-14
Thanks very much for your time sudodus (and weatherman2) - much appreciated.

Time to start looking into how to do a hard drive swap :-)

---

### Post by weatherman2 on 2016-02-14
If you have a NAS already, you probably don't need much storage space.  So I'd go for an SSD for the speed.  You can get a 250GB SSD for about $70 USD shipped, routinely.

Replacing a desktop PC hard drive is usually easy, and your Dell might even have a screwless plastic caddy to make it super simple.  If you go for an SSD (laptop drive size), you'll need a 2.5" to 3.5" adapter as well.

---

### Post by sudodus on 2016-02-15
> **weatherman2 said:**
> If you have a NAS already, you probably don't need much storage space.  So I'd go for an SSD for the speed.  You can get a 250GB SSD for about $70 USD shipped, routinely.

Replacing a desktop PC hard drive is usually easy, and your Dell might even have a screwless plastic caddy to make it super simple.  If you go for an SSD (laptop drive size), you'll need a 2.5" to 3.5" adapter as well.

+1 :-)

---

### Post by Steve Mosen on 2016-02-18
Thanks guys.

I would look into that, but I've got a spare 1TB drive that came "free" when I bought my NAS (it currently has 2 2TB drives in it).  I put it in last night and will be looking around here to find a recommended partitioning set up for dual booting Windows and Ubuntu 14.04.

Cheers,
Steve

---

### Post by Steve Mosen on 2016-02-18
Actually - forget the dual boot, I've just seen this: 

> [COLOR=#333333][FONT=Ubuntu]This page describes how to set up your computer in order to dual boot Ubuntu and Windows. [/FONT][/COLOR][IMG]https://help.ubuntu.com/moin_static193/light/img/icon_eek.png[/IMG][COLOR=#333333][FONT=Ubuntu] While there are some benefits to dual-booting (e.g. better performance for a native install), it is not recommended. Instead, it is best to do a native install of Ubuntu, and then virtualize the other operating system.[/FONT][/COLOR]

from [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)


My laptop still dual-boots, so I might try the visualisation route.  If anything, I'll learn more about Ubuntu, which can only be a good thing.

---

### Post by kurt18947 on 2016-02-18
> **Steve Mosen said:**
> Actually - forget the dual boot, I've just seen this: 



from [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)


My laptop still dual-boots, so I might try the visualisation route.  If anything, I'll learn more about Ubuntu, which can only be a good thing.

I have a couple Windows 10 installs running in VirtualBox. For simple things such as web browsing or office stuff it seems to work fine. The only thing that was a little tricky was getting a Samsung networked printer to work. The default virtual network adapter uses NAT. I could ping the printer but couldn't get it to print. Fortunately there are 4 virtual ethernet adapters available :cool:. I configured a second adapter as bridged and now everything works as expected.  Running Windows in a VM probably wouldn't be a good idea if you're a gamer. The max video memory I've been able to create on a Thinkpad with Intel graphics is 256 MB which I suspect is pretty low for gaming. I'd want an absolute minimum of 4 GB. RAM with a Windows VM as well and 32 bit Windows requires less RAM than 64 bit Windows. 

If someone needs Windows to run something like Solidworks, Adobe CS or other graphics intensive use, a VM may not cut it. Setting up Windows dual boot on a machine with 'traditional' BIOS seems pretty simple and reliable. On machines with UEFI BIOS, it seems like a "YMMV" situation. It may be pretty straight forward or it may be very difficult.

---

### Post by Steve Mosen on 2016-02-18
Thanks for the comment Kurt, it gives me some confidence that going virtual should be fine.

I'm not a PC gamer and for anything intensive I can stick with Ubuntu.

---

### Post by weatherman2 on 2016-02-18
I do it both ways - dual booting and virtual machines.  Virtual Windows within Ubuntu is really handy - I use it for running tax software and using Canon scanning software for my all-in-one printer/scanner that works better than the generic scanner stuff I've found for Linux.  (I had no trouble getting my Canon printer working via network.)  On the other hand, dual booting really isn't a big issue on a single hard drive anymore, either.  I've done it so many times that I never think about it.  It's just inconvenient to have to shut down and reboot into Windows.

There may be a few things that won't work well in a virtual machine in Windows.  Sometimes you need to do things like update your GPS - software works only in Windows - and the USB port may not be exposed through the virtual machine automatically (possible to make it work - but not automatic).  And of course, to do something like update a firmware or BIOS you will need a native Windows install not a virtual machine.

If you have a 1TB drive, personally I'd do the dual boot AND maybe the virtual machine.  You can always erase the dual boot Windows partitions later.  It's just a little more work now but harder to do later.

I'd re-install Ubuntu using LVM if you didn't the first time.  That makes things like expanding your partitions and real-time backup of the OS far easier.

---

### Post by Steve Mosen on 2016-02-18
Hi Weatherman

I'm afraid your comment was just a little too late, I just finished the install (with LVM).

The satnav update isn't an issue as I have a Windows/Ubuntu laptop as well.  If I struggle with the virtualisation, I can always start over later with a dual boot - the laptop is getting on a bit, so that may be good insurance anyway.

---

### Post by weatherman2 on 2016-02-18
No worries!  Glad you used LVM, anyway.  The main point I wanted to make is that dual booting on a single drive really isn't that big of a worry.  There are a few helpful tips people might try to understand before proceeding, but it's not the nightmare some have made it out to be.  I consider it routine.

---

