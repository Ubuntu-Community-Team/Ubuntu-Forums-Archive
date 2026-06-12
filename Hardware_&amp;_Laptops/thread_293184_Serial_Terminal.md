---
title: "Serial Terminal"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by anthonyc78 on 2006-11-04
I have a wyse serial terminal that I run top on hooked up to my box I'm having problems getting this work on the new upstart system any help would be great 

thanks

---

### Post by bigfox on 2007-08-27
I figured this one out on my own and I will post the way I got it working here

Create a file in the /etc/event.d directory with the fallowing text.

```
# ttyS0 - getty
#
# This service maintains a getty on ttyS0 from the point the system is
# started until it is shut down again.

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5
start on runlevel 6

stop on runlevel 0
stop on runlevel 1
#stop on runlevel 6

respawn
exec /sbin/getty 19200 ttyS0 vt100
```

I am not sure about the runlevel 6 lines.  I added the start on runlevel6 and commented out the stop on runlevel 6.   Seamed to get it working or my, or it my have been what I did to when fiddling with the settings on my screwy wyse dumb terminal.

Also, my wyse terminal only seams to work when connected to its AUX port and when data is configured to its AUX port and only on 19200

---

### Post by bigfox on 2007-08-27
Well, looks like sometimes it works and sometimes it doesn't.

Don't know if it is my method for getting it working or my Wyse dumb terminal.

---

### Post by bigfox on 2007-08-27
Ok, I got it working properly now.


The file /etc/event.d/ttyS0  Needs to look like this

```
# ttyS0 - getty
#
# This service maintains a getty on ttyS0 from the point the system is
# started until it is shut down again.

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5
start on stopped ttyS0

stop on shutdown

respawn
exec /sbin/getty 19200 ttyS0 vt100
```

the bit "start on stopped ttyS0" restarts it if it crashes or exits or something.
Sometimes it takes a few seconds to restart, but it always restarts.

---

