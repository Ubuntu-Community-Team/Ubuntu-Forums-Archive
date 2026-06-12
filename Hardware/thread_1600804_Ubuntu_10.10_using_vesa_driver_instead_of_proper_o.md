---
title: "Ubuntu 10.10 using vesa driver instead of proper one? Choppy video on Thinkpad x40"
date: 2010-10-19
forum: Hardware
---

### Post by deckoff on 2010-10-19
Hello
I installed 10.10 (tried upgrade and clean install) on my thinkpad x40. I  could not enable desktop effects and video playback is very sloppy. On  10.04 works fine. I tried compiz-check
```

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


```This is the output on 10.04
```

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card.

``` 
As far as I understand, my machine is running the generic vesa driver, instead of the proper intel one... 
I tried to install the newer driver from intel, but it did not help.  I am not quite sure I managed to install them properly, though :sad:
I tried with installing newer kenel, but with no luck, too?
Any ideas how to make Ubuntu 10.10 choose the proper driver?

---

### Post by madmax1735 on 2010-10-20
same issue i am also stuck with generic vesa driver.
i had desktop effects enabled in 10.04, had used the main line kernel to get it working then, but later it was fixed in the ubuntu kernel itself.

compiz-check gives me following output:

```
max@alienware:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

```

---

### Post by deckoff on 2010-10-20
[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

This should be the answer

---

### Post by mr_skater99 on 2010-11-12
Thanks deckoff - i tried creating the xorg file and rebooting - but i still couldn't enable desktop effects - and my mouse cursor disappeared...

Anyone else try the fix to enable the intel driver?

---

### Post by b00paul on 2010-12-02
I have the same problem. Tried the fix, same issues you had. Mouse no longer worked. If anyone has any ideas of how to fix this, please help us! Thanks.

---

### Post by mr_skater99 on 2010-12-15
Anyone got any ideas??

---

### Post by SirWeazel on 2010-12-17
I have a different laptop, but same/similar graphics card. I also followed the link in the #3 post, and created the xorg.conf file, and also installed the ppa:glasen/intel-driver.

This resulted in 2 things.
1. Still cannot enable visual effects. When i try, the screen shakes, windows disappear, and after the 30 secs it reverts back to the way it was.

2. I do have increased performance after trying these solutions.  Before i was unable to watch a DVD full screen, and now video is much smoother.

I'll be following this thread. I hope someone with more knowledge thank i finds a solution. I've spent an "all-nighter" trying to get this laptop to work correctly. HP Pavilion dv1000 (dv1240us).

---

### Post by OpenDream on 2011-09-29
Hello 

I have the same problem with the new vostro v131, Did you guys find the solution?

Thanks in advance

---

### Post by SirWeazel on 2011-10-04
Sorry, i never found a solution. I started running ubuntu 11.04 with the daily build of unity 2d. I have no complaints. Ubuntu 11.10 will be coming out in about 8 days (on the oct 13th). Maybe it will be fixed in for you in that release.

---

### Post by sgaap on 2011-10-04
You should be using the xorg-video-intel driver on the vostro and it should be able to run compiz, if it falls back to vesa or software rasterizer then it either might not be used, mesa isn't properly installed, libgl isn't linked properly or the support from the driver package just sucks (in that case maybe try the x-edgers ppa).

I had the same problem with the oss ati driver due to libgl not loading properly

```

glxinfo | grep render

```

should give something like:


```

direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) <bunch of other info>

```

if dri isn't enabled and/or software rendering is mentioned then something doesn't work properly, then just rename your xorg.conf (if you have one) and reinstall mesa and your driver (i am assuming that intel's oss drivers use mesa for this, since i don't have any intel gpu's this can be totally wrong)

apt-get update
apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core xserver-xorg-video-intel

if that doesn't load the proper driver you can force it through xorg.conf (enough data on that via google or forum search), it can also be that alternatives uses a wrong libGL (also, search for update-alternatives and libGL to find more info on that).

---

