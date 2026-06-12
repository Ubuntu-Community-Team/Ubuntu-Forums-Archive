---
title: "Multi Stream Transport(MST) and Displayport"
date: 2013-12-29
forum: Hardware
---

### Post by gmiller2007 on 2013-12-29
Hi folks,

I recently purchased a dell up2414q, which can push 3840 x 2160 at 60hz via Displayport 1.2a. I'm having some issues getting to 60hz on Ubuntu 12.04. The system I'm running ubuntu on is capable of 2160p@60hz via displayport according to both Intel and the motherboard manufacturer. I'm using the integrated video from the processor. Also of note, I've run the same display on a separate computer(Windows 7) at said resolution and refresh rate without issue. That said, I'm not sure how to configure X either through xrandr or x.org conf files to run the monitor at its full ability. On my Windows box I run a radeon card and in order to run the monitor at full resolution/refresh rate the computer has to register the display it as two virtual displays(each at 1920x2160 @ 60hz).

I've tried the following via xrandr and cvt/gtf:
1) Changing the resolution and refresh rate to their desired values via xrandr
2) Changing the resolution and refresh rate to 2 half-width virtual displays
3) And lastly I tried adding a monitor x.org conf file.


1) Here's what I tried for a single display at 3840 x 2160 @ 60 hz:
```

$ gtf 3840 2160 60.0
  # 3840x2160 @ 60.00 Hz (GTF) hsync: 134.10 kHz; pclk: 356.17 MHz
  Modeline "3840x2160_60.00"  712.34  3840 4152 4576 5312  2160 2161 2164 2235  -HSync +Vsync
$ xrandr --newmode "3840x2160_60"  356.17  1920 2072 2288 2656  2160 2161 2164 2235  -HSync +Vsync
$ xrandr --addmode DP2 3840x2160_60
$ xrandr --output DP2 --mode 3840x2160_60

```

The screen hangs for about 5 seconds and then reappears and returns the following:
```

xrandr: Configure crtc 0 failed

```


2) Here's what I've tried to emulate two displays @ 1920x2160:
```

$ gtf 1920 2160 60.0
  # 1920x2160 @ 60.00 Hz (GTF) hsync: 134.10 kHz; pclk: 356.17 MHz
  Modeline "1920x2160_60.00"  356.17  1920 2072 2288 2656  2160 2161 2164 2235  -HSync +Vsync
$ xrandr --newmode "1920x2160_60" 356.17  1920 2072 2288 2656  2160 2161 2164 2235  -HSync +Vsync
$ xrandr --addmode DP1 1920x2160_60
$ xrandr --addmode DP2 1920x2160_60
$ xrandr --output DP1 --mode 1920x2160_60 --left-of DP2 --mode 1920x2160_60

```

And again the screen hangs for about 5 seconds and then reappears and returns the following:
```

xrandr: Configure crtc 0 failed

```

3) I played around with an xorg file to configure the resolution to 3840x2160, but that turned into a boot issue and so I rolled the changes back.


Has anyone successfully configured a 4k display @ 60hz that could shed some light on the process?

Lastly, a few system specific things:
According to xrandr, my current output is over display port 2 (DP2) despite having just one displayport output.
I'm running kernel 3.5.0-45-generic on 12.04 x64.
The processor is an i5-4670 with integrated HD4600 video and the motherboard chipset is a z87.
I've opted in for pre-release updates ("precise-proposed").
The video drivers I'm running are from a ppa provided by Valve for steam(ppa:glasen/intel-driver).

Thanks!


Edit: In 13.04 The screen's resolution is detected correctly by default but the refresh rate is still maxed at 30hz. Intel doesn't appear to support MST on linux with their integrated gpu drivers yet. Here's a (very brief)thread on their forums regarding their driver support:
[https://01.org/linuxgraphics/node/160](https://01.org/linuxgraphics/node/160)

Also for those interested, it sounds like a dedicated nVidia card may be able to push 60hz on linux. Here's a related thread from nvidia's developer forums regarding that info:
[https://devtalk.nvidia.com/default/topic/681356/can-t-enable-60hz-with-display-dell-up2414q-](https://devtalk.nvidia.com/default/topic/681356/can-t-enable-60hz-with-display-dell-up2414q-)

---

