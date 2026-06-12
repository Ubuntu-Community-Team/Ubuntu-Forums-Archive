---
title: "Fans run fullspeed after wake from suspend ... 12.04.3 X64 / HP6910p / 3.8.0-33"
date: 2013-11-29
forum: Hardware
---

### Post by Scotsilv on 2013-11-29
Fans running fullspeed after suspend on fresh install of 12.04.3 (kernel 3.8.0-33) and HP6910p laptop, video Gallium 0.4 on ATI RV515, with latest HP BIOS for the machine (F.19).  Did not do this with 12.04.

I note the problem in other thread with other releases and laptops; the script suggested below saved as /etc/pm/sleep.d/99fancontrol.sh executable has **no effect.**

$ uname -a
Linux 6910p 3.8.0-33-generic #48~precise1-Ubuntu SMP Thu Oct 24 16:28:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


---------------------------------------[INDENT=2]
**Does not** fix the problem with 12.04.3 fan control on HP6910p

#!/bin/sh
#
#

case "$1" in
hibernate|suspend)
# Stopping is not required.
;;
thaw|resume)
# In background.
echo -n 0 > /sys/devices/virtual/thermal/cooling_device0/cur_state;
sleep 2
echo -n 0 > /sys/devices/virtual/thermal/cooling_device1/cur_state;
sleep 2
echo -n 0 > /sys/devices/virtual/thermal/cooling_device2/cur_state;

;;
*) exit $NA
;;
esac
[/INDENT]
[INDENT]
[/INDENT]
  

Is there a solution to the fanspeed problem?

---

### Post by Scotsilv on 2013-11-30
From [http://superuser.com/questions/229849/high-fan-speed-after-return-from-suspend-on-ubuntu](http://superuser.com/questions/229849/high-fan-speed-after-return-from-suspend-on-ubuntu), this has fixed the fan speed after resume problem:  /etc/pm/sleep.d/fancontrol.sh that looks like this:

-rwxr-xr-x 1 root root  228 Nov 30 09:07 99fancontrol.sh


#!/bin/sh

case "$1" in
        resume|thaw)
                for i in $(seq 0 13) ; 
                do 
                        echo "0" > /sys/devices/virtual/thermal/cooling_device${i}/cur_state
                done
;;
esac


I used 0 to 13 as my /sys/devices/virtual/thermal directory had this:

drwxr-xr-x  3 root root 0 Nov 30 03:54 cooling_device0
drwxr-xr-x  3 root root 0 Nov 30 03:54 cooling_device1
drwxr-xr-x  3 root root 0 Nov 30 03:54 cooling_device10
drwxr-xr-x  3 root root 0 Nov 30 03:54 cooling_device11
drwxr-xr-x  3 root root 0 Nov 30 03:54 cooling_device12
drwxr-xr-x  3 root root 0 Nov 30 03:54 cooling_device13
drwxr-xr-x  3 root root 0 Nov 30 03:54 cooling_device2
drwxr-xr-x  3 root root 0 Nov 30 03:54 cooling_device3
drwxr-xr-x  3 root root 0 Nov 30 03:54 cooling_device4
drwxr-xr-x  3 root root 0 Nov 30 03:54 cooling_device5
drwxr-xr-x  3 root root 0 Nov 30 03:54 cooling_device6
drwxr-xr-x  3 root root 0 Nov 30 03:54 cooling_device7
drwxr-xr-x  3 root root 0 Nov 30 03:54 cooling_device8
drwxr-xr-x  3 root root 0 Nov 30 03:54 cooling_device9


I see a number of posts about this workaround in various hardware/Ubuntu releases.  Hope a permanent fix is found.

---

