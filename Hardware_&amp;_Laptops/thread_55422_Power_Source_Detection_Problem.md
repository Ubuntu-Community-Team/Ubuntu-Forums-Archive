---
title: "Power Source Detection Problem"
date: 2005-08-08
forum: Hardware &amp; Laptops
---

### Post by warpforge on 2005-08-08
I have suspend, the battery level indicator, and even SpeedStep working, but the detected power source has a strange bug. Changing from battery to AC when the OS is running isn't a problem, but if I suspend, pull the AC power, and resume, the system still thinks I'm running on AC. Plugging in AC and pulling it again corrects the status back to battery. If I suspend on battery and resume, it also has the correct status.

I'm running a ThinkPad T40p.

---

### Post by s_p_a_r_k_y on 2005-08-09
seems like a strange little bug, probably the batery status monitor isn't refreshing. Try to submit a bug report to gnome

---

