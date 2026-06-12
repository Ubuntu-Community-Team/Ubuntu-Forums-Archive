---
title: "Configuring Video for a Toshiba Portege 7010CT"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by lkvee on 2006-06-08
I have a Toshiba Portege 7010CT whose native LCD goes up to 800x600x24 but can go to 1024x768x?? on an external monitor.  Its video chipset is NeoMagic.

After installing xubuntu on a docking station I only get 640x480 resolution and worse, pixel stuttering is active.  The result's very ugly.  The only other alternative setting (at least with xubuntu) was 320x240x8 (ugh).  The 800x600 resolution's not offered, and that gives me the impression xubuntu didn't exactly recognize my video card.

I'd like to resolve the problem by adding boot/kernel parameters, but I've tried screen=800x600 depth=24 and fb800x600 (I tried it anyway even though I found 'em on the KNOPPIX cheat code section).   I've aso tried to change xmodule to fbdev and vesa but X didn't even start.

I also discovered the /etc/X11/xorg.conf but I'm very light with regards to modifying the file accordingly.  I would actually rather add boot/kernel parameters in the /boot/grub/menu.lst file because I can use these settings and parameters when I boot up live distributions like SLAX (Slackware) and BitDefender Live! (KNOPPIX).  

I'd still be grateful for reading thoughts on modifying xorg.conf

I'm really hoping for a set of boot/kernel parameters that would work with live distributions.

What else I can tweak?

---

### Post by ncs on 2006-08-19
The solution posted by da2na on following thread for the 7000CT also works for the 7010CT.  

[http://ubuntuforums.org/showthread.php?t=135197](http://ubuntuforums.org/showthread.php?t=135197)

It won't solve your question about boot parameters for live CDs but should give you 800x600 option on you current install

---

### Post by lkvee on 2006-08-19
barely h-fi's recommendation to use the following command:

sudo dpkg-reconfigure xserver-xorg

also just worked for me.   I'm not sure if this solution will work for a liveCD.   My hope is yes.   I have yet to try it.

My eyes don't hurt from looking at the LCD anymore!

---

