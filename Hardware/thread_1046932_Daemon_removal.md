---
title: "Daemon removal"
date: 2009-01-21
forum: Hardware
---

### Post by DeltaFee on 2009-01-21
Hi I know that I can edit which daemons turn on, but I am not sure which ones that I don't need. I was wondering if anyone have any knowledge of a guide or such. Thxs:D

---

### Post by linux_tech on 2009-01-21
To get list of daemons running or processes whose parent pid is 1:
```
ps -aef | awk "{if ( \$3 == 1 ) { print \$_ }}"
```

replace 1 with 2 if you want to see all with ppid of 2

```
ps -e
```also works

[http://unixhelp.ed.ac.uk/CGI/man-cgi?ps](http://unixhelp.ed.ac.uk/CGI/man-cgi?ps)

---

### Post by linux_tech on 2009-01-21
This explains more about daemons and what they do
[http://www.sorgonet.com/linux/linuxdaemons/](http://www.sorgonet.com/linux/linuxdaemons/)

Performance guides show which ones to turn off to optimize
[http://www.linuxmonitor.net/blog/2007/03/ultimate-ubuntu-performance-tweaking.html](http://www.linuxmonitor.net/blog/2007/03/ultimate-ubuntu-performance-tweaking.html)

---

### Post by tommcd on 2009-01-22
Install **sysv-rc-conf**. It presents a simple interface that you can use to toggle on / off services in each runlevel. Ubuntu runs from runlevel 2, which you can confirm with the comand **runlevel**. Any services you don't need can be turned off in the runlevel 2 column in sysv-rc-conf.

---

### Post by DeltaFee on 2009-01-22
Do you have any tutorials for 8.04?

---

### Post by tommcd on 2009-01-22
> **DeltaFee said:**
> Do you have any tutorials for 8.04?

This is not specific to 8.04, and may be a bit out of date, but see this tutorial for speeding up Ubuntu:
[http://ubuntuforums.org/showthread.php?t=89491&highlight=speed+system+general](http://ubuntuforums.org/showthread.php?t=89491&highlight=speed+system+general)

---

