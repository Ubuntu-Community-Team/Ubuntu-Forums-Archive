---
title: "Dual boot Vista/Ubuntu on two separate hard drives"
date: 2012-02-26
forum: Hardware
---

### Post by joncann on 2012-02-26
I kinda fell into Ubuntu and fell in love with the OS. My wife hates it though - I hate Vista. I've got a hard drive with Vista installed. Is there any easy way to hook the second hard drive into this Ubuntu machine without a complete reformat? 

I'm pretty much a novice when it comes to most of the hardware and have never tried to run two hard drives let alone two operating systems. I'm not even sure what information to give to make this question easier to answer.

---

### Post by ahallubuntu on 2012-02-26
Pretty easy to do.  There are a few methods.

The first thing to do, though, is: make sure the Vista drive is the first one seen in the BIOS (and by the operating system).  If these are SATA drives, I assume, on your motherboard, the SATA connectors are probably numbered.  Figure out which one is the first one (SATA0?  SATA1?) and plug the Vista drive into that one and the Ubuntu drive into the other one.  That will help Vista not get confused about it being on the 1st vs 2nd hard drive in the system.  Ubuntu generally doesn't care.

Next, you need to either tell Vista how to boot Ubuntu or install Grub on the Vista partition so you'll get a boot menu of Ubuntu or Vista when you turn the power on.

The easiest way is to install Grub on the Vista drive.  To do that, you boot up your Ubuntu live CD with both drives plugged in as described above, then update grub and install it on the Vista drive.  However, before doing that, in a terminal I highly recommend you do this:

sudo dd if=/dev/sda of=./vista.mbr bs=446 count=1

This will create a file called vista.mbr in current directory.  SAVE that file in case you need to restore Vista later so it can boot without Ubuntu again.  If you do the dd command above with the live CD, then make sure you copy the vista.mbr file to a flash drive or email it to your Gmail account or something.  Later you can restore it to the Vista drive in case you have to remove the Ubuntu drive - because once you install Grub on the Vista drive, you MUST have the Ubuntu drive attached to boot Vista!

Then, from the live CD, follow the chroot method of re-installing Grub:

[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

The last thing you'll have to figure out is how to make Vista the default operating system that boots when you power up instead of Ubuntu (to make you wife's life easier than yours).  I forget exactly how to do this - do some googling, you can figure it out.

---

### Post by ahallubuntu on 2012-02-26
An entirely different approach by the way is to use Vista's boot loader to boot Ubuntu (to have a boot menu when you power up, Vista or Ubuntu).  The upside of this is, if you remove the Ubuntu drive later, Vista will still boot just fine.  The downside is you have to muck with a boot file in Vista.  But if you can follow that, you might consider this approach instead of the one I described above.

I've done this myself with Windows 7 but Vista should be pretty much the same:  you'll have to exact the Grub boot sector from your Ubuntu drive (let's assume it's now on /dev/sdb if Vista drive is on /dev/sda if you re-ordered as I suggested).  Then from a live CD, extract the Ubuntu grub boot sector to a file:

sudo dd if=/dev/sdb of=ubuntu.bin bs=512 count=1

and copy the file "ubuntu.bin" to your C:\ partition in Vista.

