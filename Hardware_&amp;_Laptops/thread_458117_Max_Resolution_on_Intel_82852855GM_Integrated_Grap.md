---
title: "Max Resolution on Intel 82852/855GM Integrated Graphics?"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by billyimiller on 2007-05-29
Hello,

I'm not sure if this is the right forum on which to post, but here goes.

I would like a higher resolution on my laptop LCD display.
I have attempted to increase the display resolution, but to no avail and am now wondering what the maximum display resolution is.

I have a Gateway MX6030 with an  Intel(R) Celeron(R) M processor 1.40 GHz, and an Intel Corporation 82852/855GM Integrated Graphics Device (rev 02). I am running Ubuntu Feisty 7.04. The video driver in xorg.conf is i810.

At first, all I could get was a display resolution of 1280x768, however after installing 915resolution, the display was automatically corrected to the 1280x800.  I would like to increase this to another 16:10 resolution: either 1440x900 or 1680x1050. 

I've attempted to change these by running: dpkg-reconfigure xserver-xorg  and selecting the display modes, manually editing the display modes in /etc/xorg.conf, running something similar to 915resolution 5a 1440 900, editing /etc/default/915resolution to reflect that change, and adding the Option "ForceBIOS" "1024x768=1440x900" option under the devices section in xorg.conf.

I've never had the option to select a higher display resolution in System>Preferences>Screen Resolution. (Is there another way to select the resolution via the command line?)

Perhaps, I've not tried the right combination of these configurations, or perhaps the graphics card doesn't support these display resolutions (hopefully it does). Or, I'm just completely going about this the wrong way.

Any help or advice would be greatly appreciated.

Thanks,
billy

---

