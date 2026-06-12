---
title: "Dell Precision M65 hangs when docked with Edgy"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by Kurgan_it on 2006-11-07
I have installed Edgy on my Dell Precision M65 while undocked, and everything works like a charm. I even installed Nvidia proprietary drivers, all is fine.

Now, when I dock the notebook and then try to boot Edgy (splash disabled), the computer locks up after trying to start networking (I have WLAN switched off, and ethernet connected and configured for DHCP. 

It says "soft lockup on CPU#0", and the only thing I can do is press CTRL-ALT-DEL, which tries to switch to runlevel 6, then halts completely without shutting down anything, and I have to power off.

I have found that some other users are experiencing issues with Dell docking stations, but related to graphical video output... I don't even get to the time when X starts...

Any suggestions? I am stuck with Windows when using the docking station (and external monitor).

Thanks a lot.

[COLOR="Red"]NEW INFO ADDED: I have found that booting with acpi=off or acpi=ht solves this issue, so now it's time to check for acpi issues.[/COLOR]

---

### Post by Kurgan_it on 2007-01-08
I have finally solved my problem, that is related to Intel wireless NIC. The bug shows up only when docked, this behaviour was misleading and made me think about something about docking, while it was wireless-related. 

I'm writing this post to leave a trace on the forum to help people that have the same problems.

You should download a patched driver for your intel wireless NIC. Read about it in this bug report:

[http://ubuntuforums.org/showthread.php?t=322180](http://ubuntuforums.org/showthread.php?t=322180)

---

