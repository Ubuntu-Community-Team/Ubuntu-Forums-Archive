---
title: "Updated Nvidia Drivers - Resulted in Flickering Display"
date: 2014-09-12
forum: Hardware
---

### Post by mo13 on 2014-09-12
Not sure if "jerky" is the correct term to use here, but what is happening is that the window would autoscroll up and down really quickly. This seems to happen in Firefox and other windows as well, such as Nvidia's X Server Settings. I captured an example video showing the outcome here: [http://youtu.be/Bp25Fyy_GsI](http://youtu.be/Bp25Fyy_GsI)

Notice how the tab selection keeps changing by itself without me  selecting anything with the mouse or keyboard. Also hovering over  different parts of the window will change the tab selection and the  display. It's much worse when it happens in Firefox since I can't properly click on a link due to the page scrolling really quickly.


This started happening after I  updated my video card driver for my GTX 560 Ti from 331.38 to 340.32  using the xorg-edgers PPA.  I did the update by performing a ```
**sudo apt-get purge nvidia***
```. After which I performed a restart and installed the **nvidia-340** package (also tried the 343 package and got the same results). Did I break something in the process? How do I fix it? Is there a way to at least reset whatever caused this back to default settings? I'm not sure what application or service is responsible for this display glitch.


  Any help is appreciated. Thanks

**EDIT:** I think flickering is a more appropriate word to describe the issue.

Using Ubuntu 14.04.1 LTS with Nvidia GTX 560 Ti.

**EDIT2:** I think I found the fix. [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1314367/comments/22](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1314367/comments/22) so far so good. I'll update this if it starts flickering again. For those that are wondering, you need to install compizconfig first (*_sudo apt-get install compizconfig-settings-manager_*). Open it and go to workarounds and then place a check on **Force full screen redraws (buffer swap) on repaint**. DO NOT MESS WITH ANYTHING ELSE! No restart necessary (at least for me).

---

### Post by bonzini on 2014-11-16
mo13, thank you for posting your fix.

This worked for me too (GTX 750 running on 14.10).  Sometimes the launcher would flicker, and one app that always flickered was gmusicbrowser.

No flickering now with that compiz adjustment!  Thanks again!

---

### Post by krzysztofpater on 2014-12-31
> **mo13 said:**
> 
**EDIT2:** I think I found the fix. [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1314367/comments/22](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1314367/comments/22) so far so good. I'll update this if it starts flickering again. For those that are wondering, you need to install compizconfig first (*_sudo apt-get install compizconfig-settings-manager_*). Open it and go to workarounds and then place a check on **Force full screen redraws (buffer swap) on repaint**. DO NOT MESS WITH ANYTHING ELSE! No restart necessary (at least for me).

In terminal you can run:
>ccsm
go to Workarounds as mentioned above and check "Force ...." on
This helped me @100%!

---

### Post by Gunther_Van_Dooren on 2015-01-06
This solved my problem i think in TTY7.
 TTY1 to TTY6 still flicker allso when i shutdown the screen flickers.

```

lspci -vnn | grep -i VGA -A 12
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF114M [GeForce GTX 670M] [10de:1213] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device [1179:fb18]
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at d0000000 (32-bit, non-prefetchable) [size=32M]
    Memory at c0000000 (64-bit, prefetchable) [size=128M]
    Memory at c8000000 (64-bit, prefetchable) [size=64M]
    I/O ports at 3000 [size=128]
    [virtual] Expansion ROM at cc000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia

01:00.1 Audio device [0403]: NVIDIA Corporation GF114 HDMI Audio Controller [10de:0e0c] (rev a1)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]


```
```

glxinfo | grep OpenGL | grep renderer
OpenGL renderer string: GeForce GTX 670M/PCIe/SSE2

```

---

### Post by sharma-deepak83 on 2015-03-17
This worked for me too sir. Thank you once again....

> **mo13 said:**
> Not sure if "jerky" is the correct term to use here, but what is happening is that the window would autoscroll up and down really quickly. This seems to happen in Firefox and other windows as well, such as Nvidia's X Server Settings. I captured an example video showing the outcome here: [http://youtu.be/Bp25Fyy_GsI](http://youtu.be/Bp25Fyy_GsI)

Notice how the tab selection keeps changing by itself without me  selecting anything with the mouse or keyboard. Also hovering over  different parts of the window will change the tab selection and the  display. It's much worse when it happens in Firefox since I can't properly click on a link due to the page scrolling really quickly.


This started happening after I  updated my video card driver for my GTX 560 Ti from 331.38 to 340.32  using the xorg-edgers PPA.  I did the update by performing a ```
**sudo apt-get purge nvidia***
```. After which I performed a restart and installed the **nvidia-340** package (also tried the 343 package and got the same results). Did I break something in the process? How do I fix it? Is there a way to at least reset whatever caused this back to default settings? I'm not sure what application or service is responsible for this display glitch.


  Any help is appreciated. Thanks

**EDIT:** I think flickering is a more appropriate word to describe the issue.

Using Ubuntu 14.04.1 LTS with Nvidia GTX 560 Ti.

**EDIT2:** I think I found the fix. [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1314367/comments/22](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1314367/comments/22) so far so good. I'll update this if it starts flickering again. For those that are wondering, you need to install compizconfig first (*_sudo apt-get install compizconfig-settings-manager_*). Open it and go to workarounds and then place a check on **Force full screen redraws (buffer swap) on repaint**. DO NOT MESS WITH ANYTHING ELSE! No restart necessary (at least for me).

---

### Post by teknorah on 2015-04-23
> **mo13 said:**
> **EDIT2:** I think I found the fix. [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1314367/comments/22](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1314367/comments/22) so far so good. I'll update this if it starts flickering again. For those that are wondering, you need to install compizconfig first (*_sudo apt-get install compizconfig-settings-manager_*). Open it and go to workarounds and then place a check on **Force full screen redraws (buffer swap) on repaint**. DO NOT MESS WITH ANYTHING ELSE! No restart necessary (at least for me).

This worked! Thank you! :)

---

### Post by theller on 2015-09-15
> **mo13 said:**
> 
**EDIT2:** I think I found the fix. [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1314367/comments/22](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1314367/comments/22) so far so good. I'll update this if it starts flickering again. For those that are wondering, you need to install compizconfig first (*_sudo apt-get install compizconfig-settings-manager_*). Open it and go to workarounds and then place a check on **Force full screen redraws (buffer swap) on repaint**. DO NOT MESS WITH ANYTHING ELSE! No restart necessary (at least for me).

That worked for me on Ubuntu 14.04, an asus monitor & Radeon HD 8570D

Update: I was wrong, it did not work for me. It only stopped until the monitor locked. When It woke it up it started flickering again? Actually the flicker has turned into a longer blink.

---

