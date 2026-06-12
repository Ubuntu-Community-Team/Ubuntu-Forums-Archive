---
title: "Edgy Install Doesn't Recognize Hard Drive"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by redDEADresolve on 2006-11-14
SOLVED there are two methods for loading edgy onto your Dell 1501. Look to see which one works for you. I recommend the pci=nomsi method.

I wrote a visual guide on my blogg about getting Ubuntu on the Dell 1501
Check it out for all things 1501 and Ubuntu
[http://ubuntu1501.blogspot.com/](http://ubuntu1501.blogspot.com/)


----------------------------------------
ORGINAL POST
----------------------------------------
Im am trying to install Edy Eft, Ubuntu 6.10 on my new Dell laptop. Everything loads up and goes smoothy until it asks me to manually partition the hard drive. Edgy does not "see" my hard drive. I just have a bank list (see attached picture). Hard drive has win xp on it and loads fine.

Any Help?

Dell AMD Laptop Model Number 1501

Mobile AMD Sempron 3500+ Processor (1.8GHz/512K)
ATI Radeon Xpress 1150 256MB HyperMemory (integrated)
512 MB of 533 DDR2 RAM (1 Dimm)
60gb 5400 RPM SATA hard drive
DVD+/-RW with Dual Layer DVD+R write capacity
Dell Wireless 1390 802.11g Mini Card (54Mbps)

---

### Post by miceyman on 2006-11-17
I'm having the same issue. I just purchased an Inspiron 1501. It wants to use the ahci module for the disk, but spits out the message "dev 0 failed to IDENTIFY (I/O error)" when booting from the Live CD. The plot thickens: GParted's Live CD boots and recognizes the drive just fine using ahci. It seems like there's some sort of timeout? Any ideas?

---

### Post by redDEADresolve on 2006-11-17
> **miceyman said:**
> I'm having the same issue. I just purchased an Inspiron 1501. It wants to use the ahci module for the disk, but spits out the message "dev 0 failed to IDENTIFY (I/O error)" when booting from the Live CD. The plot thickens: GParted's Live CD boots and recognizes the drive just fine using ahci. It seems like there's some sort of timeout? Any ideas?

gparted alsp worked fine with my 1501, I downloaded the alternative install CD and I couldn't find the driver for the hard drive. I went through the disc's list of thirty and none worked. Is this just an Ubuntu thing?

---

### Post by redDEADresolve on 2006-11-17
The hard drive is a:

Toshiba MK6034GSX Serial ATA
HDD2D35 D ZK01T RevAoo
DP/N PH-0TH991-26402-6AI-164D
S/N X616T45PT

Hope this helps I really want to be able to run Ubuntu on this laptop

---

### Post by hades_6_6_6 on 2006-11-18
Same problem. Inspiron 1501 and HD not detected. However I don't have the same disk. In my laptop it is a:
80gb 5400 RPM SATA (fujitsu MHV2080BH)

It seems not to be HD related, but probably the controler.
Any Idea:confused:

---

### Post by redsymbol on 2006-11-19
Hi all,

Same boat.  I just purchased a Inspiron 1501, and when I attempt to install Ubuntu, it fails to perceive the hard drive.  (80 MB SATA, Fujitsu MHV2080BH).  Upon booting off the CD, there is nothing matching sd* or hd* in /dev/ . 

So there's at least four of us... Maybe working together we can figure this out.

BTW, I am installing off the ubuntu-6.10-desktop-i386.iso , which I got at [http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download) .  The processor is an AMD 64 X2, but the 32-bit kernel runs on it just fine (and even recognizes both cores correctly).  I'm sure that is not related to this hard drive issue.

If I don't get the ubuntu install working by later today, I will attempt to install straight Debian.  I'll post what I discover to this thread.  In the meantime, anyone else make any progress?

Thanks,
Aaron

---

### Post by hades_6_6_6 on 2006-11-19
Didn't make any progress. :( 
Everything I tried (most around acpi deactivation) just failed.](*,)
Also tried to install Suse 10.1 but it neither detect the HD, nor even the CD-drive!!
If you figure something out, let us know. Pleeeaaase!

---

### Post by raldz on 2006-11-19
same here! I have an old Inspiron 2500, Ubuntu 6.06-1 and Ubuntu 6.10 doesn't recognize the HD.. I did an install of Windows and the HD was recognized fine, but of course installing Windows is not my choice solution...

---

### Post by redsymbol on 2006-11-19
I put in a request to Dell tech support for information.  I don't think they normally support Ubuntu, but I explained how I was asking on behalf of a number of us (and pointed them to this thread).  So perhaps they will decide to provide us some information that will help, assuming they know yet.

Incidently, apparently they provide support for some other Linux distros, including SuSe and RH.

Will let you all know if I learning anything.

-Aaron

---

### Post by chaosgeisterchen on 2006-11-19
To all of you:

