---
title: "REISUB fails on laptop"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by Harpoon on 2007-12-08
On those occasions where I experience a tough Gnome lockup (no keyboard, mouse, etc) I have had to resort to a hard reboot because the "magic reisub" solution has no mojo on this particular laptop (Lenovo 3000 N100).  In short, there is no response regardless of the key combination used - - alt-prtsc, fn-prscr, alt-fn-prscr . . .  or using uppercase or lowercase letters.

This has been driving me nuts for months.  I have finally discovered that the sysreq key needs to be defined in the kernel (/proc/sys/kernel/sysrq).  This file exists, has zero length, and is truly empty. The man page for proc does not list the file.

Question: does anyone know what the contents of /proc/sys/kernel/sysrq should be, and whether I can enable the "magic" by modifying this file?   I almost never use the printscreen function, and would gladly try to map it to a more irrelevant key if that is at all possible.

---

### Post by obnibolongo on 2007-12-18
Weird, in mine /proc/sys/kernel/sysrq is at '1'.

I've checked in [http://www.linux.com/base/ldp/howto/Remote-Serial-Console-HOWTO/security-sysrq.html]("http://www.linux.com/base/ldp/howto/Remote-Serial-Console-HOWTO/security-sysrq.html")

I suppose a 
```
echo 1 > /proc/sys/kernel/sysrq
```
should be enough for a temporary enabling of the functionality.

To make it more permanent:

(taken from the page mentioned above)
```
"sudo nano -w /etc/sysctl.conf" and then, to permanently activate the magic SysRq key:

# Enables the magic SysRq key
kernel.sysrq = 0

```

---

