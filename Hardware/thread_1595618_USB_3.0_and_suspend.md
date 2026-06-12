---
title: "USB 3.0 and suspend"
date: 2010-10-13
forum: Hardware
---

### Post by Tronman on 2010-10-13
Hello,

I recently purchased a system with USB 3.0 ports as well as an NTFS-formatted 2 TB USB 3.0 external hard drive. I'll be installing a fresh copy of 10.04 soon. I understand there's an out standing bug in the XHCI module which prevents suspend (which I've been following here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522998)). The current work around is to add SUSPEND_MODULES="xhci-hcd" to /etc/pm/config.d/unload_module so the USB 3.0 module will be disabled allowing for suspend as normal.

This makes sense, but I have a few additional concerns:

1. Will USB 3.0 support be re-enabled on wake up? If not, how to do so?
2. What happens if I have my external mounted and myself, or a script, etc, tries to take the machine into suspend?
3. Similarly, can I have it warn me, prevent suspend, or automatically unmount the device if the machine tries to go into suspend?

I'll be tinkering with it myself, just wanted to get some initial feedback before I start the install later on today and couldn't find any other posts on this. Thanks for your input!

---

