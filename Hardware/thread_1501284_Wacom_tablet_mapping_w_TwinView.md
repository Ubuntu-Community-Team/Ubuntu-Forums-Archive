---
title: "Wacom tablet mapping w/ TwinView"
date: 2010-06-04
forum: Hardware
---

### Post by RenderRob on 2010-06-04
First of all, let me say just how maddening it is that I can't find one decent tutorial which states the basic steps to configuring a wacom tablet.
1) Describe in detail how to edit xorg.conf.
2) Describe in detail what the user might want to add or remove to or from xorg.conf.
3) Describe in detail what to do after xorg.conf has been edited.

[edit]
I forgot that, for ubuntu 10, we're concerned with 10-wacom.conf in /usr/lib/X11/xorg.conf.d/, instead of xorg.conf.
[/edit]

I've seen the ridiculously long, exhausting, stupid details over at linuxwacom.sourceforge.net. I'm assuming I don't have to worry about all that crap since my tablet already works, and all I have to do is get the settings right in my 10-wacom.conf file.

I have two monitors. I'm using ubuntu 10.04 64-bit. **My wacom works as is, but I need to map it to just one monitor**, or it can flip between the two when the cursor nears the edge. Can someone please tell me how to do that? And please don't assume that I know what to do after I edit the file, because I don't.

I tried adding this to my 10-wacom.conf file:

> 
Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "Twinview" "horizontal"
        Option          "KeepShape" "off"
EndSection


---

### Post by Jonsan on 2010-06-04
The pressure sensitivity is mostly for "natural media paint". As you are  an artist, you know that on real paper, with a real brush, how hard to  push the brush down would make for different strokes and different  effects. Modern paint programs emulate this by using multiple  sensitivity levels from the tablet. I don't know if you actually need  2048 different sensitivity levels, as I'm not an artist, but if you can  afford it, you may as well get it now.

---

### Post by RenderRob on 2010-06-04
> **Jonsan said:**
> The pressure sensitivity is mostly for "natural media paint". As you are  an artist, you know that on real paper, with a real brush, how hard to  push the brush down would make for different strokes and different  effects. Modern paint programs emulate this by using multiple  sensitivity levels from the tablet. I don't know if you actually need  2048 different sensitivity levels, as I'm not an artist, but if you can  afford it, you may as well get it now.

The question essentially is, how do I map the area of my tablet to the area of **one** of my monitors. Right now it is mapped to both of my monitors.

---

### Post by Favux on 2010-06-04
Hi RenderRob,

Please see this thread:  [http://ubuntuforums.org/showthread.php?t=1461978](http://ubuntuforums.org/showthread.php?t=1461978)

See also:

[URL="http://ubuntuforums.org/showpost.php?p=6546012&postcount=1"]the linuxwacom HOW TO
[/URL]
[the Wacom wiki]("https://help.ubuntu.com/community/Wacom"), and note there is a Wacom tablet thread associated with it

---

