---
title: "Canon MP620 printer stopped working"
date: 2012-02-17
forum: Hardware
---

### Post by ratcheer on 2012-02-17
My Canon MP620 printer has been working for months, I just printed some stuff on it last week. But this week, it quit. When I tried to print stuff, Ubuntu gave a warning that "Canon MP620 may not be connected" and the print jobs just queued up.

So, I removed the printer and tried to reinstall it. Here is what I got:

```
Installing any and all dependencies for Printing and Scanning
Configuring CUPS
dpkg: regarding libcupsys2_1.3.9-17ubuntu3.9_all.deb containing libcupsys2:
 [COLOR=Red]libcups2 conflicts with libcupsys2[/COLOR]
  libcupsys2 (version 1.3.9-17ubuntu3.9) is to be installed.
[COLOR=Red]dpkg: error processing libcupsys2_1.3.9-17ubuntu3.9_all.deb (--install):
 conflicting packages - not installing libcupsys2[/COLOR]
[COLOR=Red]Errors were encountered while processing:
 libcupsys2_1.3.9-17ubuntu3.9_all.deb[/COLOR]
Building BNJ Networking
Installing Printer Packages
Installing Scanner Packages
Restarting CUPS
[COLOR=Red]restart: unrecognized service[/COLOR]
```

There is some conflict among the cups modules. How to resolve?

Thank you,
Tim

---

### Post by ratcheer on 2012-02-17
Apparently, this problem has been happening to various printers for several years.

My package manager shows that libcups Version: 1.5.0-8ubuntu6 is installed, and shows the following for libcupsys2:

```
No current or candidate version found for libcupsys2
Package: libcupsys2
State: not a real package
Provided by: libcups2
```

I need more help than I have found so far on the Internet.

Tim

---

### Post by ratcheer on 2012-02-17
Canon (the company) does not support Linux, so I cannot get any revised driver from them. I have been trying to use the installer from [MP 620 – 630 | Debian Based Univeral Installer | RackerUA]("http://rackerua.com/2011/05/mp-620-630-debian-based-univeral-installer/") It has apparently not been updated since May, 2011. It was how I originally got the printer installed and working, but it's not working for me, now.

Tim

---

### Post by ratcheer on 2012-02-17
Actually, although the page at rackerua.com has not been updated since May, 2011, the downloadable script was updated on 1/30/2012. I re-downloaded it and ran the new version. I no longer get the errors about libcups and libcupsys2.

However, I still cannot add my printer. The detection runs and does not find it.

With it attached to the PC by a USB cable, lsusb does not detect it, either. Has the printer died, or is it still a configuration issue?

Tim

---

### Post by ratcheer on 2012-02-17
***Can anyone help?*** I don't print much, but when I need to print something, I need to print it.

This printer was working just fine about a week ago. I wonder if the 3.0.0-16 kernel upgrade killed it?

Tim

---

### Post by ratcheer on 2012-02-17
Bug 872711 on Launchpad seems to be the same as my problem.

Tim

---

### Post by ratcheer on 2012-02-17
Ok, some brilliant guy on [http://us.generation-nt.com](http://us.generation-nt.com) suggested surfing to [http://127.0.0.1:631](http://127.0.0.1:631) in the web browser. Amazingly, that let me set up the printer, again. However, I am back to where I was when I started this morning. When I try to print something, it queues up and never prints. And the system occasionally throws up the dialog saying the printer may not be connected.

[http://us.generation-nt.com/answer/11-10-unable-set-up-printer-help-205120631.html](http://us.generation-nt.com/answer/11-10-unable-set-up-printer-help-205120631.html)

Also see bug 871985

Tim

---

### Post by ratcheer on 2012-02-20
I finally fixed it, although I feel that the solution is weird.

I disconnected the USB cbale from the PC. I reinstalled the printer drivers, providing the LAN address of the printer. I have *_never_* had to do this before, but now the printer is printing, happily.

Tim

PS - I believe, after all the research I did trying to discover a solution, that the cause of the problem was a CUPS package upgrade.

---

