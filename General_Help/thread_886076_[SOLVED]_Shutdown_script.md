---
title: "[SOLVED] Shutdown script"
date: 2008-08-10
forum: General Help
---

### Post by Kain000 on 2008-08-10
Hey everyone,
I am interested in telling my server to boot up at 8am daily and to shutdown arround midnight when it wont be needed to save power.   So far I've gone into the Bios on the server and set the wake up event generator to 8am so that end works.

My question for you guys is this:

under system>admin>services I can see there are two programs (anacron and atd) there by default to handle scheduled tasks such as a shutdown, however I cannot find a place to input what tasks I want to schedule.  This leads me to believe that they are command line only, witch leaves me wondering how to input to them and what script I would need.

-I would like the shutdown time to be midnight 
-I would also like (if possible) to have an if-then sort of script to have the server first check for activity on port 5900 (vnc, so if i'm still awake and using the server it wouldn't just shut down) and 21 (in case anyone is downloading from the server) 
-----again if the above is possible, is there a way to say if there are active connections on those ports, retry in 5 mins?

thanks in advance
-sean

---

### Post by tuxxy on 2008-08-10
I use kshutdown for this, although this is GUI based.

---

### Post by damoxc on 2008-08-10
```
sudo netstat -ntap | awk '{print $4}' | sed -rn '/[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}:21/p' | wc -l
sudo netstat -ntap | awk '{print $4}' | sed -rn '/[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}:5900/p' | wc -l
```

Those 2 lines can be used to check the number of incoming connections.

I'll come up with a script that could be called by cron.d in a few minutes.

---

### Post by Kain000 on 2008-08-10
> **damoxc said:**
> ```
sudo netstat -ntap | awk '{print $4}' | sed -rn '/[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}:21/p' | wc -l
sudo netstat -ntap | awk '{print $4}' | sed -rn '/[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}:5900/p' | wc -l
```

Those 2 lines can be used to check the number of incoming connections.

I'll come up with a script that could be called by cron.d in a few minutes.

awesome, now how would I envoke cron?  As in anacron?

---

### Post by damoxc on 2008-08-10
```

#!/bin/sh

check_incoming()
{
    netstat -ntap 2> /dev/null | awk '{print $4}' | sed -rn "/[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}:$1/p" | wc -l 
}


do_shutdown()
{
    FTP=`check_incoming 21`
    VNC=`check_incoming 5900`
    if [ $FTP -gt 0 ] || [ $VNC -gt 0 ]; then
        sleep 300 
        do_shutdown
    else
        shutdown -h now 
    fi  
}

do_shutdown

```

This may want some testing but I believe this will do what you are after. Just place this in /usr/local/bin/shutdown.sh or something along those lines then stick a "shutdown" file in /etc/cron.d/ with the contents:
```

# m h dom mon dow user command
  0 0  *   *   *  root /bin/sh /usr/local/bin/shutdown.sh

```

---

### Post by Kain000 on 2008-08-10
thank you so much!
does this kind of script have a name?  I'm wondering where I can look to learn what commands bash understands and how I am sposted to weave them together like you just did to do things like shutdown.

---

### Post by damoxc on 2008-08-10
It's shell/bash scripting. Just do a google search on that.

[http://www.hsrl.rutgers.edu/ug/shell_help.html](http://www.hsrl.rutgers.edu/ug/shell_help.html)

Quick one threw up that page.

Other than that it's just learning to manipulate the command line programs and their output.

---

