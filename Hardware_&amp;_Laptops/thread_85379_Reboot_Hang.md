---
title: "Reboot Hang"
date: 2005-11-02
forum: Hardware &amp; Laptops
---

### Post by phanboy_iv on 2005-11-02
Just a small problem.
Whenever I try to reboot from Ubuntu, the system goes through the steps, and shuts down everything, including itself, 
like it's supposed to. Except it doesn't power the laptop down and restart it. It just sits there. This was a problem with Hoary as well, and almost every other distro I've experemented with, so I imagine it's a kernel problem.
That being said, is there any config file I can play with to try to get reboot working? Or will I just have to wait for a newer kernel version? Oh, and shutdown works fine, it's just kind of a pain to do that all the time when I need to restart my computer.

---

### Post by John.Michael.Kane on 2005-11-02
Could you post your sys spec's.

---

### Post by phanboy_iv on 2005-11-02
Okay.

Toshiba Satellite A85-S1072
1.4 ghz Celeron M
256 MB RAM
40 GB hard drive
Atheros Wireless NIC
ATI Mobility Radeon 9000 IGP
Alps Touchpad
DVD/CDRW Drive
BIOS is made by Phoenix, I think

Sorry if that's not the right info, I'm still learning. If there is a terminal command I need to run for this, 
let me know.

---

### Post by department27 on 2005-11-03
I had the same problem with a sony vaio. I changed my menu.lst by adding noapic and nolapic :

kernel          /boot/vmlinuz-2.6.12-9-686 root=/dev/hda1 ro no apic nolapic quiet splash

and that fixed it for me.

---

### Post by phanboy_iv on 2005-11-03
[QUOTE=department27]I had the same problem with a sony vaio. I changed my menu.lst by adding noapic and nolapic :

kernel          /boot/vmlinuz-2.6.12-9-686 root=/dev/hda1 ro no apic nolapic quiet splash

and that fixed it for me.[/QUOTE]


Bother. Didn't work. Thanks though.

---

### Post by wcarty on 2005-11-04
I also have the same problem when rebooting my laptop.

I have a Toshiba Satellite P35-S605
:(

---

### Post by John.Michael.Kane on 2005-11-04
Try installing 5.10 with out acpi support hit F1 the for it should be there. it sounds like this may be cause of the hang..

---

### Post by Dormous on 2005-11-04
I too am having this issue, and had it with Hoary as well, but turning off ACPI doesn't seem like a viable solution. This solution seems to defeat the purpose of owning a laptop.  Disabling ACPI turns off all the nifty power saving features that you need so desperately on a laptop.  Are there any other solutions?

I have a toshiba laptop as well (don't remember the model number right now) with a Radeon 9000 IGP graphics card.  Maybe it's the radeon and not ACPI?

Just noticing patterns here...

---

### Post by John.Michael.Kane on 2005-11-04
The origial poster has a Celeron which if im not worng does not have speed step technology. so he should be able to use his/her laptop with out acpi. i dont know what you have in your laptop as you posted no specs.

---

### Post by phanboy_iv on 2005-11-07
[QUOTE=SD-Plissken]The origial poster has a Celeron which if im not worng does not have speed step technology. so he should be able to use his/her laptop with out acpi. i dont know what you have in your laptop as you posted no specs.[/QUOTE]

Yes, my Celeron M doesn't have speedstep.

Thanks for the tip. Maybe I'll just live with it though. A reinstall doesn't appeal to me at this point for a 
minor(for me)issue such as this. 

And it's "his";)

---

### Post by Dormous on 2005-11-07
I have a mobile Pentium 4 3.0 GHz with HyperThreading.  I have 1 gig of ram and a 60 gig hard drive, 15 of which is partitioned for linux.

Turning off ACPI doesn't help on my machine.

Dormous

---

### Post by souki on 2005-11-07
same problem for me when rebooting, but I have "shutdown" working properly.

I've tried to force the reboot from the command line with "reboot -d -f -i" with no success

---

### Post by Raoul Duke on 2005-11-29
I have the same thing on my Toshiba Satellite 2450. I never had the problem before moving to Ubuntu, reboot & shutdown always worked properly with both Debian and vanilla kernels with both ACPI and APIC turned on. Besides turning those off really seems to me to be no solution at all...kind of like pooping in the garden because your toilet won't flush.

---

### Post by Richard the turd on 2005-12-09
Hi i have a problem with my Toshiba Satellite P35 512mb Ram P4

Whenever I start it I get this error 
" IRQ Problem with network Controller in PCI Slot 3"
I got this error when I tried to connect it to the office Network 
(Its my bosses Laptop and he was having trouble with it before this - he couldnt elaborate anymore on this GREAT )

I disabled the Network Card in Slot 3 

Still get same error (Only starts in safe mode)

I uninstalled the Network Card yet still get the same error 

Reinstalling the OS doesnt fix it either (Using the Toshiba Restore CD)

Any Idears ... Anyone ????

---

### Post by wb0gaz on 2006-02-05
I have just installed Ubuntu 5.10 on a machine and was curious that I could not restart it (shutdown -r, telinit 6, etc.), instead shutting the machine down cold, and discovered this thread. My machine is not a laptop - instead, it is a specialized machine used for point of sale and other industrial applications - it is called LT5000 by cappuccinopc.com. My intended use is for industrial telemetry server in unmanned location, so inability to restart remotely is a very severe problem. I like other apsects of the Unbuntu install (it is very compact at ~250MB disc space, important because I'm using a flash-based "disc") so I'd like to solve this rather than just moving on to try other distributions. I'm not sure now ACPI and related stuff will apply to this machine - power consumption is important, but I'm not far enough along to understand if/how I can optimize things like dynamic speed, etc. I have not experimented yet with modifying boot-time options, but I did want to join the thread with this information because it is clearly first- and foremost problem for me to solve before even considering Ubuntu for this application.

The machine's technical properties include this (the remaining properties are pretty much generic video-floppy-ide-usb-memory-etc...):

On-board VIA C3/Eden 376 PIN EBGA package
Front side bus 100/133MHz
VIA Eden Processor 533M
Chipset 	VIA PLE133 VT8601A and VT82C686B

Tks,

Dave
[email]wb0gaz@hotmail.com[/email]

---

### Post by ranf on 2006-02-05
You guys could try to add the option "reboot=h" to the kernel command line.

From:
zless /usr/share/doc/linux-doc-2.6.12/Documentation/kernel-parameters.txt.gz
(gets installed when you install the package `linux-doc-2.6.12')

---

### Post by wb0gaz on 2006-02-07
The three kernel arguments I've tried - noacpi, nolacpi, reboot-h - all did not correct the problem (it still halts in response to any reboot type command issued.)

I went ahead and disabled ACPI in the BIOS set-up. This corrected the problem, although there are two modules the kernel now doesn't load - fan.ko and thermal.ko. I don't believe these are too serious (the machine has no fan); I'll do some research. This probably is of no help with the rest of the people in this thread that have laptops, but at least I have a workaround.

In any event, I hope this thread reaches the keepers of the relevant part of Ubuntu - I like the system and am looking forward to applying it.

Tks,

Dave
[email]wb0gaz@hotmai.com[/email]

---

### Post by Dormous on 2006-02-07
Just as an FYI, I was getting similar reboot hangs in Debian Sarge with both the distro's kernel, and custom compiled kernels as well.

Dormous

---

