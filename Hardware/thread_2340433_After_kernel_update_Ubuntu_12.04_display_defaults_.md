---
title: "After kernel update Ubuntu 12.04 display defaults to 1k"
date: 2016-10-18
forum: Hardware
---

### Post by Regenpak on 2016-10-18
I have a mini-ITX Celeron based mobo (Gigabyte GA-C1037) with integrated Intel MN70 graphics. I got a kernel update (to 3.13.0-98) and after reboot my monitor reported 1024x768 resolution video instead of the native 1920x1080. The Display applet doesn't recognize my VGA connected LG E2370 anymore. With a lot of hassle (xrandr) I managed to get my X11 desktop behave again, and by including the xrandr lines to the [FONT=Courier New].profile[/FONT] file made it survive reboots. The only thing is that the console (tty1~6) is still at 1k resolution and I can't get it to use the same resolution as my desktop that it did before the update. Booting to previous kernels did not solve the issue nor did hacking 00_header (grub2). How can I get the original situation back?

---

### Post by Regenpak on 2016-10-23
Bah. It was not the kernel update after all but my LG monitor which decided to stop providing VGA I2C data. All my display adapter drivers, even the Windows ones, defaulted to 1k@85Hz as to drive a CRT which the LG duly refused to display. A replacement monitor had everything behave correctly. The LG has been violently decommissioned.

---

### Post by nevets68 on 2016-10-23
The monitor has been terminated with extreme prejudice. ;)

---

