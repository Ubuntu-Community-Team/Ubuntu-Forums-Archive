---
title: "HP L2000 SE and Ubuntu"
date: 2005-12-23
forum: Hardware &amp; Laptops
---

### Post by rainkinz on 2005-12-23
Has anyone had any experience with installing Ubuntu on this laptop and if so any advice? 

I would also like to install dual boot.

Thanks

---

### Post by rainkinz on 2005-12-24
Ok, so it was very easy. (I'm currently running Ubuntun on my L2000 SE as I write this). Only slightly tricky part was using vga=771 no_timer_check for boot options and setting:

        option          "noaccel"

to the xorg.conf file.

I also haven't got the wireless card going yet, but will leave that for the morning.

---

### Post by wolfjb on 2006-01-05
To get the ethernet (eth0) to work you need the 8139too for the RealTek RTL-8139/8139C/8139C+ (rev 10) chipset. For the wireless, you'll need to install ndiswrapper and get the WinXP driver.

For the video card, get the driver directly from ATI and install it. If you get the .run version (as oppossed to the .rpm version), you'll also need to have the kernel source installed. I tried with just the kernel headers and that didn't work for me. 

HTH
--WolfJB

---

### Post by mstrstvns on 2006-05-15
What is the method for installing ndiswrapper and the WinXP driver?

---

### Post by alek01 on 2006-12-28
> **mstrstvns said:**
> What is the method for installing ndiswrapper and the WinXP driver?
for the ndiswrapper ( as other stuff, like fonts and software, the easiest by for is to use "automatik2". The scripts take care of everything. Worked fine for me and my HP L2000 (LiveStrong). Except regarding the ATI Driver which I have downloaded and installed but has a Pb with the fglr command. Good luck.

---

