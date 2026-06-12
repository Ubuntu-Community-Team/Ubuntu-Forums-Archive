---
title: "add 3rd monitor"
date: 2009-10-13
forum: Hardware
---

### Post by tobyjoiner on 2009-10-13
I am trying to add a third monitor to my system but when I change the setting to use all three it will only use mirror mode.  

It does show all the same thing on all 3 screens, so they all work (I think).

If I change it to just 2, it works fine and the desktop extends.

This is a laptop if that matters.

One screen is laptop screen, other 2 are optiquest (which are detected as viewsonics).

I am pretty new at this stuff, so please go easy on me.

I have tried running ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` from this post: [http://ubuntuforums.org/showthread.php?t=1227071]("http://ubuntuforums.org/showthread.php?t=1227071")

I have also tried this: ```
sudo dpkg-reconfigure xserver-xorg
```

Thanks for any help,

Toby

---

### Post by markbuntu on 2009-10-13
What hardware do you have and what driver are you using?

---

### Post by tobyjoiner on 2009-10-13
its an ATI card, not completely sure the model, and I have tried the default drivers and the proprietary drivers.

The proprietary driver makes the machine really slow and doesn't seem to help at all.

The default driver makes the screen mirror fine on all 3.

Thanks again for your help.

Toby

---

### Post by tobyjoiner on 2009-10-14
I found the card model:

ATI Technologies Inc Mobility Radeon HD 3650

---

