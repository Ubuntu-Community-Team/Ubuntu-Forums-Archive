---
title: "wireless card stops working"
date: 2009-05-08
forum: Hardware
---

### Post by izar on 2009-05-08
this seems to be a hardware failure. 
many times in the middle of my work the wireless card stops working. (nm-applet says the network connection has been disconnected, then it tries to reconnect for a wile and fails)

ifconfig dosent show wlan0 (which is my wireless card) so i tried:
```
~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such device
```

this happens also in MS windows, so the only thing that makes me think nothing is wrong physically is that restrating the laptop solves the problem.

lspci:
```
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
```

---

### Post by izar on 2009-05-14
help! my computer doesnt recognize my wireless card any more!!!
how do i know if this is a hardware or software problem, and if it is asosiated with the card itself or with the motherboard? and how do i fix it?

---

### Post by izar on 2009-05-27
please if anyone knows about this issue or how too fix it!!!
i have a hp dv6406nr notebook pc and wireless card stopped being detected. (as mentioned above).
replaced with an other card and the problem remains. put my card in an other computer and it works.
can this be a bios fault? can it be fixed?

---

