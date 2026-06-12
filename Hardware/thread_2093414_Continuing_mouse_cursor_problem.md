---
title: "Continuing mouse cursor problem"
date: 2012-12-10
forum: Hardware
---

### Post by mistergil on 2012-12-10
Running Xubuntu 11.10 (oneiric) with current updates on an AMD 64 machine.

Have searched the forum and discovered that others have this problem but there doesn't appear to be a solution. Approx. every tenth boot or so the mouse cursor is missing when reaching the login. Have to reboot the unit and the cursor reappears as normal for a number of reboots only to disappear again at a later boot. I have probably done three or four kernel and header updates since installing Xubuntu and the problem still remains.  I also dual boot with Slacky and do not experience the issue there so I don't believe it is a USB hardware/optical mouse issue but a software glitch within Xubuntu. Could anyone shed some light on this? Thanks.

---

### Post by saphil on 2013-06-21
I had a similar issue, where mouse and keyboard worked before an up grade and not after, but they worked fine if the gui was started from the tty1 with startx.
Check and see if the gdm and the mouse services are set to start at the same time.  if so, make sure the mouse starts sooner.

That is how I had to fix my issue.

Sorry this is 6 months late.

---

### Post by mistergil on 2013-06-21
Thanks for the tip.  Since one of the kernel upgrades the problem resolved so it is no longer an issue. Regards.

---

