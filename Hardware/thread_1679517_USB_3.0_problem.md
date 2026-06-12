---
title: "USB 3.0 problem"
date: 2011-02-01
forum: Hardware
---

### Post by exelero on 2011-02-01
Hi,

I found a problem with my notebook about USB 3.0 ports. Normally, if I don't connect any device to USB 3.0 during boot, they won't work. But if I connect sth at the beginning they works fine. I didn't check the speed if they work faster or not.

is there any suggestion? 
Thanks

---

### Post by Pernig on 2011-02-01
I am having the same problem with a USB 3.0 host card I just bought. You will probably find that you are only getting USB 2.0 speeds, and if so you may be getting these kind of errors if you use dmesg | tail:

[17213.875593] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint

I have a copy of Fedora installed on this machine which has a later kernel installed. I might see if my ports function properly with this.

---

