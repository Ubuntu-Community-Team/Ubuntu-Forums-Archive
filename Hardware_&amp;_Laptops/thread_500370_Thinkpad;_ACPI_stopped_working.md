---
title: "Thinkpad; ACPI stopped working?"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by W. Irving on 2007-07-13
I've been running Feisty on my Thinkpad T23 since a week after it was released, and it's been working brilliantly. Best release yet.
But for no reason suspend, hibernate, and switching off the display with stopped working today - completely out of the blue. It is the same appalling behaviour I would only expect of Windows XP. I have not installed anything in at least a month, including updates. Usually the laptop is doing nothing but run Apache + mySQL, and it doesn't crash, so I can't see what could've happened!

Fn+F3/4/12 keys do absolutely nothing (nothing in the syslog either). I can suspend the PC from within XFCE, but it won't resume properly, requiring a hard reboot. Haven't tried hibernate yet. The display off time out is gone as well.

```
ps ax | grep acpi
```

..returns..

```

   31 ?        S<     0:00 [kacpid]
   32 ?        S<     0:00 [kacpi_notify]
 4656 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket

```

Suggestions?

---

### Post by Senex on 2007-07-13
I have started having the same problem, with my fairly new X60. Hibernate stopped working completely and now its a 70/30 percent chance that suspend will fail. I don't know how to fix it, but if anyone has any ideas I would be glad to hear them. Thanks, 
Bridget

---

### Post by Buchuki on 2007-07-27
I'm also having a similar problem with my X60; my volume and thinkpad key all stopped responding recently, and I suspect its related. My brightness keys work fine in hardware, but are not issuning ACPI events, I believe, as the brightness applet is not displaying.

When I enter the gnome keyboard shortcuts applet to try to update the volume mute (for example) shortcut and press the mute key, it doesn't seem to recognize it all.  I have maintained my updates, and have assumed that the problem was caused by one of those. I have no idea how to solve this since it was working fine from the start. Any suggestions?

Dusty

---

