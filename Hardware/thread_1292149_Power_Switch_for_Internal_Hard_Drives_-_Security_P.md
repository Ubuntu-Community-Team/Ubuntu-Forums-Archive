---
title: "Power Switch for Internal Hard Drives - Security Precaution"
date: 2009-10-15
forum: Hardware
---

### Post by Gosport on 2009-10-15
We have all seen dual boot arrangements and such but I am interested in the extra security that a physical separation of hard drives would provide.  I am curious why I have never seen switches on (power or data) cables for internal drives.

I would like to install two separate hard drives in my computer with one operating system loaded on one (say with my sensitive data) and another drive with a separate operating system loaded on it (say for email and browsing the internet).  (On occasion I could turn them both on to transfer select information.)

I could load an alternate operating system on an external drive but I would still like the option of turning off the internal drive with all of my sensitive information.   Plus, I dont like the clutter of extra "stuff".

Has anyone done this before?
Where did you put the switch: power or SATA cable?
If you put the switch in the power cable where did you put it: there are two power (colored) and two ground (black) wires?

I have heard in the past that this kind of arrangement could fry your computer but the way we hot swap external hard drives I find it hard to believe.  Am I wrong?

---

### Post by Giblet5 on 2009-10-15
> **Gosport said:**
> We have all seen dual boot arrangements and such but I am interested in the extra security that a physical separation of hard drives would provide.  I am curious why I have never seen switches on (power or data) cables for internal drives.

I would like to install two separate hard drives in my computer with one operating system loaded on one (say with my sensitive data) and another drive with a separate operating system loaded on it (say for email and browsing the internet).  (On occasion I could turn them both on to transfer select information.)

I could load an alternate operating system on an external drive but I would still like the option of turning off the internal drive with all of my sensitive information.   Plus, I dont like the clutter of extra "stuff".

Has anyone done this before?
Where did you put the switch: power or SATA cable?
If you put the switch in the power cable where did you put it: there are two power (colored) and two ground (black) wires?

I have heard in the past that this kind of arrangement could fry your computer but the way we hot swap external hard drives I find it hard to believe.  Am I wrong?


You could install a DPDT switch on each drive that bridges the 12V and 5V power legs when "on". It would be best to buy some Molex disk drive power cable extenders and put the switches on those.

WARNING: changing the position of such a switch while the PC was powered on might easily result in damage to the drive, the motherboard, the power supply, or any combination of the three. DO IT AT YOUR RISK. If you don't care, then you might want to put a 0.2uf capacitor across each pole of each switch to prevent excessive spike noise on the power bus.

---

### Post by Gosport on 2009-10-15
Is a 0.2uf capacitor what they use to protect external drives? 

Why not put some sort of switch in the SATA data cable?  My eSATA port plugs directly into the SATA plug on the motherboard and you can plug/unplug external drives with no problems.

---

### Post by Gosport on 2009-10-16
Are there any switches sold commercially for this purpose?

---

