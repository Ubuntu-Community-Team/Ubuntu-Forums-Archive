---
title: "clock off by 18000 sec dual booting XP/LINUX"
date: 2008-11-08
forum: General Help
---

### Post by graysky on 2008-11-08
I'm dual booting between XP and LINUX.  I have both configured to use the same timezone, but have noticed that when I go from one to the other, the time is off by exactly 6 hours.  

If the time is right under LINUX and I reboot into XP, the clock is ahead by 18000 sec.  What's going on :)

---

### Post by ciscosurfer on 2008-11-08
It's essentially a matter of your motherboard's hardware clock, Ubuntu most likely being set to use UTC/GMT, and Windows being set to local time.

More on all of this can be found [here]("https://help.ubuntu.com/community/UbuntuTime") and [here]("http://ubuntuforums.org/showthread.php?t=382199").  Also, [here]("http://ubuntuforums.org/showthread.php?t=955952") and [here]("http://ubuntuforums.org/showthread.php?t=858722").  And, well, [here]("http://ubuntuforums.org/showthread.php?t=603764") too.

---

### Post by mobilediesel on 2008-11-08
> **graysky said:**
> I'm dual booting between XP and LINUX.  I have both configured to use the same timezone, but have noticed that when I go from one to the other, the time is off by exactly 6 hours.  

If the time is right under LINUX and I reboot into XP, the clock is ahead by 18000 sec.  What's going on :)

Ubuntu sets the motherboard's clock to UTC then adjusts its display to the local time zone. Windows just uses the motherboard's clock as-is.

---

