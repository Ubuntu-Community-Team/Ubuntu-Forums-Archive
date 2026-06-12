---
title: "Load_Cycle_Count still a issue on 8.10!"
date: 2008-10-31
forum: Hardware
---

### Post by SpinningAround on 2008-10-31
It looks like Load_Cycle_Count is still a issue on my laptop (Asus X51R), downloaded smartmontools and got some values using 
```

smartctl --all /dev/sda/ | grep Load_Cycle_Count

```
I got this values from it
```

00.00.00h
193 Load_Cycle_Count        0x0012   099   099   000    Old_age   Always       -       12505
00.05.00h
193 Load_Cycle_Count        0x0012   099   099   000    Old_age   Always       -       12522
00.15.00h
193 Load_Cycle_Count        0x0012   099   099   000    Old_age   Always       -       12590

```

Given this do I have a increase of load cycles about 5,6 / min something that I guess is to high, note that I'm on AC power.

Possible fix?
Possible reason behind the problem?

---

### Post by teaker1s on 2008-10-31
sticky in hardware section solved count cycle on intrepid for us

---

### Post by SpinningAround on 2008-11-01
> **teaker1s said:**
> sticky in hardware section solved count cycle on intrepid for us

Thanks, but this might be a stupid question but where did you find that sticky?

---

### Post by teaker1s on 2008-11-01
has moved

[http://ubuntuforums.org/showthread.php?t=805570&highlight=load+cycle]("http://ubuntuforums.org/showthread.php?t=805570&highlight=load+cycle")

on an aspireone I used the uglyfix listed, but for battery power value 128 wasn't successful-used value 200

---

### Post by SpinningAround on 2008-11-01
I tried to use this guide [http://ubuntuforums.org/showpost.php?p=5031046&postcount=3](http://ubuntuforums.org/showpost.php?p=5031046&postcount=3) as you recommended but when I tried to install it did I get this error message

> 
 $sudo install 99-hdd-ugly-fix.sh  /etc/acpi/resume.d/
install: cannot create regular file `/etc/acpi/resume.d/99-hdd-ugly-fix.sh': Permission denied


Also something that confuses me regarding this bug is that at launchpad is this bug stated as fixed.
[http://brainstorm.ubuntu.com/idea/288/](http://brainstorm.ubuntu.com/idea/288/)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

At the end of the bug report are they talking about laptop-mode can it have something to do with the problem?
cat /proc/sys/vm/laptop_mode return 0 so I guess laptop mode is not activated on my laptop.

---

