---
title: "WiFi problems"
date: 2009-09-27
forum: Hardware
---

### Post by BigD77 on 2009-09-27
I have a installed Ubuntu 9.04 on a Dell Pentium 4 laptop with an NEC Warpstar Aterm WL54AG Triple Wireless Lan Card that works great if the signal is extremely strong.  If I am in the same room as the router, fine.  However, when I go upstairs, even though the signal meter shows over a 50% signal, I cannot connect.  However, I have no problems with Windows XP with the same or even a lesser signal.  Is there anything I can do to rectify this?

---

### Post by BigD77 on 2009-10-07
Bump.

---

### Post by c0mput3r_n3rD on 2009-10-07
> **BigD77 said:**
> I have a installed Ubuntu 9.04 on a Dell Pentium 4 laptop with an NEC Warpstar Aterm WL54AG Triple Wireless Lan Card that works great if the signal is extremely strong.  If I am in the same room as the router, fine.  However, when I go upstairs, even though the signal meter shows over a 50% signal, I cannot connect.  However, I have no problems with Windows XP with the same or even a lesser signal.  Is there anything I can do to rectify this?

Try going to System -> Administration -> Hardware Drivers, and see if there's a propriety driver that can be installed.  also, run a "sudo apt-get upgrade"

---

### Post by BigD77 on 2009-10-09
> **c0mput3r_n3rD said:**
> Try going to System -> Administration -> Hardware Drivers, and see if there's a propriety driver that can be installed.  also, run a "sudo apt-get upgrade"

The only driver available is the "Madwifi" driver.  Don't know if that will work with a NEC Warpstar Aterm WL54AG Triple Wireless Lan card (PCMCIA Card type).  The laptop didn't come with onboard wifi.  

Tried to upgrade, got nothing to remove or upgrade.

---

