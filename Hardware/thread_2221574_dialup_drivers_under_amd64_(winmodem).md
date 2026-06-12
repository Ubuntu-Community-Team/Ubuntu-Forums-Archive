---
title: "dialup drivers under amd64 (winmodem)"
date: 2014-05-02
forum: Hardware
---

### Post by professor_jonny on 2014-05-02
I only have dialup internet available in my area and im wondering on dial up drivers in 14.04 amd64

as it is now multiarch can i use drivers for 32bit in my system or am i still needing 64 bit drivers ?

I ran the scan modem tool and it said that my modem was only supported under I386

there is source available for my modem would i just be able to recompile it with gcc or g++

 I have compiled a few apps and it was a relativly easy process (one being ddrescue 1.18 pre10)
would i need to extensivly patch varables/ strings etc and that sort of thing?

---

### Post by grahammechanical on 2014-05-02
You may find that various drivers for modems are already compiled into the kernel. We have installed by default something called GNU/Linux PPP Configuration Utility. It is a text-based utility that can be used with dial-up modems. I used to use it before I get broadband. In a terminal run

```
sudo pppconfig
```

It is still there in 14.04. I have just checked.

[http://manpages.ubuntu.com/manpages/gutsy/man8/pppconfig.8.html](http://manpages.ubuntu.com/manpages/gutsy/man8/pppconfig.8.html)

Check Alternative way 2.  I was running the dial-up modem off of a serial port so the device or com was /dev/ttyS0

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

Regards.

---

### Post by professor_jonny on 2014-05-02
sadily there is no device  driver built in, and support for any thing other than hardware modems are very limited.

---

