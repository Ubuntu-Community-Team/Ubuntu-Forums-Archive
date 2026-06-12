---
title: "Ubuntu 6.10 on TP600E dissappointing"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by vroomfondel on 2007-01-02
:( Had this old 600E lying around not doing much so I thought I try this much discussed distro on it.
This laptop has the max memory it can take and a newish 40Gb hdd.
The software installed ok but the video performance is too slow to be useable.
e.g. if I drag a window it moves very jerkily. 
BTW the laptop runs XP fine and another Linux distro I tried on it.

---

### Post by happy-and-lost on 2007-01-02
Try installing the correct video drivers ;)

Edit: You may benefit from adding the following line to the "Device" section of the xorg.conf

```
     Option     "XAANoOffscreenPixmaps"
```

---

### Post by vroomfondel on 2007-01-02
> **happy-and-lost said:**
> Try installing the correct video drivers ;)

which are? 
Oh, doesn't the distro detect the right ones to use?

---

### Post by happy-and-lost on 2007-01-02
Well, start by 
```
sudo gedit /etc/X11/xorg.conf
```
 and do what I said in my last post.

What video cord are you using?

Also, post output of glxinfo

---

### Post by vroomfondel on 2007-01-02
> **happy-and-lost said:**
> Well, start by 
```
sudo gedit /etc/X11/xorg.conf
```
 and do what I said in my last post.

What video cord are you using?

Also, post output of glxinfo

OK thanks, I read elsewhere to set depth to 16 bit on 600E and that alone seems to have improved video perf no end.  Didn't like gedit, I'm a vi man myself  :) 

Couldn't post glxinfo o/p as 600E doesn't have a working network...
So I'm now trying to get the USR5410 wifi card working, which seems to be another can of worms as the pccard slot isn't even detected. 

Thanks for your input.

---

