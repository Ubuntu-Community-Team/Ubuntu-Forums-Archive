---
title: "What processor can I upgrade to?"
date: 2011-10-06
forum: Hardware
---

### Post by NohOne90 on 2011-10-06
Make: Hewlett Packard
Model: Pavilion 522n
Hard Drive: 60GB
RAM: 1GB DDR SDRAM
Processor: 1.8Ghz Intel Celeron 
Operating System: Ubuntu 10.10 (maverick)

Currently the processor is running at 100% all the time. I first thought  this was due to the fact that I didn't have enough RAM because I was  running the bare minimum for the Maverick OS, so I upgraded it from  256mb to 1GB. This did not solve the problem, so as it is an old  computer, I thought perhaps just a new processor would fix this. Here is  all the information given using the lspci command in the Terminal.

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 Multimedia audio controller: Avance Logic Inc. ALS4000 Audio Chipset
02:0b.0 Communication controller: Agere Systems LT WinModem (rev 02)


I have also been told that I need to "activate" the Intel drivers and was given the following link.

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus#Manually_enabling_the_Intel_driver](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus#Manually_enabling_the_Intel_driver)

The only problem with this, is that I'm told I need to make a new file. I  am new to Ubuntu and do not know how to go about this, or where the  file would be located/created. This wiki does not give any information  on this aspect of the file's creation (or the location thereof). Any  help would be greatly appreciated, or any other ideas on what I can do  to make this computer not so agonizingly slow.

---

### Post by collisionystm on 2011-10-06
> **NohOne90 said:**
> Make: Hewlett Packard
Model: Pavilion 522n
Hard Drive: 60GB
RAM: 1GB DDR SDRAM
Processor: 1.8Ghz Intel Celeron 
Operating System: Ubuntu 10.10 (maverick)

Currently the processor is running at 100% all the time. I first thought  this was due to the fact that I didn't have enough RAM because I was  running the bare minimum for the Maverick OS, so I upgraded it from  256mb to 1GB. This did not solve the problem, so as it is an old  computer, I thought perhaps just a new processor would fix this. Here is  all the information given using the lspci command in the Terminal.

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 Multimedia audio controller: Avance Logic Inc. ALS4000 Audio Chipset
02:0b.0 Communication controller: Agere Systems LT WinModem (rev 02)


I have also been told that I need to "activate" the Intel drivers and was given the following link.

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus#Manually_enabling_the_Intel_driver](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus#Manually_enabling_the_Intel_driver)

The only problem with this, is that I'm told I need to make a new file. I  am new to Ubuntu and do not know how to go about this, or where the  file would be located/created. This wiki does not give any information  on this aspect of the file's creation (or the location thereof). Any  help would be greatly appreciated, or any other ideas on what I can do  to make this computer not so agonizingly slow.


I don't know whats in your budget, but you could just buy a new computer. These days you can get one for around 200 dollars.

---

### Post by NohOne90 on 2011-10-06
> **collisionystm said:**
> I don't know whats in your budget, but you could just buy a new computer. These days you can get one for around 200 dollars.

I have another computer that works fine and is running Dual OS with Win7 and Ubuntu 11.04 (natty). The only reason I am trying to fix this computer is to get more experience with building, rebuilding, upgrading, etc...

---

### Post by diasf on 2011-10-06
get the motherboard model, visit the manufacturers website and check the processor compability list.

You can also try lubuntu or another lightweight version of linux

---

### Post by lykwydchykyn on 2011-10-06
> **NohOne90 said:**
> 
I have also been told that I need to "activate" the Intel drivers and was given the following link.

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus#Manually_enabling_the_Intel_driver](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus#Manually_enabling_the_Intel_driver)

The only problem with this, is that I'm told I need to make a new file. I  am new to Ubuntu and do not know how to go about this, or where the  file would be located/created. This wiki does not give any information  on this aspect of the file's creation (or the location thereof). Any  help would be greatly appreciated, or any other ideas on what I can do  to make this computer not so agonizingly slow.

The most direct way to do this is:
- open a terminal
- type ```
sudo nano /etc/X11/xorg.conf
```
- Assuming that file is empty, copy and paste in this:
```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

- Save the file by hitting ctrl-x and 'y'

- reboot

---

