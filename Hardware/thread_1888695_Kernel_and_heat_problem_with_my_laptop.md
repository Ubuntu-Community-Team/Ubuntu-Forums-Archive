---
title: "Kernel and heat problem with my laptop"
date: 2011-11-29
forum: Hardware
---

### Post by figo2476 on 2011-11-29
Hi,

* I have a dell xps 1645. It is running ubuntu 11.10 with
- linux-headers-3.0.0-13-generic_3.0.0-13.22+mjgaspmfix_amd64.deb
- linux-image-3.0.0-13-generic_3.0.0-13.22+mjgaspmfix_amd64.deb

* I have a serious heat problem with laptop. The CPU/GPU runs crazy and it is hot.

* According to [https://wiki.ubuntu.com/Kernel/PowerManagement](https://wiki.ubuntu.com/Kernel/PowerManagement), the above 2 should fix the heating issue (or at least the power consumption issue)

* powertop 1.97 result:

                                  
   Bad           Enable Audio codec power management
   Bad           Enable SATA link power management for /dev/sda
   Bad           Autosuspend for USB device iPod (Apple Inc.)
   Bad           Autosuspend for USB device USB Optical Mouse [2-1.2]
   Bad           Runtime PM for PCI Device Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4
   Bad           Runtime PM for PCI Device Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5
   Bad           Runtime PM for PCI Device Intel Corporation Core Processor PCI Express Root Port 1
   Bad           Runtime PM for PCI Device Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
   Bad           Runtime PM for PCI Device Intel Corporation 5 Series/3400 Series Chipset High Definition Audio
   Bad           Runtime PM for PCI Device Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1
   Bad           Runtime PM for PCI Device Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2
   Bad           Runtime PM for PCI Device Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
   Bad           Runtime PM for PCI Device Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller
   Bad           Runtime PM for PCI Device Intel Corporation Core Processor QPI Link 0
   Bad           Runtime PM for PCI Device Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe
   Bad           Runtime PM for PCI Device Ricoh Co Ltd FireWire Host Controller
   Bad           Runtime PM for PCI Device Ricoh Co Ltd MMC/SD Host Controller
   Bad           Runtime PM for PCI Device ATI Technologies Inc RV710/730
   Bad           Runtime PM for PCI Device Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6
   Bad           Runtime PM for PCI Device ATI Technologies Inc Device 9488
   Bad           Runtime PM for PCI Device Broadcom Corporation BCM43224 802.11a/b/g/n
   Bad           Using 'ondemand' cpufreq governor

---

### Post by typhoon_tip on 2011-11-29
Have you installed the FGLRX driver ? If not, that is the problem. The stock driver is going to fry the video card on laptops.

If you install FGLRX driver, you can then use only Unity since Gnome 3 is not yet compatible with ATI. (or vice-versa...)

---

### Post by bluexrider on 2011-11-29
Dell XPS 1645 isn't listed but the recommendation for Dell XPS 1130M is the 
3.0.0-13-generic-pae

Are you sure you applied the proper kernel

---

### Post by figo2476 on 2011-11-30
I solved my problem --> [http://thdonline.wordpress.com/2011/11/30/dell-xps-1645-overheat-with-kernel-3-0-0-13/](http://thdonline.wordpress.com/2011/11/30/dell-xps-1645-overheat-with-kernel-3-0-0-13/)

---

