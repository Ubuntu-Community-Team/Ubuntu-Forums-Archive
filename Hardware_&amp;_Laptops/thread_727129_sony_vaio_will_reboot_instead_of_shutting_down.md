---
title: "sony vaio will reboot instead of shutting down"
date: 2008-03-17
forum: Hardware &amp; Laptops
---

### Post by avilella on 2008-03-17
Hi all,

I have a sony vaio sz1xp and lately it has been misvehaving:

when I shutdown the computer, after 2-3 seconds of being off, it will reboot again.

the only way of completely shutting it down is to take off the battery.

any suggestions?

---

### Post by Ace2016 on 2008-03-17
Is this a linux specific issue or a hardware issue? just wondering, i mean even if was restarting on my laptop i can press the power button at grab to shut it down. Try this:

> sudo shutdown -h now

That will shut your computer down, but if its hardware related you might have to take it for a repair

---

### Post by prshah on 2008-03-17
> **avilella said:**
> Hi all,

I have a sony vaio sz1xp and lately it has been misvehaving:

when I shutdown the computer, after 2-3 seconds of being off, it will reboot again.

the only way of completely shutting it down is to take off the battery.

any suggestions?

it may be:

1) Power management related (Eg, sys thermal too high, fan kicking in)
2) LAN wakeup (are you connected to a wired LAN?)
3) Modem wakeup (connected to a phone line?)
4) try ```
sudo halt
```

---

