---
title: "Major updating issue:"
date: 2008-11-16
forum: General Help
---

### Post by plantboy1 on 2008-11-16
I figured I would ask about this before I reinstalled grub.

On my system I removed all the startup links and everything in init.d for a few programs that I don't use, don't need, or don't want.  One of those was ufw.  Now, I didn't uninstall it, which was a very bad idea.  Every time I apt-get update i get an error saying that I need to run dpkg --configure -a, which I've tried.  It fails every time since it was a system update that failed at ufw, since it couldn't find it in init.d.  Any apt-get command exits and refuses to do anything until the issue is fixed.  Is there a way to fix this?

---

### Post by fooman on 2008-11-16
just to make sure....when you ran "dpkg --configure -a",  you did put a "sudo" in front right? ...like this:

```
sudo dpkg --configure -a
```

---

### Post by plantboy1 on 2008-11-16
Yeah, I always do.  It's not that, it goes and tries to do w/e, but fails at ufw.  It's not a sudo issue :p I know that much

---

### Post by Monotoko on 2008-11-16
Can you not just put whatever it was you removed back in init.d? If you havent installed it, that should work, right?

---

### Post by plantboy1 on 2008-11-16
How would I put it back?  I did the whole "sudo rm ufw" thing there.

---

### Post by adult swim on 2008-11-16
here is my ufw file
```
#!/bin/sh -e

### BEGIN INIT INFO
# Provides:          ufw
# Required-Start:    mountall.sh
# Required-Stop:     
# Default-Start:     S
# Default-Stop:      
# Short-Description: start firewall
### END INIT INFO

PATH="/sbin:/bin:/usr/sbin:/usr/bin"

[ -x /usr/sbin/ufw ] || exit 0

. /lib/lsb/init-functions

if [ -s /etc/default/ufw ]; then
    . /etc/default/ufw
else
    log_failure_msg "Could not find /etc/default/ufw (aborting)"
    exit 1
fi
if [ -s /etc/ufw/ufw.conf ]; then
    . /etc/ufw/ufw.conf
else
    log_failure_msg "Could not find /etc/ufw/ufw.conf (aborting)"
    exit 1
fi

RULES_PATH="/etc/ufw"
USER_PATH="/var/lib/ufw"

case "$1" in
start)
    if iptables -L ufw-user-input -n >/dev/null 2>&1 ; then
        # if firewall loaded, tell to reload instead
        log_action_msg "Firewall already started, use 'force-reload'"
        exit 0
    fi
    if [ "$ENABLED" = "yes" ] || [ "$ENABLED" = "YES" ]; then
        log_action_begin_msg "Starting firewall:" "ufw"
        for m in $IPT_MODULES
        do
            modprobe $m || true
        done

        execs="iptables"

        # IPv6 setup
        if [ "$IPV6" = "yes" ] || [ "$IPV6" = "YES" ]; then
            if ip6tables -L INPUT >/dev/null 2>&1; then
                execs="$execs ip6tables"
            else
                log_action_cont_msg "Problem loading ipv6 (skipping)"
            fi
        else
            if ip6tables -L INPUT >/dev/null 2>&1; then
                # IPv6 support disabled but available in the kernel, so
                # default DROP and accept all on loopback
                ip6tables -F || error="yes"
                ip6tables -X || error="yes"
                ip6tables -P INPUT DROP || error="yes"
                ip6tables -P OUTPUT DROP || error="yes"
                ip6tables -P FORWARD DROP || error="yes"
                ip6tables -A INPUT -i lo -j ACCEPT || error="yes"
                ip6tables -A OUTPUT -o lo -j ACCEPT || error="yes"
                if [ "$error" = "yes" ]; then
                    log_action_cont_msg "Problem setting default IPv6 policy"
                fi
            fi
        fi

        for exe in $execs
        do
            type=""
            if [ "$exe" = "ip6tables" ]; then
                type="6"
            fi
            BEFORE_RULES="$RULES_PATH/before${type}.rules"
            AFTER_RULES="$RULES_PATH/after${type}.rules"
            USER_RULES="$USER_PATH/user${type}.rules"

            # flush the chains
            $exe -F || error="yes"
            $exe -X || error="yes"

            # setup built-in chains' default policy
            $exe -P INPUT $DEFAULT_INPUT_POLICY || error="yes"
            $exe -P OUTPUT $DEFAULT_OUTPUT_POLICY || error="yes"
            $exe -P FORWARD $DEFAULT_FORWARD_POLICY || error="yes"

            # setup some other chains that can be used later
            if [ "$type" != "6" ]; then
                $exe -N ufw${type}-not-local || error="yes"
            fi

            # setup ufw${type}-before-* chains
            $exe -N ufw${type}-before-input || error="yes"
            $exe -N ufw${type}-before-output || error="yes"
            $exe -N ufw${type}-before-forward || error="yes"
            $exe -A INPUT -j ufw${type}-before-input || error="yes"
            $exe -A OUTPUT -j ufw${type}-before-output || error="yes"
            $exe -A FORWARD -j ufw${type}-before-forward || error="yes"
            if [ -s "$RULES_PATH" ]; then
                if ! $exe-restore -n < $BEFORE_RULES ; then
                    log_action_cont_msg "Problem running '$BEFORE_RULES'"
                    error="yes"
                fi
            else
                log_action_cont_msg "Couldn't find '$BEFORE_RULES'"
            fi

            # setup ufw${type}-user chain
            if [ -s "$USER_PATH" ]; then
                $exe -N ufw${type}-user-input || error="yes"
                $exe -N ufw${type}-user-output || error="yes"
                $exe -N ufw${type}-user-forward || error="yes"
                $exe -A ufw${type}-before-input -j ufw${type}-user-input || error="yes"
                $exe -A ufw${type}-before-output -j ufw${type}-user-output || error="yes"
                $exe -A ufw${type}-before-forward -j ufw${type}-user-forward || error="yes"
                if ! $exe-restore -n < $USER_RULES ; then
                    log_action_cont_msg "Problem running '$USER_RULES'"
                    error="yes"
                fi
                # don't include the RETURN lines here, as they will
                # be in the USER_PATH file
            fi

            # now return from the chain
            $exe -A ufw${type}-before-input -j RETURN || error="yes"
            $exe -A ufw${type}-before-output -j RETURN || error="yes"
            $exe -A ufw${type}-before-forward -j RETURN || error="yes"

            # setup ufw${type}-after-* chains
            $exe -N ufw${type}-after-input || error="yes"
            $exe -N ufw${type}-after-output || error="yes"
            $exe -N ufw${type}-after-forward || error="yes"
            $exe -A INPUT -j ufw${type}-after-input || error="yes"
            $exe -A OUTPUT -j ufw${type}-after-output || error="yes"
            $exe -A FORWARD -j ufw${type}-after-forward || error="yes"
            if [ -s "$AFTER_RULES" ]; then
                if ! $exe-restore -n < $AFTER_RULES ; then
                    log_action_cont_msg "Problem running '$AFTER_RULES'"
                    error="yes"
                fi
            else
                log_action_cont_msg "Couldn't find '$AFTER_RULES'"
            fi
            $exe -A ufw${type}-after-input -j RETURN || error="yes"
            $exe -A ufw${type}-after-output -j RETURN || error="yes"
            $exe -A ufw${type}-after-forward -j RETURN || error="yes"
        done

        if [ ! -z "$IPT_SYSCTL" ] && [ -s "$IPT_SYSCTL" ]; then
            sysctl -e -q -p $IPT_SYSCTL || true
        fi

        if [ "$error" = "yes" ]; then
            log_action_end_msg 1
            exit 1
        else
            log_action_end_msg 0
        fi
    else
        log_action_begin_msg "Skipping firewall:" "ufw (not enabled)"
        log_action_end_msg 0
    fi
    ;;
stop)
    log_action_begin_msg "Stopping firewall:" "ufw"
    error=""

    execs="iptables"
    if ip6tables -L INPUT >/dev/null 2>&1; then
        execs="$execs ip6tables"
    fi

    for exe in $execs
    do
        $exe -F || error="yes"
        $exe -X || error="yes"
        $exe -P INPUT ACCEPT || error="yes"
        $exe -P OUTPUT ACCEPT || error="yes"
        $exe -P FORWARD ACCEPT || error="yes"
    done

    if [ "$error" = "yes" ]; then
        log_action_end_msg 1
        exit 1
    else
        log_action_end_msg 0
    fi
    ;;
restart|force-reload)
    if [ "$ENABLED" = "yes" ] || [ "$ENABLED" = "YES" ]; then
        $0 stop
        $0 start
    else
        log_warning_msg "Skipping $1 (not enabled)"
    fi
    ;;
status)
    err=""
    iptables -L ufw-user-input -n >/dev/null 2>&1 || {
        log_failure_msg "Firewall is not running"
        exit 3
    }

    if [ "$IPV6" = "yes" ] || [ "$IPV6" = "YES" ]; then
        ip6tables -L ufw6-user-input -n >/dev/null 2>&1 || {
            # unknown state: ipv4 ok, but ipv6 isn't
            log_failure_msg "Firewall in inconsistent state (IPv6 enabled but not running)"
            exit 4
        }
    fi

    log_success_msg "Firewall is running"
    ;;
*)
    echo "Usage: /etc/init.d/ufw {start|stop|restart|force-reload|status}"
    exit 1
    ;;
esac

exit 0


```
put it in a file ufw in init.d
then youll want to run ```
update-rc.d ufw defaults
```
and youll need it to be executable so ```
cd /etc/init.d
chmod +x ufw
```
you may need to restart to take care of it

---

### Post by plantboy1 on 2008-11-16
Didn't need it, I figured out online how to completely remove ufw which is what I wanted to do in the first place.  I ran "sudo dpkg --remove --force-remove-reinstreq ufw"

---

