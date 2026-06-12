---
title: "Pon isn't started at startup"
date: 2005-12-05
forum: General Help
---

### Post by NoHope on 2005-12-05
Hello all!

Since I've upgraded to Breezy Badger... my ppp conection (through ADSL) isn't be started at boot. any idea?

The scripts seems fine... I have S14ppp at rc2.d and ppp at init.d. The code for ppp script is:

```
#!/bin/sh -e
#
#   /etc/init.d/ppp: start or stop PPP link.
#
# This configuration method is deprecated, please use /etc/network/interfaces.

[ -x /usr/sbin/pppd -a -f /etc/ppp/ppp_on_boot ] || exit 0
if [ -x /etc/ppp/ppp_on_boot ]; then RUNFILE=1; fi
. /lib/lsb/init-functions

case "$1" in
start)
    log_begin_msg "Starting up PPP link..."
    if [ "$RUNFILE" = "2" ]; then
        /etc/ppp/pppoe_on_boot
    else
        pppd call provider
    fi
    log_end_msg $?
    ;;
stop)
    log_begin_msg "Shutting down PPP link..."
    if [ "$RUNFILE" = "2" ]; then
        poff -a
    else
        poff provider
    fi
    log_end_msg $?
    ;;
restart|force-reload)
    log_begin_msg "Restarting PPP link..."
    if [ "$RUNFILE" = "2" ]; then      
        poff -a || true
        sleep 5
        /etc/ppp/pppoe_on_boot
    else                  
        poff provider || true
        sleep 5
        pppd call provider
    fi
    log_end_msg $?
    ;;
*)
    log_success_msg "Usage: /etc/init.d/ppp {start|stop|restart|force-reload}"
    exit 1
    ;;
esac

exit 0
```

Any idea?

Thank you! Bye!

---

