---
title: "crontab bash script execution fails"
date: 2008-11-11
forum: General Help
---

### Post by combatwombat_nz on 2008-11-11
I am running the following script:
```

#!/bin/sh

cd /home/cw
SERVICE='qemu-system-x86_64 '
if ping 10.0.2.12 -c 5 -w 5 | grep 64 > /dev/null
    then 
    echo "$SERVICE can be pinged. Network up."
    else 
        echo "$SERVICE cannot be pinged. Network Down! "
        killall $SERVICE
        
    fi    
if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    echo "$SERVICE service running, everything is fine"
else
    echo "$SERVICE is not running"
    
    sh "/home/cw/xpstarter.sh"
fi

```It functions fine on its own, but under crontab running I get this result:
qemu-system-x86_64  cannot be pinged. Network Down! 
qemu-system-x86_64: no process killed
qemu-system-x86_64  is not running
QEMU PC emulator version 0.9.1, Copyright (c) 2003-2008 Fabrice Bellard
usage: qemu [options] [disk_image]

'disk_image' is a raw hard image image for IDE hard disk 0

Standard options:
-M machine      select emulated machine (-M ? for list)
-cpu cpu        select CPU (-cpu ? for list)...etc etc
-fda/-fdb file  use 'file' as floppy disk 0/1 image

--------------
xpstarter.sh follows:
#!/bin/sh
sh /home/cw/.profile
PARAMS="-M pc -smp 3 -m 3800 -hda /home/xp/xppro2.img -daemonize -net nic,macaddr=00:16:3e:00:00:01,model=e1000 -net tap,ifname=tap0 -boot c -hdd /home/xp/catdata.img -hdb /home/xp/plusf.img -nographic"
exec qemu-system-x86_64 $PARAMS
--------------
Why does the script work under CLI, not Cron?
The script is designed to keep a KVM of XP up.

TIA!

---

### Post by combatwombat_nz on 2008-12-16
The script fails because crontab has different path handling.

Change the line:

exec qemu-system-x86_64 $PARAMS

to

exec /usr/local/bin/qemu-system-x86_64 $PARAMS

or whereever it happens to live on your machine.

---

