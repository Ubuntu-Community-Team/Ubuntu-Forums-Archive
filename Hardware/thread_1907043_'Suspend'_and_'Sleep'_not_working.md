---
title: "'Suspend' and 'Sleep' not working"
date: 2012-01-10
forum: Hardware
---

### Post by rdlee210 on 2012-01-10
I just got Ubuntu 11.10 on my computer and the 'Suspend' feature and the 'Sleep' features don't work. They worked on W7 just fine, however. When I close the lid of my laptop it does not hibernate. It goes to a dark blue screen and won't come out of it, even if I press keys to 'wake it up'. Also if I keep it on for a little bit, when it should go into screensaver for W7 it goes to the same dark blue screen. I'm not sure what's wrong with it. Thanks in advance

---

### Post by wolfen69 on 2012-01-10
What kind of computer? And, post the output of:
```
lspci
```

---

### Post by rdlee210 on 2012-01-11
It's an Asus K53E. and I honestly don't know what you mean by the next part.

---

### Post by BlinkinCat on 2012-01-11
Enter lspci into a terminal and post the results back here - :)

---

### Post by BlinkinCat on 2012-01-11
If you don't know where to find your terminal, you can call it up with ctl, alt & T keys.

---

### Post by rdlee210 on 2012-01-11
Okay, thank you.

Here are the results:


00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
03:00.0 Ethernet controller: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)

I'm not sure if this is what you needed. I hope it is

---

### Post by BlinkinCat on 2012-01-11
Sure looks right to me - :)

Unfortunately I am a humble helper around here, so you will need to wait for somebody more learned than I to come along to help you.

---

### Post by Toz on 2012-01-11
Have a look at this solution: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug") - it should work for you.

---

### Post by hadji457 on 2012-02-09
> **Toz said:**
> Have a look at this solution: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug") - it should work for you.


Thank you so much for this link! This problem has plagued me ever since I purchased this laptop (Asus U50F). :D:D:D

---

