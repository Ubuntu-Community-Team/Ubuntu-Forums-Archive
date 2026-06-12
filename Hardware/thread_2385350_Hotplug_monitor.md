---
title: "Hotplug monitor"
date: 2018-02-19
forum: Hardware
---

### Post by jtodd.fr on 2018-02-19
I have dual monitor setup, which basically works fine. Sometime I need to move my laptop to different place, so I need to unplug the monitor and replug after coming back. The problem raises when I replug to dock station. Running udevadm shows that Ubuntu can detect monitor (with bunch of output info), and associated keyboards, mouse would function as usual. But the external monitor stays in black screen. 

My temp solution is manually check which monitor is connected by xrandr and then run command 
```

xrandr --output <external monitor> --left-of <laptop screen> --auto

```

So here are my questions: 

- Which information outputted by udevadm exactly specifies the monitors that is connected? And how can I get udev script (specified in RUN+) executed when monitor is plugged again?
There are tons of information outputted by udevadm (when unplug and plug) including add/ change/ remove, so I am not sure which one to capture (Solutions I found on the internet all already know which monitor to use, that doesn't solve my problem). Also I tested with following rule, but it doesn't work.
```

KERNEL=="card1", SUBSYSTEM=="drm", ACTION=="change", ENV{DISPLAY}=":0", ENV{XAUTHORITY}="/home/userA/.Xauthority", RUN+="/bin/bash /home/userA/bin/detect-monitor"

```
where detect-monitor append date if executed.
```

#!/bin/sh


d=`date`
echo "current time: $d" >> x.time



```
**card1** value comes from udevadm with udevadm monitor | grep change | grep drm`. And after replugging monitor, detect-monitor script doesn't get executed. 

Environment: Ubuntu 16.04 LTS, udevadm version 229. 

Thanks.

---

### Post by jtodd.fr on 2018-02-20
A stupid mistake. The problem is the  file path, i.e., x.time, should be absolute. So instead of `echo "..." >> x.time`, `echo "..." >> /path/to/x.time` fix the problem.

---

