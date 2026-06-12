---
title: "im confused: powertop"
date: 2008-10-07
forum: Hardware
---

### Post by youngalfred on 2008-10-07
Hi all, great forum!
Im a little confused by my powertop output.  I'm on an eeepc 701 4G,with adamms kernel and and ive turned the wifi off and compiz off.  This is what I get:
Any ideas why i'm not getting c3 power state?

---

### Post by youngalfred on 2008-10-07
also if its any help, when i type:
anthony@anthony-laptop:~$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            unknown
remaining capacity:      70 mAh
present voltage:         7971 mV
I get no discharge rate.  same with the gnome applet.

---

### Post by known on 2008-10-27
Could you post the output of 
# powertop -d

---

