---
title: "Unable to install Ubuntu or ANY Linux :-((("
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by optimistique1 on 2008-12-15
I Just got the Advent 5421 today and I have been trying ALL DAY to install Ubuntu or infact any Linux  distro.
I have tried around five different distros and NONE of them will install and I can't figure out why as they have installed fine on other laptops.
Basically I try and boot from the 'Live CD's' and then they all get to the step where the Linux Kernel has loaded 100% and then it completely stalls and the disc stops spinning......
Can anybody help me try and get this resolved.
I don't know if I need to somehow load 'grub' into the MBR and if so HOW?
Or does it perhaps need a bios update.
I am not a whizz on computers but I desperately need some help with this?
Many thnks
Garry

---

### Post by joff13 on 2008-12-15
> **optimistique1 said:**
> I[...]
Basically I try and boot from the 'Live CD's' and then they all get to the step where the Linux Kernel has loaded 100% and then it [...]

Hi Garry, 

did you try with a non-live distro? perhaps ubuntu-alternate ?

---

### Post by gjoellee on 2008-12-15
If you have new hardware on your computer it will normally get support in one of the next Linux kernels. There is a new kernel every 3 month

---

### Post by optimistique1 on 2008-12-15
Hi, all of the distros I have used have been LIVE CD's including the Ubuntu one.
Also, when you say that there is a new Linux kernel every so often what does this mean and how do I get the distro to boot properly and install.
I get the option to 'install witout making any changes' and then as soon as the splash screen comes on it stops......

---

### Post by eldragon on 2008-12-15
when booting a livecd.....remove the splash line from the boot command in order to see kernel logs..

write here the last line it pops before freezing. might give a clue on what needs to be done in order to have a working system..

---

### Post by optimistique1 on 2008-12-15
How do I remove the splash line from the boot command?
Many Thanks
Garry

---

### Post by eldragon on 2008-12-15
> **optimistique1 said:**
> How do I remove the splash line from the boot command?
Many Thanks
Garry

dont remember exactly, but read the screen, scan for "edit boot options" or something similar.....if you happen to have the same problem i have you will have a hard time getting the system to boot linux :(

---

### Post by joff13 on 2008-12-15
> **optimistique1 said:**
> How do I remove the splash line from the boot command?
Many Thanks
Garry

select the line you want to boot
press "e" to edit the line
press "b" to boot

---

### Post by linux_tech on 2008-12-15
What are your system specs? 

```
lshw
```

The alternate install allows you to do a text based custom install and usually runs on most systems

[http://releases.ubuntu.com/8.10/](http://releases.ubuntu.com/8.10/)

Make sure to select the correct version for your pc.

If that does not work, use the the live cd to run gparted to pre-format your hard drive as ext3.  Then try the install again.

---

### Post by optimistique1 on 2008-12-15
Thanks for that buddy will give it a go now-

Here are the sys specs - 

Processor(s)	
Number of processors	1
Number of cores	2 per processor
Number of threads	2 per processor
Name	Intel Celeron
Code Name	
Specification	Genuine Intel(R) CPU T1500 @ 1.86GHz
Package	Socket P (478)
Family/Model/Stepping	6.F.D
Extended Family/Model	6.F
Core Stepping	M0
Technology	65 nm
Core Speed	1867.1 MHz
Multiplier x Bus speed	14.0 x 133.4 MHz
Rated Bus speed	533.4 MHz
Stock frequency	1866 MHz
Instruction sets	MMX, SSE, SSE2, SSE3, SSSE3, EM64T
L1 Data cache (per processor)	2 x 32 KBytes, 8-way set associative, 64-byte line size
L1 Instruction cache (per processor)	2 x 32 KBytes, 8-way set associative, 64-byte line size
L2 cache (per processor)	512 KBytes, 2-way set associative, 64-byte line size
Chipset & Memory	
Northbridge	SiS 672 rev. 00
Southbridge	SiS 968 rev. 01
Graphic Interface	AGP
AGP Revision	3.0
AGP Transfer Rate	8x
AGP Side Band Addressing	supported, enabled
Memory Type	DDR2
Memory Size	1024 MBytes
Memory Frequency	333.4 MHz (4:10)
CAS# Latency (tCL)	5.0 clocks
RAS# to CAS# (tRCD)	5 clocks
RAS# Precharge (tRP)	5 clocks
Cycle Time (tRAS)	15 clocks
System	
System Manufacturer	DIXONSXP
System Name	DIXONSXP
System S/N	12345678901234567
Mainboard Vendor	DIXONSXP
Mainboard Model	N/A
BIOS Vendor	OEM
BIOS Version	1.13
BIOS Date	07/04/2008
Memory SPD	
Module 1	DDR2, PC2-5300 (333 MHz), 1024 MBytes, A-Data Technology
Software	
Windows Version	Microsoft Windows Vista (6.0) Home Basic Edition Service Pack 1 (Build 6001)
DirectX Version	10.0

---

### Post by optimistique1 on 2008-12-15
I also managed to boot the CD without the splash screen and I get a load of text but I don't really know what I am looking for :-(

Does this mean anything:

'MARKING TSC UNSTABLE  DUE TO TSC HALTS IN IDLE'....

---

### Post by eldragon on 2008-12-15
if your system is freezing during kernel booting, you will have the same problem when loading the alternate install cd (which needs a kernel to work).

first you need to know which kernel module is freezing your system, and then blacklist it in the alternate install cd before being able to install

---

### Post by optimistique1 on 2008-12-15
How do I find out which kernel module is freezing your system?

I also have the same problem if I try and load OSX, that freezes too.

It's almost like the only thing that will install is windows  YUK!!!!!

---

### Post by eldragon on 2008-12-15
> **optimistique1 said:**
> How do I find out which kernel module is freezing your system?

I also have the same problem if I try and load OSX, that freezes too.

It's almost like the only thing that will install is windows  YUK!!!!!

editing the freaking boot options and removing splash.

concerning osx, it might be anything. especially since osx is not supposed to run on anything but a mac..

---

### Post by optimistique1 on 2008-12-15
managed to boot the CD without the splash screen and I get a load of text but I don't know what I am looking for

---

### Post by eldragon on 2008-12-15
> **optimistique1 said:**
> managed to boot the CD without the splash screen and I get a load of text but I don't know what I am looking for

read my first post.

---

### Post by optimistique1 on 2008-12-15
I just tried to install PC BSD and this flashes up saying - 

adc0: FAILURE - READ_BIG HARDWARE ERROR asc = 0x3e ascq=0x02

Does this mean anything to anyone???

---

### Post by optimistique1 on 2008-12-15
Ok here are the last lines before it freezes in Ubuntu - 

1.982827} Marking TSC unstable due to TSC halts in idle

---

### Post by eldragon on 2008-12-15
i missed one of your posts......

edit the boot options, and try with noacpi and remove the splash command...see if that gives you a booting system

you could try adding the following option to the bootoption list: clocksource=hpet

instead of noacpi

---

### Post by optimistique1 on 2008-12-15
same as last time -

1.937234} Marking TSC unstable due to TSC halts in idle

