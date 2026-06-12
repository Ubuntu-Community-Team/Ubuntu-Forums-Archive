---
title: "Hardware Drivers (info Please HELP)"
date: 2008-07-14
forum: Hardware
---

### Post by macnyak on 2008-07-14
hello to all,..

I just want to ask about hardware issues regarding Ubuntu and Kubuntu.

Here is a PC specs:

Athlon 64 X2 6000 Dual Core (processor)
ECS GF8200A (motherboard)
500GB Western Digital SATA (hard drive)
Transcend 2GB 800 DDR2 (2pcs. memory, total of 4gig)
Inno3D 8500GT 1GB ddr2 dvi 128bit (video card)
Asus 20X DVD writer lightscribe (optical drive)

MY QUESTIONS:

- What version of Ubuntu or Kubuntu will be best to use, 32bit or 64bit?

- Motherboard driver, Video card driver, and NERO for burning in the optical drive,... Do i have to install those drivers? if YES,  How can I install it in Ubuntu or Kubuntu? if NO, How will my devices will work properly?

- Does the following PC specs is supported by Ubuntu or Kubuntu? Will it run smoothly?

- Does Ubuntu or Kubuntu have updates and will automatically updates and detects the drivers for the motherboard and video card?

- Will COmpiz Fusion run on the PC with that specs? 

- please list some programs or softwares for web developing, web design, 3d animation, 


please help me thanks....

---

### Post by logos34 on 2008-07-14
the board apparently has some sata issues:
[http://www.phoronix.com/scan.php?page=article&item=nvidia_8200_mobos&num=4]("http://www.phoronix.com/vr.php?view=12579")

there's not much diff in performance between x86 and 64-bit...the latter seems a bit zippier loading apps and is faster doing processor-instensive tasks (encoding, archiving, etc)...and of course it supports more that 4 gb ram.  Other than than it's really up to you.

Ubuntu or kubuntu?  I prefer gnome/ubuntu, but I also like the speed of kde and the all the configuration options (but that's mostly a moot point for me since I usually hand edit all my config files).  I do, however, consider two kde apps essential in gnome/ubuntu: K3b and amarok.

yes, it automatically updates, incl. graphics

compiz fusion will easily run on your machine

---

### Post by macnyak on 2008-07-15
> **logos34 said:**
> the board apparently has some sata issues:
[http://www.phoronix.com/scan.php?page=article&item=nvidia_8200_mobos&num=4]("http://www.phoronix.com/vr.php?view=12579")

there's not much diff in performance between x86 and 64-bit...the latter seems a bit zippier loading apps and is faster doing processor-instensive tasks (encoding, archiving, etc)...and of course it supports more that 4 gb ram.  Other than than it's really up to you.

Ubuntu or kubuntu?  I prefer gnome/ubuntu, but I also like the speed of kde and the all the configuration options (but that's mostly a moot point for me since I usually hand edit all my config files).  I do, however, consider two kde apps essential in gnome/ubuntu: K3b and amarok.

yes, it automatically updates, incl. graphics

compiz fusion will easily run on your machine




thanks for a very helpful link...

and it states there:

System Setup:

As we mentioned in our GeForce 8200 IGP review, this chipset has a few issues currently with Linux. If you are using a Linux distribution that ships with a pre-2.6.25 Linux kernel, the Serial ATA support will likely go undetected. This means you will have a tough time using Ubuntu 8.04 LTS or other distributions from earlier this year unless using a separate PCI/PCI-E disk controller to get you started or building a new kernel first. The distribution we were successful using with the NVIDIA MCP78S "out of the box" was Fedora 9.

from:
[http://www.phoronix.com/scan.php?page=article&item=nvidia_8200_mobos&num=4](http://www.phoronix.com/scan.php?page=article&item=nvidia_8200_mobos&num=4)


how can i fix that issue?

---

### Post by logos34 on 2008-07-15
> **macnyak said:**
> 
how can i fix that issue?

I'll check the user manual...maybe there's a choice of Bios sata settings that might work (although if there was the review would probably have noted it)

update:  ok, the Bios only seems to allow the choice of sata mode 'AHCI':


> 
**Onboard S-ATA Controller (Enabled)**
This item allows you to enable or disable the onboard SATA controller.
**SATA Mode select ([COLOR=Red]AHCI Mode) --> if no other choice try disabling it[/COLOR]**
 Use this item to select the mode of the Serial ATA.
**AHCI Configuration (Press Enter)**
Scroll to this item and press <Enter> to view the following screen:
**AHCI Settings...** Usually on more recent boards there's choice of '**IDE legacy**' or '**IDE emulation**' mode--the only thing you lose in this mode vs, AHCI is NCQ (native command queing) and hot-swapping features.  For the average desktop (i.e. non-server) workstation, I doubt you'd notice much diff.
[]("http://blog.gunbladeiv.com/2008/05/ubuntu-how-to-upgrade-to-2625-kernel.html")

good luck

---

### Post by macnyak on 2008-07-16
which board will be best to buy:

-ECS A780GM-A

or

-ECS GF8200A

---

### Post by macnyak on 2008-07-16
> **macnyak said:**
> which board will be best to buy:

-ECS A780GM-A

or

-ECS GF8200A





[http://www.hardwaresecrets.com/article/580](http://www.hardwaresecrets.com/article/580)

---

### Post by logos34 on 2008-07-16
> **macnyak said:**
> which board will be best to buy:

-ECS A780GM-A


not sure about that one either. Seems to be same issue with the chipset it uses:
                         

> AMD SB 780G
AMD SB 700See this:
[http://ubuntuforums.org/showpost.php?p=4771896&postcount=41](http://ubuntuforums.org/showpost.php?p=4771896&postcount=41)

If you can't enable IDE emulation I would look for other boards

edit:

I just decided to take a look at the manual for the A780gm and its different.  It does show a Sata Mode 'IDE', so maybe you can set it:

p.35:
> Onboard IDE Controller Enabled
Onboard SATA Mode Enabled
**SATA Configuration IDE**
Onboard AUDIO Function Enabled
Onboard LAN Function Enabled
Onboard LAN Boot ROM Disabled
Serial Port1 Address 3F8&IRQ4
USB Functions Enabled
Legacy USB Support Enabled

> ...

SATA Configuration (IDE)
Use this item to show the Serial ATA Configuration options: Disabled, Compatible,
Enhanced.
...

So if you could use ide mode with either board then maybe that would solve the sata recognition problem during ubuntu install.  I'm just surprised the guys who wrote the first review didn't try that.

---

