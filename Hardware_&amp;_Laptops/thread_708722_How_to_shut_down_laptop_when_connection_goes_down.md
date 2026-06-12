---
title: "How to shut down laptop when connection goes down"
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by Trymic on 2008-02-26
I was wondering if there is a way, script, to shutdown my pc when my connection is not working. My router is not working properly so when i not home there is no point my laptop working if i let it on for downloading

Any ideas?

---

### Post by PinkFloyd102489 on 2008-02-26
If I werent at work, I could whip you up a script to work with cron that would ping the router every few minutes and then shutdown based on the return.

Maybe someone else could do similar.

---

### Post by PinkFloyd102489 on 2008-02-26
Alright, this is something that Im writing on the fly and it might be a little bit crude. Im sure there's a better alternative, but here goes.


Adding to root crontab:
```

sudo crontab -e

#Add the following line, then save/exit.

0,10,20,30,40,50 *  * * *  /home/[COLOR="Red"]USER[/COLOR]/ping

```

Replace USER with your username. This will run the check every 10 minutes.



Now make a file in your home directory called ping. Then add this to it.

```

#!/bin/bash

ping -nqc 4 192.168.1.1 > /home/[COLOR="Red"]USER[/COLOR]/tmpping

$STATUS='grep -c "100%" /home/[COLOR="Red"]USER[/COLOR]/tmpping`

if [ "$STATUS" == "1" ]; then shutdown -hP now
else exit
fi

rm /home/[COLOR="Red"]USER[/COLOR]/tmpping

```


Replace the red USER with your username. Also if your router IP address is different, replace it with the correct address. "chmod +x ping" in the directory to set it as executable.

---

### Post by Trymic on 2008-02-27
thanks for your reply. I would try it in few days since i don't have access to my laptop since is gone for repairing

---

