---
title: "GPU broke ubuntu!"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by Echo35 on 2007-07-14
So I had a 7950 GTX2 running on my PC. I dual boot Windows/Linux and it was working fine. I had the nVidia driver and had set up xorg to use my 1440x900 monitor and it was all working fine. I just recently upgraded to an 8800 GTX and it broke my xorg! It wont let me boot into Ubuntu's GUI. It gives me an xorg error and puts me down into the terminal. Is there any way I can replace the xorg and fix the problem without reformatting Ubuntu? I seem to remember having to do something similar before, and it worked, I just cant remember how I did it...

---

### Post by w4ett on 2007-07-14
Other folks have had problems with that card.....

[http://ubuntuforums.org/showthread.php?t=497265&highlight=8800+gtx](http://ubuntuforums.org/showthread.php?t=497265&highlight=8800+gtx)

I would:

sudo dpkg-reconfigure xserver-xorg

use the versa driver,  restart x, then install ENVY and let it do the new driver install.

---

### Post by Echo35 on 2007-07-14
No dice. It says its installed, but I have no 3D support. I also have no GLX support, nor can I select any resolution higher than 1024x768, even though there are entires for higher resolutions in my xorg.conf file.

EDIT: Scratch that. I tried ENVY again, but I hit manual nVidia install, and it worked this time!

---

### Post by w4ett on 2007-07-14
> **Echo35 said:**
> No dice. It says its installed, but I have no 3D support. I also have no GLX support, nor can I select any resolution higher than 1024x768, even though there are entires for higher resolutions in my xorg.conf file.

EDIT: Scratch that. I tried ENVY again, but I hit manual nVidia install, and it worked this time!

Thought you'd get it using Envy...Works for me most every time.

Good Luck!

---

### Post by hessiess on 2007-07-14
check for compatabilaty before buying any hardwere!

---

### Post by w4ett on 2007-07-14
> **hessiess said:**
> check for compatabilaty before buying any hardwere!

Just a lesson learned I guess....what he needed to do was revert to the vesa or vga driver first, then install the new gfx card, then reinstall the Nvidia driver...it patches the kernel differently for each GPU series supported.

---

### Post by Echo35 on 2007-07-15
Yeah, I figured since Linux takes almost everything, and it was nVidia, it wouldn't be too much of an issue. Besides, Ubuntu isn't my only OS, so it wouldn't have been too much of a problem anyway, but thanks for all the help none the less.

---

### Post by w4ett on 2007-07-15
Just remember, Kernel updates also usually require a driver reinstall too.  ENVY is great for that also.

---

### Post by heldal on 2007-07-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The 8800gtx and gts gpus are supported by the current driver. I rencetly upgraded a computer from a 6800 to a 8800gts and had the same problem which turned out to be a file missing in ubuntu's packaging (nvidia-glx-new) of nvidia's drivers. The easy fix is to manually extract the missing file from the original driver-package from nvidia. 

Search the forum for "libwfb" for further discussions and workarounds.

---

### Post by misfitpierce on 2007-07-16
you can delete your corg maybe to allow 3d boot up...

sudo rm -r /etc/X11/xorg.conf

---

