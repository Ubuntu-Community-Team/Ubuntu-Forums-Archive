---
title: "Toshiba laptop mouse &quot;Tap to click&quot;"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by hygraed on 2006-07-02
Hi, I just installed Ubuntu Dapper Drake, and I'm happy to say that it's approximately twenty-nine thousand times better than Windows XP. However, I'm having a slight mouse issue.
My Toshiba laptop has a feature called "Tap to click," meaning that I can simply tap on the little mouse-pad thing, and the system treats it as a mouse click. However, it's immensely sensitive, which means that I'm constantly inadvertently closing windows and moving them and opening files. It's very irksome, and I was wondering if anyone knew of a way to turn this off in Ubuntu, either with a system command or a program.
Toshutils and toshset don't have anything to control mouse behavior, by the way.
Any help would be greatly appreciated!

---

### Post by rykel on 2006-07-02
[QUOTE=hygraed]Hi, I just installed Ubuntu Dapper Drake, and I'm happy to say that it's approximately twenty-nine thousand times better than Windows XP. However, I'm having a slight mouse issue.
My Toshiba laptop has a feature called "Tap to click," meaning that I can simply tap on the little mouse-pad thing, and the system treats it as a mouse click. However, it's immensely sensitive, which means that I'm constantly inadvertently closing windows and moving them and opening files. It's very irksome, and I was wondering if anyone knew of a way to turn this off in Ubuntu, either with a system command or a program.
Toshutils and toshset don't have anything to control mouse behavior, by the way.
Any help would be greatly appreciated![/QUOTE]

Hi there, I am using a Toshiba M40 and there is no problem with the touchpad... in fact, I am glad to say that the Linux touchpad driver does 2 things which I truly love, but yet is not found in Windows, namely: the top right hand corner tap is a Middle Click, and the bottom right hand corner tap is a Left Click.

I hope somebody out there can help you with your problem!

Perhaps you can try fully upgrading your system? Or perhaps you can install KDE Control Panel... I remember that they have some touchpad configuration section.... cheers!   \\:D/

---

### Post by Max Luebbe on 2006-07-02
I've got the same problem on my Vaio vgn-fs740, I'd be interested in knowing how to turn down the sensitivity as well!

---

### Post by evil_elman on 2006-07-02
If the Synaptics touchpad driver is the one that's used, try the following command in a terminal to see your current touchpad settings:
```
synclient -l
```

Documentation for it can be found in the built-in Ubuntu help:
'**System**' -> '**Help**' -> '**System Documentation**' -> Search for '**Touchpad**' and read the '**synaptics manual page**' and the '**synclient manual page**' for further info.

Try using the **synclient** command to alter your touchpad settings to your liking then add those settings to you xorg.conf. An example of mine:

```

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
	Option	    "FastTaps" "1"
	Option	    "SHMConfig" "on"
EndSection

```

---

