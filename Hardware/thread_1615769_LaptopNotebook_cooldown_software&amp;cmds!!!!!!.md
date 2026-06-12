---
title: "Laptop/Notebook cooldown software&amp;cmds!!!!!!"
date: 2010-11-07
forum: Hardware
---

### Post by djhorry on 2010-11-07
Hey guys! So, I own 2 laptops and a desktop, the desktop runs Ubuntu like a charm, but my laptops overheat in a few minutes. Now I've made a video showing you how I fixed it! It should work for everyone!! Here's the video:

[http://www.youtube.com/watch?v=uKi1YHAq3wM](http://www.youtube.com/watch?v=uKi1YHAq3wM)

[HTML]<object width="640" height="385"><param name="movie" value="http://www.youtube.com/v/uKi1YHAq3wM?fs=1&amp;hl=ro_RO&amp;rel=0&amp;color1=0xe1600f&amp;color2=0xfebd01"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="http://www.youtube.com/v/uKi1YHAq3wM?fs=1&amp;hl=ro_RO&amp;rel=0&amp;color1=0xe1600f&amp;color2=0xfebd01" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" width="640" height="385"></embed></object>[/HTML]CODES USED:

In Terminal: **gksudo gedit /etc/default/grub**
In GRUB: 
**GRUB_CMDLINE_LINUX="" **
replace with:
**GRUB_CMDLINE_LINUX="acpi.power_nocheck=1"**
Save, update GRUB using:
**sudo update-grub**
REBOOT, then open the Terminal again and type:
**gksudo gedit /etc/default/grub**
And replace the 2nd to last line with:
**GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=\"Linux\""**
Save and update the GRUB again.

---

