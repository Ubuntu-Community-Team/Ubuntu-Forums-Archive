---
title: "Missing LSB Information (Start Script Install)"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by wurzelbert on 2009-11-04
Hey everybody,

i tried to install domino server 8.5 on ubuntu. It all works perfectly, but now i wanted to install a start script ([http://www.danilodellaquila.com/blog/how-to-install-lotus-domino-8.5-on-ubuntu-part-ii](http://www.danilodellaquila.com/blog/how-to-install-lotus-domino-8.5-on-ubuntu-part-ii)) that makes the server start automatically. 
i downloaded the script, untared it and step "**6.5** Register the script as service for automatic startup" didn't quite work:
I always get errormessages:
"update-rc.d: warning: /etc/init.d/domino missing LSB information
update-rc.d: see <http://wiki.debial.org/LSBinitScripts>
Sytem startup links for /etc/init.d/domino already exist.

hope you can help me
greetz

---

### Post by Albert Net on 2010-02-16
Quite similar issues with mine.

I am still trying to find something information.

PS:If you solve your problem, please post it out.

---

### Post by mathman145 on 2010-02-21
I have the same problem , answer please!

---

### Post by mtb-cliff on 2010-02-24
I too have the same problem. When I go to the link identified in the error [http://wiki.debian.org/LSBInitScripts](http://wiki.debian.org/LSBInitScripts) I simply become confused at to how I am supposed to modify the script. In my case the script is simply to start WOL, however the warning doesn't seem to stop anything. Future configurations will likely need to have the init scripts changed to meet the required configuration. It would be nice to have a few more examples to understand how we supposed to make the changes correctly.

---

### Post by wittgeinstein on 2010-05-18
Hello.


I had the same problem: I had written a script e.g. **mystartupscript** and then I have done the following:

```
user@computer:/etc/init.d$ sudo update-rc.d mystartupscript defaults
```Then after some time I modified my script and thought to have to do this again. So I again wrote ... 

```
user@computer:/etc/init.d$ sudo update-rc.d mystartupscript defaults
```... and so I got the mysterious failure:

```
[COLOR=Red]update-rc.d: warning: /etc/init.d/mystartupscript missing LSB information[/COLOR]
```
I have **solved** the problem as follows:

```
user@computer:/etc/init.d$ sudo update-rc.d -f mystartupscript remove
user@computer:/etc/init.d$ sudo update-rc.d mystartupscript defaults

```

And don't forget to make the script executable:
```
user@computer:/etc/init.d$ sudo chmod +x ./mystartupscript
```


I hope it can help you.


Cheers,
wittgeinstein

---

### Post by ppatrick on 2010-10-06
to really get rid of the warning we have to add the corresponding script header as described here...
[http://wiki.debian.org/LSBInitScripts](http://wiki.debian.org/LSBInitScripts)

```
### BEGIN INIT INFO
# Provides:          scriptname
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start daemon at boot time
# Description:       Enable service provided by daemon.
### END INIT INFO
```

---

### Post by Rocko262c on 2011-07-16
Dear Everyone,

I was having a similar problem and I inserted the header as PPatrick had suggested.  That cleared the LSB problem, but I still can't get my script to run at all.

I have a laptop with a monitor attached to it and I want to make the monitor my primary screen.  This script works and can be execute to do so, here is my script:
### BEGIN INIT INFO
# Provides:          scriptname
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start daemon at boot time
# Description:       Enable service provided by daemon.
### END INIT INFO
#!/bin/bash
NR_OF_MONITORS=$(xrandr -d :0 -q | grep ' connected' | wc -l)
if [ $NR_OF_MONITORS = "2" ]; then
xrandr --output VGA1 --primary
fi

I make sure to enter the following commands every time I made adjustments to the script
sudo update-rc.d -f local.autostart remove
sudo chmod +x /etc/init.d/local.autostart
sudo update-rc.d local.autostart defaults 80

After all this I reboot the computer and login, but after I login the script doesn't run.

Further more, when I type "who -r", the output is "run-level 2  2011-07-16 21:35", so the above should work, I just can't figure out why.

Can anyone help?

Cheers,
Rocko262c

---

### Post by Rocko262c on 2011-07-16
I found a much simpler way. I just entered the script under System->Preferences->Startup Applications.

---

### Post by dilis on 2012-03-24
Yes but if you runin UBUNTU without any KDE or other interface???

---

### Post by Rocko262c on 2012-03-25
> **dilis said:**
> Yes but if you runin UBUNTU without any KDE or other interface???


Dear Dilis,

Then I would suggest getting the startup script to run upon start up. I was unable to accomplish this.

Cheers,
Rocko262c

---