---

### Post by eldragon on 2008-12-15
edited my previous post, read it :D

---

### Post by joff13 on 2008-12-15
> **optimistique1 said:**
> Ok here are the last lines before it freezes in Ubuntu - 

1.982827} Marking TSC unstable due to TSC halts in idle

[http://ubuntuforums.org/showthread.php?p=4464805]("http://ubuntuforums.org/showthread.php?p=4464805")

---

### Post by optimistique1 on 2008-12-15
Ok Eldragon this is what I get now - 

1.942928] Marking TSC unstable due to TSC halts in idle
1.943238] ACPI: CPU1 (power states: C1 [C1] C2 [C2] C3[C3])
1.943483] Processor ACPI007:01: registered as coolling_device1
1.943542 ACPI: Processpr [CPU1] (supports 8 throttling states)

The it freezes  :-(((

---

### Post by Casper Hansen on 2008-12-15
Just a thought... But did you check md5sum and burn the .iso to the disc at the lowest speed?

---

### Post by Topsiho on 2008-12-15
Someone else already said this before me: if you have new hardware you run the risk that it is not yet supported by the present Linux-kernel.
It appears to me that your processor is not yet known to the kernel you have (and the other Linuxes as well, which all of them do not use a kernel that does not yet exist), so the boot process halts.

The last line says

1.943542 ACPI: Processpr [CPU1] (supports 8 throttling states)

Not paying any attention to the typo, I think the present kernel does not know what to do with 8 throttling states: thus that the processor is not known to this kernel.

When using new hardware you always run the risk that the Linux kernel gets confused. You'll have to wait until the next (stable) kernel is released, and then try again.

Why is someone who says something useful not listened to :confused:

Topsiho

---

### Post by optimistique1 on 2008-12-15
> **Topsiho said:**
> Someone else already said this before me: if you have new hardware you run the risk that it is not yet supported by the present Linux-kernel.
It appears to me that your processor is not yet known to the kernel you have (and the other Linuxes as well, which all of them do not use a kernel that does not yet exist), so the boot process halts.

The last line says

1.943542 ACPI: Processpr [CPU1] (supports 8 throttling states)

Not paying any attention to the typo, I think the present kernel does not know what to do with 8 throttling states: thus that the processor is not known to this kernel.

When using new hardware you always run the risk that the Linux kernel gets confused. You'll have to wait until the next (stable) kernel is released, and then try again.

Why is someone who says something useful not listened to :confused:

Topsiho


Thankyou for your help Topsiho, the worst part of all of this was not understanding 'WHY' this was happending.

You mention that I will have to wait until the next stable kernel is released.  It may sound silly but how do I know when it is relased and also, when it is released what do I need to do exactly?  Does t mean that I have to download the ISO again and how will I know that it contains the kernel that I need...

I am only coming to grips with day to day usage of Linux and everything else is a bit 'over my head' at the moment.

Many thanks

Garry

---

### Post by Seq on 2008-12-15
According to this [thread]("http://ubuntuforums.org/showthread.php?p=6371433"), adding "APIC=off" or "noapic" to the boot string (the same line you edited to remove "splash") should get the livecd running.

If that works, then you might want to [Create a bug report]("https://edge.launchpad.net/ubuntu/+filebug") on Launchpad. Ubuntu's kernel team will ask you for more information (not sure what they will need) and hopefully the issue will be resolved and work out-of-the-box in the future.

---

### Post by optimistique1 on 2008-12-15
Hey Seq thanks for that I will give this whirl when I get home as I am at work now.
Will update tomorrow if I get no joy.
Fingers crossed....
:-)

---

### Post by Seq on 2008-12-15
> **optimistique1 said:**
> Hey Seq thanks for that I will give this whirl when I get home as I am at work now.
Will update tomorrow if I get no joy.
Fingers crossed....
:-)

Post back anyway, I'm sure we would all like to know how it goes.

Just one revision to my "create a bug report" entry above: Make one anyway, not just if it works ;)

