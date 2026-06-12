---
title: "Trying to write udev rule, part 1"
date: 2015-11-30
forum: Hardware
---

### Post by mringer on 2015-11-30
L-Ubuntu 14.04, udev  204-5ubuntu20.15 (most recent).

Problem 1:  man udev says that udev reads its rules from 

/usr/lib/udev/rules.d
/run/udev/rules.d           and 
/etc/udev/rules.d

The first 2 of these do not exist. There are rules files in the 3rd, also
in     /lib/udev/rules.d     My first Q is: how can I find out which if any 
of these rules does   udev    read, say on reboot?

Problem 2: I wrote a udev rule file, which does not work as hoped. 
Please is there a way to find out which rules got applied when I 
plugged in the device? 

Thank you.

---

### Post by ian-weisser on 2015-12-01
> **mringer said:**
> 
Problem 1:  man udev says that udev reads its rules from 

/usr/lib/udev/rules.d
/run/udev/rules.d           and 
/etc/udev/rules.d

The first 2 of these do not exist.

Instead of /usr/lib/udev/rules.d, try /lib/udev/rules.d
If the manpage is incorrect, please file a bug report.

> **mringer said:**
> Problem 2: I wrote a udev rule file, which does not work as hoped. 
Please is there a way to find out which rules got applied when I 
plugged in the device? 

Are you asking if your device got hijacked by some other rule?
Or are you asking for ways to troubleshoot the rule you wrote?

---

### Post by mringer on 2015-12-03
> **ian-weisser said:**
> Instead of /usr/lib/udev/rules.d, try /lib/udev/rules.d
If the manpage is incorrect, please file a bug report.



Are you asking if your device got hijacked by some other rule?
Or are you asking for ways to troubleshoot the rule you wrote?

Thank you for your reply. I will try to file a report.

I think I am asking: has the device been grabbed by some other rule?

Thank you, Mark

---

### Post by mringer on 2015-12-06
I have now attempted to file a bug report. "udev errror in man page".

---

