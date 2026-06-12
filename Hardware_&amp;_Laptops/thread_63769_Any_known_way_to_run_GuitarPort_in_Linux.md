---
title: "Any known way to run GuitarPort in Linux?"
date: 2005-09-09
forum: Hardware &amp; Laptops
---

### Post by schizoid_embolism on 2005-09-09
Hi all,

I was wondering if there is any known way to get the Line6 GuitarPort ([www.guitarport.com](www.guitarport.com)) to work in Linux.  I've been unable to find any solution online.  Can it be done?

Thanks,

Jeremy

---

### Post by gosh on 2005-12-19
I have no idea but be very intrested in making it work..

---

### Post by www.rzr.online.fr on 2006-06-13
What about :

```

modprobe -v snd-usb-audio ; dmesg | tail

```

It is said to work under wmware :
[http://rzr.online.fr/q/HiZ](http://rzr.online.fr/q/HiZ)

---

### Post by newman on 2006-06-29
I'm very interrested in this too.

---

### Post by gosh on 2007-01-17
I am trying to run GuitarPort through a VMWare Windows XP session.
Wine doesn't support USB-devices AFAIK.
VMWare does.

I have it installed, but the only problem still is the sound.
It seems that VMWare is not good enough with streaming USB audio or something.

When I know more, I'll drop in again

---

