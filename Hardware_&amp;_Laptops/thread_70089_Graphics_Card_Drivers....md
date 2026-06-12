---
title: "Graphics Card Drivers..."
date: 2005-09-28
forum: Hardware &amp; Laptops
---

### Post by marz on 2005-09-28
Hi,

Ubunti currently detects that I have a GeForce Ti4200, but it is not using it correctly (or at least I don't think it is). It won't allow me to support a resolution greater than 800x600, and the screen itself is off-centre. Is there a way for me to select a generic graphics card driver, or a way to fix my current graphics card configuration?

Thank you,

Marz

---

### Post by Hobgoblin on 2005-09-28
[This thread](http://ubuntuforums.org/showthread.php?t=64137&highlight=refresh+rate) might help.

---

### Post by marz on 2005-09-28
Yes, thank you, I've found that in the Wiki How-To section. Unfortunately, it did nothing for me. I tried two methods, one of which was to try and re-automatically detect my card, which didn't work, and the other was to fix my monitor settings, which also didn't work. Is there anyway for me to reconfigure to a "generic graphics card" of some sort?

---

### Post by Biased turkey on 2005-09-29
[QUOTE=marz]Yes, thank you, I've found that in the Wiki How-To section. Unfortunately, it did nothing for me. I tried two methods, one of which was to try and re-automatically detect my card, which didn't work, and the other was to fix my monitor settings, which also didn't work. Is there anyway for me to reconfigure to a "generic graphics card" of some sort?[/QUOTE]

A generic driver is the vesa driver, it should work with any decent video board.
I would try to edit the xorg.conf and in the section "Device" specify :
Driver "vesa"

---

### Post by wylfing on 2005-09-29
I'm not sure I'd advise using the vesa driver. The OP is complaining that he can't get higher than 800x600 resolution, and this is the maximum vesa provides. You really should be using the 'nvidia' driver, which you can get by installing the nvidia-glx package.
I'd bet your problem has to do with mis-detecting your monitor's capabilities. First, find out what the horizontal and vertical scan frequencies are for your monitor. These are essential. Then edit the /etc/X11/xorg.conf file by hand. (First make a backup of xorg.conf so if anything goes wrong you can restore the old version.) 

Find the section that looks like this:
```
Section "Monitor"
Identifier      "Generic Monitor"
Option          "DPMS"
HorizSync       30-96
VertRefresh     50-150
EndSection

```
Put in the correct horizontal and vertical numbers for your monitor.

Then edit the following section to manually add higher resolutions:
```
Section "Screen"
Identifier      "Default Screen"
Device          "NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
Monitor         "Generic Monitor"
DefaultDepth    24
SubSection "Display"
Depth           24
Modes           "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

```
Where it says Modes is where you can simply type in any resolution you want to achieve and X will try to do it for you. Just follow the format that's already there. After you've done all this, restart X with Ctrl-Alt-Backspace. It should automatically restart and everything should be golden. If it's messed up, carefully verify what you've done. If you still can't figure it out, post your errors back here.

---

### Post by Biased turkey on 2005-09-29
Yes, I think you are right Wylfing, the problem looks more like a monitor config problem and not a videoboard config one.

To Marz: What monitor do you have ? Some googling should help you find your monitor specs including the horizontal and vertical frequencies

---

### Post by marz on 2005-09-29
Hey guys,

I recently read the post at school, so I was eager to try out everything you had said when I got home. Surprisingly, when I got here everything was fixed. I remembered that before I had went to Uni I had a few more updates to do, did those, and everything got fixed. Hurray?

Thanks for the help anyway :)

---

