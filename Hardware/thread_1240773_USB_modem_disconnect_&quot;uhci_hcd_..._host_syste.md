---
title: "USB modem disconnect: &quot;uhci_hcd ... host system error, PCI problems?&quot;"
date: 2009-08-15
forum: Hardware
---

### Post by ehammond on 2009-08-15
I've been using a Verizon USB727 (USB modem) with Jaunty and it works beautifully most of the time.

However, after a number of hours of usage (sometimes less) it suddenly disconnects from the network.  The full errors from syslog are available on:

  [http://paste.ubuntu.com/253430/](http://paste.ubuntu.com/253430/)

but they start with:

  kernel: [150839.260420] uhci_hcd 0000:00:1d.1: host system error, PCI problems?
  kernel: [150839.260431] uhci_hcd 0000:00:1d.1: host controller halted, very bad!

I can unplug the USB modem from that USB port and plug it into the USB port on the other side of the laptop.  It connects and everything works well for another while.  When the error happens again, I am unable get it working again without rebooting the laptop.

I'm running 2.6.28-14-server #47-Ubuntu SMP on a Dell Latitude E6500.

The "lsusb -v" output is available here:

  [http://paste.ubuntu.com/253450/](http://paste.ubuntu.com/253450/)

Let me know if you'd like any other diagnostic info.

---

### Post by karim.mansour on 2011-03-05
I have the same problem, I am using Ubuntu 10.10 with Mobile Broadband Modem Huawei E153 and it disconnects randomly or after a certain unknown time-out. Did anyone find a solution for this problem?

---

