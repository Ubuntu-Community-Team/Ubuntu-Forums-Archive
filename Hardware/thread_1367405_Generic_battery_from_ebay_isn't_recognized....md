---
title: "Generic battery from ebay isn't recognized..."
date: 2009-12-29
forum: Hardware
---

### Post by aaronchall on 2009-12-29
I got a generic battery, 9 cells, from ebay as a Christmas present.  It works, because when I unplug my laptop, my laptop doesn't die, and it seems to work for a long time, but my laptop appears to have no idea of it's existence.  In fact, I can't find any options for my battery at all, except the very general power management settings.  

The LED seems to indicate I have a battery, but Ubuntu doesn't seem to know it.  What is missing here?

Aaron

---

### Post by aaronchall on 2009-12-29
```
sudo gedit /proc/acpi/battery/BAT0/info
```
(probably not good for me to be able to edit this, but...)
gives me this: 


```
present:                 yes
design capacity:         6600 mAh
last full capacity:      6344 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 660 mAh
design capacity low:     200 mAh
capacity granularity 1:  66 mAh
capacity granularity 2:  66 mAh
model number:            DELL 00
serial number:           36582
battery type:            LION
OEM info:                GWÿ
```

---

### Post by aaronchall on 2009-12-29
If someone can suggest more information I could provide to help get a solution on this issue, it would be greatly appreciated.

---

### Post by aaronchall on 2009-12-30
```
:~$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            1 mA
remaining capacity:      6600 mAh
present voltage:         12504 mV
:~$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         6600 mAh
last full capacity:      6344 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 660 mAh
design capacity low:     200 mAh
capacity granularity 1:  66 mAh
capacity granularity 2:  66 mAh
model number:            DELL 00
serial number:           36582
battery type:            LION
OEM info:                GW&#65533;

```

I think all of this means that my laptop knows there is a battery and that it is charged, but I don't get the battery icon at the top of my screen anymore.  The power management applet seems to think I am still plugged into the wall, even when I'm unplugged.

Thoughts?

---

### Post by aaronchall on 2009-12-30
I wouldn't say I have this fixed, but as a workaround I installed KPowersave, which purports to be able to tell me when I go to battery and how much battery I have left.  Testing... and it's telling me I have 2:23 hours remaining.  Great to know.  Original problem unsolved, but has been worked around.

Now I don't like that I had to install another program to do what my original setup was supposed to do, AND this one purports to manage my processor usage and other power settings as well, which I had been using the standard applications to handle.  

Maybe that's ok, and maybe it isn't.  I do know that my concerns have just dropped off anyone who might have cared's radar, but I'd like to know what went wrong, and how I could have fixed it.  This is the sort of thing that really bothered me about Windows, and it seems like I might never get away from it altogether, but what I do like about Linux is there is an answer out there somewhere, if you look hard enough.

Aaron

---

### Post by IcarusR on 2009-12-30
You could boot from the live CD & see if it works there. 
This would help tell you whether your install has a problem or not.

---

### Post by aaronchall on 2009-12-30
That's a good suggestion, thank you.

I'll try it later and see what happens...

---

