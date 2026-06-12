---
title: "New Wireless Card"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by brandoncolorado on 2007-12-21
Hi everyone,

I have been waiting and hoping Ubuntu would work with my laptop, but it just seems it won't happen.  Right now (after almost 1.5 years of trying) the wireless on this laptop still has a major issue.  Next laptop will for sure be Ubuntu ready when I buy it!  

I am using a Realtek 8185 Wireless card on this puppy, and it has a known serious bug (serious for me at least).

[https://bugs.launchpad.net/ubuntu/+bug/152527](https://bugs.launchpad.net/ubuntu/+bug/152527)

Other than the typical PCMCIA and USB wireless card solutions, would it be possible for me to swap the actual card on the motherboard by removing the keyboard?

---

### Post by alan34 on 2007-12-21
You might like to try this ....................

My card is a Peak pci wireless card with rtl8185 chipset I also had the kernel panic when I tried to connect to my wireless router, really annoyed as the card worked with Edgy and Fiesty.

The solution is to use the Window drivers and ndiswrapper and blacklist the linux r818x driver.

Get the Window files - should have something,inf and something.sys in the same directory. I got net8185.inf and rtl8185.sys from the cd that came with my card.

In System - Administration - Software Sources make sure there is a tick against the Ubuntu 7.10 cd. Load the cd
(you may have to untick all the other software sources just note which ones are ticked now!!)

In System - Administration - Synaptic Package Manager search for ndiswrapper and install.

In a terminal change directory to where the Window files are then (in my case)
(Go to Applications - Acessories - Terminal)

then copy and paste

sudo ndiswrapper -i net8185.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo ndiswrapper -l
------------You should see something like this

alan@alan-desktop:~$ sudo ndiswrapper -l
[sudo] password for alan:
net8185 : driver installed
device (10EC:8185) present (alternate driver: r8180)

Now to load the driver when you boot

sudo gedit /etc/modules
----------You should see something like this add ndiswrapper at the end of the file

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper


Now we blacklist the linux driver

sudo gedit /etc/modprobe.d/blacklist
---------------At the end of the file add

# wireless network card driver
blacklist r8180

Reboot and you should be okay well at least I was. Only re-installed three times to get it to work

Good luck

---