Did you already try out another distribution? I could work just fine with it so the possiblity of a general Linux failure occuring these problems could be minimized. 

Could be an Ubuntu issue. One of you had also problems with SuSE 10.1. What about Fedora Core 6? It's known for above-average hardware detection skills.

---

### Post by redDEADresolve on 2006-11-19
> **chaosgeisterchen said:**
> To all of you:

Did you already try out another distribution? I could work just fine with it so the possiblity of a general Linux failure occuring these problems could be minimized. 

Could be an Ubuntu issue. One of you had also problems with SuSE 10.1. What about Fedora Core 6? It's known for above-average hardware detection skills.

I tried OpenSUSE 10.01 but it didnit work. OpenSUSE Live DVD really sucks anyways. Only flavor of Linux that was a pain to install on my desktop. I'm downloading Fedora Core 6 and Debian 3.1r3 maybe those will work. 

I'll Let everyone know when I try. Please post if you've got any flavor working.

---

### Post by miceyman on 2006-11-19
Fedora Core 6 also did not work. Same issue after loading ahci (dev 0 failed to IDENTIFY).

---

### Post by raldz on 2006-11-19
> **chaosgeisterchen said:**
> To all of you:

Did you already try out another distribution? I could work just fine with it so the possiblity of a general Linux failure occuring these problems could be minimized. 

Could be an Ubuntu issue. One of you had also problems with SuSE 10.1. What about Fedora Core 6? It's known for above-average hardware detection skills.

I've already tried Mandriva 2007 Powerpack, MEPIS 6.0, PCLOS 93, and even GParted LiveCD couldn't recognize the HD for partitioning.. so I guess it's a Dell issue... I'll try FC 6, still have to download the ISOs...

---

### Post by redDEADresolve on 2006-11-19
> **raldz said:**
> I've already tried Mandriva 2007 Powerpack, MEPIS 6.0, PCLOS 93, and even GParted LiveCD couldn't recognize the HD for partitioning.. so I guess it's a Dell issue... I'll try FC 6, still have to download the ISOs...

I used gparted to clear up the hard drive to install Windows XP. Those other Distros might not work but the stand alone gparted Live CD worked perfectly.

---

### Post by raldz on 2006-11-19
> **redDEADresolve said:**
> I used gparted to clear up the hard drive to install Windows XP. Those other Distros might not work but the stand alone gparted Live CD worked perfectly.

yup, it does clear up the HD by creating a new partition table, but I could not create a new partition.. just a clear partition..

---

### Post by miceyman on 2006-11-19
> **raldz said:**
> I've already tried Mandriva 2007 Powerpack, MEPIS 6.0, PCLOS 93, and even GParted LiveCD couldn't recognize the HD for partitioning.. so I guess it's a Dell issue... I'll try FC 6, still have to download the ISOs...

GParted *did* load the drivers. I've attached the dmesg output as a reference, as well as the Ubuntu dmesg output as a cross-reference. I wish I could do more with it, but unfortunately I don't really know what I'm doing. Are there any kernel boot options that could help with drive detection?

---

### Post by miceyman on 2006-11-19
> **raldz said:**
> yup, it does clear up the HD by creating a new partition table, but I could not create a new partition.. just a clear partition..

I didn't have a problem reformatting to ext3, too.

---

### Post by miceyman on 2006-11-20
Also, Knoppix found the drive, Debian did not. They all used the same version of libata and ahci, though. Still very confused.

---

### Post by redsymbol on 2006-11-20
I just tried straight Debian (3.1r3) and FC 6 (Zod).  Neither of their installers detected the hard drive.

I'm sure there is a way to install Linux on this thing.  It's just a matter of time until we figure it out.  I'm still waiting for a response from Dell tech support - hopefully they will have some advice.  (I'll post it here, of course.)

-Aaron

---

### Post by hades_6_6_6 on 2006-11-20
> **raldz said:**
> yup, it does clear up the HD by creating a new partition table, but I could not create a new partition.. just a clear partition..

For me the gParted Live CD worked perfectly with default parameters. I've managed to create 4 partitions* (1 primary for / and 3 logical for /home /swap and shared). No Problem. At all. All partitions are accessible.

*I had to remove the hidden 2 Gb FAT32 partition created by Dell, but Windows still "works fine".

---

### Post by redDEADresolve on 2006-11-20
doh double post

---

### Post by redDEADresolve on 2006-11-20
Thanks Aaron I was going to call Dell in the morning. My 1501 is being sent back to Dell, bad unit. I'm expecting the replacement shortly, hopefully their will be a solution when it returns. I only thing I've found researching this problem was with other SATA drives not being recongized was that:

look in the BIOS start up to find the number of the southbridge interface to SATA and then do some searching

If anyone wants to look this up might help us find a solution or point others in the right direction.

---

