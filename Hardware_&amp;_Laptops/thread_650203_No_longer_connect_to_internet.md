---
title: "No longer connect to internet"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by LarryEdwards on 2007-12-26
Newb running 7.04.  Since I downloaded updates 3 days ago. I cannot get to internet.  Before that internet was accessible via ethernet.  (Wireless doesn't work.).  Machine is Toshiba satellite A215-S7422 dual booted with Vista.  I don't remember what I downloaded, just what was offered.
Any ideas would be greatly appreciated.

---

### Post by Mithrilhall on 2007-12-26
Open a console and type this and post back the results:

```

ifconfig

```

---

### Post by LarryEdwards on 2007-12-26
In response to ifconfig I get
lo    Link encap:Local Loopback
       inet addr:127.0.0.1  Mask:255.0.0.0
       inet6 addr:  ::1/128 Scope:Host
       UP LOOPACK RUNNING   MTU:16436  Metric:1
       RX packets:1416 errors:0 dropped:0 overruns:0 frame:0
       TX packets:1416 errors:0 dropped:0 overruns:0 frame:0
        collisions:0 txqueuelen:0
        RX bytes:70800 (69.1 KiB)   TX bytes:70800  (69.1 KiB)

I forgot to mention that when I Shut Down, the laptop hangs with
Unmounting temporary filesystems
Deactivating Swap
Unmounting local filesystems
Will now halt

Then I have to turn it off with the power switch.

---

### Post by LarryEdwards on 2007-12-26
Furthermore, if I let it alone for many minutes, it writes to the screen a series of lines like
[ 4072.524000 ] usbdev2.3_ep0a : PM: resume from 0, parent 2-6:1.0 still 2
Finally it writes
[ 4088.468000] Power down.
[ 4088.468000] System halted.
[ 4088.468000] Please power me down manually

---

### Post by LarryEdwards on 2007-12-26
With the help of a friend we concluded that some nasty corruption happened when I did the updating.  So I am now starting over with Gutsy.

---

