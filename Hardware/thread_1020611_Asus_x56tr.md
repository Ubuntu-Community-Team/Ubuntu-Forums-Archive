---
title: "Asus x56tr"
date: 2008-12-24
forum: Hardware
---

### Post by Egarretsen on 2008-12-24
Hi everyone,

I've bought an ASUS X56T (X56TR) last week and i had some serious problems installing Ubuntu and dualbooting Vista.

The specs:
AMD TURION X2 64
ATI 3200 & ATI HD3470
Atheros Wireless AR 928X

Some problems i eventually solved myself. I will post solutions for others.

The main problem now is that i cannot install Intrepid, due to the new xorg 7.4 presumably. 

Installing Ubuntu only works with the extra boot options acpi=off or MAXCPUS=1. Ubuntu Intrepid installed, but i couldn't get any GUI. I tried ati, radeon, vesa, radeonhd. I tried installing the official ati-drivers. Nothing worked, then after hours of mindbreaking i installed Hardy Heron, IT worked! Installed the restricted drivers and the screen looks nice. No sound though and no wireless.

But i couldn't dual boot vista from grub. When i booted vista a giant red error showed up and a error about recover.dat . This is solved by altering the menu.list line for Vista by changing hda(0,0) to hda(0,1). Apperantly grub or ubuntu doesn't install right and does not see the hidden rescue / recovery partition on my notebook. Now i can Dualboot!

My question:
How can i get Intrepid Ibex to work?

or if it's not possible:
1. how can i get Hardy to recognize my Atheros WLan, Intrepid did when using the live-cd. 
2. Will Jaunty be compatible with my notebook?
3. How to send a bug to the developers of ubuntu / xorg. i don't now how to do this.

question 1 is answered:
this is how to get wifi in 8.04 using atheros AR928:

[http://vaioubuntu.wordpress.com/tag/ath9k/](http://vaioubuntu.wordpress.com/tag/ath9k/)

Thanks in advance.

---

