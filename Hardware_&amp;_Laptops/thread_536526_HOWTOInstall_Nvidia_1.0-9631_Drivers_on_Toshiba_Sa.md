---
title: "HOWTO:Install Nvidia 1.0-9631 Drivers on Toshiba Satellite Pro 6100(GeForce 4 420 GO)"
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by wkimberly on 2007-08-27
This short HOWTO takes you through the links to make Toshiba Satellite Pro 6100 with the graphics card Nvidia GeForce 4 420 GO work at 1400x1050 resolution on Feisty Fawn (might work on others).

First you need to **install the drivers**. There are many ways, one is on is the Add/Remove... Applications menu. I used METHOD 1 in [[COLOR="Sienna"]this guide[/COLOR] ]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html")([[COLOR="Sienna"]http://www.albertomilone.com/latest_nvidia_udsf_feisty.html[/COLOR]]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html")) ignoring what is says about the GeForece 4 420 GO (point 7 of the PROBLEMS SECTION) The guide was found in a post by **tseliot **in the post:
[[COLOR="Sienna"]http://ubuntuforums.org/showthread.php?t=432056[/COLOR]]("http://ubuntuforums.org/showthread.php?t=432056")

If you restart your X server (Ctrl+Alt+BkSp) you sould get a black screen or **blank screen**. This is because the display (screen) is routed by default to the analog output. To fix this you have to add:

Option         "UseDisplayDevice" "DFP-0"
This solution is found post [[COLOR="Sienna"]http://ubuntuforums.org/showthread.php?t=417188[/COLOR]]("http://ubuntuforums.org/showthread.php?t=417188")
After this it should be possible to start X and see the nVidia Logo, But the resolution es 800x600. On the last post mention they talk about a .BIN file (it refers to the monitor EDID file) but the file is missing and it is for another monitor.

To fix this you need to create your own EDID.bin file, instructions are  here: [[COLOR="Sienna"]http://www.edwiget.name/content/view/144/26/[/COLOR]]("http://www.edwiget.name/content/view/144/26/")
You have to get the original EDID.bin file and open it in a HEX editor (as the guide says) and modify two values in the file. This values defer from what the guides says
Change Offset 56 ( HEX:38 ) to 78 (NOT C9 as the guide says)
Change Offset 58 ( HEX:3A ) to 51 (NOT 41 as the guide says)

This translates into a resolution of 0x578 (hexadecimal number) witch means 1400 in decimal. You can see more about EDID in wikipedia:
[[COLOR="Sienna"]http://en.wikipedia.org/wiki/EDID#EDID_1.1_data_format[/COLOR]]("http://en.wikipedia.org/wiki/EDID#EDID_1.1_data_format")

In total the lines added to the /etc/X11/xorg.conf file where in Section "Screen" where:
    Option         "UseDisplayDevice" "DFP-0" 
    Option "AddARGBGLXVisuals" "true" 
    Option "CustomEDID" "DFP-0:/usr/lib/edid_new.bin"

Hope this helps someone else, I'm sure it will help me if I re-install the OS. Thanks for all the post in the forums, with out them and with out you I would still be trying to fix the problem.

---

### Post by deepwave on 2007-09-18
Thanks for the HOWTO guide!  Saved my day when I installed Feisty Fawn on a Satellite 2410.  Just reiterated what you said: [http://opensourcegamer.blogspot.com/2007/09/penguin-and-rusty-wrench.html]("http://opensourcegamer.blogspot.com/2007/09/penguin-and-rusty-wrench.html")

---

### Post by wkimberly on 2007-09-19
Good! I'm glad it did help someone else. And thanks for the step by step instructions, much clearer.

---

