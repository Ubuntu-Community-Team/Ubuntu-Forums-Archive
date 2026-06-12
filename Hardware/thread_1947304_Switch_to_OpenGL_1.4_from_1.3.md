---
title: "Switch to OpenGL 1.4 from 1.3"
date: 2012-03-26
forum: Hardware
---

### Post by Aster.Orthrinos on 2012-03-26
Hi to everyone! I need OpenGL 1.4 for some application to work. ```
glxinfo | grep -i "OpenGL version"
``` say I that have 1.3 right now.

My Dell Inspiron 8500 laptop video card is Radeon RV250 Mobility FireGL 9000 as ```
lspci | grep VGA
```states. 

From [[COLOR="Red"]here[/COLOR]]("http://en.wikipedia.org/wiki/Comparison_of_AMD_graphics_processing_units") I found that my video card support OpenGL 1.4. Also Mesa 7.11 that I have supports it. 

I searched in internet and [[COLOR="Red"]found[/COLOR]]("https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/44772") that problem could be with  DRM (Direct Rendering module), and that probably means I need to have newer kernel. But I have lubuntu 11.10 so I think answer could be somewhere else. 

Also I [COLOR="Red"][[COLOR="Red"]found[/COLOR]]("http://www.cnx-software.com/2011/11/13/enable-opengl-2-0-and-webgl-for-intel-gma3150-in-ubuntu/")[/COLOR] that newer OpenGL could be turned on through **driconf** utility by switching on options "Enable limited ARB_fragment_shader support on 915/945" and "Enable stub ARB_occlusion_query support on 915/945". I installed driconf but I do not see these options listed there.
Could anyone help me?

---

### Post by Aster.Orthrinos on 2012-03-26
Update about DRM. I do not know which version I have and which supports OpenGL 1.4. In [[COLOR="Red"]this[/COLOR]]("http://www.opengl.org/discussion_boards/ubbthreads.php?ubb=showflat&Number=245824") page is told that /var/log/Xorg.0.log should contain some string pointing, like [COLOR="Black"]DRM interface version 1.3[/COLOR]. But I have found in this file only these with **drm** word:

 ```
[    42.992] drmOpenDevice: node name is /dev/dri/card0
[    42.992] drmOpenDevice: open result is 11, (OK)
[    42.992] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    42.992] drmOpenDevice: node name is /dev/dri/card0
[    42.992] drmOpenDevice: open result is 11, (OK)
[    42.992] drmOpenByBusid: drmOpenMinor returns 11
[    42.992] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
```.

---

### Post by Yellow Pasque on 2012-03-26
Radeon wiki says opengl 1.4 has not yet been implemented for r200-class cards: [http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

> Also I found that newer OpenGL could be turned on through driconf utility by switching on options "Enable limited ARB_fragment_shader support on 915/945" and "Enable stub ARB_occlusion_query support on 915/945". I installed driconf but I do not see these options listed there.
Those options are for intel cards and are completely irrelevant to your hardware...

---

### Post by Aster.Orthrinos on 2012-03-29
Hi, thanks for describing about driconf.


> **Temüjin said:**
> Radeon wiki says opengl 1.4 has not yet been implemented for r200-class cards: [http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)


This is strange becouse I found from this page that R250 supports OpenGL 1.4 (see 1st and 3rd tables).

---

### Post by Yellow Pasque on 2012-03-29
You're reading it wrong.
R200 OpenGL Compliance (Driver/Hardware) = 1.3/1.4
means Driver only supports 1.3 even though hardware supports 1.4

---

### Post by Aster.Orthrinos on 2012-03-29
Well, if it is so then I think  my questions are over. Thanks!

---

