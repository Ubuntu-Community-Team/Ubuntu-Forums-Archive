---
title: "Shutdown"
date: 2008-10-11
forum: General Help
---

### Post by cmani on 2008-10-11
Ubuntu 8.04 the shutdown is not always succeed, there is no regular pattern, sometimes i get the progress bar while shutdown, sometimes the screen went blank and need to shutdown by removing power. Is there is any log where can i find the root cause of error.  Is there is any configuration or patches to be applied to over come this.

Pl. advice.

---

### Post by chrone on 2009-02-15
i'm having the same problem, sometimes it shuts properly, often it hangs. lock the gdm but i can still moving mouse but could not click any. :(

---

### Post by eljalill on 2009-03-12
I'm having the exact same problem as the OP: The computer sometimes crashes when I shut down, and there is just a black screen, the fan runs wildly (but there seems to be no harddisk action) and nothing happens even with skinny elephants. It sometimes also happens when I restart the desktop. 

Is there really no-one out there who can even help with troube shooting? I really have no idea where to start looking for the solution!

Would also be really grateful for advice!

---

### Post by robert.rankin.jr on 2009-03-12
> Try this:
Press alt+f2,
type in
```
sudo gedit /etc/init.d/alsa-utils
```

The file opens in Gedit and around line 353 you'll find the instruction "stop)". Below this instruction you should add these two instructions:

ifconfig wlan0 down
ifconfig eth0 down

So, the file should be this way:

stop)
ifconfig wlan0 down
ifconfig eth0 down
EXITSTATUS=0 

If that doesn't work to fix it, please post a copy of your /var/log/syslog and a copy of the output the command 'lspci'.

Robert

---

