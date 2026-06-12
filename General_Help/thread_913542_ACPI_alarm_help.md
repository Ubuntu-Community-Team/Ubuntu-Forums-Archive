---
title: "ACPI alarm help"
date: 2008-09-07
forum: General Help
---

### Post by jako91 on 2008-09-07
G'day all,

I'm having trouble setting the ACPI alarm to wake up my computer. (and then once working to integrate with mythtv). The problem it only seems to be setting the time, and not the date. 

```

mythtvback@mythback:~$ cat /proc/acpi/alarm
2008-09-00 00:48:00
mythtvback@mythback:~$ sudo sh -c 'echo "2008-09-08 01:25:00" > /proc/acpi/alarm'
[sudo] password for mythtvback: 
mythtvback@mythback:~$ cat /proc/acpi/alarm
2008-09-00 01:25:00
mythtvback@mythback:~$ sudo sh -c 'echo "2008-09-08 01:25:00" > /proc/acpi/alarm'
mythtvback@mythback:~$ cat /proc/acpi/alarm
2008-09-00 01:25:00

```

**The time changes in the BIOS but the date stays set at the 1st of the month.** 
I am entering the time in UTC as the bios is in UTC time. 

Any ideas as to what i can do??

---

### Post by jako91 on 2008-09-11
Anyone??

---

