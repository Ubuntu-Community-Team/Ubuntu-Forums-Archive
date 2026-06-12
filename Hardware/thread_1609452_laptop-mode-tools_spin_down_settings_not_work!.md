---
title: "laptop-mode-tools spin down settings not work!"
date: 2010-10-30
forum: Hardware
---

### Post by ario on 2010-10-30
Whatever I set in /etc/laptop-mode/laptop-mode.conf spin down timer for on Battery is 5 seconds. Which is dangerous. I set LM_BATT_HD_IDLE_TIMEOUT_SECONDS=90 but it is 5 seconds in action.
I think the main problem is that these commands:
```
hdparm -B 1 /dev/sda
hdparm -S18

```
Will enable spin down ability but will not change the drives default 5 seconds time out. No matter what number I use in hdparm -S command it will be always 5 seconds. I also tried these:
[CODE]hdparm -B 127 /dev/sda
hdparm -B 128 /dev/sda
hdparm -B 254 /dev/sda
hdparm -B 255 /dev/sda
[CODE]
But none of them made -S command able to change the default 5 second time out.
I do not know where else to change settings.
Please help me.

---

### Post by ario on 2010-11-01
Bump!

---

### Post by ario on 2010-11-09
Bump!

---

### Post by ario on 2010-11-16
Bumpity Bump!

---

### Post by ario on 2010-11-23
Thanks for nothing. It seems that it's impossible in linux, which means you use a free operating system, so you have less quality!

---

### Post by efflandt on 2010-11-24
You did not mention if you used **sudo** to do those commands as root.  If you simply do them as a normal user, without using sudo, they may not have any effect (did you get any errors?).

---

