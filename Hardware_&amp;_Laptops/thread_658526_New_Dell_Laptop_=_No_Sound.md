---
title: "New Dell Laptop = No Sound"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by CarlosinFL on 2008-01-04
Yup - got my new Dell Latitude D830 and installed 7.10 on it. Everything is fine however one issue...My audio is not present. I then searched and found [this](http://ubuntuforums.org/showthread.php?t=205449) thread and now have no idea what to do after step 3. 

When I did a "lspci -v" command in shell, I can see my card:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 01fe
        Flags: fast devsel, IRQ 20
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

Now I have really no clue why it is not being recognized or how to get drivers for it. I have never had Linux not detect any onboard devices.

Please help.

---

### Post by Ub1476 on 2008-01-04
Always, at least often, troubles with the latest Intel ICH family (in this case ICH8|). Looks like there is a [fix here]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/"). It was the first link I got after searching on Google for "ubuntu intel ich8".

Tell me if it work:)

EDIT: Actually [this]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller") might work better since you got rev2, not rev3 (as in the guide).

---

### Post by CarlosinFL on 2008-01-04
Yup - that worked perfect!

---

