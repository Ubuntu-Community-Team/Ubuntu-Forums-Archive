---
title: "Dell Vostro 1500 builtin webcam with skype"
date: 2009-11-14
forum: Hardware
---

### Post by grj23 on 2009-11-14
Hi beautiful people

I have a Dell Vostro 1500 running Ubuntu 9.10.  Works beautifully, I must say.

I've installed skype (yes I know it's not open source!), and it too works well in general.  All of this happened with the minimum of effort.  Wonderful.  (I used the medibuntu repos).

The one minor problem, is that whenever I switch on the webcam during a skype call, skype immediately closes and needs to be restarted.  The little blue light next to the webcam comes on for a split second and then it all goes.  It restarts without any problem.

Incidentally I don't know how to test the webcam other than with skype?  Is there a program I can use?

Ta

---

### Post by grj23 on 2009-11-16
Hi.  I just ran lsusb and got the following:
```

grj23@dell-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I don't really know what that means, but gathered from various forums that it might mean something to someone out there...):P

---

### Post by grj23 on 2009-11-16
Hi.

I downloaded cheese, and the webcam appears to work fine there.

So perhaps it's a skype problem.

Mmm.  Will have to try it again later...

---