### Post by hades_6_6_6 on 2006-11-20
I've just made a BIOS update (from 1.0 to 1.1).
As expected, no improvement concerning the HD issue:(

I've also opened [this]("http://forums.us.dell.com/supportforums/board/message?board.id=insp_harddrive&message.id=57140") thread at Dell's community. Who knows...

---

### Post by redsymbol on 2006-11-20
I think I got it.  I got ubuntu to recognize the hard drive on my Dell Inspiron 1501 notebook.

I got it by adding this boot param:
acpi=force irqpoll

Hit 'F6' at the initial ubuntu install menu, and you will be able to add it in with the other boot params.  I typed it between the 2nd and 3rd parameters, or thereabouts; but I believe you can put it in anywhere between other boot params. **Edit:** When you press F6, a line of preset boot parameters is shown for you to edit.  On further testing, you can just append ' acpi=force irqpoll' to the end of that line.

I'll hang around a bit to help anyone who needs it.  Try adding this boot parameter and see if it works for you.

Miceyman, thanks for posting those dmesg logs - by doing that you directly enabled me to figure this out.

> **miceyman said:**
> GParted *did* load the drivers. I've attached the dmesg output as a reference, as well as the Ubuntu dmesg output as a cross-reference. I wish I could do more with it, but unfortunately I don't really know what I'm doing. Are there any kernel boot options that could help with drive detection?

I noticed the following difference in the dmesg dump.

From the one for ubuntu (with failed drive detection):
--- begin ---
> [17179583.244000] ata1: SATA max UDMA/133 cmd 0xF883E100 ctl 0x0 bmdma 0x0 irq 209
> [17179583.244000] ata2: SATA max UDMA/133 cmd 0xF883E180 ctl 0x0 bmdma 0x0 irq 209
> [17179583.244000] ata3: SATA max UDMA/133 cmd 0xF883E200 ctl 0x0 bmdma 0x0 irq 209
> [17179583.244000] ata4: SATA max UDMA/133 cmd 0xF883E280 ctl 0x0 bmdma 0x0 irq 209
> [17179583.628000] ata1: SATA link up 1.5 Gbps (SStatus 113)
> [17179583.628000] unexpected IRQ trap at vector b0
> [17179613.628000] ata1: qc timeout (cmd 0xec)
> [17179613.628000] ata1: dev 0 failed to IDENTIFY (I/O error)
--- end ---

And here is the corresponding section from the gparted dmesg:
--- begin ---
< <6>ata1: SATA max UDMA/133 cmd 0xF8822100 ctl 0x0 bmdma 0x0 irq 11
< <6>ata2: SATA max UDMA/133 cmd 0xF8822180 ctl 0x0 bmdma 0x0 irq 11
< <6>ata3: SATA max UDMA/133 cmd 0xF8822200 ctl 0x0 bmdma 0x0 irq 11
< <6>ata4: SATA max UDMA/133 cmd 0xF8822280 ctl 0x0 bmdma 0x0 irq 11
< <6>ata1: SATA link up 1.5 Gbps (SStatus 113)
< <7>ata1: dev 0 cfg 49:2f00 82:346b 83:7f09 84:6063 85:3469 86:bf09 87:6063 88:203f
< <6>ata1: dev 0 ATA-7, max UDMA/100, 117210240 sectors: LBA48
< <6>ata1: dev 0 configured for UDMA/100
--- end ---

So the successful gparted looks at irq 11, while the unsuccessful ubuntu looks at irq 209.  I did a web search on the topic, and what I found suggested trying 'acpi=force irqpoll'.  I did, and it worked :mrgreen: 

-Aaron

---

### Post by miceyman on 2006-11-20
I think I'm in love. It works for me!

---

### Post by raldz on 2006-11-20
Damn that was good! Thanks! I guess this thread should be marked as solved?

---

### Post by hades_6_6_6 on 2006-11-20
worked also for me :) 
RedSymbol, my hero! ;)

---

### Post by redsymbol on 2006-11-20
Okay, good, it works for at least a couple of people besides myself.  Hopefully it will work for everyone.

As an aside, this is probably less than an ideal solution in one sense. When booting like this, I get a message like "unexpected IRQ trap at vector b0" in the output of dmesg.  It's literally listed over 2000 times.  I guess that's a side effect of the polling.  But it does seem that the system is completely healthy once the bootup is complete.

On my system, the only thing left is to get the wireless connection up.  Ubuntu didn't seem to be able to bring the wlan0 interface up automatically.  I haven't had time to look into it yet; I think that will be easier to fix.  If anyone else has this problem and wants to start another thread for it, please point me to it.

-A

---

### Post by hades_6_6_6 on 2006-11-20
> **redsymbol said:**
> On my system, the only thing left is to get the wireless connection up.  Ubuntu didn't seem to be able to bring the wlan0 interface up automatically.  I haven't had time to look into it yet; I think that will be easier to fix.  If anyone else has this problem and wants to start another thread for it, please point me to it.
Indeed, I couldn't managed to set up the wifi neither.
Could you please open a "how to" thread if you get it to run?

