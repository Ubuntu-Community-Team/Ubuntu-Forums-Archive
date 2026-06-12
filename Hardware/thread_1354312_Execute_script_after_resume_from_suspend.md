---
title: "Execute script after resume from suspend"
date: 2009-12-13
forum: Hardware
---

### Post by govt_cheese on 2009-12-13
Running 9.10 on Thinkpad T61p:
With the changes to PM/ACPI when moving from 9.04 -> 9.10, I am unable to find an obvious method of executing a script when the box comes out of suspend. Seems like this would be a no-brainer, and pardon me if the question has been axed before, but I can't for the life of me find anything on setting this up.

---

### Post by meijer.o on 2009-12-14
Dear linux user,

Place your scripts in /etc/pm/sleep.d

They must have a special format

This is an example,

--------------------------------
#!/bin/sh
# to unload modules before suspend
# this script makes hibernate work properly on a eeepc 1000h and 2.6.31.5


PATH=/sbin:/usr/sbin:/bin:/usr/bin



case "${1}" in
        hibernate)
modprobe -r psmouse
modprobe -r rt2860sta 
                echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind

               
 ;;
        thaw)
               	echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
modprobe psmouse
                ;;
esac

---

