---
title: "Kernel Panic after kernel update"
date: 2005-12-24
forum: Hardware &amp; Laptops
---

### Post by siennalizard on 2005-12-24
Hello everyone!
I got my kernel upgrade through the automatic system yesterday, and then the advice that I should reboot. Before i did that, I cleaned up my grub menu.lst file to add my usual acpi=off option. i then wrote grub to the mba and rebooted.

All went well until the computer hung completely when it arrived at the GDM login screen. When did an emergency sync, unmount and reboot, it did it again, but I watched the kernel messages this time, and saw this:
[code]
unknown boot option+0x0/0x1da
<0>Kernel Panic - not syncing: fatal exception in interrupt.

Since then, I've copied the kernel from the live disk into my /boot directory, chrooted and made the necessary changes in grub and rebooted. I can start the computer, but many modules refuse to load and X fails because it can't find my mouse. I don't have an internet connection, either, because the IPTABLES kernel stuff is apparently not right, so I can't even get DHCP.

Is there an easy way out of this mess? Can I give you more information
Could kernel upgrades maybe be dealt with separately from userland software in future?!

Cheers, and have a great Christmas!
J.

---

### Post by siennalizard on 2005-12-25
An update:
It seems that the issue lies with the 2.6.12-10-686 kernel. I'm confused as to why it asked me to upgrade it, as that was what it was using. I've now switched to the -386 kernel, and can boot, but the system is unstable: I get a freeze within a few minutes is starting up. Using Synaptic to install the 2.6.12-9 kernels didn't really help, as I have the issue I mentioned above: no networking; very unstable.

Any suggestions for how to mend whatever it is I've broken would be appreciated.

J.

---

### Post by bunutu on 2005-12-25
What kind of x86 system do you have?  Also, it may be easier just to compile the kernel yourself than to continue wrestling with packages and hacking away a frakenstein kernel from the install disk.

There is a nice ubuntu howto on doing this here:
[http://www.ubuntuforums.org/showthread.php?t=85064&highlight=kernel+sources](http://www.ubuntuforums.org/showthread.php?t=85064&highlight=kernel+sources)

---

