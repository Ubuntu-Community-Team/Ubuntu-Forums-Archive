---
title: "VGA Port on Dell e1505 (Ubuntu 10.10)"
date: 2010-11-25
forum: Hardware
---

### Post by shadowblade989 on 2010-11-25
Hello,

I just installed Ubuntu 10.10 on my Dell laptop and I can't seem to get the monitor connected to the display port working correctly.

I can cause an image to appear on the screen using the keyboard hotkey ( Fn+F8 ), but it's 640x480 panning around with the mouse. The only options in the nVidia settings panel for resolution for that display are 640x480 and lower. The only way I know of to add custom resolutions is by using xrandr. The problem with that is xrandr seems to know nothing about the external display.

X doesn't seem to start at all if I set the external display to "Separate X Display" using the nvidia panel. (Restarting the machine causes it to start in tty1. neither X nor a login terminal would be running on tty7 at that point)

I'm hoping to set this machine up as a media center, so any help would be greatly appreciated.

---

### Post by pawhtiobo on 2010-11-25
Hi :).

Some monitors don´t give X the correct DDC values and you have to set it manually in xorg.conf, it has happened to me a lot of times.
What's the model of the monitor?

See ya...

---

### Post by shadowblade989 on 2010-11-25
> **pawhtiobo said:**
> Hi :).

Some monitors don´t give X the correct DDC values and you have to set it manually in xorg.conf, it has happened to me a lot of times.
What's the model of the monitor?

See ya...

It's actually a Samsung LCD TV - Model LN32B380C5D

(Thanks for the quick reply)

---

### Post by pawhtiobo on 2010-11-26
Hi :)

I couldn't find any information about that Samsung LN32B380C5D in there Samsung's homepage, is the model correct?

I found this googling, about another model that was setup in the xorg.conf file:


Section "Monitor"
    Identifier           "Monitor1"
    VendorName     "Samsung"
    Identifier           "LE32B350"
    HorizSync          31.5 - 67.0 
    VertRefresh       56.0 - 65.0
    Option               "DPMS"
    


I also found this old thread:

[http://ubuntuforums.org/showthread.php?t=1142103](http://ubuntuforums.org/showthread.php?t=1142103)

I hope some of this can help you....

See ya...

---

