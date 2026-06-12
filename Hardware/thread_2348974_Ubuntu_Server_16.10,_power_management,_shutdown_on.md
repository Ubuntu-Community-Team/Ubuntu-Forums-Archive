---
title: "Ubuntu Server 16.10, power management, shutdown on switch to AC?"
date: 2017-01-09
forum: Hardware
---

### Post by nraygun on 2017-01-09
Can someone point me in the right direction?
I'm playing with a laptop running Plex and Ubuntu Server 16.10 headless. I'd like for the laptop to shutdown properly when it goes to AC or some short time after going on AC.
I read around a bit and found some package that might be needed (acpid) are no longer recommended.

I'm guessing there's a config file somewhere in /etc that controls this.

Can anyone help?

---

### Post by nraygun on 2017-01-18
I think I got it.

I created a shell script as follows. Then I followed these directions on how to enable rc.local: [https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd](https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd)
I then edited /etc/rc.local to call the script.

Only thing I couldn't figure out is how to post to the login prompt that the system was going down. Tried wall and that didn't work.

Otherwise, it powers down gracefully upon removal of the AC adapter.
:)

checkpower.sh:
```
#!/bin/sh
while true
 do
    if ! on_ac_power; then    # System is not on main power
        sleep 10
        shutdown -h now
    fi
    sleep 300 # check main power status every 5 minutes
 done
```

/etc/rc.local:
```
#!/bin/sh
sh /home/plex/checkpower.sh &
exit 0
```

---

### Post by nraygun on 2017-01-20
I found an easier way to shutdown immediately on AC loss on the laptop I have running Ubuntu Server.

1. Create new rule in udev:
```
sudo nano /etc/udev/rules.d/50-ac-unplugged.rules
```

Contents:
```
SUBSYSTEM=="power_supply", ENV{POWER_SUPPLY_ONLINE}=="0", RUN+="/sbin/shutdown now"
```


2. Restart udev service:

```
sudo udevadm control --reload-rules
```

---

