---
title: "(Fixed) Dell Precision T1600 - Xubuntu 16.04 hangs on shutdown"
date: 2018-02-06
forum: Hardware
---

### Post by chaslinux on 2018-02-06
We have a couple of Dell Precision T1600 desktops with Xubuntu 16.04 installed and updated. When we shut down either of the systems they hang on the shutdown screen. Both have passed Memtest86+ RAM test and GSmartcontrol shows both drives are free of any SMART errors. It seems like some kind of incompatibility?

---

### Post by #&amp;thj^% on 2018-02-06
I had a friend with the same hang on shutdown, I quickly found it was due to "systemd"
What worked for that machine was:
I had a 'STOP JOB' running I reduced the timeout in" /etc/systemd/system.conf:"

```
sudo nano /etc/systemd/system.conf
```

remove # and change timings in the following lines:

```
DefaultTimeoutStartSec=5s
```

```
DefaultTimeoutStopSec=5s
```

Then run:

```
sudo systemctl daemon-reload
```

This worked for me.  Good Luck!

---

### Post by chaslinux on 2018-02-07
Thanks for the suggestion. These steps didn't seem to make a difference on our machines, but we did find a fix in an old (2012) Ubuntu bug report which suggested to add reboot=pci to grub.cfg.

---

