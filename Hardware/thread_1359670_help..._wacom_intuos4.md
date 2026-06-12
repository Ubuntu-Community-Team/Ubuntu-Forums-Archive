---
title: "help... wacom intuos4"
date: 2009-12-19
forum: Hardware
---

### Post by confubar on 2009-12-19
Please, can anybody tell me how to get my Wacom Intuos4 tablet working in 9.04.
And, please, explain so that a newbie can understand. ](*,)

---

### Post by Favux on 2009-12-20
Hi confubar,

I'll try.

Basically the Intuos4 was so new the default linuxwacom version's (0.8.2-2 in Jaunty) wacom.ko (the usb kernel driver/module) does not communicate with the tablet.

So you need a newer wacom.ko which you can get by compiling linuxwacom.  You don't install the new version of linuxwacom but instead copy the new wacom.ko into place.

A modified 10-wacom.fdi is also helpful.  See [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") on the "Re: Wacom tablets in Ubuntu guide/howto" thread.  The post has explanations, instructions and helpful links, one of them to gali98's HOW TO on compiling the wacom.ko.  But here is the direct [link]("http://ubuntuforums.org/showpost.php?p=7093065&postcount=104").  Remember only Section 1!

---

### Post by confubar on 2009-12-22
I have attempted this... never used a command line before.
I don't know what to do with this:
confubar@dell-desktop:~/Desktop$ wget [http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.4-3.tar.bz2](http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.4-3.tar.bz2)
--2009-12-22 12:18:06--  [http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.4-3.tar.bz2](http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.4-3.tar.bz2)
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-12-22 12:18:09 ERROR 404: Not Found.

---

### Post by Favux on 2009-12-22
Hi confubar,

Not your fault.  The LWP project updated linuxwacom to 0.8.4-4 and gali98 hasn't updated his tutorial yet to reflect that.  So just change 0.8.4-3 to 0.8.4-4 the few times you encounter it and you'll be good.

PS:  They used to keep their old drivers available but recently they started dropping them when they post the new one.

---

### Post by confubar on 2009-12-22
Now I have:

checking for Xlib... no
checking for X lib directory... found, /usr/lib
checking for XSERVER... no
checking for valid Xorg SDK... "xf86Version.h missing"
Tried /usr/include, /usr/include/xorg, and /usr/xc/include
checking for lib xf86config... checking for XORG... configure: error: Package requirements (xorg-server) were not met:

No package 'xorg-server' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I dont at all understand the previous two paragraphs

I have Xserver-org-core
Synaptic lists a lot of things , but not xorg-server

Now what????????????????

---

### Post by Favux on 2009-12-22
Hi confubar,

It looks like you missed on step 2.  Notice the middle line, between the update and upgrade lines, extends beyond the edge of the box.  You can use the slider at the bottom to see the whole thing.  Make sure you copy the entire line

Each line is a command and you hit enter after each line copy and pasted into your terminal.

---

