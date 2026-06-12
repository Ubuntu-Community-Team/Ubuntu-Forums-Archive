---
title: "trackpad unresponsive when ac adapter plugged in"
date: 2008-10-06
forum: Hardware
---

### Post by mikesf on 2008-10-06
this is weird one: all of sudden, my trackpad became extremely sluggish in ubuntu 8.04 on my toshiba laptop. this was never an issue before! the mouse cursor would pretty much just freeze up for a few seconds and then i'd be able to move it a little bit, like an inch, then it would freeze up again.
when i plugged in a usb mouse, the problem was solved. THEN ... i discovered, somewhat by accident, that when i unplugged the ac adapter, the trackpad worked fine. SO... i believe that somehow acpi and trackpad are not happy together anymore.
does anyone have a clue as to how i can trouble shoot this? i looked at dmesg and /var/log/messages for some incriminating info, but nothing sticks out.

---

### Post by hybby on 2011-01-11
surprisingly, i have this issue in 10.10.  after battling with an unresponsive trackpad for weeks, i came across this post mentioning that the bug doesn't manifest when the ac adapter is unplugged.  so i tried it, and lo and behold the trackpad worked fine.  

so i imagine that there is a bug with acpi and xorg/synaptic with a subset of laptop devices.  i'm running an ASUS F3U series and would be interested to hear if anyone else has this problem.

in the mean time, i'll just be unplugging when i need to use the mouse i suppose!

---

### Post by mozart_ar on 2011-10-05
same issue here, it began to happen today. I have used ubuntu since 2008 in this laptop, from version 8, currently I have installed 11.04. My brother has the same issue from a month ago around. He has the same laptop model (HP DV9000), but Windows Vista. 
 The problem is the same, mouse freeze aleatory by 1 or 2 seconds, both mouse pad and usb attached mouse. When I unplug the AC adapter, mouse works well inmediately.
 Maybe this be a clue, I have forgotten my AC Adapter in my apartment this week, and I got my brother's one for working here (my parent's home). And other clue, today I have used an AC Adapter for cars (12V).
 This is very weird, crazy issue.

---

