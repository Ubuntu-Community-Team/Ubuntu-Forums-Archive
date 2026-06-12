---
title: "Grub Read Error - hard drives pissed at each other! Mayday!"
date: 2005-09-27
forum: Hardware &amp; Laptops
---

### Post by trinaryouroboros on 2005-09-27
I really don't know what the deal is, in all my time working with Linux, Windows, general hardware, and silly IDE hard drives - I've never encountered such an oddity, and I want to rule it out as Hardware, but I just can't accept that - both hard drives are perfectly fine and fully tested...

 Here's the setup, so I can get this out of the way before the software end :

DFI LanParty nF4 Ultra-D Motherboard
AMD64 3000+ Processor (1.81 GHz - no overclocking)
1 GB (2 x 512MB) Corsair kick-ash RAM, Dualiez
DVD-Rom (Matshita SR-8584A)
SONY CD-RW CRX175E2
Hard Drives (both simple IDE): 
 WDC AC26400B (bout 6.something Gig hard drive) = Windows XP Corp (32bit)
 WDC 30 Gig = Ubuntu Hoary 64-bit (loading Xeon kernel, AMD64 standard)
External BUSLINK 120GB drive (switchable, using USB2.0 instead of IEEE1394, too much trouble in Ubuntu for some reason for 1394)
PS2 Mouse/Keyboard
+ USB Mouse/Keyboard (don't ask)
650W Uber Power Supply (freakin 'spensive)
Good old PCI ATI All in Wonder Pro 128 video card (so I can watch TV and play some good oldie games until I save enough cash for SLI cards)

 I originally did not have the 6 gig hdd in there, but had been using it on an older pc, which I ran tests previously for bad blocks before using, standard stuff. I went rage-man against Winblowz and decided to go for this well reviewed Ubuntu Hoary 64-bit, which surprisingly took only a few days to completly configure with everything I could ever want - with a few exceptions, including the ability to play certain older games. I became mildly possessed about that, and my girlfriend was planning to start a rebellion against Linux (by using Before and After pics) because of my need for a shave and shower due to intense research. Hey, a man needs his video games working (Cedega) - even if they're old.

:???: 

 To alleviate said situation, I decided to allow the burning microsoft death an opportunity until I can resolve some of the odd issues I've been having getting the games working.

Now, cutting a obviously long story short:

 I popped in the 6 GB hdd as Master on the primary IDE cont. - originally, silly me decided to install the 30 GB w/ ubuntu while the thing was set as secondary...my bust. Either way. I say to myself, hey, I want to get the most out of my sick DFI Bios, and keep the 30 Gig active as the main bootable drive. Whoops? At time of start up, all I get is:

**"Grub Read Error."**

 -  and that's it...searched the Internet with stranded advice. Per a friend's assistance, I took the opportunity to switch up the menu.lst, so that the linux Kernel is set up as hdd 0,1 instead of 0,0...Same problem.

 I said, ok, well whatever lets try the WDC 6GB hdd as the bootable main drive, and hope partition magic or something will help in the future. I pop in a WinXP Corp cd-rom, it goes all the way through it's silly blue screen endless seeming startup - and out of nowhere...a BSOD...boom...restart. Hmm, maybe a one time thing? Tried a couple of times...same BSOD...getting weird.

 Getting frantic, I unplugged the 30 GB hard drive to avoid my baby getting burned...and - voila! Win XP Corp installs just fine...perfect example of embedded booting warcode.

 Okay, no biggie, right? I try switching menu.lst back, and put the 30 Gig (ubuntu) hdd as primary this time...Grub Read Error.

 Actually it was more like : 

**Grub LoadiRead Error.**

 What the heck was that??? :confused: 

 Now, trying the Windows hdd as the main bootable - Windows XP startup black screen comes up with logo...although dim...then BSOD...restart...messed up! :mad: 

 All in all, I'm being forced to leave my full tower open, which I'm sure it appreciates because I've put a big desk fan next to it to keep it happy and extra cool for these tough times. When I want windows, I must disconnect the 30 Gig Ubuntu Drive - visa versa for to get Ubuntu loaded...

 In leui of recent events, I bought my girlfriend some wonderful ice cream, took her to a concert, and came back accepting mild defeat. Yet I'm still in high hopes some brave soul out there may scream "Eureka!" my direction and help with this strange calamity...I mean, I still have a few months to half a year before I can seperate boxes (mmm SLI sounds yummy with Ubuntu) - well, cheers till then. And high hopes for all those who seek.

:cool:

---

### Post by trinaryouroboros on 2005-09-28
Hey, anyone get a chance to check this out? :smile:

---

### Post by spd106 on 2005-09-28
In terms of hardware first check the bios to see if both drives are detected properly. One of the drives might be affecting the others ability to talk to the PC. Have you tried putting them on separate ide channels. This would involve swapping one of the drives for one of the CD/DVD drives. Just make sure you remember to double check the master/slave jumpers.
On which drive did you install grub? It should have replaced the MBR on the 6 gig drive (hda). Then be set up to dual boot. The menu.lst should be set up to have windows on (hd0,0) and Ubuntu on (hd1,0) assuming you put the root partition first. The read error means that it was unable to find the the next stage, which should be on the root partition of the 30 gig drive (hdb0). You could always make a grub boot floppy. This would allow you to look for the kernel and initrc files from the grub cli. See, the floppy isn't dead yet!
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
Have you tried a live CD? If it is able to mount both drives then you don't have a hardware problem. 
Hard drive space is so cheap these days it's almost not worth the time bothering with such a small drive. Hey it's almost an insult to the DFI board :cool: You could always repartition the 30 Gig drive to include windows. But you don't need to that, right?

---

### Post by trinaryouroboros on 2005-09-29
[QUOTE=spd106]In terms of hardware first check the bios to see if both drives are detected properly. One of the drives might be affecting the others ability to talk to the PC.[/QUOTE]

I confirmed this, the BIOS says everythings cool, and the drives are detected appropriately. Something cool about the DFI BIOS I found out is that you can specify which drive (master / slave) on which channel, or even which firewire/usb drive you want the system to look for a partition on first. I did try popping the jumpers manually and trying to get the BIOS to load the partitions manually - which seemed to work, but as a result, I got the Grub Read Error (when booting the Ubuntu drive) and I got the Win XP crash (when booting the other drive).

[QUOTE=spd106]Have you tried putting them on separate ide channels. This would involve swapping one of the drives for one of the CD/DVD drives. Just make sure you remember to double check the master/slave jumpers.[/QUOTE]

This I have not tried yet, but am considering, I'll let you know the results. In the long run, I expect that this process might work, but I would have to reinstall both Ubuntu and Windows XP to get it working.

[QUOTE=spd106]On which drive did you install grub? It should have replaced the MBR on the 6 gig drive (hda). Then be set up to dual boot. The menu.lst should be set up to have windows on (hd0,0) and Ubuntu on (hd1,0) assuming you put the root partition first. The read error means that it was unable to find the the next stage, which should be on the root partition of the 30 gig drive (hdb0).[/QUOTE]

Again, as I mentioned in the original post - I originally didn't even have the 6GB hdd in there, and installed Ubuntu permanent on the 30GB I had at the time. I couldn't even install Windows XP without literally taking the 30GB drive out of the equation. When re-adding it, this is where I encountered the Windows XP boot fail and the Ubuntu Grub Read Error - when trying to get one or the other to boot, and with editing menu.lst appropriately.

[QUOTE=spd106]You could always make a grub boot floppy. This would allow you to look for the kernel and initrc files from the grub cli. See, the floppy isn't dead yet![/QUOTE]

That's good to hear, glad I haven't trashed the floppy drive yet. They still sell disks these days? :D 

[QUOTE=spd106][http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
Have you tried a live CD? If it is able to mount both drives then you don't have a hardware problem.[/QUOTE]

That also seems logical, thanks for the advice I'm going to try it in the order you specified, I think you're on the ball about this. :mrgreen: 

[QUOTE=spd106]Hard drive space is so cheap these days it's almost not worth the time bothering with such a small drive. Hey it's almost an insult to the DFI board :cool: You could always repartition the 30 Gig drive to include windows. But you don't need to that, right?[/QUOTE]

Like I said before I'm waiting until I get SLI happening before worrying about what hard drive I'm going to use - but people are broke these days. I'm dying for a SATA Raid 10K rpm setup - obviously I've got to save up zee cash...no need to tell me I'm doing wrong to this thing. It's like driving a lawnmower on an expensive paid-for race track...abuse!

---

