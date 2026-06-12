---
title: "How can I install a driver?"
date: 2010-10-26
forum: Hardware
---

### Post by macnomore on 2010-10-26
I recently got my own somewhat used computer.:)It is somewhat old, but no older than Windows XP. When I got it, the hard drive was wiped clean, so I installed an Ubuntu 10.04 dvd that I obtained from a friend on it. I originally intended to work in openGL:popcorn:, but every time I attempt to do something that does openGL, such as Celestia(GOME), it crashes.:frown: The monitor goes black and displays a pattern of purple and white vertical stripes, then goes black and blinks a pattern of black and white stripes fully cycling about once each second. This also happens randomly when watching something in flash, but does not happen in flash when I disable hardware acceleration. It also happens randomly in Eclipse.:(
I know that Ubuntu has been known to be really stable, so I can only assume that it is a hardware problem, unless a scratch or smudge on the installation DVD has caused a small error in the operating system distribution itself. My friend who gave me the installation DVD suggested I look up drivers for the graphics card, and so I did. A simple call of lspci reveals this information about my graphics card:
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```
From that, I understand that I have a 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device graphics card distributed by Intel, so I looked up a driver for this and found it in a list of supported graphics cards at [http://intellinuxgraphics.org/documentation.html](http://intellinuxgraphics.org/documentation.html).
I ended up downloading the xf86-video-intel-2.13.0 tarball at the link to the downloads page:confused:
Now comes the part that I am stuck at. I extracted its contents and found a bunch of things. In the file called INSTALL, I found instructions on how to install the driver, and it dumped a lot out. I retried it and piped it to a text file (calling ```
./configure >~/errors.txt
```).
  Here's basically what was dumped to the console as what I guess was an error:
```
Package xorg-macros was not found in the pkg-config search path.
Perhaps you should add the directory containing `xorg-macros.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xorg-macros' found
configure: error: Package requirements (xorg-server >= 1.6 xproto fontsproto ) were not met:

No package 'xorg-server' found
No package 'fontsproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
What should I do? Specifically the "package requirements not met " part lowers my hope:(. I am somewhat new](*,) to the UNIX Terminal, so I don't know how to set environment variables:confused:, but I do know a few commands. There is no 'xorg-server' package available to install or already installed according to Synaptic Package Manager. Should I try downloading a different driver? If I can obtain a new graphics card, should I replace my current one?

---

### Post by akand074 on 2010-10-26
To install your proprietary graphics drivers go to System > Administration > Hardware Drivers, install them there. Why your having crashes, I don't know. I suggest you download a new disk (10.10 is the newest release if you want the newest release) and burn it at a slow speed and verify. Then just do a clean install. If the problem persists then we can try to figure out what's wrong. At least that will probably save you some time.

---

### Post by odzk on 2010-10-26
you have to install those missing packages from synaptic.

---

