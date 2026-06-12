---
title: "Screen problems when running Ubuntu on my laptop"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by Gummi on 2007-02-10
As the title says I'm having a problem with the screen on my laptop. The problem is that it turns completely black when I start up Ubuntu, Just like if it turned it self down. 
Now I am fairly new to all this, I've used Windows all my life, nothing else. So I have no idea whatsoever of what I'm doing. 

If it helps my laptop is an acer aspire 1690, and my video card is ATI radeon X7600 I think.

---

### Post by rucadulu on 2007-02-10
After your bois loads you get a 2 second pause at the grub boot loader. Press the esc key and boot into recovery mode.
Once in recover mode type   dpkg-reconfigure xserver-xorg 

This will allow you to reset the xorg.conf file. Do not autoselect your grapchics card use vesa option everything else you can auto select. 

Once you have reconfigured the xorg.conf file reboot and hopefully all will work well. 

If this works for you, you will want to download the latest drivers for your graphics card and then install them and reconfigure the xserver to point to the new driver.

If you have not all ready done so I suggest getting a book like "Ubuntu Unleashed" or "Beginning Ubuntu Linux" I have both and they have helped me out of many problems. 

Hope this all helps. Russell

---