---

### Post by miceyman on 2006-11-21
> **hades_6_6_6 said:**
> Indeed, I couldn't managed to set up the wifi neither.
Could you please open a "how to" thread if you get it to run?

This isn't an exact thread, but it's very relevant and I was able to use it to set up wifi without a problem.

[http://ubuntuforums.org/showthread.php?p=1750002](http://ubuntuforums.org/showthread.php?p=1750002)

Just get the most recent dell driver for the Inspiron 1501 in place of the link they give (the self-extracting windows driver)

You'll also need network-manager and network-manager-gnome if you have WPA encryption.

Pat

---

### Post by Leed on 2006-11-23
first of all, great respekt for the person who found out the thing about "acpi=force irqpoll", I'm setting up my younger brothers new PC, with only a SATA Disk in it and was facing the same problem. Now Linux finds the partitions on the disk. 

However I ran into another Problem, during install I cannot set up Edgy to use one of the partitions as root of the filesystem, and of course it won't install that way. I strongly suspect this is because Ubuntu classifies the devices as USB drives (addressed by /usb/scsi/sda1 etc.). Is there a way round this so that I can install Ubuntu onto his drive?

So far I've been trying to add a further Harddisk, one using IDE. However the Edgy CD won't boot for some reason. Booting with Dapper LiveCD works, but that does not recognise the SATA Disk (which I definitly don't want to remove, especially because it contains a pre set Windows partition from the manufactorer and I do want to set up a dual boot system).
My plan is to install Dapper and upgrade to Edgy once on disk, then somehow find out how to address the SATA in Grub, so that I can set up the dual boot. Does anyone have any experience with this. Of course the optimal would be a sollution to get Edgy to accept the SATA partition as root. 

Many thanx in advance
Dave

---

### Post by pyros on 2006-11-24
what I did was delete the 3.5 gig partition, which is a ghost image of xp they set up at the factory, resize the main 75 gig partition to 25 gig and tell the edgy installer to setup the partitions automatically. it left the 75mb partition, which I'm assuming is for the built-in diagnostics, and the 25 gig resized ntfs partition, and created a root and swap partition in the free space.

---

### Post by fireball47 on 2006-11-27
Thanks to that "acpi=force irqpoll", I was able to get the Ubuntu installer to detect my SATA drive so that I could install Edgy on my Dell Inspiron 1501 (AMD-64).

But now when I try to boot Ubuntu from the hard drive, it freezes. Booting in safe mode shows me that the hard drive is once again not being detected. But this time, adding "acpi=force irqpoll" to the boot options doesn't seem to make a difference. Has anyone else experienced this problem once they got the install to work?

I have a dual-boot with Windows XP (grub), but that shouldn't make a difference. Thanks in advance.

---

### Post by mues on 2006-11-28
Hi everybody,

"acpi=force irqpoll" in the boot options let me install Ubuntu / SuSE on the 1501.
Nevertheless both distributions keep throwing "unexpected IRQ trap at vector b0" messages (about 10 per second) all the time. That may be the reason the harddrive is constantly accessed and the 1501 is slowed down -a lot- (Am I the only one whose hd light is permanently blinking?! ).
As I use the Turion X2 I'm wondering if the APIC is not properly supported by current kernels.

Greets & thx for your help
- Mues

:neutral:

---

### Post by Hamill23 on 2006-11-28
Hi 
I have read threw all the threads, and it seams that i have the same problem with my hard drive ( Fujitsu MHV2080BH) while trying to install Fedora Core 3, as yous have had. I've deleted the partion that contained the windows recovery. and tried it with the Force irqpoll command 
( well i think i did, not sure what i'am doing tell the truth! )
but it still fails to detect the hardisk, i've selected every driver there is for it there! 
i'am using a 
Philips Freevents X52 

help

---

### Post by fireball47 on 2006-11-28
Well, I figured out my problem. I just got confused by GRUB trying to add the boot option "acpi=force irqpoll". When you edit the kernel command in GRUB, you need to hit ENTER to save your change and then "b" to boot from the edit screen. Hitting ESC at any point will discard your changes.

With the boot option in place, Ubuntu starts up. I was able to change GRUB once and for all by editing /boot/grub/menu.lst

---

### Post by redsymbol on 2006-11-28
> **mues said:**
> Hi everybody,

"acpi=force irqpoll" in the boot options let me install Ubuntu / SuSE on the 1501.
Nevertheless both distributions keep throwing "unexpected IRQ trap at vector b0" messages :neutral:

I get that too.  I think that using "acpi=force irqpoll" is slightly hackish, in the sense that it works, but may not be the best possible solution. 

Documentation on the Linux boot parameters doesn't seem to be readily available through search engines, for some reason.  So I dug for it and put a page up here:
[Linux Boot Parameter Reference]("http://redsymbol.net/linux_boot_parameters/")

I think some other argument to the acpi parameter, or perhaps some other boot param altogether, might help the hard drive calm down.  I haven't had a chance to throughly try the options yet.  I'll post if I find something.

---

### Post by heathman001 on 2006-12-03
This allowed me to detect / install Edgy on my Inspiron 1501's SATA disk. Thanks!

---

### Post by Joshua Hesketh on 2006-12-03
I have been having troubles with my SATA drive after it worked with dapper but not when I formatted with edgy. I wanted to give SuSE 10.2 RC1 a try and I did so only to find the same problem with my hard drive with edgy. Unable to get the  "acpi=force irqpoll" solution to work in either distribution I found another solution on the SuSE forums ([http://www.suseforums.net/index.php?showtopic=25046)]("http://www.suseforums.net/index.php?showtopic=25046%29").

The solution which worked for me is to set the boot parameters to 
```
insmod=ide-generic
```Don't know if it will help with edgy, but it may. I'll try it out when I'm sick of playing around in SuSE ;) (unless of course I fall in love with it :p).

Hope this helps anybody with the same problem :cool:

---

### Post by mues on 2006-12-04
The "insmod=ide-generic"-solution is unfortunately not working on the Inspiron 1501. I tried with SuSE 10.1 and Edgy :-|

---

### Post by lusich on 2006-12-06
I have the same problem. 

I tried different distros Gentoo, Mandriva,... they all do the same thing.
I was able to get partial success with acpi=force irqpoll but I get a load of errors and the computer freezees at shutdown (goes in a loop).
I found some other threads in hope of resolving this:
[http://forums.gentoo.org/viewtopic-t-519339.html](http://forums.gentoo.org/viewtopic-t-519339.html)
[http://community.livejournal.com/linux/1554783.html](http://community.livejournal.com/linux/1554783.html)
[http://forum.club.mandriva.com/viewtopic.php?t=58173&sid=e9e33a8b55943621fd72a2ebf50f0be7](http://forum.club.mandriva.com/viewtopic.php?t=58173&sid=e9e33a8b55943621fd72a2ebf50f0be7)

---

### Post by iguanamind on 2006-12-06
This is happening to me as well on the Dell Inspiron 1501.  I have the amd64 bit Edgy installed but the acpi=force irqpoll is filling up the messages with "unexpected IRQ trap at vector b0".

I know there is no solution at the moment, but I figured it was necessary to put my word in about the problem.  This is definitely a big issue because it is sucking up resources to write to the hard disk all day.  Eventually, the system freezes if I keep it on long enough.  Or it will freeze on shutdown.

I am wondering if a solution is being worked on.  Maybe someone has seen a thread in another forum about it.  Or is it time to send the machine back before the 30 days is up?

---

### Post by peacekpr on 2006-12-06
I, too, am having problems.  Will passing the "acpi=force irqpoll" command at the boot prompt overstress the laptop?  I don't want undue damage occuring to his machine.  Anyways, for what it's worth, I've attached some output from my machine (working in LiveCD).  Maybe an expert will come along and be able to troubleshoot with the info.

If there is anything I forgot or you would like to see, let me know.  I'm hesitant to wipe all partitions clean and install Ubuntu Edgy until I feel very comfortable with a workaround.  I'm not yet comfortable using "acpi=force irqpoll" - thanks for the work you all have done and are doing.

---

### Post by christoforever on 2006-12-08
Same problem with me. Dell inspiron 1501 amd64 turion dualcore, it freezes at partition, step 5.

---

### Post by wool on 2006-12-08
> **christoforever said:**
> Same problem with me. Dell inspiron 1501 amd64 turion dualcore, it freezes at partition, step 5.

You need the edit the boot parameters
**acpi=force irqpoll**
browse pages 3 and 4 of this thread

> **peacekpr said:**
> I, too, am having problems.  Will passing the "acpi=force irqpoll" command at the boot prompt overstress the laptop?  I don't want undue damage occuring to his machine.  Anyways, for what it's worth, I've attached some output from my machine (working in LiveCD).  Maybe an expert will come along and be able to troubleshoot with the info.

If there is anything I forgot or you would like to see, let me know.  I'm hesitant to wipe all partitions clean and install Ubuntu Edgy until I feel very comfortable with a workaround.  I'm not yet comfortable using "acpi=force irqpoll" - thanks for the work you all have done and are doing.
same here. is "acpi=force irqpoll" safe to implement

---

### Post by gbordiga on 2006-12-10
I think i have a better solution than acpi=force irqpoll .
Try with pci=nomsi . For me is working, i do not get any error messages and the drive is not stressed.

---

### Post by peacekpr on 2006-12-10
> **gbordiga said:**
> I think i have a better solution than acpi=force irqpoll .
Try with pci=nomsi . For me is working, i do not get any error messages and the drive is not stressed.

I tried "pci=nomsi," and I no longer have any issues with the "irqpoll" option.  When I was using "irqpoll," I was getting several (perhaps hundreds, thousands?) messages about irq resources (as others have mentioned in this thread).

I am going to do some more researching about why "pci=nomsi" seems to work so well.  I'll return to this thread once I find out and edit this posting.

Thanks for the help!

EDIT:
I found a good link about MSI (Message Signaled Interrupts).  If you were willing to recompile your kernel and debug individual devices, you can zero out which devices use MSI and which don't.  I'm still unclear on the performance benefits of MSI - will I actually see a performance improvement?  This is what the MSI HowTo says:

> 
PCI Express endpoints uses INTx emulation (in-band messages) instead of IRQ pin
assertion. Using INTx emulation requires interrupt sharing among devices 
connected to the same node (PCI bridge) while MSI is unique (non-shared) and 
does not require BIOS configuration support. As a result, the PCI Express 
technology requires MSI support for better interrupt performance.

Using MSI enables the device functions to support two or more vectors,
which can be configure to target different CPU's to increase scalability.


I found this information at: [http://lwn.net/Articles/44139/]("http://lwn.net/Articles/44139/").
Good luck!

END EDIT.

---

### Post by mues on 2006-12-10
> **gbordiga said:**
> I think i have a better solution than acpi=force irqpoll .
Try with pci=nomsi . For me is working, i do not get any error messages and the drive is not stressed.

That is it!
Even OpenSuSE 10.2 (which used to crash badly with the other bootparams) runs perfectly now.
Thanks a lot for the hint!

:D

---

### Post by cw7585 on 2006-12-10
Thanks to everyone who has been working on this - I've got a new 1501 on its way to my house, and these two solutions (acpi=force irqpoll and pci=nomsi) are very timely. 

Hopefully this new pci-nomsi one will do the trick and keep the hard drive from getting stressed. I'll try it first. Thanks again - a lot of people are being helped!

---

### Post by zarafiq on 2006-12-10
> **redsymbol said:**
> I get that too.  I think that using "acpi=force irqpoll" is slightly hackish, in the sense that it works, but may not be the best possible solution. 


I am not an expert but I have the same feeling.
I discovered thet Gentoo 2006.1 amd64 netinstall cd (iso md5 '38ef14df8e8c9849271ccf8d09210cc8') boots without any extra parameters, detects the disc and doesn't show 'unexpected IRQ trap...', while Gentoo 2006.1 livecd (the output of uname -r and cat /proc/cmdline is the same as in netinstall cd) needs the 'irqpoll' parameter. I cannot discover the difference between livecd and netinstallcd :(

---

### Post by Zanwar000 on 2006-12-10
EDIT
Okay I managed it to install with pci=nomsi however after I have installed it onto my harddrive Ubuntu won't load. It just freezes at the bootup screen. What would I do here?

Okay this is marked as solved, but did you mean by the irqpoll method because it doesn't seem to be working for me. Isn't there a list of everything that isn't compatible with Inspiron 1501 out-of-the-box?

---

### Post by lusich on 2006-12-10
yeah, it works!!! thanks for everyone's help. The linux community wins again :)

---

### Post by lusich on 2006-12-10
> **Zanwar000 said:**
> EDIT
Okay I managed it to install with pci=nomsi however after I have installed it onto my harddrive Ubuntu won't load. It just freezes at the bootup screen. What would I do here?

Okay this is marked as solved, but did you mean by the irqpoll method because it doesn't seem to be working for me. Isn't there a list of everything that isn't compatible with Inspiron 1501 out-of-the-box?

have you changed your grub or lilo bootloader options to include the pci=nomsi line?
If not, you will manage to install it, but then your computer will "forget" what you specified during install. You need to enter the pci=nomsi option into the grub file on your hard drive,too, and save it.

---

### Post by Zanwar000 on 2006-12-10
How would I go about inserting that line into GRUB. I plan on having multiboot, will the option be in the screen where I choose which OS I want?

Also I have heard on this thread that one of the methods puts stress on the hard drive. Is it pci=nomsi or can pci=nomsi cause any damage to my laptop? Sorry for all the posts in such a short time but I am a complete Linux newbie.

---

### Post by peacekpr on 2006-12-10
> **Zanwar000 said:**
> How would I go about inserting that line into GRUB. I plan on having multiboot, will the option be in the screen where I choose which OS I want?

Also I have heard on this thread that one of the methods puts stress on the hard drive. Is it pci=nomsi or can pci=nomsi cause any damage to my laptop? Sorry for all the posts in such a short time but I am a complete Linux newbie.

Edit the "kernel" line in the file:```
/boot/grub/menu.lst
```
You just need to append to it pci=nomsi.  Good luck.

---

### Post by peacekpr on 2006-12-10
> **Zanwar000 said:**
> EDIT
Okay I managed it to install with pci=nomsi however after I have installed it onto my harddrive Ubuntu won't load. It just freezes at the bootup screen. What would I do here?
When you boot your notebook, hit the Escape key to enter the grub menu.  When you're there, following the instructions to edit the "kernel" line.  You'll need to add pci=nomsi to the end of that line.  Keep in mind that once your Ubuntu desktop loads, you'll need to edit the file /boot/grub/menu.lst to append pci=nomsi to the "kernel" line.  That will make it permanent.
> **Zanwar000 said:**
> Okay this is marked as solved, but did you mean by the irqpoll method because it doesn't seem to be working for me. Isn't there a list of everything that isn't compatible with Inspiron 1501 out-of-the-box?
To be honest with you, I have all of my Dell Inspiron 1501 hardware in good working order, and it all works very well.

Good luck!

---

### Post by mistik1 on 2006-12-13
Thanks again for working this one out guys.
I would like to know if anyone has a working xorg.conf for the ATI Xpress 200M card, with or without fglrx .

I'm having some X related lockups on this machine.
The lockup are very random even when using just the opensource radeon drivers.

---

### Post by xphere on 2006-12-17
Add me to the list, same problem, mine is a 1501 actually works on Mandriva 2007 free on installation it shows this ( ati SB660 non raid-5 sata) and install normally after that, but i have become pretty fund of Automatix and want to install Ubuntu. I hope this helps in some way.

---

### Post by theurgy on 2006-12-18
Haven't installed Ubuntu yet however I installed Xandros Desktop Professional 4.0 on it and I thank everyone in this thread for the advice.
Here's what I've found out:
When using the irqpoll option it detects the harddrive however I'll get a constant "unexpected IRQ trap at vector ##" error message related to IRQ 176.
If I use the pci=nomsi option the message goes away but then the bcm43xx drivers for the Dell 1390 Wireless card have issues. 
So what I've done is use irqpoll AND pci=nomsi in my kernel params.
Another option I've added is the noapic parameter as I was getting the message: 
"MP-BIOS bug: 8254 timer not connected to IO-APIC"
I had tried the disable_8254_timer option but that had no effect.

I've been getting some issues with ACPI too, seems it sometimes comes on but only if the battery is a bit drained or if the stars or aligned or whatever. 
I still get the messages on bootup:
PCI: Cannot Allocate Resource Region 7 of bridge 000:00:05.0 
PCI: Cannot Allocate Resource Region 8 of bridge 000:00:05.0

I'm still playing with this but so far it's running great for now aside from those minor details.
Here are the stats:

I have the Inspiron 1501 with the Turion MK-36 Chip and 1 GB of RAM.

Kernel: 2.6.18 DCC Uni
KDE: 3.4.2
Qt: 3.3.4
VGA Driver: fglrx
LAN Driver: bcm4400 
WiFi Driver: bcm43xx (native)

---

### Post by aquaxbat on 2006-12-19
I am still in the no HD recognition boat. I have tried all the recipes you have put down, the noapic works for that error but none of the others seem to do the trick. Tried the irq trick, ide-generic, and the pci=nomsi is not recognised as a command. So far i am stuck with crummy windoze xp home and no way to get ubuntu installed. I just received my dell 1501 in the mail today. I have an AMD Sempron 3800+ with a 60GB SATA drive, just like the rest and nothing works. I am downloading the 64-bit version and am going to try that next. We shall see. I hope if anyone has any new insight or information on this issue, please let us know!! thanks a bunch

---

### Post by aquaxbat on 2006-12-20
Ubuntu 6.10 64-bit installed perfectly on my Dell 1501. No problems like the ones stated before. I am not sure if the 32-bit has been causing all the problems, but if you are experiencing them, try the 64-bit version, it may work.

---

### Post by tonyblum1343 on 2006-12-21
Hi, I am trying to install Edgy (AMD 64 version) on my HP Special Edition (L2005US) with no luck.  The Live CD boots up but when I try to install it freezes everytime at Step 5 (partition part).

I have tried the boot options of acpi=force irqpoll with no avail and pci=nomsi.  Neither worked.  Does anyone have any other suggestions?  Should I try installing the non-64 version.

By the way, I am completely new to installing Linux.

Thanks,

Tony

---

### Post by BlueN1nja on 2006-12-21
Today I booted into Ubuntu and noticed my wireless wasn't working. Checked ndiswrapper-no problems there. The card wasn't listed in Networking, and I couldn't get the wifi light to come on. Rather than acpi=force irqpoll, I had switched to pci=nomsi a few days ago and hadn't used Ubuntu since.

I rebooted with acpi=force irqpoll, and suddenly I've got wifi... But I'm still getting lots of "unexpected IRQ trap at vector b0" messages.

Any way to keep wifi functionality while still not putting the HDD into overdrive?

Thanks.

EDIT: Never mind... Just rebooted a couple times and it's working. Strange.

---

### Post by theurgy on 2006-12-22
> **BlueN1nja said:**
> Today I booted into Ubuntu and noticed my wireless wasn't working. Checked ndiswrapper-no problems there. The card wasn't listed in Networking, and I couldn't get the wifi light to come on. Rather than acpi=force irqpoll, I had switched to pci=nomsi a few days ago and hadn't used Ubuntu since.

I rebooted with acpi=force irqpoll, and suddenly I've got wifi... But I'm still getting lots of "unexpected IRQ trap at vector b0" messages.

Any way to keep wifi functionality while still not putting the HDD into overdrive?

Thanks.

EDIT: Never mind... Just rebooted a couple times and it's working. Strange.

Please read my post but try putting BOTH acpi=force irqpoll and pci=nomsi kernel parameters.
Again I had the same issues with the Wi-Fi until I put both.

---

### Post by theurgy on 2006-12-22
Also a note to all 1501 owners... make sure to upgrade your BIOS's to V 1.7

---

### Post by peacekpr on 2006-12-22
> **theurgy said:**
> Also a note to all 1501 owners... make sure to upgrade your BIOS's to V 1.7

Is there a specifc reason for this or is this just a general suggestion?

---

### Post by jeff_ch on 2006-12-23
seems i picked a good time to take my 1501 out of the box ... too ironic.  i'm having the same problems with CentOS 4.4 i386

trying now with linux acpi=force irqpoll pci=nomsi

hey i made it past the partition screen without a "no drive" error!

will letchall know how it goes

---

### Post by jeff_ch on 2006-12-23
> trying now with linux acpi=force irqpoll pci=nomsi

so far so good.  when i rebooted after a clean install, the command line options contained acpi=force, but none of the rest.  It did not reboot successfully until i added the irqpoll as well.  Adding the pci=nomsi made grub complain that it was an unrecognized option, but it booted okay.

Summary: installing with above flags, I was able to reboot into a working CentOS dist by making sure i had:

acpi=force irqpoll

in addition to whatever was there before.

Best of luck, i'll report any problems

---

### Post by aross6 on 2007-01-05
I used the "pci=nomsi" boot option to install OpenSuSe 10.2 on my wife's Inspiron 1501, and everything was smooth as silk!!!  All I did was pop in the Install DVD, and when the installation menu appears, highlighted "Installation" and typed "pci=nomsi" in the boot options field that is already provided there (no F6 required).  I hit enter and away she went!  No errors whatsoever!  Everything installed fine, the system booted quick (no need to alter the GRUB Bootloader parameters file w/ OpenSuse 10.2 either), and everything worked natively & to a T (except the Dell 1390 Wireless card, which was a breeze to get working using NdisWrapper).  

Thanks so much for the Help!!!

Down w/ Windows!!! Linux is the Way!!!!

---

### Post by redDEADresolve on 2007-01-22
i got it working and made a great visual guide. read it on my blogg.
[http://ubuntu1501.blogspot.com/](http://ubuntu1501.blogspot.com/)

or click the link to my signature

---

### Post by Zanwar000 on 2007-02-26
I have now heard of three methods to enable the hard drive:
1. pci=nomsi
2. acpi=irqpoll
3. all-generic-ide

Of these I have heard that PCI=NOMSI and ACPI=IRQPOLL can both damage the hard drive while ALL-GENERIC-IDE greatly reduces performance. Can anyone assure me that PCI=NOMSI does not cause harm to a computer? (I learned that PCI=NOMSI can be harmful from a HOWTO tutorial for Fedora).

---

### Post by Athanasius on 2007-03-06
I just got an Inspirion 1501 and had the hard drive problem.  Initially I just asked if they could just send me a hard drive that worked with Linux.  They wouldn't do that but they sent me to [HTML]http://www.linuxquestions.org/questions/showthread.php?t=507629[/HTML]
and it led me here.  Everything seems to be working fine for me.  Thanks, everyone, for your blood, sweat and tears

---

### Post by ArtDeco on 2008-01-21
Brand Newbie with new cheap Dell 1501 with nothing but Vista and Adware installed. Copy of Unbuntu Fiesty 7.04  in my CD slot, Running Gparted in another window - prompting me to Nuke Now? or Reconsider ?:popcorn:

 I wonder if  Edgy vs. Feisty vs. Gutsy really matters? Have to ponder upgrade anyway.

Art Deco

---

### Post by OMNIpotus on 2008-02-16
Oh my god this works!  I have been looking for months through BIOS settings, different distros, etc etc etc... the F6 acpi=force irqpoll worked like a charm.  You are my hero red.  If I could send you money I would (ok, maybe not, but still..).

I am posting this from my newly installed Ubuntu.

---

