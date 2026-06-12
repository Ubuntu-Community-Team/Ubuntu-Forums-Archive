---
title: "Is this a hardware problem?"
date: 2012-10-15
forum: Hardware
---

### Post by Olympe on 2012-10-15
Hi,

I tried asking this at the "Installation & upgrades", but didn't get any replies. 

I'm wondering now if the problem might be with the hardware, so any views on this would be appreciated:


I upgraded my laptop from 10.04 to 12.04 LTS. For a couple of days it  worked fine, but then it started freezing (maybe after an update) all  the time. No matter what I was doing with it. I tried to look for advice  on the forums but it only got worse and now I cannot  do anything with it: when turning on the computer it only shows the  purple colored screen. The only thing I have managed is to press f11  when switching the computer on, to choose the recovery mode and an   older version. Then it works okay. The problem is that then the screen  looks a little distorted or ”stretched” and soon the screen gets sort of  pixely.. (partly see through yellow and purple pixel mess) Sometimes the pixel mess  disappears just to reappear soon again.
 

 Any ideas what's wrong? And how do I make the older version the default. Now I  have to go through f11 every time I switch on the computer..
 

My laptop is HP Pavillion dv6000.  
  2.0 GiB
  AMD Turion(tm) 64 X2 Mobile Technology TL-60  
 Graphics: VESA: G86 Board – e416h01c
 
 32-bit
 113,3 Gt
 
 The laptop is from 2007, and the dvd-drive is broken already. Maybe  it's the end of the laptop? Or is there something I can try to fix this?
 
 (I've been using Ubuntu for 5 years. I've managed to fix some problems  during the years with the help found online, but now I haven't had any  problems for some time and have forgotten even the basic commands.. So  please give precise instructions..)

some code anyway:
 
 uname -a 
Linux apparaatti 2.6.32-42-generic #96-Ubuntu SMP Wed Aug 15 18:57:09 UTC 2012 i686 athlon i386 GNU/Linux  
 

 sudo lshw -C display
[sudo] password xxxx
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: G86 [GeForce 8400M GS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:b1000000-b1ffffff memory:c0000000-cfffffff(prefetchable) memory:b2000000-b3ffffff ioport:4000(size=12:cool:

---

### Post by ALinuxWindowsBalance on 2012-10-15
I have a Dell D610, about 5 years old, too. It refused to upgrade to 12.04, so it stayed at 11.10.

**Try upgrading to 11.10, then going to 12.04. If it doesn't work, stay with 11.10. If 11.10 doesn't work(which it should) try 11.04.**

Yeah, some computers just aren't made good enough to cross over to 12.04. Don't worry, 11.10 is fine, and still supported.

---

### Post by Olympe on 2012-10-17
Thanks, I'll try to install the 11.10. Only my dvd drive is ****** and as i tried booting from usb with 11.10 it didn't succeed.. "no operating system found" or something like that. Guess I have no bootable flash drive..

---

