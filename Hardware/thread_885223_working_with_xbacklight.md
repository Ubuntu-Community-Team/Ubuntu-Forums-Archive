---
title: "working with xbacklight"
date: 2008-08-09
forum: Hardware
---

### Post by davethewave83 on 2008-08-09
Ive installed xbacklight and tried to used it. But to all my commands it responds
"No outputs have backlight property".

Any ideas? Maybe an example command too:)

---

### Post by sdennie on 2008-08-10
It's possible that your display simply isn't supported by xbacklight.  I run a very well supported Dell laptop and xbacklight gives me the same output.  However, the Fn related brightness control keys work just fine.

---

### Post by davethewave83 on 2008-08-12
Ok Thanks! The FN keys work for me also, but they do not dim the back lights very much. They go down only about 7 or 8 settings, I'd like to be able to go down to complete darkness if desired.

---

### Post by KEYofR on 2012-09-22
Try this:
[http://forums.bodhilinux.com/index.php?/topic/5985-brightness-scripts/page__view__findpost__p__56911](http://forums.bodhilinux.com/index.php?/topic/5985-brightness-scripts/page__view__findpost__p__56911)

xbacklight doesn't do anything at all for me, not even write any message like it did for you. But both xrandr and /sys/class/backlight/*/backlight do work fine.

As for the 7 or 8 steps, it's probably 8. There are often 2 possible interfaces to the backlight, one using acpi, one using the video driver. The acpi one seems to always use 8 steps from min to max. The video driver one might be almost anything, I'v seen at least 0-8, 0-32, 0-100, 0-255.

Maybe the acpi one is being partially controlled by the bios and the min setting isn't all that low, but maybe the other interface (if you have one) can go further.

So try the script above. By default it tries to use the xrandr interface, which may not work, since that's what xbacklight does, then again it may work, because xbacklight doesn't work for me either but xrandr does.

Try various options manually until you figure out what works best for you, then write the options you want into ~/.xbl, then edit your keybindings for the Fn keys to use "xbl -" and "xbl +" and if you want make a menu entry that runs "xbl" with no options so you can pop up a slider. Maybe depending on what desktop you use you may be able to tie that to a systray icon.

---

### Post by cariboo on 2012-09-23
This thread is 4 years old, things have changed quite a bit since then, please create a new thread, as this one is closed.

---

