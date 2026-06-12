---
title: "nvidia graphic caard"
date: 2009-04-04
forum: Hardware
---

### Post by cuteboysmith on 2009-04-04
hi. i am using a p4 1.6 Ghz pc with nvidia fx 5200 graphics card
i have dual boot on my pc... on windows the graphics card is detected 
but in ubuntu does not detect my graphics card... help (sorrry for poor english)

---

### Post by Melk79 on 2009-04-04
Don't worry about your english, we can help if we know more about the problem.  Are you saying you are running in low graphics mode and your screen resolution is not correct?  Can you not even start a graphic session and are stuck in a terminal session?  Which version of Ubuntu are you trying to install?  Hardy Heron (8.04) Intrepid Ibex (8.10)/ 32 or 64 bit?

---

### Post by cuteboysmith on 2009-04-04
i am using a ubuntu 8.10 and i ubuntu is booting in low graphics resolution ...  and when i used lspci i get this 



rudra@rudra-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)
01:00.0 VGA compatible controller: Trident Microsystems XGI Volari XP5 (rev 02)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by Melk79 on 2009-04-04
From Intrepid Release Notes:
Hangs with desktop effects on Intel 830MG and 845G video cards

There is a bug in the Intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and will freeze the system. For new installations, please install using the safe graphics mode (press F4 in the startup screen) on these systems and disable desktop effects via System -> Preferences -> Appearance, clicking on "Visual effects" and choosing "None".

---

### Post by cuteboysmith on 2009-04-04
but how do i install the nvidia grapgics driver 
i have nvidia fx 5200 card

---

### Post by norwoods on 2009-04-04
open System-->Administration-->Hardware Drivers.
if there is an active video driver, click on it and then click Deactivate
click on the NVIDIA 
click Activate.
clock Close
reboot

or install the nvidia-ati video driver installer, envyng, and use envyng to install a driver.

---

### Post by cuteboysmith on 2009-04-04
well in my system

System-->Administration-->Hardware Drivers.

does not detect any nvidia card, but i have connected  the card and when i boot in windows the nvidia card works fine.........

---

### Post by norwoods on 2009-04-04
install envyng using synaptic and use envyng to install a driver.

---

### Post by cuteboysmith on 2009-04-07
using envyNG it does not show any driver compatible
and if i install the not compatible drivers the result is same 
ubuntu boots in low graphics resolution

---

### Post by norwoods on 2009-04-07
according to the nvnews.net site, 173.14.18 is the current official release for 5 series gpus.
can you install a 173 driver with envyng?
can you run gksu nvidia-settings after installing a 173 driver and see what the nvidia-settings gui says your driver is?

---

### Post by cuteboysmith on 2009-04-09
i can install the 173 driver from envyng but it shows incompatible driver
and after running gksu nvidia-settings it shows error "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server"
while in dula booting in xp the card is working fine....

---

### Post by norwoods on 2009-04-10
> **cuteboysmith said:**
> but how do i install the nvidia grapgics driver 
i have nvidia fx 5200 card

your lspci says you have 01:00.0 VGA compatible controller: Trident Microsystems XGI Volari XP5 (rev 02)

you say you have nvidia fx 5200 card

maybe you should look closely at the card or look in your bios for which card is active.

---

