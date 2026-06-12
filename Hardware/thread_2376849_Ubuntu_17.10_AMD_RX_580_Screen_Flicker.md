---
title: "Ubuntu 17.10 AMD RX 580 Screen Flicker"
date: 2017-11-06
forum: Hardware
---

### Post by etrigan63 on 2017-11-06
Hi,

I just setup Ubuntu 17.10 Gnome Desktop on my custom built Ryzen 1800X system. Everything is fine except that the screen flickers randomly. I especially see it on my conky panel. Here are my system specs:
[IMG]https://photos-4.dropbox.com/t/2/AABmC2kImrCSdfqPIMV6Fp0kpyZE_ltjsLlC-jJYNqqDhg/12/69118/png/32x32/1/_/1/2/Screenshot%20from%202017-11-06%2016-42-24.png/EOWrJBiv_5DDBCACKAI/PA8BRyGpWfVBldtcrQWb6WwiO0ZmRDBZQgiKFDVu9kg?size=1600x1200&size_mode=3[/IMG]
I am running the default drivers that Ubuntu installs. In spite of what screenfetch says, it is an RX580.

---

### Post by Cavaseul on 2017-11-25
I have the same problem on my Lenovo R60. Older Ubuntu versions work perfectly.

---

### Post by Yellow Pasque on 2017-11-25
If you try using Xorg session instead of Wayland session, do you have the same issue?

---

### Post by RobGoss on 2017-11-26
I'm also running 16.04, and occasionally I get a flickering from time to time, after the system startup but it goes away pretty quick. Not really sure why this is occurring

I'm thinking it might be a driver issue

---

### Post by Yellow Pasque on 2017-11-26
> **RobGoss said:**
> I'm also running 16.04, and occasionally I get a flickering from time to time, after the system startup but it goes away pretty quick. 

The other posters in this thread state their issue is with 17.10 and does not occur on earlier versions, so you are describing a different problem (and you don't even tell us what video you have).

---

### Post by RobGoss on 2017-11-26
> 00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0e)
  

I don't want to take any focus away from the **OP** I was just stating there are others with this same issue. This also happens in 16.04 also

I'm using the following 
```
00:02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0e0
```

At one point it was really bad but after a few updates I don't see it as much

---

