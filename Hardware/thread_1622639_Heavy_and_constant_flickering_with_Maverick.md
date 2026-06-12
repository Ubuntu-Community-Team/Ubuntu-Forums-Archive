---
title: "Heavy and constant flickering with Maverick"
date: 2010-11-15
forum: Hardware
---

### Post by alswar on 2010-11-15
Hi all,

I need a technical advise here.

Basically I bought few weeks ago a MSI X410 laptop, which is using ATI X1250 with AMD chipset RS690M.
As Maverick came out just few days before i wanted to trash Windows 7 and going for it.
Problem: during Live CD and even installing it the screen was flickering constantly from the beginning.
This is a video I've just made with Ubuntu Maverick with Live CD: [http://www.youtube.com/watch?v=Pq1Hm8nGv24 ]("http://www.youtube.com/watch?v=Pq1Hm8nGv24")

As I'm a newbie I didn't try to understand why it was doing it so i went for Lucid. Which is working fine except video in HD that a so choppy that make me upset.
So I started a desperate search for other distro trying many of them.
This is the result:
Mint 10: same problem of Maverick as expected
Fedora 14: same problem of Maverick, didn't expect
Mint 9: slow HD video trying any single solution present on internet.
PCLinuxOS last version: same problem of Maverick, didn't expect
Suse 11.3: like Lucid
Ubuntu 9.10: like Lucid
Upgrading from Lucid: still the problem
maverick 64bit: same problem

Now I'm running Lucid and I was almost in peace with myself but then I've found a guy that owns exactly the same laptop saying that Maverick is working perfectly :S
Check comment on this page: [http://www.linlap.com/wiki/msi+x-slim+x410](http://www.linlap.com/wiki/msi+x-slim+x410)

To conclude I would like to have some advise after you see the video if that problem could be an hardware issue (laptop comes with warranty 1 year) as I didn't see anyone anywhere complaining about a similar issue. Thankfully MSI support is coming back promptly so PLEASE if you can help me to spot an hardware  issue on GPU or Monitor please let me know how or otherwise let me know if there's anything i could do to make Maverick running smoothly.

Thanks for you time

---

### Post by alswar on 2010-11-16
Ok, me stupid I didn't think to test with an external monitor...

I just tried and it looks ok on an external monitor via VGA.

No what should I do? I was looking on the Monitor settings but except Refresh rate (60Hz available only) and resolution there's not so much to change :(

---

### Post by alswar on 2010-11-16
Any help? :(

I was even trying to play with xrandr commands trying many different combination but only for Hz and HSync and VSync. I didn't touch the values in the middle.

This is the output of xrandr on Lucid:

```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 174mm
   1366x768       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
HDMI-0 disconnected (normal left inverted right x axis y axis)
  1368x768_60.00 (0x119)   85.0MHz
        h: width  1368 start 1440 end 1576 total 1784 skew    0 clock   47.6KHz
        v: height  768 start  771 end  781 total  798           clock   59.7Hz
  1368x768TEST (0x11d)  155.0MHz
        h: width  1368 start 1440 end 1576 total 1784 skew    0 clock   86.9KHz
        v: height  768 start  771 end  781 total  798           clock  108.9Hz

```And cvt

```
cvt 1366 768
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync

```I've also attached XOrg log on Maverick

Please help :cry:

---

### Post by alswar on 2010-11-18
Up!

---

### Post by pfalcon on 2010-11-22
Hi, thanks for starting a thread. Confirming issue. But first off, what about making a thread heading more search-friendly, like "Heavy and constant flickering with Maverick (MSI X410/X430, Radeon)" ? Maybe we'll catch more folks this way. Thanks.

Now, I'm having a X430-006UA model here, it has Radeon HD 3200. And yet the behavior is exactly the same as on your video. I so far booted from LiveCD, and was able to avoid flicker by booting with the following kernel parameters:

1. nomodeset - passing this, you get no filcker on (FB?) console during boot (removing splash param assumed). It still starts to flicker on X boot.
2. xforcevesa - expectably, forcing X to Vesa drivers allows it to boot w/o issues and at 1024x768 w/o even saying about performance.

So, priliminary diagnosis is:

1. Kernel modesetting is related. Either it's not that good yet, or doesn't support our peculiar (huh?) hardware.
2. We might have "buggy" LCD matrix which misreports its frequencies and stuff, so driver chooses wrong params.


Thanks for trying various distros, saves me time to do more investigation in other directions.

---

### Post by pfalcon on 2010-11-22
Did you try to install fglrx driver btw? (Can't try it with Live CD)

---

### Post by pfalcon on 2010-11-22
Solved! Apparently, we have crap in EDID.

So, how to do that:

1. Running cvt just as you did:

```
$ cvt 1366 768
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
```

But note that cvt rounded up width up to next 8 or something, if we'll use that, xrandr will complain later, so will need to use 1366 still.

2. Register new mode:

```

xrandr --newmode "136**6**x768_60.00"   85.25  136**6** 1440 1576 1784  768 771 781 798 -hsync +vsync

```

3. Add this mode for LVDS output:

```

xrandr --addmode LVDS "1366x768_60.00"

```

4. Launch it!

```

xrandr --output LVDS --mode "1366x768_60.00"

```

---

### Post by pfalcon on 2010-11-22
For reference, few prooflinks that there exist such problem as broken EDID:

[https://bugs.launchpad.net/nouveau/+bug/540632](https://bugs.launchpad.net/nouveau/+bug/540632)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539730](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539730)

Hints how to fix KMS:
[http://www.mail-archive.com/dri-devel@lists.sourceforge.net/msg46741.html](http://www.mail-archive.com/dri-devel@lists.sourceforge.net/msg46741.html)

---

### Post by pfalcon on 2010-11-22
Note: all xrandr manipulations above must be performed when booted with nomodeset . KMS messes everything up, and so far I wasn't able to make it ignore EDID and instead use what I give it.

---

### Post by pfalcon on 2010-11-24
Also got quick reply from KMS driver people, [http://lists.freedesktop.org/archives/dri-devel/2010-November/005770.html](http://lists.freedesktop.org/archives/dri-devel/2010-November/005770.html)

Quoting:

> Assuming your laptop contains a radeon, the panel timing comes from a
table in the vbios.  The timing problem is most likely not due to an
EDID problem, but to pll dividers that that panel doesn't like.  Try
booting with radeon.new_pll=0 on the kernel command line or try kernel
2.6.37.

That works like a charm and the only extra kernel param you need to boot 10.10 well and with KMS support.

---

