---
title: "XSERVER crashes (I think)"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by finneyabraham on 2009-10-10
[FONT="Arial Narrow"][FONT="Book Antiqua"][SIZE="2"]I was running 32 bit 9.04 on the AMD/ATI system. I wanted to change the kernel to 32 bit PAE kernel so that all 8GB of the memory on my system can be utilized. 
To prepare for the kernel change, I de-activated the ATI Proprietary driver through System->Administration->Hardware Drivers.
Next, through synaptic I installed the 32 bit PAE kernel (the server kernel) and when I booted the system, the GRUB came on and then the ubuntu load screen came on. Nothing happens beyond that. The screen is blank or frozen with a line of snow.
Since then, I deleted the server kernel through command line accessed through the recovery mode. I tried rebooting with the original kernel of 9.04 regular 32 bit. Same outcome.

Please help because I have a lot of my files for school on it.[/SIZE][/FONT][/FONT]

---

### Post by finneyabraham on 2009-10-10
I solved the problem.

I uninstalled throught the command line the following:
sudo apt-get remove xserver-xorg

Then reinnstalled through command line
sudo apt-get install xserver-xorg

The desktop came up and then activated the proprietary driver .

I am so relieved.

---

