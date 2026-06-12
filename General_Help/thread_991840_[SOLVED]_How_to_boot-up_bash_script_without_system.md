---
title: "[SOLVED] How to boot-up bash script without system freeze?"
date: 2008-11-24
forum: General Help
---

### Post by abcuser on 2008-11-24
Hi,
on Ubuntu 8.10 I would like to write a boot script thats will start [bash script which has while...do infinitive loop inside.](http://ubuntuforums.org/showthread.php?p=6222577)

For boot script I have saved the following bash script to /etc/init.d/ directory and name it 'cpulimit'.
```

#!/bin/sh
#
# Script to start CPU limit daemon
#
set -e
. /lib/lsb/init-functions
case "$1" in
start)
/root/cpucontrol.sh
;;
stop)
echo Write commands to stop.
;;
esac
exit 0
```

I changed user and group to root:
sudo chown root:root cpulimit

I changed permissions:
sudo chmod 755 cpulimit

Updated rc.d:
sudo update-rc.d cpulimit defaults

And reboot. Ubuntu starts up, but freezes at boot process. (I know how to solve this problem from recovery console). I also know the boot process freezes because it is waiting infinitive while...do loop to finish.

So, I would like to start cpulimit bash script with every boot process in such a way boot process would not frozen. **Is there any command to start script, but continue without waiting script to finish**? Just like on Windows using command "start command".
Regards,
Abcuser

---

### Post by __Ryan__ on 2008-11-24
You can add an ampersand here:

```
/root/cpucontrol.sh &
```

This will make the script execute in the background and allow the current script to continue.

---

