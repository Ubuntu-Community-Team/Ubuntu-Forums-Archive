---
title: "Asus u30jc-a1"
date: 2010-04-23
forum: Hardware
---

### Post by nokbar on 2010-04-23
Hi,

I just bought an Asus u30jc-a1 laptop, and I want to install Ubuntu 64 bit on it alongside Windows 7.
Specs:
> System   
--------------------------------------------------------------------------------
 
  Manufacturer ASUSTeK Computer Inc.  
  Model U30Jc 
  Total amount of system memory 4.00 GB RAM 
  System type 64-bit operating system 
  Number of processor cores 2 
 
Processor
Intel(R) Core(TM) i3 CPU M 350 @ 2.27GHz


Storage   
--------------------------------------------------------------------------------
 
  Total size of hard disk(s) 283 GB 
  Disk partition (C:) 43 GB Free (75 GB Total) 
  Disk partition (D:) 209 GB Free (209 GB Total) 
  Media drive (E:) CD/DVD 
 
Graphics   (Nvidia Optimus with Nvidia Geforce 310M)
--------------------------------------------------------------------------------
 
  Display adapter type Intel(R) Graphics Media Accelerator HD 
  Total available graphics memory 1696 MB 
        Dedicated graphics memory 64 MB 
        Dedicated system memory 0 MB 
        Shared system memory 1632 MB 
  Display adapter driver version 8.16.11.8871 
  Primary monitor resolution 1366x768 
  DirectX version DirectX 10 
 
Network   
--------------------------------------------------------------------------------
 
  Network Adapter Atheros AR8131 PCI-E Gigabit Ethernet Controller 
  Network Adapter Atheros AR9285 Wireless Network Adapter 
 

However, when I boot off of the 64 bit Ubuntu 9.10 LiveCD, I can't see anything on the monitor after I choose either "try" or "install" from the initial menu.  I know that it is working because I can hear the Ubuntu start sound when I choose "try".  However, since I can't see anything on my laptop screen, I can't do much with it.  I haven't tried using a monitor, because I don't have one available.

Can someone please help?

---

### Post by stenlee on 2010-04-25
you should use 10.04 version. There is already support for Intel arrandale graphic. [http://www.ubuntu.com/getubuntu/releasenotes/1004overview](http://www.ubuntu.com/getubuntu/releasenotes/1004overview)

---

### Post by Nosferax on 2010-05-16
How about support for the nvidia card? 

I'm writing this from my own asus u30jc. I don't really understand how ubuntu is dealing with the dual card setup right now... is ubuntu able to configure/use the optimus switch? if it doesn't - how does the system even works? are both cards activated at the same time or is the intel one activated by default?

---

### Post by l_synapse_l on 2010-05-17
> **Nosferax said:**
> How about support for the nvidia card? 

I'm writing this from my own asus u30jc. I don't really understand how ubuntu is dealing with the dual card setup right now... is ubuntu able to configure/use the optimus switch? if it doesn't - how does the system even works? are both cards activated at the same time or is the intel one activated by default?

I have the same laptop. I will be trying to install Ubuntu 10 and will let you know how it goes. As for Optimus, what I've read online says that you should not try and install the NVidia drivers for now just use integrated graphics. The Intel is activated by default in Ubuntu from what I know.

I will be able to help you further only after I have tried installing Ubuntu myself.

---

### Post by l_synapse_l on 2010-05-23
> **l_synapse_l said:**
> I have the same laptop. I will be trying to install Ubuntu 10 and will let you know how it goes. As for Optimus, what I've read online says that you should not try and install the NVidia drivers for now just use integrated graphics. The Intel is activated by default in Ubuntu from what I know.

I will be able to help you further only after I have tried installing Ubuntu myself.

I am writing this from Ubuntu 10.04. The install went smooth and just as I had expected the integrated graphics are installed by default. 

Does anyone know how to enable the Nvidia discrete graphics on this laptop?

---

### Post by Nosferax on 2010-05-23
The latest linux kernel comes with support for this type of laotop. It is supposed to allow the switching of video cards but it requires a restart of the X server as X is not built for this type of graphics switching (it is unlikely that we will see hot video card switching before another year or two). 

I have tried the said kernel and have been unable to make it work with my u30jc. I think it's because the driver failed to detect my two video cards properly - thus not activating itself. 

As for the nvidia drivers, I installed the ones from the ubuntu repositories and they did screw up my installation beyond repair, so don't waste your time with those. There are a couple beta drivers on the nvidia website listed for the 310M video cards, I haven't tried these and wonder if it's worth trying because by default it's the intel video card which is activated. So if I'm right about this, installing -any- nvidia driver should screw your installation. But that's just a supposition. Has anyone else done some more tests and can share their experience?



Here are some links and resources - that covers pretty much all the information I found on the interwebs. There is also a guy from nvidia who posted that they do not intend to write linux drivers for the optimus enabled laptops anytime soon : 

Here is the blog of the developer : [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)
He built a how-to to patch the kernel and compile it manually : [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
There is also a launchpad for hybrid graphics support in linux, you might want to join it and post your specs : [https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)
Finally you should go check the corresponding bug and say it affects you as well so we might gain more impact : [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756)


Edit : Last thing, the one bug I found with 10.04/2.6.22 was that I could not switch X display using Ctrl-Atl-fX hotkeys or even the console command. That bug seems to be fixed on 2.6.24.


Edit 2 : I forgot the launchpad for asus u/ul owners : [https://launchpad.net/~asus-ul30](https://launchpad.net/~asus-ul30)

---

### Post by rosencrantz on 2010-07-23
I thought about getting the U30Jc, but after reviewing all the Nvidia haggle, I decided to wait.
From what I gathered from the linux-hybrid-graphics.blogspot.com page and this surprisingly informative [Nvidia whitepaper]("http://www.nvidia.com/object/LO_optimus_whitepapers.html"), there are two flavours of hybrid graphics: ATI/Hybrid SLI nVidia switchable graphics and the Nvidia Optimus technology, which has been on the market since this spring. While in the conventional setup you have two separate chips switched manually by hardware multiplexers, cards using Optimus use the integrated chip as a display controller all the time and use the discrete chip for rendering duties if needed.
To get this to work apparently would need a major Xorg makeover, so right now the workarounds and kernel patches are rather targeted at the switchable system and there is no timeline on Optimus support yet.
Also keep in mind that Nvidia has both kinds of hybrid setups with the same chip model - the Geforce 310M is also available in a Hybrid SLI configuration (or a single card setup) and you can't tell from the chip's name alone whether it's going to work or not. Well, the U30JC definitely has Optimus and accordingly it's Intel integrated only for Linux users for now...

---

