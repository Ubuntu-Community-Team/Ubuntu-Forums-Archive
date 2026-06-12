---
title: "Frozen Mouse Pointer  on v5.10"
date: 2006-09-18
forum: Hardware &amp; Laptops
---

### Post by Mat10 on 2006-09-18
I have a serial mouse running on ttyS0 and it registers fine and useable on a debian sarge, however after installing Ubuntu 5.10 it is now freezing after the boot at desktop.  I also can't seem to change anything at the console level since it just keeps refusing access to any of the tools or configs.  I try sudo su and it goes to the root prompt but still no love.  All I need to do is change the configuration files for X11 , where are some useable instructions for problems like this.  I checked the FAQs and nothing there for a mouse problem and command prompt instruction.

Thanks 
TRM

---

### Post by zxee on 2006-09-19
Perhaps more of your hardware specs would be helpful too, but from the terminal type > sudo dpkg-reconfigure xserver-xorg
<Enter> That should allow you to select a serial mouse-along with many other xserver related configurations.

---

