---
title: "Fan control is not working – PC overheats"
date: 2010-11-10
forum: Hardware
---

### Post by Daniel_le_Rouge on 2010-11-10
Hello!

I have a serious problem with my Fujitsu Siemens Pi 2530 running with Ubuntu 10.10.

Since several days the fan is not working anymore. The hardware was checked in store, but the problem resides on the software side.

So I tried some bugfixes:
[LIST=1]
[*]Changing the DSDT file does not work since Jaunty.
[*]In **/etc/default/grub** I changed the following:
```
GRUB_CMDLINE_LINUX="acpi.power_nocheck=1"
```
[*]I created this small script as in **/etc/init.d**:
```
#!/bin/bash
#
sleep 5
echo -n 0 > /proc/acpi/fan/FN1/state
echo -n 0 > /proc/acpi/fan/FN2/state
echo -n 3 > /proc/acpi/fan/FN1/state
echo -n 3 > /proc/acpi/fan/FN2/state

```[/LIST]

Nothing of it worked probably. Sometimes the fan works, but most of the time it does not. In the moment I cool the CPU with a blow dryer, but I need to find a solution, otherwise I will be doomed to use Windows.

Thanks for any help!

Daniel

---

### Post by azitizz on 2010-11-21
If you find a solution to this I would be interested to know as well.

My fan works but only on a very low speed and unless I put the computer into suspend mode then log in again, it will overheat shutdown.

However now with 10.10 I cant successfuly log back into Ubuntu after suspending. It simply freezes up every time.

---

### Post by Daniel_le_Rouge on 2010-11-22
At the end I bought a new fan and new everything is working all right again.

So it was no software, but a hardware problem.

---

