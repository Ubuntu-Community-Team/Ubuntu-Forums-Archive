---
title: "GPU hardware acceleration Intel HD Graphics 5000"
date: 2015-01-07
forum: Hardware
---

### Post by kassai on 2015-01-07
I'm running a fresh install of Ubuntu 14.10 on a [D54250WYKH]("http://www.intel.com/content/www/us/en/nuc/nuc-kit-d54250wykh.html") Intel NUC with an Intel HD Graphics 5000 gpu. Neither Google Chrome nor Firefox is able to play youtube clips in 1080 without pixelation. Netflix under Chrome suffers from the same issue.

Typing chrome://gpu/ in Chrome, displays the following, even when having enabled "Override software rendering list" under chrome://flags/:
```
**Graphics Feature Status**
Canvas: Software only, hardware acceleration unavailable
Flash: Software only, hardware acceleration unavailable
Flash Stage3D: Software only, hardware acceleration unavailable
Flash Stage3D Baseline profile: Software only, hardware acceleration unavailable
Compositing: Software only, hardware acceleration unavailable
Multiple Raster Threads: Disabled
Rasterization: Software only, hardware acceleration unavailable
Threaded Rasterization: Unavailable
Video Decode: Software only, hardware acceleration unavailable
Video Encode: Software only, hardware acceleration unavailable
WebGL: Unavailable

```

Not sure whether they same problem is described in this post [http://www.phoronix.com/forums/showthread.php?107972-Ubuntu-14-10-Officially-Released&p=448535#post448535](http://www.phoronix.com/forums/showthread.php?107972-Ubuntu-14-10-Officially-Released&p=448535#post448535)

According to to the Xorg log file, the gpu is correctly identified.

According to [Intel's web page]("https://01.org/linuxgraphics/downloads") for linux drivers, only 14.04 is supported through their installer. Do I need to install Intel's drivers (when they are out for Ubuntu 14.10) to get hardware acceleration?

I've been searching in forums for others with the same problem, but haven't came up with other hits than the above mentioned one. Starting to believe that I'm doing something wrong on my end, I appreciate all support I can get. :)

Thanks in advance!

---

### Post by kassai on 2015-01-08
I'll try to answer my own question.

The goal for me is to be able to watch Netflix and Youtube through a web browser. My question mentioned Chrome and Firefox. I'm taking Firefox out of this scope, as I've been extremely unsuccessful with getting hardware acceleration from it. Also it won't natively play Netflix.

To get hardware acceleration in Chrome, the following three steps were needed:

[LIST=1]
[*]Search for "hardware" and tick the checkbox for "Use hardware acceleration..." in  chrome://settings
[*]Enable "Override software rendering list" in chrome://flags/
[*]Launch Chrome from the command line with the --single-process argument: /usr/bin/google-chrome --single-process
[/LIST]

Have a look at what chrome://gpu/ looks like now. For me, everything but "Multiple Raster Threads" (which is disabled) is "Hardware accelerated":

```
**Graphics Feature Status**
Canvas: Hardware accelerated
Flash: Hardware accelerated
Flash Stage3D: Hardware accelerated
Flash Stage3D Baseline profile: Hardware accelerated
Compositing: Hardware accelerated
Multiple Raster Threads: Disabled
Rasterization: Hardware accelerated
Threaded Rasterization: Enabled
Video Decode: Hardware accelerated
Video Encode: Hardware accelerated
WebGL: Hardware accelerated

```

Without overriding the software rendering list (step 2) above), I wouldn't get full hardware acceleration.

Keep in mind, with the [--single-process]("http://www.chromium.org/developers/design-documents/process-models#TOC-Single-process") argument follows a browser behavior that isn't always desired nor stable.

---

### Post by kassai on 2015-01-25
Reply to my own thread again. In Google Chrome version 40.0.2214.91 accelerated graphics now works without any settings or overrides needed. Happy news for Netflix users who natively want to use a Linux distro to watch movies without performance issues.

---

### Post by mamamia88 on 2015-01-26
Thanks.   I had no idea about that option.

---

