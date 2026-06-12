---
title: "fglrxinfo returns segmentation fault (core dumped)"
date: 2006-11-12
forum: Hardware &amp; Laptops
---

### Post by Krash1201 on 2006-11-12
here is the skinny.  I am trying to get that nifty 3d desktop switch trick working in edgy with beryl.  after installing the fglrx drivers, and assuming there is 3d acceleration support, since all the info i can find says there is, i install xgl and beryl.  when i boot into a temporary xgl session, the session crashes.  when i boot into my normal session beryl-manager starts without any problems, but none of the nifty features work without xgl.

Thinking that 3d acceleration was the problem, i checked whether my mobility firegl t2 would support 3d acceleration.  fglrxinfo returned
```
segmentation fault (core dumped)
```

I have to note really quick that this is not a fresh edgy install, but an update from dapper using xserver-xorg-video-ati to fix a video display problem after the update.

Any ideas on how i can get 3d acceleration working, or another way to install xgl?

Thanks in advance.

---

### Post by Krash1201 on 2006-11-17
figured out, changing to the fglrx drivers after installing xserver-xorg-video-ati requires running sudo dpkg-reconfigure xserver-xorg and using fglrx instead of ati as the driver.

Still having problems with 3d acceleration though my hardware should support it.

---

### Post by fattmox on 2008-04-03
Thank you for sharing. I was having a very difficult time getting the fglrx driver working until I ran sudo dpkg-reconfigure xserver-xorg.

---

