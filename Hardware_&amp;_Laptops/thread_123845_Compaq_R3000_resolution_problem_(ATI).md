---
title: "Compaq R3000 resolution problem (ATI)"
date: 2006-01-31
forum: Hardware &amp; Laptops
---

### Post by sargeras on 2006-01-31
Hi everyone,

I have a compaq r3000 model laptop with the onboard ATI mobile 9000 IGP graphics.  Installing breezy was easy and the resolution was correct at this point (1280x800).  After installing fglrx for the onboard ATI graphics card (using the ATI installer), the resolution is stuck at 1024x768.  I have tried putting only 1280x800 in the xorg.conf file, however, the resolution remains unchanged.  Is breezy reading the resolution from another location as well? I have attached my xorg.conf file that was created by the ATI installer. Any help/suggestions would be appreciated.


Solved
Had to reinstall the ATI drivers after removing all the 'restricted packages'.:rolleyes:

---

### Post by ScreemingBlue on 2006-01-31
Hi,

It seems that you have two "Device" sections. One using a 'vga' driver and the other using the 'fglrx' driver. It's probably worth hashing out the 'vga' device section and hitting CTRL-ALT-Backspace. I sometimes find a re-boot does the trick also. 
Just make sure you know how to change it back if X doesn't start. You can use > sudo nano -w /etc/X11/xorg.conf to edit the xorg file and CTRL-X to then save it. Then enter > startx to start the display.

Hope this helps.

---

