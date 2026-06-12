---
title: "[SOLVED] Acer Aspire One - dev.wifi0.ledpin error"
date: 2008-11-13
forum: Hardware
---

### Post by victorbrca on 2008-11-13
Anyone else getting this error on a Acer Aspire One with 8.04?

> error: "dev.wifi0.ledpin" is an unknown key

I log in, then my desktop is loading X crashes, takes me back to the terminal and displays the error right bellow /etc/rc.local. After that it
reloads XDM and repeats the whole step. At some point it stops doing that.

I have this on my rc.local, as instructed on the [Ubuntu Aspire one page]("https://help.ubuntu.com/community/AspireOne"):

```
cat /etc/rc.local
## Fix Wireless led
sysctl -w dev.wifi0.ledpin=3
sysctl -w dev.wifi0.softled=1

# Wifi kill switch
/usr/bin/setkeycodes e055 159
/usr/bin/setkeycodes e056 158

```

```
$ uname -r
2.6.24-21-generic

$ sudo sysctl -a | grep dev.wifi
error: permission denied on key 'kernel.sched_nr_migrate'
error: permission denied on key 'net.ipv4.route.flush'
error: permission denied on key 'net.ipv6.route.flush'

```

rc.local has a permission of 755.

Thanks,

Vic.

---

### Post by victorbrca on 2008-11-18
The problem was actually related to my xserver crashing. 

I found the following line on my logs:
```
gdm_slave_xioerror_handler: fatal x error
```

After more digging I found that this was related to ttf I d was using in my conky script.


Vic.

---

