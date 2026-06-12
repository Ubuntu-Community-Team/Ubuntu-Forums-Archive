---
title: "Callhome script run on startup ?"
date: 2008-08-06
forum: General Help
---

### Post by dbee on 2008-08-06
I want to fit my laptop with a callhome script that will run on startup. I want it to run before the user has to log into the actual system. It's basically an anti-theft device and i'm assuming any thief that boots up the system and then sees the ubuntu login would automatically just wipe the drive and put windows on there.

I tried placing 
```

wget -O /dev/null http://myserver.com/callhome.html

```

in /etc/rc.local, but apparently Ubuntu/Debian doesn't use this on system startup ? 

Instead I created a start up script ...
```

#!/bin/sh

# Script to call home on system startup
OPTIONS=""

PATH=/sbin:/bin:/usr/sbin:/usr/bin

start () {
        echo -n "Starting domain name service: callhome"
         wget -O /dev/null http://myserver.com/callhome.html
        echo "."
}

stop () {
        echo "."
}

case "$1" in
    start)
        start
    ;;

    stop)
        stop
    ;;

    restart|force-reload)
        stop
        sleep 2
        start
    ;;
    
    reload)
    ;;

    *)
        exit 1
    ;;
esac

exit 0

``` 
then i placed it in multiuser startup ( without stopping ) mode ...
```

update-rc.d callhome multiuser

```
then i tested it 
```

/etc/init.d/callhome start

```

problem is that it isn't working (ie. it's not leaving any traces on my logs when i start up my system ).

Also pls note. I don't want to use crontab for this task as i don't see how it can be used properly ....

Thanks,

---

### Post by caljohnsmith on 2008-08-06
Just a thought, but I think your original idea of sticking it in /etc/rc.local is the simplest. That rc.local script should be run on startup before the user logs in, so I wouldn't know why it doesn't seem to be executing for you. I would test it with something really simple by putting the following as the first command in rc.local:
```
touch /home/<username>/Desktop/rc.local_executed_OK
```
That will tell you if rc.local is being executed. I suspect your problem is other than rc.local not getting executed.

---

### Post by Vivaldi Gloria on 2008-08-06
/etc/rc.local should run without a problem. If it's not running then try commands of the sort

```
sudo update-rc.d rc.local defaults 
sudo update-rc.d rc.local multiuser 
```

See

```
man update-rc.d 
```

for more info. First use with the flag

```
-n     Don’t do anything, just show what we would do.
```

---

### Post by Vivaldi Gloria on 2008-08-06
Also maybe it's better to put your script in

```
/etc/network/if_up.d/your_script
```

The scipts here are run when a network connection is started.

---

