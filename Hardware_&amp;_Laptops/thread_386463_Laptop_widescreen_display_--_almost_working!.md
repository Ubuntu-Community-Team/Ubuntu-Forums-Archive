---
title: "Laptop widescreen display -- almost working!"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by ott0 on 2007-03-17
My laptop has a 1280 x 768 display. I got installed the 915resolution package to edit the vbios to add 1280x768 support. If I run 915resolution and then restart X it works great!

But I can't get 915resolution to run automatically at startup. I don't understand how startup works in linux so I have to ask here :confused: 

The package added this script: /etc/init.d/915resolution

```
#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
PROG=/usr/sbin/915resolution
NAME=915resolution
DESC=915resolution

test -x $DAEMON || exit 0

# Include 915resolution defaults if available
if [ -f /etc/default/915resolution ] ; then
        . /etc/default/915resolution
fi
if [ "$MODE" = "" ] || [ "$XRESO" = "" ] || [ "$YRESO" = "" ] ; then
   echo "*** Your 915resolution hasn't been configured! ***"
   echo "Please read /usr/share/doc/915resolution/README.Debian and define"
   echo "MODE, XRESO, and YRESO."
   exit 0
fi

set -e

case "$1" in
  start)
        echo -n "Starting $DESC: "
        $PROG $MODE $XRESO $YRESO $BIT
        echo "$NAME."
        ;;
  stop)
        #echo -n "Stopping $DESC: "
        #echo "$NAME."
        ;;
  restart|force-reload)
        #echo -n "Stopping $DESC: "
        #echo "$NAME."
        echo -n "Starting $DESC: "
        $PROG $MODE $XRESO $YRESO $BIT
        echo "$NAME."
        ;;
  *)
        N=/etc/init.d/$NAME
        # echo "Usage: $N start" >&2
        echo "Usage: $N start" >&2
        exit 1
        ;;
esac

exit 0

```

My /etc/default/915resolution is filled out so it seems like it should work..
```
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE
# 
MODE=58
#
# and set resolutions for the mode.
#
XRESO=1280
YRESO=768
#
# We can also set the pixel mode.
# Please note that this is optional,
# you can also leave this value blank.
BIT=

```

So... can anyone help me understand why it's not working? I assume it's just not running the 915resolution script at startup because like I said if I run it manually later it works great.

Thanks!

---

### Post by ott0 on 2007-03-17
I updated it to the latest version with the package manager and now it works.

Super.

---

