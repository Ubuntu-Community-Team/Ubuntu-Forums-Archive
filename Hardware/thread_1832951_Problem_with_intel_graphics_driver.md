---
title: "Problem with intel graphics driver"
date: 2011-08-25
forum: Hardware
---

### Post by Impavidus on 2011-08-25
Hello, I am having a problem with the graphics driver on my new laptop (fresh install of Ubuntu 10.04). My machine has an Intel i5-2410M processor with integrated graphics controller. It appears that X.org detects the correct driver, but loads the generic vesa driver nonetheless. The sympoms are being unable to switch to any decent screen resolution on my 16:9 display capable of 1600x900 and having slow 3D graphics. I have used Ubuntu for five years, until now all drivers always worked out of the box.

The package xserver-xorg-video-intel version 2:2.9.1-3ubuntu5 has been installed.

This might be some relevant output:
```

# lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
# xrandr -q
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600        61.0  

```Also included part of my Xorg.0.log.

---

### Post by .... on 2011-08-25
Use a newer version of Ubuntu. ;)

---

### Post by Impavidus on 2011-08-26
Solved, in 11.04 it works. I had expected the LTS version to work as well.

---

