---
title: "Battery Not Recognized, Machine Believes it's plugged in."
date: 2010-12-19
forum: Hardware
---

### Post by dustinmoorman on 2010-12-19
Good day, I recently bought a Toshiba Satellite L645, and of course, wiped the hard drive clean to install my favorite operating system. Save for having to install the WLAN driver, everything works perfect out of the box. However, I am experiencing one other concern. Even when unplugged, my machine believes it is on AC, and will display the lightning bolt in the notification area. I would be Very appreciative to get any suggestions on this, it's not a terribly big deal, but I'd like to know when to plug it in. I haven't let it discharge completely as I do not know what behavior it will take when the battery reaches the end of its life - an instant cutoff, or the soft shutdown as if it were on battery power. Thanks.. I hope we can find a solution. Let me know what information I can provide to better help with this.

---

### Post by dustinmoorman on 2010-12-19
Further exploration reveals:
```
dustin@dustins-laptop:~$ cat /proc/acpi/battery/BAT1/state
present:                 no

```

So acpi is fine, I am assuming. I wonder what in ubuntu, manages the battery status. I always believed it was acpi without any research to back that assumption.

---

