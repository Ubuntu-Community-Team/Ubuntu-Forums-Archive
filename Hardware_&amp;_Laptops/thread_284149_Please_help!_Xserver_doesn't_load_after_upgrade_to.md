---
title: "Please help! Xserver doesn't load after upgrade to 6.10 RC"
date: 2006-10-25
forum: Hardware &amp; Laptops
---

### Post by rpalyvoda on 2006-10-25
Hi,

I've upgarded yesterday from 6.06 to 6.10 RC. Everything was fine, but after rebbot, my Xserver doesn't load.

I get the following message

> Module ABI major version (0) doesn't match the server's version (1) 
Failed to load module "vesa" (module requirement mismatch 0) 

Fatal server error: no screens found

I've already tried

> sudo dpkg-reconfigure xserver-xorg

And I tried different video drivers (nvidia, nv, vesa), but the problem clearly isnt't there!

PLEASE HELP!!!!!!!!!!!!!!!!!!!!

P.S. I use a 3y.o. Toshiba Satelite laptop with Nvidia GeForce 4 420 card.

---

### Post by ebutton on 2006-10-25
Assuming that you have a command line, have you looked at (use more or gedit) your /boot/grub/menu.lst file?  If you haven't altered the "timeout" value in this file, at boot time you have 3 seconds to open the grub menu and choose recovery mode or a previous kernel.

Sorry, I'm too new at linux to help with the actual error that you're getting.

Warm Regards,
EdB

---

### Post by rpalyvoda on 2006-10-25
Hi,

thanks for you answer, but it's not a problem: my Ubuntu starts fine, I have my command line, but Xserver doesn't load.

From my little experience with Linux, it's possible that either the new version of xserver-xorg doesn't work with the combination my harware + new kernel, but I've got no clue of how to resolve this problem

---

