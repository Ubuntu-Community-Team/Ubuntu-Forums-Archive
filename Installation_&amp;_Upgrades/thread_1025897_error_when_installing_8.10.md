---
title: "error when installing 8.10"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by Darling_Nikki1119 on 2008-12-30
Package: installation-reports

Boot method: CD
Image version: [http://lug.mtu.edu/ubuntu-releases/intrepid/ubuntu-8.10-desktop-amd64.iso](http://lug.mtu.edu/ubuntu-releases/intrepid/ubuntu-8.10-desktop-amd64.iso) 
Date: 12/16/08 8:30pm pacific time

Machine: Custom built MSI K9A2 Platinum AM2+/AM2 AMD 790FX ATX AMD Motherboard running vista 64 bit trying to do a dual boot
Processor: AMD Phenom 9950 2.6GHz Socket AM2+ 125W Quad-Core Black Edition Processor
Memory: OCZ Reaper HPC 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) Dual Channel 8gb
Partitions: 80gb partition

Output of lspci -nn and lspci -vnn:

Base System Installation Checklist:
[O] = OK, [E] = Error (please elaborate below), [ ] = didn't try it

Initial boot:           [E]
Detect network card:    [ ]
Configure network:      [ ]
Detect CD:              [ ]
Load installer modules: [ ]
Detect hard drives:     [ ]
Partition hard drives:  [ ]
Install base system:    [ ]
Clock/timezone setup:   [ ]
User/password setup:    [ ]
Install tasks:          [ ]
Install boot loader:    [ ]
Overall install:        [ ]

Comments/Problems:initial boot off the cd gave me this error… this kernel requires an x86-64 CPU but only detected an i686 CPU unable to boot please use a kernel appropriate for your CPU


but if you look above I do have a 64 bit cpu quad core? 

can someone please help me figure out what I am doing wrong?:confused:

---

### Post by Antone Alecto on 2008-12-30
Hi there,

If applicable, have you attempted to install Ubuntu Intrepid 8.10 (64-bit) in a Virtual Machine?  How about 32-bit Ubuntu?  Which VM software are you using and which release is it?  What were your results of attempting to install 64-bit vs. 32-bit in a VM?

Can you please provide some more specific details about your overall system configuration.  For example:

Video card make/model/interface (PCI, PCI Express, AGP, etc.)

Installed BIOS information such as type/brand, version/build / release date (if you have it).  Is AMD-V enabled in BIOS?

Network configuration/speed and network card make/model?

What kind of hard disk(s) are you using? Brand, model, capacity, speed, what type of interface does it (or do they) utilize?  How are they partitioned now?

How do you have your BIOS boot up sequence and settings set?

Is your CPU overclocked?  If so, how and by how much?  What is the stock setting?

Have you tried to install another flavor of 64-bit Linux (Mandriva, SUSE, CentOS, etc.) to compare if the same problem occurs with them, or only with Ubuntu?

When you go into Device Manager on Vista and expand the "Computer" item at the top, what does it show beneath it?

Any further details on your motherboard that you can provide might be helpful.  Same with your CPU(s).

I am sorry to "interrogate" you, I just want more information so maybe someone can further assist you and offer suggestions.  Good luck and welcome to the forums.

---

