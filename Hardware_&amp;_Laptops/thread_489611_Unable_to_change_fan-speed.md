---
title: "Unable to change fan-speed"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by jostmart on 2007-07-01
Hi all

Have been able to change my fan-speed with the "echo 'level 2' > /proc/acpi/ibm/fan" line for a while. Now I upgraded my kernel and I am only able to read the data in /proc/acpi/ibm/fan

root@aaa:/proc/acpi/ibm# uname -a
Linux bbb 2.6.22-7-generic #1 SMP Mon Jun 25 17:07:55 GMT 2007 x86_64 GNU/Linux


root@ccc:/proc/acpi/ibm# lsmod |grep think
thinkpad_acpi          50552  1

root@ddd:/proc/acpi/ibm# echo "level 1" > /proc/acpi/ibm/fan
Error: Unknown argument


So I guess something have changed in the kernel between 2.6.20 and 2.6.22 regarding this?

---

### Post by tocomo on 2007-08-05
you will find a daemon who makes the job at 
[http://projekte.f4.fhtw-berlin.de/trac/s0332819-linuxtools/wiki/](http://projekte.f4.fhtw-berlin.de/trac/s0332819-linuxtools/wiki/)

i am using it since half a year - and it just works.

Tobias

---

