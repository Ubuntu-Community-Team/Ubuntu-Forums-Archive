---
title: "intel 82855 card s-video"
date: 2008-07-17
forum: Hardware
---

### Post by Ozeuss on 2008-07-17
Hi,
I have a Dell D505 with an intel 82855 graphics which i want to connect to my TV (in the future, maybe turn it to a PVR).
The problem is- i couldn't make the TV more than flicker when connected through s-video. xrandr doesn't recognize the TV at all, and i tried multiple xorg.conf variations from many threads, also changing my driver from "intel" to the old "i810" (which showed a laptop image in like half the TV screen), and building the intel driver from git, and nada.
 XP on the other partition displays fine, so it's not the hardware.
Any help would be appreciated.

---

### Post by Ozeuss on 2008-07-18
*bump**

---

### Post by Ozeuss on 2008-07-19
anyone?

---

### Post by sparvik on 2008-10-14
I don't Know if you have given up yet or not but this might help

[http://ubuntuforums.org/showthread.php?t=361124&highlight=svideo+component](http://ubuntuforums.org/showthread.php?t=361124&highlight=svideo+component)

I am still tweaking his conf files to see if it will work on my Dell inspiron 1100 with the intel 845GL chipset.  I myself have been messing with it for 2 weeks now with no luck, so if you do figure it out, well then please help.

---

### Post by johnnylavah on 2008-11-25
> **Ozeuss said:**
> Hi,
I have a Dell D505 with an intel 82855 graphics which i want to connect to my TV (in the future, maybe turn it to a PVR).
The problem is- i couldn't make the TV more than flicker when connected through s-video. xrandr doesn't recognize the TV at all, and i tried multiple xorg.conf variations from many threads, also changing my driver from "intel" to the old "i810" (which showed a laptop image in like half the TV screen), and building the intel driver from git, and nada.
 XP on the other partition displays fine, so it's not the hardware.
Any help would be appreciated.

did you ever figure this out?  i am looking for a solution too.

---

### Post by Ozeuss on 2008-11-26
nope. AFAIK, the intel driver is a dead end for tv-out. the i810 is supposed to work, but i didn't manage to get it to display normally.

---

### Post by seuzy13 on 2008-12-13
I have this same graphics card. How can I switch to the i810 driver to see if I can at least get it to display in some way?

---

