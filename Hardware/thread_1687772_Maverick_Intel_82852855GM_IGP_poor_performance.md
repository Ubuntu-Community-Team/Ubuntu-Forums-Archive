---
title: "Maverick Intel 82852/855GM IGP poor performance"
date: 2011-02-14
forum: Hardware
---

### Post by .zolder on 2011-02-14
I have a Dell Inspiron 1150 with an Intel Extreme Graphics 2 chip. I have very limited GFX capabilities:
- No form of compositing is supported.
- SD youtube and regular avi's play choppy. (1 to about 15fps)
- Google Earth 6 works at about 1fps and every time it starts up, it asks if I want it to use DirectX.
- Stellarium (3D nightsky) 0.75fps

Other 2D functions seem to have reasonable performance (scrolling in Firefox, general window management)

```
~$ lspci | grep 'VGA'
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

```
~$ glxinfo *(some highlights)*
direct rendering: Yes
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.9-devel

```

So, no hardware OpenGL rendering.. 

I added Xorg-edgers PPA and apt-updated as mentioned [**here**](http://ubuntuforums.org/showthread.php?t=1657009). This left me with a system unable to boot into GDM. DKPG'ing kernel 2.6.36 didnt help me much with this issue.. Using ppa-purge, I went back to the way it was before adding the PPA. Also, I went back to the default maverick kernel.

Then, I tried installing some drivers as mentioned [**here**](http://ubuntuforums.org/showthread.php?t=1358299). This didn't help either.

I don't use xorg.conf, it's completely empty.

Does anyone have any idea how I can fix this??

---

### Post by .zolder on 2011-02-15
I'd really like hardware OpenGL rendering! anyone???

---

### Post by Sirius1977 on 2011-02-15
> **.zolder said:**
> 

I don't use xorg.conf, it's completely empty.

Does anyone have any idea how I can fix this??

You have to add 
```
Section "Device"
Identifier     "Intel "
Driver         "intel"
EndSection
```

in the xorg.conf because in Maverick the 855gm is blacklisted. Without the above section Maverick uses Vesa only.

---

### Post by kcstoner on 2011-02-27
Same integrated graphics chip. Intel 82852/855GM on 2005 Samsung Q30 (512 mb ram, 1ghz centrino)
OS: Lubuntu 10.10.

Exactly the same problem over here. Video (avi) and audio (mp3) playback stutters in VLC, mplayer, gnome mplayer.

Am going to try to install drivers and see what happens, even though OP said that didn't help much. Will check and post in this thread.

---

### Post by kcstoner on 2011-02-27
I managed to get rid of video playback stuttering using this guide:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Mplayer now works without frame skipping, vlc ... not so much.
There is a a number of methods for fixing this problem (about 7 workarounds variants). I used the 1st, Brian Rogers, method

> 
Brian Rogers has packaged this fix as an experimental Natty (11.04) kernel. 
 
**Install the 855gm PPA and the patched kernel**

 [https://launchpad.net/~brian-rogers/+archive/graphics-fixes-testing]("https://launchpad.net/%7Ebrian-rogers/+archive/graphics-fixes-testing")Mplayer plays video normally, with terminal and chromium in the  background. More load slows the playback quality and frame rate so i  guess this is hardware rather than the software issue. VLC causes rapid brightness changes (refreshing maybe?).

---

### Post by .zolder on 2011-03-13
Thanks a lot for helping me out! The "i915 modeset=1" fix mentioned in the link kcstoner posted fixed everything. Proper 3D, compositing, stutter-free videoplayback, the whole lot works now.

---

### Post by bugbear6502 on 2011-06-24
> **.zolder said:**
> Thanks a lot for helping me out! The "i915 modeset=1" fix mentioned in the link kcstoner posted fixed everything. Proper 3D, compositing, stutter-free videoplayback, the whole lot works now.

Before I follow along, can anyone tell me how to REVERSE the "i915 modeset=1" in case it doesn't work?

  BugBear

---

### Post by Dangertux on 2011-06-24
> **bugbear6502 said:**
> Before I follow along, can anyone tell me how to REVERSE the "i915 modeset=1" in case it doesn't work?

  BugBear

All you have to do to reverse it is change the i915.modeset=1 to 0 or nomodeset in your grub.cfg / menu.lst file.

---

