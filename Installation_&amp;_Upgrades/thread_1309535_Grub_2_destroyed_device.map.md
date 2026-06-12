---
title: "Grub 2 destroyed device.map"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by OpenTangent on 2009-11-01
Grub 2 scrambled my device.map file and now i can't boot into windows 7. I edited /etc/default/grub and then ran: "sudo update-grub". All i edited was GRUB_TIMEOUT=1 to speed up boot time. Ubuntu still boots fine and the grub timeout has been set to 1 sec so i didn't notice anything until i tried booting into window. The error says "Error: Invalid Argument".

I googled a bit and found [this post]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=473340") which pointed me to the device.map file. My device.map file only has "(hd0)	/dev/sda" in it.

I'm hoping for a solution along the lines of:
```
sudo reconstruct-devicemap
sudo update-grub
```

---

