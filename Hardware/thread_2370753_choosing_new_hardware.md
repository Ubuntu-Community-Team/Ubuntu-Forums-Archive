---
title: "choosing new hardware"
date: 2017-09-06
forum: Hardware
---

### Post by Ka Fish on 2017-09-06
I can only guess my power supply has shorted out after 9 years of...  Long story short time to upgrade. I'm told it's a standard size Power Man atx model no  IP-P300AJ2-0 running an Aopen motherboard that maxes out at 2 gigs. It's  in an unnamed prototype tower. I believe the parts I've selected are  compatible with each other & Ubuntu 16.04 lts. What do you think? 
**EVGA - B3 450W 80+ Bronze Certified Fully-Modular ATX Power Supply**

**MSI - 970 GAMING ATX AM3+ Motherboard**

**AMD - FX-6200 3.8GHz 6-Core Processor**

**Kingston - Savage 8GB (1 x 8GB) DDR3-2133 Memory**

**Diamond - Radeon R7 250 1GB Video Card**

**LG - GH24NSB0B DVD/CD Writer**

---

### Post by lammert-nijhof on 2017-09-07
It is hard to reply, because not everybody has your hardware in use. I expect you will be OK, since most HW is around for a couple of years; from well known companies and thus probably well supported. Sometimes there are problems with Radeon Video Cards, but you have to try to find an owner of that card or google for it. When I googled for it, it seems supported in Ubuntu 16.04.

---

### Post by oldfred on 2017-09-07
Do not know AMD as I use Intel but AMD Gigabyte boards need IOMMU settings.
And both AMD & nVidia video cards normally need nomodeset until proprietary driver installed.

  GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370) 

      
 AMDGPU: [https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)
AMDGPU-PRO: [https://help.ubuntu.com/community/AMDGPU-PRO-Driver](https://help.ubuntu.com/community/AMDGPU-PRO-Driver)

---

### Post by Bucky Ball on 2017-09-07
Good power supply from a name brand. And I am a stickler for a reliable, efficient power supply. It's the heart of the machine and shouldn't be overlooked. If the PSU dies in a tower, it generally takes another component or two out with it. Generic, no-name silver box PSUs should be outlawed! ;)

I might suggest you find a PSU calculator and run those components through it (and any others you intend to use or install now or later) to see if that 450W unit is going to handle it. No need for overkill, in fact I'd advise against it as a waste of energy, but you need to cover your demands.

---

### Post by Ka Fish on 2017-09-08
Thank you all that helps. I did change to 
[h=1]Rosewill - 500W 80+ Gold Certified ATX Power Supply.[/h]

---

