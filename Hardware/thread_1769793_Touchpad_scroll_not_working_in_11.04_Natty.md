---
title: "Touchpad scroll not working in 11.04 Natty"
date: 2011-05-28
forum: Hardware
---

### Post by amaroKer on 2011-05-28
I couldn't figure out how to make scroll work on my HP Mini after upgrading to 11.04.  It had always worked out of box before that.  I found this year old thread after multiple searches so I thought I'd post it here for everyone to find easier.

[http://ubuntuforums.org/showthread.php?t=1470041]("http://ubuntuforums.org/showthread.php?t=1470041")
solution is in link at bottom

Edit: See post 3 below.

---

### Post by BrokenKingpin on 2011-06-07
I have the same issue on my Acer 532h. If your fix was to set the mouse to IMPS (PS2 mouse instead of a touchpad) that is a horrible workaround because you do not get the touchpad features in the mouse settings.

---

### Post by india12 on 2011-07-03
[http://superuser.com/questions/136568/touchpad-scrolling-is-gone-in-kubuntu-10-04-how-to-get-it-back](http://superuser.com/questions/136568/touchpad-scrolling-is-gone-in-kubuntu-10-04-how-to-get-it-back)

it will work,,helped me with scroll of vaio

---

### Post by tb070 on 2011-10-19
For my Acer, my Natty 11.04 and me the above didnt work.

What helped was:
- installing Gsynaptics (for Gnome) [dunno this did the trick]
- turning Syspad Off in Gsynaptics (system - preference - pointing devices)
- turning Syspad On in Gsynaptics

Perhaps you can first do this in Mouse (system - preference - mouse)
meaning turning Syspad off/on
before you install Gsynaptics.

I seem to remember my Acer (or UBU) needed this Off/On thing before to get the Syspad working.

Good luck!

---

### Post by RockMumbles on 2012-02-12
I have xubuntu 11.04 on my 2 year old Acer Aspire One and didn't have scrolling working, come to think of it I don't think tapping worked either... 

I tried the " psmouse proto=imps " hack and it didn't work ... 
so then I unloaded the psmouse module and reloaded it ... 
```

sudo rmmod psmouse
sudo modprobe psmouse
``` 
without the proto=imps, now scrolling and tapping works ???

---

