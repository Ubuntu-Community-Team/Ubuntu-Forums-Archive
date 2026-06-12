---
title: "Acer Aspire one Screen Size"
date: 2009-05-17
forum: Hardware
---

### Post by beakersoft on 2009-05-17
I've installed 8.04 on my Acer Aspire one, and am very happy with it apart from one thing. The output on the monitor is disappearing off the bottom of the bottom, its seems to be missing 20pxls or so off the bottom

Its not a huge problem but its a pain, i cant re-size some windows (like an rdp window) and i have turned off the bar at the bottom (sorry i'm fairly new to Linux i'm not sure what its called)

I've tried playing about with the screen res, but as i said i'm new to Linux so i'm not sure where to start looking

---

### Post by jlh68 on 2009-05-17
I recommend updating to 8.10 then update again to 9.04 Netbook Remix, or just use 9.04 and reformat your drive.  You will find that the Jaunty Jackalope 9.04 Netbook Remix will work fine on your Acer ONE.  You will have only one thing to fix after the install and that is to get the media card readers to work.  That is not hard all that is needed is to add pciehp.pciehp_force=1 to the grub menu.

> pciehp module still missing. Left-hand SD and all USB ports are hot-pluggable, RH SD works if card is present on boot. As workaround add "pciehp.pciehp_force=1" to defoptions in /boot/grub/menu.lst   from [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) web page.

Both 8.10 and 9.04 will recognize the correct screen resolution.  I am using 9.04 NR on my Acer ONE and I have full operability.  UNR is great for the ONE.

Here is the HOW-TO to addign the media card readers:

> OPTION 1:  
Open the Terminal via Accessories>Terminal and then type (or copy-n-paste) the line "sudo gedit /boot/grub/menu.lst".  It will likely prompt you for a password.  After which, the menu.lst file will open -- if you drop all the way to the end of the file, you should see the boot options available (the first line should start with something like "title          Ubuntu 9.04, kernel 2.6.28-11-generic"). 

You will want to append that code right after the kernel line, which
ends with "ro quiet splash" so that it becomes "ro quiet splash
pciehp.pciehp_force=1".  Then save and reboot your Acer.


OPTION 2: 
Same as OPTION 1, but instead of going through the Terminal, you can just press ALT+F2 to bring up the Run window and type in "gksu gedit /boot/grub/menu.lst" to open the file automatically.  Or just put in "gksu gedit" if you want to open the Text Editor with Root access only and then navigate to /boot/grub/menu.lst yourself using File>Open.

Try it.  Good Luck

---

### Post by beakersoft on 2009-05-17
Thanks for the info, ill give it a try

---

