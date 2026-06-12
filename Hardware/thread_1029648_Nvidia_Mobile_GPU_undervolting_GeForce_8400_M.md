---
title: "Nvidia Mobile GPU undervolting GeForce 8400 M"
date: 2009-01-03
forum: Hardware
---

### Post by psihodelia on 2009-01-03
Hello dear Ubuntu experts!

I have new 17" Laptop which has a "Nvidia GeForce 8400M G" graphics chipset. It is very fast but very loud. 

In order to eliminate fan noise, I have applied a  CPU undervolting kernel patch [https://www.dedigentoo.org/trac/linux-phc/]("https://www.dedigentoo.org/trac/linux-phc/").

Now, my CPU is much cooler, but fan noise is still disturbing, especially if I am watching any fullscreen online movies like youtube or video.google.com. I have tried different Linux distros and diferent Nvidia drivers. Currently I use 180.17beta.

Temperature sensors sometimes show even 90C on Nvidia. CPU is Intel Pentium Dual Core T2370 1.73GHz which has temperature between 55 and 67C. Fan noise is very very loud! This is no doubt a problem of hot Nvidia GPU.

Normally if I am only surfing the Internet, Nvidia GPU is constantly about +78..+80°C. In my opinion it is very very high value and I am looking for a solution, probably GPU's voltage should be decreased. But how? Any idea? nvclock doesn't work with mobile GPUs.

PS:
Maybe to resolder some pins or so, but I cannot find any circuit design schema of any Nvidia hardware...

here is some useful info:
> ~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +55.8°C  (crit = +105.0°C)                  
temp2:       +77.2°C  (crit = +126.8°C) 

> ~$ cat /proc/cpuinfo | grep name
model name      : Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz
model name      : Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz

> ~$ lspci 
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M G (rev a1)
05:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
06:04.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
06:04.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
06:04.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller


> ~$ lsusb 
Bus 005 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:c050 Logitech, Inc. RX 250 Optical Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


---

### Post by psihodelia on 2009-01-06
Can anybody with mobile GeForce 8400 M please confirm you have the same high temperature numbers?

---

### Post by rossmoore on 2009-05-27
Hey. I've got a Dell laptop which has an 8600M graphics chipset. I get temperatures in the mid 60s on idle. I've also been playing with PHC's CPU undervolting. I havent completed optimizing it and stuff, but I get the distinct feeling, like you, that I'm going to have to reduce the GPU power draw too if I want the fans to run slower (and keep the thing safe).

So - I can't help you, I get slightly cooler results with a slightly different chipset, and I'm looking for similar help! Not much use, but you're not alone at least.

---

### Post by Gausian on 2009-05-27
my 8400M GS normally floats around 56-62 degrees.  the nvidia powermizer should underclock the gpu when not in use or under light load.

do you have the thermal monitor and powermizer monitor options enabled in the nvidia config?

---

