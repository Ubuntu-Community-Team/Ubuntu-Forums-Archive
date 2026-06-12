---
title: "Some monitors won't work with intel hd5500?"
date: 2016-06-14
forum: Hardware
---

### Post by chefarov2 on 2016-06-14
I have recently got a Dell Latitude e5550 with ubuntu 15.04 preinstalled. Currently I have ubuntu 16.04 with kernel 4.4.0-24-generic.

My issue is that connecting my LG TV (which was working normally with my previous laptop), through hdmi, the monitor isn't detected neither by display settings nor by:
```
:~$ xrandr
HDMI1 disconnected (normal left inverted right x axis y axis)
```

/etc/X11/xorg.conf does not exist, and trying to generate one while the monitor is connected:
```
 :~$ sudo Xorg -configure
(EE) 
Fatal server error:
(EE) Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.
(EE) ...

```


The strange thing is that I borrowed a Samsung PC monitor and it's **working normally** (hdmi) with the current laptop!


Any Ideas how can I debug this peculiar selective compatibility issue?

---

### Post by chefarov2 on 2016-06-18
I was wrong. It was probably Tv/Monitor's issue... thus closing the thread.

---

