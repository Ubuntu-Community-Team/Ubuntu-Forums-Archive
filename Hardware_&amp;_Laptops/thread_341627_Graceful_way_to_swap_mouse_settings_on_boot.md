---
title: "Graceful way to swap mouse settings on boot"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by tweedledee on 2007-01-18
I am seeking a graceful way to have my laptop use different xmodmap settings for when I have a USB mouse connected (which, among other things, I use left-handed) to my laptop, and when I don't (so the built-in eraser mouse works correctly - it needs to be in "right hand" mode to function properly).  Right now I have the event for attaching a USB mouse in Removable Media set to execute my desired xmodmap command for when I have a mouse connected.

There are two problems, which may have independent solutions:
1. If I connect the mouse before booting, the command is not triggered - I have to unplug & plug in the mouse to trigger the event.  Not a big deal, but annoying.

2. If I unplug the mouse, I'm still left with the last xmodmap command I executed - which really messes up my built-in mouse.  Is there a simple way to trap the unplug event so I can execute the appropriate command?

Thanks for any help.

---

### Post by tweedledee on 2007-01-21
I have tried playing with udev rules to get the desired behavior, but have not had any real success.  Modifying other example rules doesn't seem to working for me, and even what seems to be the best guide available ([http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)) hasn't been helping.  Does anyone have a working example of a udev rule that triggers a program upon plugging in a mouse?

Or some other solution?

---

### Post by tweedledee on 2007-02-07
In the event anyone else is interested, I posted a solution in this thread: [http://www.ubuntuforums.org/showthread.php?t=350464](http://www.ubuntuforums.org/showthread.php?t=350464).

---

