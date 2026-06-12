---
title: "Well, it's back to the rt3562sta / rt2860 driver"
date: 2012-02-13
forum: Hardware
---

### Post by ratcheer on 2012-02-13
Is it just me, or is this weird?

For exactly one minor kernel release, the standard supplied driver for my Ralink 3062 wireless card, rt2800pci, worked like a charm. That was kernel 3.0.0-15. Before that, I always had to make and install the chipset vendor's driver, rt3562sta / rt2860.

But, with this morning's upgrade to kernel 3.0.0-16, I could not get rt2800pci to connect. It was at least trying to connect, but it asked for the WPA2 authentication password over and over. I reinstalled rt3562sta and the connection came right up.

What on earth are they doing with rt2800pci that it works for one minor kernel release, then it fails again?

Tim

---

### Post by ratcheer on 2012-02-13
The current problem with new kernel 3.0.0-16 is identical to bug 851339, which was not resolved but has been marked "Expired".

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/851339](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/851339)

Tim

---

### Post by glendavee on 2012-02-14
I have a similar problem (I think). My Netgear N300 usb wireless dongle stopped working when I went to 3.0.0-16. Going back to 3.0.0-15 fixed problem. The N300 has Broadcom bcm43231, and I'm running 64bit 11.10

---

