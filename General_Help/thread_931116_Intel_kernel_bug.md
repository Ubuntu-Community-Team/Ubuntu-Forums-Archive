---
title: "Intel kernel bug"
date: 2008-09-26
forum: General Help
---

### Post by L815 on 2008-09-26
I was downloading Kubuntu Intrepid alpha 6 and there was a warning about intel ethernet hardware.

How can I check if I have the specific hardware that would be affected by the bug? 

My laptop model if sony vaio vgn-fz240e.

---

### Post by cariboo on 2008-09-27
Depending on what version you are downloading you may not have anything to worry about. Have a look here:

[http://ubuntuforums.org](http://ubuntuforums.org) /showthread.php?t=927943

To see if you are affected.

Jim

---

### Post by mc4man on 2008-09-27
lshw will show your Ethernet interface and list the driver used.

If you run it this way it's very easy to find and read (look in home dir. for hardware.html
```

sudo lshw -html > hardware.html
```

scroll down to you see the Ethernet box (id -network) and check your driver version.

---

