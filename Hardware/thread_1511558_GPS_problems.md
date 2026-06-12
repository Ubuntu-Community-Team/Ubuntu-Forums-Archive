---
title: "GPS problems"
date: 2010-06-17
forum: Hardware
---

### Post by ve3tru on 2010-06-17
Anyone know anything about GPS units
I am running Ubuntu 10.04 and I thought id try out my usb GPS, but I get errors like this

peter@peter-laptop:~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[   17.185622] usb 7-1: pl2303 converter now attached to ttyUSB0

peter@peter-laptop:~$ gpsd -N -n -D 2 /dev/ttyUSB0
gpsd: launching (Version 2.92)
gpsd: Can't bind to port gpsd
gpsd: Maybe gpsd is already running!
gpsd: Can't bind to port gpsd
gpsd: Maybe gpsd is already running!
peter@peter-laptop:~$ 

What does "Can't bind to port gpsd mean", and how do I fix it?

---

### Post by IcarusR on 2010-06-17
gpsd is probably already running & you tried to start it again from terminal. 

To close the first instance:

```
kill -SIGINT `pgrep gpsd`
```

To see if gpsd is running:

```
ps aux | grep gpsd
```

Then try running your gpsd command.


Do a google search for 'GPS linux' or 'GPS ubuntu' for info on GPS & linux

---

