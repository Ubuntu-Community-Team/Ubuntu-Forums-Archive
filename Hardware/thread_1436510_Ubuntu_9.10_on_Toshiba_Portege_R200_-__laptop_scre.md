---
title: "Ubuntu 9.10 on Toshiba Portege R200 -  laptop screen not working with ext. monitor"
date: 2010-03-22
forum: Hardware
---

### Post by westinman on 2010-03-22
Hi !
I have Ubuntu 9.10 installed on a Toshiba Portege R200.  By itself things seem to be working fine.  So one day I got an external monitor and plugged it into the R200.  When I performed a "Configure display settings", unchecked the "mirror screen" and clicked "detect monitors", the laptop basically hung and the external monitor remained blank.  In fact the power light remained amber color indicating it did not detect any signal coming from the laptop.
So I read on this forum a suggestion to reboot the R200 with the external monitor plugged in.  Rebooted and the output went to the external monitor BUT the laptop monitor remained blank !  Went to "Configure display settings", unchecked "mirror screen" and clicked "detect monitors" and the external monitor goes blank BUT I still see and can move the mouse pointer around.  Nothing else.
I've tried a bunch of variations but can't seem to get both external and laptop monitor to work at the same time.
Any ideas ???
Thanks
Westinman

---

### Post by emilioldc on 2010-12-12
Exactly the same problem here. My toshiba portege r200 is unable to show mirror screens when an external monitor is connected to the laptop. I can see the screen in the external monitor, but not in the laptop, and only if I boot the computer connected to the external monitor.
If I use Fn+F5 to swap screens I loose image on external monitor and laptop monitor remains blank.
I'm using Ubuntu 10.10.

---

### Post by emilioldc on 2010-12-13
Problem solved:

1st: enter BIOS setup menu (or whatever its name is). I think is pulse ESC early in the boot sequence. Then F1.

2nd: look something like "external monitor" or "TV out" or similar and do NOT choose the default option "automatic". Instead of that default option, choose "LCD+CRT" or "LCD+external" or similar option.

3rd: reboot.

See you.

---

