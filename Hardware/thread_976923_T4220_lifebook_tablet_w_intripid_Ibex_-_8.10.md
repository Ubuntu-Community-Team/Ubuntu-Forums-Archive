---
title: "T4220 lifebook tablet w/ intripid Ibex - 8.10"
date: 2008-11-09
forum: Hardware
---

### Post by achristoffersen on 2008-11-09
Hi community,

I have read [this]("https://help.ubuntu.com/community/T4220") wikipost abot the t4220 and hardy. However - I have just upgraded to 8.10 ibex and as a noob, would like to know if someone would update the guide - if anything has changed?

I initially got some of the tablet working (partially) with [this guide for 4215]("http://ubuntuforums.org/showthread.php?t=604011")... But there might be something new under the sun?

Sincerely
Andreas

---

### Post by JPLGuy on 2008-12-21
I recently upgraded to Intrepid as well, and started following the wiki mentioned above. I have run into a snag with the buttons packages mentioned.

First, the repository containing fscd and fsc_btns does not have an intrepid distribution, and the hardy distribution doesn't use the latest kernel headers, so Synaptic cannot install it. 

I also tried to compile from the source code, but the fscd ./configure fails with:

```
checking for X11... configure: error: Package requirements (x11 xi xext xtst xrandr) were not met:

No package 'x11' found
No package 'xi' found
No package 'xext' found
No package 'xtst' found
No package 'xrandr' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables X11_CFLAGS
and X11_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

None of those packages exist in any of the default repos. XRandR is covered by x11-server-utils at least. 

I would like to get these compiled, but I don't know what to set the X11_CFLAGS and X11_LIBS variables to get it to install correctly.

The fsc_btns package compiled and installed without an error, but modprobe fsc_btns failed with "Module fsc_btns not found". 

Any help or ideas is appreciated!

---

