---
title: "Update: Intel 4500MHD external monitor flicker"
date: 2010-05-17
forum: Hardware
---

### Post by puetti on 2010-05-17
Hi all!

I'm running Lucid on an (almost) brand new Dell Vostro 3300 with Intel  chipset (Core i5, Intel graphics 4500MHD).

Basically, everything worked fine out of the box. The only BUT is that I  am experiencing problems with my external monitor, connected via VGA.  (Unfortunately, I don't have a digital port such as DVI or HDMI.) 
While the laptop screen works perfectly, the external device shows some  sort of blurred picture. All contours are somehow horizontally distorted  and are billowing. Some may also call it flicker...

Here is what I have already tried to locate the problem:

[LIST]
[*]Tested with 4 different monitors. Always the same effect.
[*]All kinds of different resolutions and refresh rates. No  difference.
[*]Installed the new 2.6.33 (and now also 2.6.34rc) kernel from mainline and xf86-video-intel  2.11.0 because it's supposed to bring "improved support for Intel  graphics with Core i5". Again, all the same.
[*]Altogether, my problem seems to be pretty similar to some issues  about ATI or nVidia cards. But I don't have such a thing...
[/LIST]
 As it works under Windows, I can also exclude a hardware problem.

Lately, I found out that seemingly it is NOT an X issue, as the problem also occurs if I only boot into the console without loading the X drivers.
Moreover, I can switch to the external monitor already while inside the GRUB boot menu. So far, the picture is just fine. But as soon as the boot process starts, I get the described blurring.

I'm really at a loss now... :(

Doesn't anyone have an idea that could help me? Or maybe is it a known kernel issue without a fix yet?
I'd be also curious if there's anyone facing similar problems.

Andreas

---

### Post by kmatteo on 2010-06-07
I have the same problem with dell VOSTRO 3300 and Ubuntu 10.04.. :(

---

### Post by vipw on 2010-06-18
I also see this problem, but again on Vostro 3300. It would be good if someone could confirm this on any other 45000MHD. Perhaps it is specific to this laptop.

---

### Post by zluspai on 2010-06-21
Hi,

Same here with a vostro 3300 and the intel i3 processor. I think that's a linux driver bug; because the very same machine and monitor is perfectly fine when I boot to Windows 7.

Zoltan

---

### Post by vipw on 2010-06-23
> **zluspai said:**
> Hi,

Same here with a vostro 3300 and the intel i3 processor. I think that's a linux driver bug; because the very same machine and monitor is perfectly fine when I boot to Windows 7.

Zoltan

My Vostro 3300 has an i5 processor so, we know that this is a problem for both CPU families.

---

### Post by puetti on 2010-06-24
Well, at least I don't seem to be the only person in the world to have this problem any more...

However, this doesn't help, of course...

By the way, meanwhile I switched from Ubuntu to Fedora 13 which naturally runs on the 2.6.33 kernel. Unfortunately, as could be expected from my unsuccessful tests with the mainline kernels, which I described in my first post, this didn't make any difference either.

Anyway, it's really interesting that the problem has so far only occurred on the Vostro 3300...

---

### Post by steve108 on 2010-07-30
I have this problem too, ati X1600 card, compaq nc8430 laptop, 10.04.

---

### Post by Maxime81 on 2010-08-18
Hi,

Same problem with my Vostro 3300 (core i5). The bug is know : 

[https://bugs.freedesktop.org/show_bug.cgi?id=28306](https://bugs.freedesktop.org/show_bug.cgi?id=28306)
[https://bugs.freedesktop.org/show_bug.cgi?id=28858](https://bugs.freedesktop.org/show_bug.cgi?id=28858)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614238](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614238)

Please help the developers to fix this issue !

Max.

---

### Post by steve108 on 2010-08-18
Well, I got mine fixed. I just followed the instructions in this link:

[http://beyondteck.blogspot.com/2010/05/flickering-monitor-in-ubuntu-1004-for.html]("http://beyondteck.blogspot.com/2010/05/flickering-monitor-in-ubuntu-1004-for.html")

Works like a charm now, I can finally watch movies while I work again!

---

### Post by benjamimgois on 2010-10-02
I have the same problem with my core i5 graphics. When using it the image is terrible, the only way i could enhance a little bit the problem was to reduce the resolution to 1024x768 and force 60hz.

---

### Post by dbeth on 2010-10-04
(Sorry for my poor english, but I'm desesperate)

Hi, I have the same problem with my Intel integrated chip. I have a laptop Dell Vostro 3300 with Intel i3 and Ubuntu Lucid.

I have been searching in many sites, forums, etc. and nothing. I have upgrading my kernel from 2.6.32 to 2.6.35-v9patch... and nothing. I tested many resolutions and refresh rates on many external monitors (LCD, CRT, data shows, etc.) and nothing. I tested from 1024x768 to 1920x1080, and from 50 mhz to 75 mhz, and the flikering still there.

Please help me!, I'll be very grateful

This is my lspci | grep -i vga:

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)

xrandr show this:

Screen 0: minimum 320 x 200, current 3286 x 1080, maximum 8192 x 8192
VGA1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1920x1080      60.0*+
   1360x768       59.8  
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
LVDS1 connected 1366x768+1920+312 (normal left inverted right x axis y axis) 293mm x 164mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9

---

### Post by dbeth on 2010-10-04
Oops, I almost forgot, my sudo lshw -c video:

*-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 12
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:fac00000-faffffff memory:c0000000-cfffffff ioport:f080(size=8)

---

### Post by benjamimgois on 2010-10-04
> **dbeth said:**
> (Sorry for my poor english, but I'm desesperate)

Hi, I have the same problem with my Intel integrated chip. I have a laptop Dell Vostro 3300 with Intel i3 and Ubuntu Lucid.

I have been searching in many sites, forums, etc. and nothing. I have upgrading my kernel from 2.6.32 to 2.6.35-v9patch... and nothing. I tested many resolutions and refresh rates on many external monitors (LCD, CRT, data shows, etc.) and nothing. I tested from 1024x768 to 1920x1080, and from 50 mhz to 75 mhz, and the flikering still there.

Please help me!, I'll be very grateful

This is my lspci | grep -i vga:

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)

xrandr show this:

Screen 0: minimum 320 x 200, current 3286 x 1080, maximum 8192 x 8192
VGA1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1920x1080      60.0*+
   1360x768       59.8  
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
LVDS1 connected 1366x768+1920+312 (normal left inverted right x axis y axis) 293mm x 164mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9

I think that it might be a driver issue, here i can overcome this problem switching the intel GPU to my integrated ATI RADEON graphics. Maybe your best shot is to active the XORG-EDGES PPA and use the latest intel drivers.

---

### Post by dbeth on 2010-10-05
Thanks for you help benjamimgois, but with Xorg Edges PPA the results was worse. The X crashed with the packages from this repository.

However, checking the other symptoms of this problem, I can say that the flikering is from the plymouth to the CTRL+ALT Fx consoles. Maybe, for this symptoms, this problem is more deeper than just the Xs or the xorg Intel drivers. I don't know, I'm not an expert in this things.

---

### Post by warrenb on 2010-10-13
> **benjamimgois said:**
> I have the same problem with my core i5 graphics. When using it the image is terrible, the only way i could enhance a little bit the problem was to reduce the resolution to 1024x768 and force 60hz.

I have the same issue with my TOSHIBA C650 laptop (i3 core) and Ubuntu 10.10. Likewise the best picture I can get on my external monitor is 1024x768 (60Hz) and that is still really fuzzy and not at all usable. 

I really like a fix as I miss my 2nd monitor :(

---

### Post by raphinou on 2010-11-10
Same problem here. I bought this laptop because it was certified by Ubuntu:
[http://webapps.ubuntu.com/certification/hardware/201001-4955/](http://webapps.ubuntu.com/certification/hardware/201001-4955/)

I'm running 10.10, and saw it was certified for 10/04 LTS. Anyone runnin 10.04 confirming it's working fine?

Raph

---

### Post by puetti on 2010-11-10
> **raphinou said:**
>  I'm running 10.10, and saw it was certified for 10/04 LTS. Anyone runnin 10.04 confirming it's working fine? 

No.

My first post was referring to 10.04 LTS.

Meanwhile I've tried 
Ubuntu 10.04
Fedora 13
Ubuntu 10.10

always with the same problems... still waiting for a fix...

---

### Post by julio prada on 2010-12-01
> **zluspai said:**
> Hi,

Same here with a vostro 3300 and the intel i3 processor. I think that's a linux driver bug; because the very same machine and monitor is perfectly fine when I boot to Windows 7.

Zoltan
Same for me, my AOC f22s 22" 1080p flickers with Ubuntu but not Windows 7.
I have a Toshiba with a P6100 processor with integrated graphics like the Core i, this is what lspci displays:
Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

---

### Post by benjamimgois on 2010-12-02
It seens to be a problem with kernel mode setting. The intel driver is just fine.

[https://bugzilla.kernel.org/show_bug.cgi?id=21742](https://bugzilla.kernel.org/show_bug.cgi?id=21742)

---

### Post by toni.ef on 2011-01-19
A patch has been found.
Do you think it's going to be included in next official releases?

---

### Post by benjamimgois on 2011-01-19
> **toni.ef said:**
> A patch has been found.
Do you think it's going to be included in next official releases?

Wow, that's very good news. 
[https://bugs.freedesktop.org/show_bug.cgi?id=28306#c48](https://bugs.freedesktop.org/show_bug.cgi?id=28306#c48)

Let's hope that it will be merged into 2.6.37 or 38 so it will be fine in natty.

---

### Post by aridus on 2011-03-31
I have the same problem with a Vostro 3300 and VGA output to an external monitor. If one goes to the but indicated in the last but one post it states at the top:

RESOLVED PATCH_ALREADY_AVAILABLE 

I don't understand these matters. Does anybody more knowledgeable than me know how one can apply this patch and where it is (if such a thing is possible?)?

With grateful thanks, Martin

---

### Post by aridus on 2011-03-31
With respect to my previous post, I am herewith adding some further information in case it means anything to somebody: I have just tried the 11.04 beta 1 release, which came out today, as a live CD, and the problem occurs in this release also.

Martin

---

### Post by thispixel on 2011-04-26
> **warrenb said:**
> I have the same issue with my TOSHIBA C650 laptop (i3 core) and Ubuntu 10.10. Likewise the best picture I can get on my external monitor is 1024x768 (60Hz) and that is still really fuzzy and not at all usable. 

I really like a fix as I miss my 2nd monitor :(

I have the same laptop and have the exact same problem. I have installed 32 / 64 bit / Updated to the latest mainline kernel and also Ubuntu 11. All with the same god dam problem. I really dont want to have to go back to windows due to this silly problem.

Any time on a patch / fix?

---

### Post by aridus on 2011-04-26
I read somewhere (don't remember where..) that it could be many months before this is sorted out... Sigh... If somebody who is wiser about these matters could post something here to enlighten those of us in this situation, I'm sure we would all be grateful (I looked at various bug reports that I found about this but I really can't follow them... I'm just a humble user). Those of us without an hdmi or dvi port are stuck for now.

With thanks, Martin

---

### Post by shawark on 2011-08-09
This is known kernel bug 38750.
[https://bugs.freedesktop.org/show_bug.cgi?id=38750]("http://https://bugs.freedesktop.org/show_bug.cgi?id=38750")

Current fix makes intel GPU working
you can download the kernel 2.6.38-11 from this link
[http://people.canonical.com/~sforshee/lp614238/linux-2.6.38-11.48~lp614238v201108032108/]("http://people.canonical.com/%7Esforshee/lp614238/linux-2.6.38-11.48%7Elp614238v201108032108/")

It solved my Dell Vostro 3300
Other posts which mentioned kernel version 3.0.0.997, or 2.6.*.997 did not fix my laptop

However I still not able to get NVIDIA driver proper installed.

---

### Post by puetti on 2011-08-14
Thanks for the info shawark.

Just installed the recommended 2.6.38-11 kernel with my 11.04 system. All in all, the picture on the external screen is now much better than before. However, sharp color gradients (e.g. black text on white background) are still wavy. Thus: the VGA port is still not usable... :(

---

### Post by aridus on 2011-09-08
This is just to say that this problem (in my case with Dell Vostro 3300 and Dell external monitor, connected with VGA port) still exists in Oneiric 11.10 beta 1

---

