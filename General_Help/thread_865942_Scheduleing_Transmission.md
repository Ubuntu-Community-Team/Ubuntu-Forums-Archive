---
title: "Scheduleing Transmission"
date: 2008-07-21
forum: General Help
---

### Post by ttboyd on 2008-07-21
Hi Im a little new at all this and was wondering how I can schedule the torrent client 'transmission' to come on at 12am and stop at 8am. So it comes on and carries on with any downloads then stops, my internet plan allows free traffic between these hours.  

Cheers

---

### Post by justleen on 2008-07-21
i dont think you can schedul within transmission itself, but you could make a start/stop script, and run that true cron
start script:```

!#/bin/bash
nohup transmission  & 
``` (the nohup "disconnects" it from your current login, so you can even logout)

stop script (as example): ```

!#/bin/bash 
pid=`ps -ef|grep transmission|awk '{print $2}'`
kill -9 $pid 
```
 
cronttab:
```

1 0 * * * /usr/local/bin/transmission_start.sh
1 8 * * * /usr/local/bin/transmission_stop.sh

```
will start the script @00:01 and stop @08:01

---

