---
title: "USB unstability on AMD 790FX chipset"
date: 2009-02-11
forum: Hardware
---

### Post by c1981 on 2009-02-11
Hello,

I'm having rather serious USB issues - while running Ubuntu 8.04 - and hope to find either a solution OR confirmation that the mainboard (stated below) is dodgy in the USB department.

When performing read/write operations on any type of cardreader or USB harddrive; the USB subsystem comes to a near-complete standstill - everything freezes except for a secondary wireless keyboard/trackball combo - which continues to work.. But very badly after the error.. (mouse cursor mapping hardly works). Without the ability to use USB storage devices - this hardware / software combination is pretty much useless to me. 
 
Only a full reboot returns the system to normal - zapping X doesn't help.
Rebooting causes the system to repeat long system alarm beeps; right around the shutting down hal-daemon message.

Provided no mass storage devices are attached, Ubuntu works perfectly.

I've tried "noapic" "nolapic" and "irqpoll" kernel options - but none of them have any influence.

I considered power problems; attached devices with powered hubs as well as directly to the system ports. 

I also tried switching power management from powernowd, to powersaved, cpufreq and dyncpu (software side) - but the problem remains.

Frustrated with this problem - I even installed Windows XP for a test run (for the first time in Years)- ...and it has no USB problems whatsoever... 

Switching back to Windows or another Linux distribution is not an option;

A: I've been running Linux since 1993 / 1994 and love it.
B: Only Ubuntu features a completely free LTS option, and 
   offers commercial support for companies. As I do my best
   to migrate all those around me to free (libre) and 
   no-cost software, I see no other viable option at the 
   moment. (The Debian project does not offer large scale
   support for businesses... and openSolaris lacks too many
   features at the moment).

I've also tested the system on openSuSE 11.1 - which also works perfectly - aside from the occasional "ghost key strokes".

     ------could it be that Windows and SuSE up the voltage on the USB 
           subsystem by default? or that they have a different device
           enumeration method? 

The system also won't boot any Debian or Gentoo based system from USB - which leads me to believe Debian and Gentoo may have similar configurations in USB handling.

The hardware I use:

PSU:      Antec Earthwatts 650 Watt
Mobo:     MSI K9A2 Platinum (AMD 790FX chipset)
CPU:      AMD Phenom X4 9550
GPU:      Gigabyte Nvidia Geforce 8600GT
RAM:      2 x 2 GB Kingston HyperX DDR-2 1066 running @ 800 Mhz for compatibility.

Any thoughts?

Any comments on similar problems would also be helpful...

Thanks in advance..

---

### Post by Yashiro on 2009-02-11
It's a kernel driver issue. OpenSuse is using at least 2.6.27.
Hardy is 2.6.24.
Gentoo self build should be fine.
Debian will probably be broken.

USB dropout on amd 780+ was fixed after Hardy was released.
So unless the fix is backported you are screwed.

Debian 5 should work fine and it's out this week.

---

### Post by c1981 on 2009-02-11
Thanks for the reply :)

Kernel issue... of course... should have thought of that one :redface:

So, I guess it's either: searching for a fix, building a custom kernel or moving on to Ubuntu 8.10 or Debian 5... 

Gentoo would be fine for myself, but not for those I'm helping to migrate to free software.. it would take up too much of my time to deal with the phone calls etc...

For the past few years I've been using Intel chips and Gigabyte Ultra-durable hardware almost exclusively; the hardware setup mentioned in the post, is my test rig to provide a more affordable solution.

---