[Note: BE CAREFUL with these dd commands!  Don't mistype - you could easily blow away your whole hard drive if you type something wrong!  the "if" and "of" are EXTREMELY IMPORTANT to get correct!!!]

Or just follow these instructions (written a few years ago but should still work):

[http://zaher14.blogspot.com/2008/04/booting-ubuntu-with-vista-boot-loader.html](http://zaher14.blogspot.com/2008/04/booting-ubuntu-with-vista-boot-loader.html)

---

### Post by oldfred on 2012-02-26
With 2 drives, you just want to be sure to install the grub2 boot loader to the Ubuntu drive and not overwrite the Windows boot loader. You can back it up with dd, but if you have a Windows repairCD you can easily restore the boot loader. Then in BIOS set to boot from the Ubuntu drive.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Many suggest to disconnect the Windows drive as that absolutely insures that your install of Ubuntu will not modify the Windows system. But your install of Ubuntu will not find your Windows install to dual boot until your rerun the os-prober with a update of grub menu with this command:
```
sudo update-grub
```Other ways to install to a second drive with Windows still connected. You have to use the manual install or Something else to get the choice on which MBR to install the grub2 boot loader.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")

---

### Post by ahallubuntu on 2012-02-26
> **oldfred said:**
> With 2 drives, you just want to be sure to install the grub2 boot loader to the Ubuntu drive and not overwrite the Windows boot loader.

Well, the OP wants the Grub boot loader installed on the FIRST hard drive in the system (the BIOS-assigned "first" drive).  If he puts the Ubuntu drive first and the Vista drive 2nd as you suggest (so Grub boots off the Ubuntu drive), Windows could have issues being the "second" drive - at least in my experience.  It might work with Vista, but I personally wouldn't risk it.  Ubuntu is much more forgiving about its drive location being moved around than Windows in my experience, so I like to make it as easy as possible for Windows not to be disturbed.

---

### Post by oldfred on 2012-02-27
Even if you boot with grub on the second drive you can make Vista be the default "first" system to boot. I assume that is so the spouse is kept happy and that is of course the most important part.;)

---

### Post by ahallubuntu on 2012-02-27
> **oldfred said:**
> Even if you boot with grub on the second drive you can make Vista be the default "first" system to boot.

Of course - but that's not the issue.  The (potential) issue is the way the hard drives are reported to the operating system, no matter which one boots first.  If the Ubuntu drive is second, for example, it will show up as /dev/sdb - which shouldn't matter to Ubuntu.  However, if Vista is the second hard drive (because Ubuntu drive is /dev/sda and the first drive in the BIOS boot order), it will be reported to Vista as being on a different partition than it was installed on.

I don't really know if this will matter to Vista, but I have seen problems like that with Windows; my philosophy is not to disturb it to reduce the possibility of issues.  I once found an obscure problem with XP where the drive was moved to become the slave not master drive in an old PATA/IDE system, and it would no longer suspend/resume.  Turns out it was a known problem; moved it back to being master and all was well.

---

### Post by joncann on 2012-02-28
Wow. Thanks for all the help. I'll update you as soon as I get a chance to do it. 

I should have been a little more specific about a few things though. This is an old IDE system. Every time I suggest getting a new computer my wife says something about wasting all my time playing games. Like I have time to play games. That's what I have the PS3 for. If Sony wasn't so ridiculous about bricking the things I would jailbreak it and not worry about this dinosaur of a computer.

Anyways I've always been pretty good at the software end of things but never really played with the hardware other than switching out the simple stuff. The day after I posted this I pulled an amazing stupid switching power supplies and RAM and a graphics card. The graphics card bit me because I didn't put the drivers on the windows machine and am now perpetually see the BSOD. So I got to find a recovery disk. Or lie and say it's beyond repair. Either way she'll be giving me dirty looks for weeks. Thank God WiFi works and she can get on facebook from her phone or this would be unforgivable.

Regardless I figured if I was going to destroy a couple of machines it better be cheap one the learning curve's a little easier to deal with if I destroy it. I want to learn to dual boot this thing so I can make it happen on a new machine without fear.

Thanks again. I'll keep in touch.

---

### Post by ScientificProp on 2012-02-28
Interesting thread for me as I am also thinking to install a 2nd SATA hard drive on to my HP AMD64 dual-core machine. I have Vista on the original hard drive that came with the computer. I've been learning 11.10 with a USB live install, I verified I could install driver for the new NVidia graphics card I added.
The instructions seem rather complicated and exact, that is, to make sure the Grub is in the right place and pointing to the right drive. Could the bios boot option menu also be used to tell the system which drive to boot, either Vista on the 1st SATA drive (0), or Ubuntu on the 2nd SATA drive (1)?
Unless I can be sure I can get back to Windows Vista, I may need to delay installing Ubuntu until after I've finished my taxes with TurboTax on Windows.

---

### Post by ScientificProp on 2012-02-28
Almost forgot a 2nd related question. Ultimately, I'd like to install another Ubuntu distribution for special uses (scientific software and CAD work). What is the best partition arrangement for multiple Linux OS? Can they share a swap partition? or a /home partition?

Thanks.

---

### Post by ahallubuntu on 2012-02-28
Yes, you can use the BIOS menu if you wish instead of Grub to choose a boot drive.  

However, you may wish simply to use Vista's boot loader to boot Ubuntu. (See my early post in this thread about that.)  You can install Ubuntu on your 2nd drive but choose not to install Grub on the primary drive's boot sector - choose the boot sector of the Ubuntu drive instead.  If you are worried about missing this step, simply unplug the Vista drive during Ubuntu install.  Then you can't accidentally mess up Vista.

Yes, you can share swap and /home partitions among different installed Linux OSes.  It's typical to allocated as much space as you think you'll need (20GB is typical) to your / partition and everything else to /home.  You can do that plus leave enough free space to install other operating systems.  You might create a small (200MB) separate /boot partition as well.

---

### Post by oldfred on 2012-02-29
If you have IDE, ahallubuntu's comments are more important as some only boot from the first drive sda and only a fewer newer BIOS (that also support SATA) will let you choose which IDE drive to boot. SATA drives are more flexible.

@ScientificProp
You may be better to start your own thread as it starts to get confusing on which system we are discussing.

---

