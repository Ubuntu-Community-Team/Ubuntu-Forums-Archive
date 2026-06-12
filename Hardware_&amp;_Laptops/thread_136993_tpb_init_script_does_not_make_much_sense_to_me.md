---
title: "tpb init script does not make much sense to me"
date: 2006-02-27
forum: Hardware &amp; Laptops
---

### Post by mority on 2006-02-27
Hi,

the file /etc/init.d/tpb looks like this:

```

#!/bin/sh
#

test -f /lib/lsb/init-functions || exit 1
. /lib/lsb/init-functions

case "$1" in
  start)
        /sbin/lsmod | /bin/grep nvram > /dev/null
        if [ $? != 0 ]
        then
                log_begin_msg "Loading nvram module"
                modprobe nvram
                log_end_msg 0
        fi
        ;;
  stop)
        ;;
  restart|force-reload)
        ;;
  *)
        echo "Usage: tpb {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0

```

So if you use it with ```
/etc/init.d/tpb start
``` it will just load the nvram module but not start the tpb program afterwards. I don't get what it's good for to load the modules and then not starting the program which I loaded the modules for in the first place. So I added ```
tpb -d
``` after the if-statement testing for the nvram module and now it works like I expected.

I would file a bug about this, but I don't know if I got something wrong. What's your opinion about this?

---

### Post by jimrz on 2006-03-04
I am having the same problem with tpb not working.
Not too good with code, so if yours is now working without issues, can you post your revised "/etc/init.d/tpb" so I can see exactly where to place cange.

Thanks

---

### Post by mority on 2006-03-07
[QUOTE=jimrz]I am having the same problem with tpb not working.
Not too good with code, so if yours is now working without issues, can you post your revised "/etc/init.d/tpb" so I can see exactly where to place cange.

Thanks[/QUOTE]

Sure:

```

#!/bin/sh
#

test -f /lib/lsb/init-functions || exit 1
. /lib/lsb/init-functions

case "$1" in
  start)
        /sbin/lsmod | /bin/grep nvram > /dev/null
        if [ $? != 0 ]
        then
                log_begin_msg "Loading nvram module"
                modprobe nvram
                log_end_msg 0
        fi
        # I just added this line to actually start the daemon.
        tpb -d
        ;;
  stop)
        ;;
  restart|force-reload)
        ;;
  *)
        echo "Usage: tpb {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0

```

This works for me. But I still have to start the daemon by hand with
```

/etc/init.d/tpb start

```
even though I have a symlink to the script in /etc/rc2.d/ to the start script:
```

mo@ash:/etc/rc2.d$ ls -l S99tpb
lrwxrwxrwx  1 root root 13 2006-02-25 20:15 S99tpb -> ../init.d/tpb

```

This still sucks but its better than nothing.

---

### Post by jimrz on 2006-03-08
Thank you! If you find any improvements please post here and I will do, as well.

---

### Post by glonn on 2006-11-11
The script mority improved isnt bad but the problem is because of it isn't startet with init... is that the user daemon (which starts the script) dont know where the binary tpb is and he has no rights to the nvram device. Also you must change the lines:  

in /etc/init.d/tpb

> 
instead of tpb -d ......../usr/bin/tpb -d
           killall tpb........./usr/bin/killall tpb


And then you have to edit the /etc/group  config file

you have add your user that should have access to the tpb to the groups nvram and thinkpad 
for example: 

> 
nvram:x:109:<yourusername>
thinkpad:x:109:<yourusername>



It is also possible that all is working if you do only the second part. I dont test it, but i think it's more secure to use the absolute path.


Sorry for bad english

---

