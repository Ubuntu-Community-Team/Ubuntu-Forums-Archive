---
title: "Nvidia driver installed but lshw still shows nouveau, desktop freezing"
date: 2016-08-30
forum: Hardware
---

### Post by abefroman99 on 2016-08-30
Nvidia driver installed, via "Software and Updates"-->Additional Drivers, but lshw still shows nouveau

The nouveau driver is causing the desktop to freeze every 30 minutes or so, the mouse still moves.

```
$ sudo lshw -c video  |grep configuration
       configuration: driver=nouveau latency=0

```

How can I get that to show Nvidia?

---

### Post by #&amp;thj^% on 2016-08-30
Just checking only...but have you rebooted yet?

---

### Post by abefroman99 on 2016-08-30
Yes.

It seems nouveau is gone now, but the nvidia driver is no loaded, and I only have basic resolution and the dual monitors stopped working:
```
$ sudo lshw -c video  |grep configuration
       configuration: latency=0

```

---

### Post by #&amp;thj^% on 2016-08-30
What dose this report from the terminal
```
apt-cache policy nvidia
```
And one more please
```
inxi -G
```

---

### Post by abefroman99 on 2016-08-30
I messed something up and couldn't log in, so I reinstalled the OS and its work OK now.

```
$ lshw -c video |grep configuration
WARNING: you should run this program as super-user.
       configuration: driver=nvidia latency=0

```

---

