---
title: "Screen Resolution on Ultra portable"
date: 2008-11-14
forum: Hardware
---

### Post by kambuku on 2008-11-14
Hi, Im new to Linux, and I have just installed Ubuntu as a dual boot on my new laptop which runs Windows XP. The laptop is an Ultra Portable PC using a VIA C7-M® Mobile processor and VIA chipset-1600MHZ, with a 10.2"WVGA wide-screen running at a max resolution of 1024*600 on a 10.2" screen.

Under Windows XP, I can adjust the resolution correctly and view the entire page. Under Ubuntu, the system is set at 1024 X 700, clipping part of the page. When I try to change the resolution to a lower resolution, I loose the image completely and I cant restore to the original working resolution unless I re-install! Can anyone help?:confused:

---

### Post by overdrank on 2008-11-14
> **kambuku said:**
> Hi, Im new to Linux, and I have just installed Ubuntu as a dual boot on my new laptop which runs Windows XP. The laptop is an Ultra Portable PC using a VIA C7-M® Mobile processor and VIA chipset-1600MHZ, with a 10.2"WVGA wide-screen running at a max resolution of 1024*600 on a 10.2" screen.

Under Windows XP, I can adjust the resolution correctly and view the entire page. Under Ubuntu, the system is set at 1024 X 700, clipping part of the page. When I try to change the resolution to a lower resolution, I loose the image completely and I cant restore to the original working resolution unless I re-install! Can anyone help?:confused:

Hi and welcome, if you are using Hardy 8.04 you can use the command ```
gksu displayconfig-gtk
``` and adjust there. What is the model of the graphics? If it is the VIA this may be a little harder to adjust.

---

