---
title: "Dell E6500 Fingerprint"
date: 2013-01-05
forum: Hardware
---

### Post by TheNavigator on 2013-01-05
Hello. As of my knowledge, Dell E6500 has fingerprint reader implemented in the touchpad. I want to use that to login. I've tried installing that fprint-demo thing, but it said "drivers not detected" or something with the same meaning. Can't exactly remember.

Can someone help?

---

### Post by TheNavigator on 2013-01-06
Any help? :|

---

### Post by TheNavigator on 2013-01-07
Hello?...

---

### Post by Whoopie on 2013-01-07
You don't even provide useful information like "lsusb" output.

If your laptop is equipped with a VFS5011, then it's not supported by libfprint at the moment. But someone is working on it. -> [http://permalink.gmane.org/gmane.linux.fprint/2199](http://permalink.gmane.org/gmane.linux.fprint/2199)

BTW, you should be more patient. ;-)

---

### Post by TheNavigator on 2013-01-07
> **Whoopie said:**
> You don't even provide useful information like "lsusb" output.

If your laptop is equipped with a VFS5011, then it's not supported by libfprint at the moment. But someone is working on it. -> [http://permalink.gmane.org/gmane.linux.fprint/2199](http://permalink.gmane.org/gmane.linux.fprint/2199)

BTW, you should be more patient. ;-)
Well, I'm just bumping the topic :)

That's lsusb output.

```
nav@Eark:~$ lsusb
Bus 005 Device 002: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 006 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
nav@Eark:~$ 
```

And VFS5011? How can I know?

---

### Post by soccnut on 2013-01-07
Your fingerprint device is the 1st item in the list.

USB Vendor ID 0a5c
USB Product ID 5800

A check on [http://www.freedesktop.org/wiki/Software/fprint/libfprint/Supported%20devices](http://www.freedesktop.org/wiki/Software/fprint/libfprint/Supported%20devices) shows that it is currently unsupported

---

### Post by Whoopie on 2013-01-08
Here the Launchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/libfprint/+bug/602071](https://bugs.launchpad.net/ubuntu/+source/libfprint/+bug/602071)

And the upstream bug report: [https://bugs.freedesktop.org/show_bug.cgi?id=56752](https://bugs.freedesktop.org/show_bug.cgi?id=56752)

---

### Post by TheNavigator on 2013-01-19
It's not there in the list, I see :|

And it's 5800. Not 5801 :|

---

### Post by TheNavigator on 2013-01-27
Bump..

---

### Post by Whoopie on 2013-02-12
Experimental fingerprint reader support is available: [http://article.gmane.org/gmane.linux.fprint/2241](http://article.gmane.org/gmane.linux.fprint/2241)

---

