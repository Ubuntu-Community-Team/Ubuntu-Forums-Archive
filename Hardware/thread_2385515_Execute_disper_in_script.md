---
title: "Execute disper in script"
date: 2018-02-21
forum: Hardware
---

### Post by jtodd.fr on 2018-02-21
Manually executing commands `disper -s` and `disper -d auto -e -t left` works when external monitor is unplugged and plugged. But it doesn't work when placing those commands in the script to get executed when the udev event gets triggered (external monitor still stays black when `disper -d auto -e -t left` is executed by the script).
 
My udev rules (/etc/udev/rules.d/98-monitor-hotplug.rules)
```

KERNEL=="card?", SUBSYSTEM=="drm", ACTION=="change", ENV{DISPLAY}=":0", ENV{XAUTHORITY}="/home/user/.Xauthority", RUN+="/home/user/bin/detect-monitor"

```

And the script
```

LOG_DIR="/home/user/logs"
LOG_PATH="$LOG_DIR/monitor-hotplug.log"


if [ ! -d "/home/user/logs" ]; then
  mkdir -p "$LOG_DIR"
  touch "$LOG_PATH"
fi


cat /dev/null > "$LOG_PATH"


USER=user


export DISPLAY=:.0
export XAUTHORITY="/home/user/.Xauthority"


count=`for i in $(find /sys/class/drm/*/status); do cat $i | grep -w connected; done | wc -l`
  
if [ "1" = "$count" ]; then
  echo "[INFO] Only $count monitor available!" >> "$LOG_PATH"
  
  sudo -u $USER -E bash -c "disper -s"
elif [ "2" = "$count" ]; then
  echo "[INFO] $count monitors available!" >> "$LOG_PATH"
  
  sudo -u $USER -E bash -c "disper -d auto -e -t left"
else
  echo "[WARN] \"$count\" monitors found!" >> "$LOG_PATH"
fi



```

What causes the different results between executing script by udev event, and manual command execution? And how to get it work (execute disper in script by udev event)?

---

### Post by jtodd.fr on 2018-02-21
It looks like when executing with `disper -u $USER -E bash -c "disper -d auto -e -t left"`, disper complains 'no suitable backend' or something. Changing to use following script basically fix my problem. 

From my observation. Basically two issues (Can't be sure if my reckoning is correct or not):
1. write udev rules 
2. X environment variable (DISPLAY, and XAUTHORITY)
3. disper command

```

KERNEL=="card?", SUBSYSTEM=="drm", ACTION=="change", ENV{DISPLAY}=":0", ENV{XAUTHORITY}="/home/user/.Xauthority", RUN+="/path/to/disper-script"

```


```

#!/bin/sh

LOG_DIR="/home/userA/logs"
LOG_PATH="$LOG_DIR/monitor-hotplug.log"

if [ ! -d "/home/userA/logs" ]; then
  mkdir -p "$LOG_DIR"
  touch "$LOG_PATH"
fi

cat /dev/null > "$LOG_PATH"

USER=userA

XPID=`pgrep X | head -n 1`

XCOMMANDLINE="ps --no-header -o command $XPID"
export DISPLAY=`$XCOMMANDLINE | sed 's/.\+:/:/;s/ \+.*//'`
export XAUTHORITY=`$XCOMMANDLINE | sed 's/.*-auth *//;s/ \+-.*//'`
DISPER="disper"
echo "DISPLAY is set to $DISPLAY" >> $LOG_PATH
echo "XAUTHORITY is set to $XAUTHORITY" >> $LOG_PATH


sudo -u $USER disper -e


```

Edit: The link [https://bugs.launchpad.net/disper/+bug/330258](https://bugs.launchpad.net/disper/+bug/330258) might provides some info.

---

