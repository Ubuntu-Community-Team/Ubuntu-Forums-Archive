---
title: "ATI and Broadcom Problems. Dell i9400"
date: 2008-06-05
forum: Hardware
---

### Post by myslin on 2008-06-05
I'm new to linux and I started on debian until my friend told me that I may possibly like Ubuntu more. I decided to give Ubuntu a try but I've run into some problems.

**ATI X1400:** I've tried both the restricted drivers and the proprietary ones. No avail. When I try to use the restricted drivers; after a reboot ubuntu will go into "safe graphics mode". I've tried to manually change the driver to fglrx there with no luck. 
I've also tried to go into console and do a aticonfig --initial -f and then restart gdm but the problem I run into there is that you cannot even tell whats going on. You can see the colors and outlines of windows but everything is jumbled. The proprietary drivers also did not work. I've tried the automatic installation and I've also tried the dpkg Ubuntu/8.04 installation. They always revert back to mesa. I'm not going to bother posting my xorg since you would probably know what it looks like (this seems like a common problem).

It seems weird. Ubuntu is based off of Debian yet I was able to get DRI and fglrx working on Debian in a flash.

**Broadcom: **I'm sure everyone hates this damn card. I had the unfortunate luck of getting the most problematic one, since I decided to skimp out on the 30$ when ordering the laptop from dell. It is the BCM94311. I've never gotten it to work in Debian no matter how hard I've tried. This was a big reason for me to try Ubuntu. However I did get fairly far in the Ubuntu configuration of this card.

I'm using the new Kernel 2.6.25.4 which means that I now need to use the b43 wireless drivers, I've got those and the necessary firmware however the problem that I'm running into is even though I can scan for networks and see the ones around me. I still cannot connect to any of them. I've tried removing all encryption from my Wireless router and trying to connect it manually but it just gets stuck at "Waiting or DHCPDISCOVER".

I'm stuck here guys and any help you could give me would be highly appreciated.

I hope that it's not this new kernel giving me problems.

---

### Post by myslin on 2008-06-05
also, I tried ndiswrapper in the old kernel. However I'd much rather use ndiswrapper as a last resort.

---

### Post by myslin on 2008-06-06
bump

---

### Post by mtbsoft on 2008-06-07
I have an Inspiron 9400 laptop.  I loaded Hardy as a fresh install, ran all the updates, enabled the restricted ATI driver and haven't done anything out of the ordinary - all is working fine, the only issue I've found so far is the WIFi light doesn't work but a recent update has now made the keyboard on/off shortcut work (was always on before).

---

