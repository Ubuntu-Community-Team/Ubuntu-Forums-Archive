---
title: "thinkpad trackpoint 9.10 iussue - unable to find device TPPS/2 IBM TrackPoint"
date: 2010-01-03
forum: Hardware
---

### Post by bruno314 on 2010-01-03
Hello,

I installed ubuntu 9.10, and I found an issue
I followed article about enabling scrolling with trackpoint and adjusting speed&sensitivity, but nothing worked (tried with **hal**)

Actually, my trackpoint does work (but not scrolling, and speed adjusting).
xinput list-props "TPPS/2 IBM TrackPoint"   returned :

"unable to find device TPPS/2 IBM TrackPoint"

so, it looks like it doesn't see it, but it it must work (because normal usage of trackpoint does work). Can you find, where is problem please (e.g. to make hal work with it)? thanks

(model R61i)

edit: also, configure-trackpoint utility says that track point is not detected

---

### Post by ceykooo on 2010-01-03
I'm having the same issue with same symptoms on a clean Lucid-Alpha-1 install on a Thinkpad r60 .  

Every solution I can find involves using either HAL or xorg.conf.  But now both of these are deprecated!

---

### Post by bruno314 on 2010-01-04
Hi.

Finally, I found solution. On some types of thinkpads as I saw (x200,x300) and also R61i (my notebook) It works if you disable in bios touchpad. That will make correct detection of trackpoint (which is for trackpoint addicted users good), but the price for this is disabled touchpad...

hope that helps for other with same issue

---