---

### Post by optimistique1 on 2008-12-15
No worries will post back tomorrow and let you all know either way how it goes.  Hopefully with 'good' news. :popcorn:

---

### Post by optimistique1 on 2008-12-16
Hi Guys, bad news still no joy.  It still hangs at the same place.
Looks like it isn't ever going to work so I am either stuck with windows or I will have to get another latop :-(

---

### Post by eldragon on 2008-12-16
i still believe its something else..

i remember being able to run my buggy notebook with DSL (damn small linux) forcing it NOT to detect any hardware and go with old standards (which are usually supported by new hardware).

you could try that.

test it here: [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

it wont give you what you want, but it will help you get a working system to work with (and for example, list hardware, start adding modules 1 by 1).

id feel really exited to debug your notebook! you will learn a lot :D

i dont remember which was the combo to disable hardware detection, read their website :D

---

### Post by Topsiho on 2008-12-17
> **optimistique1 said:**
> Thank you for your help Topsiho, the worst part of all of this was not understanding 'WHY' this was happening.

You mention that I will have to wait until the next stable kernel is released.  It may sound silly but how do I know when it is released and also, when it is released what do I need to do exactly?  Does t mean that I have to download the ISO again and how will I know that it contains the kernel that I need...

I am only coming to grips with day to day usage of Linux and everything else is a bit 'over my head' at the moment.

Many thanks

Garry

The kernel is updated sometimes quite often with the regular updates from Ubuntu. And I am afraid there is a snag here: these updates are applied to an already installed Ubuntu system.
So if I am right (which in this special case I hope I am NOT :)) I fear that you'll have to wait for the next version of Ubuntu, or one of it's Release Candidates (beta versions that are released in the latter part of it's development cycle).
If you have another working computer that is connected to the internet you can watch for these events, download the .iso's, burn them, check them for errors in the drive you are going to use for the install, and then try to install them.

If I am not correct you could of course listen to the other posters and try their suggestions. Keeps you busy in the mean time, and you probably learn a lot from this. People learn more from when the going is tough then when all is going smoothly :) Only don't get frustrated...

If this helps you: usually the install of Ubuntu is very smooth indeed. I use Ubuntu from the start (4.10) and have also used numerous other distributions, such as Mandrake (now Mandriva), Red Hat (my first, 5.1), Fedora and Suse. All are great, but none of them beats Ubuntu (except for the Dutch translations, in Ubuntu these are a mess, but this probably does not bother you :)).

But sometimes Ubuntu does not install on one of my computers, and then I try the alternate version. (Hey: did someone mention this to you? I did not read all posts).
But all my computers that I have and that I had were older ones, except for a Toshiba laptop (which gave no problem at all) and my new Acer netbook, in which only the really new wifi chip gave problems (which were cured insufficiently in a newer kernel), which were fixed very well by compiling and installing a new driver, from a suggestion on a website dedicated to this specific netbook (it helps if you have a very popular computer).

Hope this will help to you,

Topsiho

---

### Post by gjsduarte on 2009-02-21
Hi there.

Try combining the previous parameters adviced in this forum.

"noapic acpi=off irqpoll"

RGDS

---

### Post by Mez on 2009-10-02
Sory if I'm dragging up an old topic, but I've got one of these myself, and know how to fix it.

The system needs the kernel command "nolapic_timer" to boot... 

I can't remember how to change this on a live CD off of the top of my head, but if you can find how to edit the boot parameters, you need to add "nolapic_timer" (without the quotes) after "quiet splash" on the kernel line.

Surprisingly however, Karmic boots without this! - Yay!

---

