---
title: "USB Mouse Stopped Working"
date: 2015-06-19
forum: Hardware
---

### Post by casey5 on 2015-06-19
Ever since the kernel was upgraded to 3.13.0.46 my USB mouse doesn't work (No Lights on mouse, doesn't appear as if Ubuntu even knows its there)  If I force Ubuntu to use the 3.13.0.45 Kernel, then things work.  Its just a cheap Dell Laptop, and external mouse also from dell.   I'm running Ubuntu 14.04 (64 Bit Desktop).

---

### Post by PaulW2U on 2015-06-20
I have a VPS and two laptops running *buntu 14.04 and they are all on the 3.13.0-55 kernel. I looked at the change logs and can see that there have been hundreds of bug fixes released recently.

So, have you tried to update? And if so, do you not get prompted to update the kernel and reboot?

---

### Post by akash14 on 2015-06-20
Update Packages and Reboot will Help, same problem happens to me too :)

---

### Post by casey5 on 2015-07-02
Been trying that, it will occasionally work, but the only one that works without issues is 45.

---

### Post by tgalati4 on 2015-07-02
Look through the log files to see if you can find USB errors:

```
more /var/log/syslog
```

Spacebar to page forward, "q" to quit.

Also:

```
dmesg | grep usb
```

---

