---
title: "X won't start on a new Toshiba Satellite L25"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by Psycs on 2005-12-01
So, I'm doing a fresh install of Ubuntu Breezy B. on my grandpa's new Toshiba Satellite L25.  It came preloaded with WinXp, but it is absolutely necessary to have the OS in Spanish and I thought of Ubuntu.

I formatted the laptop and went through the entire installation procedure.  At the very end, I got the message (in Spanish) that X server won't start.  

Could you guys please help me troubleshoot?

The specs for the laptop are as follows:

- Celeron 1.5Ghz
- 256 Ram
- ATI chipset 
- ATI Xpress 200M w/ 32 Ram
- 60GB 5400RPM Fujitsu HD

---

### Post by invalid on 2005-12-01
If you can paste the exact error here, as well as you /etc/X11/xorg.conf file, we could inspect it.

Just for now, you can try```
sudo dpkg-reconfigure xserver-xorg
```which works a lot of the time for most errors.

Cb

---

### Post by Psycs on 2005-12-01
[QUOTE=invalid]If you can paste the exact error here, as well as you /etc/X11/xorg.conf file, we could inspect it.

Just for now, you can try```
sudo dpkg-reconfigure xserver-xorg
```which works a lot of the time for most errors.

Cb[/QUOTE]

I would have pasted the error, but its very impractical since I'm not on the laptop right now typing this. ;) 

Thanks for the tip on reconfiguring x server, I'll post as soon as I'm done... :p

---

### Post by Psycs on 2005-12-01
"sudo dpkg-reconfigure xserver-xorg" didn't work.  Most likely my fault.

X's error says something like this:

> 
(...)
Skipping 
"/usr/X11R6/lib/modules/extensiones/libGlcore.a:m_debug_clip_o": No
symbols found
Skipping 
"/usr/X11R6/lib/modules/extensiones/libGlcore.a:m_debug_norm_o": No
symbols found
Skipping 
"/usr/X11R6/lib/modules/extensiones/libGlcore.a:m_debug_xform_o": No
symbols found
(..)
Unable to find valid framebuffer device
RADEON (0): Failed to open framebuffer device, consult warnings and/or erros above for possible reasons
(...)
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o" No symbols found
RADEON (0): (dri) DRIScreenInit failed. Disabling DRI


Hope that helps...

I have another question.  I've been trying to figure out how to display the contents of my xorg.cong without the graphical display.  How can I do it?

---

### Post by kyle.quamme on 2005-12-01
I have the same Laptop and had display issues. Try changing the driver in xorg.conf from "ati" to "vesa". That fixed mine.

As far as editing the file, I would copy it onto a flash drive, if you have one, modify it and then copy it back over. If you don't have a flash drive you should be able to "cd" to the X11 directory and run "vim xorg.conf" but I don't know how to use vim.

---

### Post by Psycs on 2005-12-01
Thanks, kyle, although it didn't work.

---

