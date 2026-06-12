---
title: "Corrupt display (Ubuntu 14.10 + Intel Mobile GM45)"
date: 2015-02-19
forum: Hardware
---

### Post by edantes2 on 2015-02-19
Ever since I upgraded 14.04 -> 14.10, I have been having this problem.  This is a Dell Inspiron notebook running Ubuntu 14.10/64.  The system starts fine at boot and eventually icons on the desktop and application bars go bad.  I have been keeping Ubuntu up to date  and upgraded the latest  Intel graphics driver using their installer (You have to fool the Intel installer into thinking you are still running 14.04).  But no avail, keep the machine on long enough and the display gets corrupt.  Attached a screenshot of the Unity side panel.

---

### Post by Gavin77 on 2015-02-20
You could try the following:
Create the file /etc/X11/xorg.conf.d/20-intel.conf and then paste this into it ```
Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option      "AccelMethod"  "uxa"
EndSection
```
then log out/back in.

See if that helps, if not just remove the file again and reboot.

Source: [https://wiki.archlinux.org/index.php/Intel_Graphics#Tips_and_tricks](https://wiki.archlinux.org/index.php/Intel_Graphics#Tips_and_tricks)

---

### Post by expertup on 2015-03-20
I had that same problem. After install and reinstall a lot of drivers, problem don't stop.

After resert compiz to default settings, problem with artifacts has stoped.

But now, I don't know what is source artifacts problem. But I know, that artifacts intensified after run virtualbox.

---

### Post by TheoFromSed on 2015-04-06
Same problem. Ubuntu 14

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

"intensified after run virtualbox" - confirm this. See this bug only when virtualbox started, and only one way to fix is to reboot my main system.

---

