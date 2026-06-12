---
title: "Problem with Wacom Intuos 2 on Hardy 64"
date: 2008-06-11
forum: Hardware
---

### Post by aleb on 2008-06-11
Hi,

The problem appears when I boot the computer and plug (or replug) the tablet. The tablet is mapped to the screen in a weird random way. Usually the mapped screen area leaves some unmapped space to the left, right and top.

If I leave the tablet plugged and boot, or restart X with ctrl-alt-backspace, the tablet is mapped correctly.

Any ideas how I could fix this?

Thanks!

I attached /etc/X11/xorg.conf.

---

### Post by ZabiGG on 2008-06-27
Hi there :)

Sorry it took so long for someone to answer. Just fixed my own tablet so I can help.

[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

Includes two important sections

One to set your tablet preferences in both Gimp and Inkscape and this setup for your xorg.conf file. You will have to play with the numbers, but it worked for me. You'll have to remove the "Absolute" options for your stylus and eraser or change them to "Relative" in your xorg file for this to work. Here it is:

 
**use a specific area of the tablet**

 You can limit the used area of the tablet to get the correct aspect ratio (if you draw circles and get something oval).  {{{Section "[InputDevice]("https://help.ubuntu.com/community/InputDevice")" 

[LIST]
[*]..      Option          "TopX"        "100"      Option          "TopY"        "200"       Option          "BottomX"     "14000" Option          "BottomY"     "6000" 
[*].. 
[/LIST]

[LIST]
[*][EndSection]("https://help.ubuntu.com/community/EndSection")}}} 
[/LIST]
Although you can make this different for the pen and the eraser, you propably want to have the same area for both of them. On the Graphire4 XL the resolution is 800 dots per cm, so 6000-200 is 7.25 cm on the tablet. 

I hope this helps!

Z.

---

### Post by aleb on 2008-06-27
> **ZabiGG said:**
> Hi there :)

Sorry it took so long for someone to answer. Just fixed my own tablet so I can help.


Hi, I have a question, what happens if you (boot, login and then) unplug and plug back the tablet, does it work (exactly) the same?

---

### Post by ZabiGG on 2008-06-27
Unfortunately, the plug&play aspect of the tablet is not yet covered. If you need to unplug and replug your tablet, you'll need to restart X every time you replug (ALT+CTRL+Backspace) for it to work again. But the configuration details you entered in your xorg.conf file will remain, so your tablet will work the same way once it's re-enabled. I'm sifting the Web for a workaround. 

Based on the Linux Wacom Project ([http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/)) there appears to be an application that can solve this problem (wdaemon), but they don't provide any installation instructions.

I'll try compiling it (I figure it's source code because of the extension) as soon as I have a chance to see if it works.

I'll keep you posted if it does.

Cheers,

Z.

---

