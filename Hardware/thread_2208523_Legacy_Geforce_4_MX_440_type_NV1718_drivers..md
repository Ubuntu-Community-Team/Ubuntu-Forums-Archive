---
title: "Legacy Geforce 4 MX 440 type NV17/18 drivers."
date: 2014-02-28
forum: Hardware
---

### Post by thenh813 on 2014-02-28
***EDIT***
IMPORTANT INFO FOR ANYONE READING THIS THREAD!
This GPU is no longer supported as of ubuntu 12.04.1 due to drivers not being updated for newer versions of X and the Linux Kernel. You will have to use a older kernel and version of X.org or use a older version of Ubuntu. The other option is to upgrade your GPU.



Ubuntu 13.04 based distro wattOS 7.5

I will try not to seem too mad about this and will not swear, although I feel like it.
I have spent all of today since 10:30AM and about 6 hours last night trying to get unexistant drivers to work (it is 4:12PM now). Nvidia's drivers seem to hate me, they throw up exceptions and errors, unable to find the kernel headers or unable to compile kernel correctly. I spent half this time tracking down the dependancies and putting the .DEB files on my flash drive so when I had to reimage the Ubuntu partition again, I wouldnt have to redownload the again. I keep getting errors and broken installations left and right, I am beginning to feel I should give and and just play games on Windows XP.

First question, How can I install the add additional drivers thing, It appears to go correctly and reports success installing jockey-gtk, but when I try to run it, it says ask an adaministrator to install the jockey-gtk package for you. This plain sucks, if it worked I wouldnt be trying to manually install drivers.

Second question, why does Nvidia's installer NOT FIND the kernel headers that are in the EXACT PLACE THEY ARE SUPPOSED TO BE. I tired using th parameter to tell it where to look but it claims "unexistant" and basically gives up, dumping a useless log with no errors in it. I understand that Nvidia's spport for Linux kindof sucks, but this is simply horrid.

Third question, what happened to nvidia-legacy-dkms in synaptic, it was there for me a year ago. I even tried the debian repositories, but theose drivers refuse to load or are missing OpenGL for some reason even though I install it. The internet revals nobodsy having the same problem, or it is for a older version of Ubuntu.

I know this version of Ubuntu is dieing and will be soon unsupported, but can I at least get some help? This is just stupid, and I absolutely have no idea what to do now as my usual hacks and methods have failed me. I just want to play some games (mostly Minecraft) which worked perfectly on Zorin OS but Zorin itself runs kindof hard on my PC so I downloaded wattOS which is simply amazing. It does everything I need, even installing Java only took one command (I prefer apt-get to software center). This would be the perfect OS if someone, anyone could help me. I know this card gets 30-45 FPS in Minecraft on windows, and usually at least 70FPS on Linux. I still cant believe that wattOS boots in a little over 10 seconds on 2001 hardware and only uses 142MB of ram idleing. I might run light Compiz effects if I can the the drivers working, which I installed and preconfigured, but does not work good at all with the Nouveau drivers so I disabled it.

I know my way around Linux, and have been learning about it and heavily using it since 2010-2011.

This is kindof urgent, but not serious.

Please help,
                     -TheNH813

---

### Post by Yellow Pasque on 2014-02-28
IIRC, nvidia's 96.xx legacy branch does not support Ubuntu versions beyond 12.04.1 (because it would need updated for newer X and kernel versions). Attempting to use it on newer releases is like pissing against the winds of a hurricane. You should hardly be surprised or angry, since your GPU is ancient...

---

### Post by thenh813 on 2014-02-28
Thank you for a decent explanation of why it dosent work. I had no idea.  I thought it was still supported, I saw no mentoin that it did not work  on newer kernels or versions of X on the download page on geforce.com.  Thanks for the help, I will upgrade the GPU. I edited the first post to tell anyone that may read this in the future it is unsupported in newer versions of Ubuntu past 12.04.1.

---

### Post by mörgæs on 2014-03-01
Upgrading the GPU is a good solution.

13.04 is already out of support. If you want to experiment I recommend 13.10 (and Lubuntu in stead of Ubuntu).

There are always open-source drivers available though Nvidia understandably is letting go of closed-source drivers for a 12 years old card.

---

### Post by thenh813 on 2014-03-01
> 
13.04 is already out of support.

I know,  right? Only thing, wattOS hasnt made V8 a stable version yet, I think  its 14.04. Meh, for now, I downgraded to wattOS R6 which is 12.04.1  based. Suprisingly, it boots WAY faster and sits idling on 130MB of RAM.  I am shocked to say I have absolutely no idea why, it has the EXACT  SAME version of LXDE as the new wattOS, and the EXACT SAME versions of  most programs (disregarding X and the Kernel). Also, I cant believe the  MX 400 is pushing 120FPS in Cube2 on near max settings with shaders  disabled. I am getting a PCI (not PCIE, my MB doesnt have that) card,  and will keep both GPUs, I'l put my unused 15" Dell CRT, which sadly  sits lifeless on my desk due to the lack of DVI cables for the LCD, on  the old GPU and let it use generic drivers. It is a really good dispaly,  supporting up to 1152x864, and looks as good as a flat screen. I will  compile the drivers for the new GPU, which is supported by wattOS R6  (basically 12.04.1 Lubuntu) and that will be the end of it. I will be  getting a ZOTAC NVIDIA GeforceGT 610 810MHz PCI video card. I too understand why they dumped the old drivers, its not worth it. If someone cant spend $50 for something many times better, they should probabally not upgrade the OS, as their other hardware will struggle too. Hmmm... $20 for a used P4 3.4GHZ dosent look too bad, along with the GPU, itd be like a world of a difference. I could run this for five more years easily, I dont do heavy gaming, just Open Source games Like ACR, Cube2, etc and the usual Minecrafting.

PS: wattOS is going Debian  as of R8, for many reasons. wattOS in general is nearly as light as Puppy Linux, and a good choice for aging computers. A Win98 machine can run as good as something a few years newer.

---

### Post by martaz2 on 2014-06-30
Hi, 

I have the nvidia Geforce4 MX 440 (N17) graphic card on one of my PCs.
I installed Linux Mint 17 xfce, which means Linux kernel 3.13 and an Ubuntu 14.04 package base.
I've read this thread with despair, even trying to upgrade my GPU...
But then I've given a last chance to the "Nouveau" driver and modified the /etc/default/grub file, with GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nouveau.noaccel=1".
And now it's ok. I feel it works as well as with the proprietary Nvidia drivers in Linux Mint 13. 
So my old Geforce4 MX 440 will work some more years.

---

### Post by quadrplax on 2014-06-30
I had the same issue with a GeForce4 MX 420, and I got like 4 error messages, but for my purpose the generic VGA driver worked for my needs (I removed Noveau, it was glitchy). That probably wouldn't work for you though. I'm turning the computer into a HTPC so the limited resolutions (max: 1024x768) is no problem for me.

---

