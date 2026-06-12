---
title: "Ubuntu on Pavilion Desktop PC 570-p017no ?"
date: 2018-06-18
forum: Hardware
---

### Post by thomasa88 on 2018-06-18
Hi,

Has anyone tried Ubuntu on the HP Pavilion Desktop PC 570 series? Specifically Pavilion Desktop PC 570-p017no.

---

### Post by oldfred on 2018-06-18
Have you tried booting live installer in live mode just to test how well it works?
It looks like you have nVidia, so you will need nomodeset boot parameter.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Since UEFI system be sure to always boot in UEFI boot mode. Do not turn on Legacy/BIOS/CSM boot modes.
       
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

See also link in my signature below.

Issues are often common across models within brand, then whether AMD or Intel and then which video card/chip is used. So most HP with Intel 7th gen and nVidia will be same as yours.

      
 HP UEFI boot order change with efibootmgr does not stick, but change in HP's UEFI does work
[https://ubuntuforums.org/showthread.php?t=2390309](https://ubuntuforums.org/showthread.php?t=2390309)
HP 11m reinstall Windows & dual boot with Ubuntu 16.04
[https://ubuntuforums.org/showthread.php?t=2389104](https://ubuntuforums.org/showthread.php?t=2389104)
Probook G4 470 Ubuntu works fine with UEFI and secure boot. 
[https://ubuntuforums.org/showthread.php?t=2381663](https://ubuntuforums.org/showthread.php?t=2381663)

---

### Post by thomasa88 on 2018-06-19
Thanks for the very content-filled answer! A bit scary with e.g. the BIOS bricked Lenovos.

I have actually not yet bought the computer (still deciding whether to build my own), but if I get in the mood to buy it, I'll see if a store lets me run the live mode. Good point :)

---

### Post by oldfred on 2018-06-19
I prefer to build my own. I do prefer Intel, but AMD is often cheaper.

I wanted SFF size system so paid bit more for smaller case & power supply.
And prices now seem higher, but older parts may not be as available.
Best to not use bleeding edge hardware, I had to use 16.04 before it was released to get this system to work.
       oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)
[http://pcpartpicker.com/p/8QKkCJ](http://pcpartpicker.com/p/8QKkCJ)

---

