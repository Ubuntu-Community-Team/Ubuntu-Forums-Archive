---
title: "Can't reboot"
date: 2006-02-15
forum: Hardware &amp; Laptops
---

### Post by Moosechees on 2006-02-15
After upgrading from Hoary to Breezy a few months ago, I started having this problem.  When I attempt to reboot (whether through Gnome or using /sbin/reboot via terminal) my system goes through the shutdown process, then the monitor  either goes black (the monitor doesn't think it's been disconnected, though) or displays a bunch of oddly colored vertical lines.  Which one it decides to do seems random.

At that point, nothing happens until I have to hold the power button in until it cuts the power and then turn the computer back on.

I've got a Dell Dimension 4800, and am dual booting WinXP, in case it might matter.

---

### Post by bluevoodoo1 on 2006-02-15
From a terminal, will this work for you? (it's a command to restart)

```

sudo shutdown -r now
```

---

### Post by NikoC on 2006-02-16
Perhaps the solution is in this thread:
[http://www.ubuntuforums.org/showthread.php?t=75314]("http://www.ubuntuforums.org/showthread.php?t=75314")

---

