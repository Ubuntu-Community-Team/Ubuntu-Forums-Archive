---
title: "Laptop with external keyboard switching layouts?"
date: 2008-09-03
forum: Hardware
---

### Post by MeganMcD on 2008-09-03
Hi everyone,

I have my laptop set up with an external monitor and keyboard. I would like to be able to switch between the laptop keyboard layout and the external keyboard layout. I've tried looking in the keyboard preferences but it seems that the keyboard switching is just between language layouts.

Is this even possible? If so, how do I do it?

Thanks for any help!

---

### Post by Pigsflew on 2008-10-22
bump...

I have this problem a Macbook Pro and a Microsoft Natural Ergonomic 4000 keyboard. They're both very different hardware and need specific models set...

The expected behavior would be for xkb to read the two with two separate models, one for the macbook pro keyboard, and the other for the MS Natural Ergonomic, but the way it works I can set it to use the Macbook Pro layout, which works fine, or I can set it to use the MS layout, which also works fine, but as soon as I switch keyboards the other one doesn't work.

The other part is that when I change layouts a lot, I end up sometimes getting "Error activating XKB configuration"--I now get this on startup and none of my media keys work...

I know it sounds like a problem with X and XKB, is there any non-gui way to do this? Is there a bug open for this?

---

### Post by darioshanghai on 2011-08-24
Two years later the issue still stands: how do you switch keyboard without having to reconfigure ubuntu manually?

---

### Post by taojian on 2011-10-05
Looks like writing udev rules is the solution, [this page]("http://superuser.com/questions/95187/script-in-udev-rule-doesnt-run") has a pretty good example.

---

