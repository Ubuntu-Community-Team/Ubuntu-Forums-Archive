---
title: "Targa Taveller 826T with X700 now working with fglrx drivers + hardware acceleration"
date: 2005-06-20
forum: Hardware &amp; Laptops
---

### Post by dex80 on 2005-06-20
hi,
after weeks i just have got it running.

after installing fglrx drivers with X700 support, i always had a black
screen after starting xserver.

one simple change has done the job for me
Adding:
**Option  "MonitorLayout" "LVDS,AUTO"** 
to my "Device" Section of XF86Config-4

now i have full hardware acceleration.

i have tried this with debian. do not know if it also is running
with ubuntu (ubuntu is crashing so i switched to debian) 
but i think it should also work because i had the same
black screen problem. 

i hope i can switch back to ubuntu but i could not find out why it is crashing.

there are still some other problems with this laptop. sound for example
is coming out only when headphones are plugged in.

i hope i can help someone with this thread to safe much of googling-time and playing with fglrx drivers. it took me to much time.

---

