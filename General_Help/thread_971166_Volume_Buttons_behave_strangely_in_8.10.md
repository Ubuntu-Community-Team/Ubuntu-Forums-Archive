---
title: "Volume Buttons behave strangely in 8.10"
date: 2008-11-04
forum: General Help
---

### Post by Altay_H on 2008-11-04
My volume buttons worked out of the box in Hardy Heron. I recently did a clean install of Intrepid Ibex and my volume buttons now behave strangely. Mute works without issues. However, pressing volume up or down causes it to behave as though I don't release them. The volume will continue to increase or decrease until I press mute. It also causes my keyboard and menus from working, presumably because the volume key is being constantly input. My guess is that it only recognizes on press and not the on release. Is there an easy solution? Thanks.


Here's what xev says about my mute button, which is working:
```

FocusOut event, serial 33, synthetic NO, window 0x3600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 33, synthetic NO, window 0x3600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

```

What it says for volume up/down is basically the same, except that it repeats what's above indefinitely. I'm forced to restart every time I press volume up/down because there's little I can do with no keyboard. Any ideas?


EDIT: Interestingly, I just noticed that mute can cause the same behaviour, it's just not consistent.

---

### Post by Dave in Tempe on 2008-11-06
I have this exact same problem and am interested in an answer.  My computer is an HP Pavilion zv6000.  Other threads that seem to address a similar problem seem to only concern Lenovo laptops.

---

### Post by Altay_H on 2008-11-06
> **Dave in Tempe said:**
> My computer is an HP Pavilion zv6000.
I have the exact same model. What particularly annoys me is that Hardy Heron was one of the few distributions to actually have my volume buttons working out of the box.

---

### Post by Altay_H on 2008-11-06
> **Altay_H said:**
> I have the exact same model. What particularly annoys me is that Hardy Heron was one of the few distributions to actually have my volume buttons working out of the box.


It looks like there are at least two other people here with the same problem: [http://ubuntuforums.org/showthread.php?t=964674](http://ubuntuforums.org/showthread.php?t=964674)


There's also already a bug report: [https://bugs.launchpad.net/ubuntu/+bug/278781](https://bugs.launchpad.net/ubuntu/+bug/278781)

---

### Post by ktemkin on 2008-11-09
Here's a tentative 'patch': [http://ubuntuforums.org/showthread.php?t=974723](http://ubuntuforums.org/showthread.php?t=974723)

---

