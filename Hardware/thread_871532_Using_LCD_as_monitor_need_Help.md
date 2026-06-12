---
title: "Using LCD as monitor need Help"
date: 2008-07-27
forum: Hardware
---

### Post by Dennis1337 on 2008-07-27
ok i have an Nvidia 7600 GS agp what im tring to do is hook it up to my Sharp LCD tv through dvi to hdmi and ive tried the how toos and nothing has worked soo if anyone could help me that would be great

---

### Post by gretarsson on 2008-07-27
> **Dennis1337 said:**
> ok i have an Nvidia 7600 GS agp what im tring to do is hook it up to my Sharp LCD tv through dvi to hdmi and ive tried the how toos and nothing has worked soo if anyone could help me that would be great

Hi I have same card as you and I hook it to Samsung LCD TV but it was pc inplug on it but my sceen did only display 640x400 but I fixed from terminal code.
gksudo displayconfig-gtk

from that list you can get driver for LCD tv and fix your display
hope this help

---

### Post by Dennis1337 on 2008-07-27
no that didnt work a second display didnt even show up and there isnt a sharp driver on the list also im runing on hardy 8.04 if that makes a difference im realy new to linux

---

### Post by gretarsson on 2008-07-28
> **Dennis1337 said:**
> no that didnt work a second display didnt even show up and there isnt a sharp driver on the list also im runing on hardy 8.04 if that makes a difference im realy new to linux

Hi
I have same system and graphic card but on that list you can find LCD drivers it only say LCD not type or brand of TV. I had this problem about my TV Samsung LCD 23" wide screen and in that program I found LCD list and then I find nvidia 7x and look for right display and it works fine for me.

---

### Post by Dennis1337 on 2008-07-29
i tired doing that and nothing the secondary display thing i cant even highlight maybe im just stupid or maybe ive just used windows to long but im beginning to think this isnt possible

---

### Post by gretarsson on 2008-07-29
> **Dennis1337 said:**
> i tired doing that and nothing the secondary display thing i cant even highlight maybe im just stupid or maybe ive just used windows to long but im beginning to think this isnt possible

Have you install nvidia driver? and if so try to get in add/remove programs 
nvidia X server settings and after you have install it,you will find it in the list of system / administration see what the settings can do for you.

---

