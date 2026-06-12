---
title: "Creative Technology Webcam (041e:4058) not working properly in Precise 12.04"
date: 2012-05-19
forum: Hardware
---

### Post by maxweld on 2012-05-19
I have a fresh install of Precise 64bit. The webcam which has worked in previous versions seems not to want to cooperate.
I have used Cheese to see if I can get an image. It seems to have some recognition of the webcam, as the webcam lights up to show it is active but there is no picture. Cheese just shows a black screen.

```
>> lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 005 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 003: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 005: ID 041e:4058 Creative Technology, Ltd Live! Cam Optia AF
Bus 002 Device 006: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 004: ID 046d:c52e Logitech, Inc. 
```

Any suggestions would be appreciated.

---

### Post by bmullan on 2012-05-22
I just pulled my Logitech Optia AF out of a drawer and tried it yesterday and I have the same problem

With Cheeze the blue ring led lights as if the web cam is on but there is no picture.

Still looking to find out whats wrong myself.

---

### Post by bmullan on 2012-05-23
same bug/problem with Redhat:

[https://bugzilla.redhat.com/show_bug.cgi?id=739448]("https://bugzilla.redhat.com/show_bug.cgi?id=739448")
Re: 3.1/3.2 uvcvideo and Creative Live! Cam Optia AF

Hi Josh,

On Wednesday 29 February 2012 17:58:52 Josh Boyer wrote:
> Hi Laurent,
> 
> We've had a bug report [1] in Fedora for a while now that the uvcvideo
> driver no longer works on the Creative Live! Cam Optia AF (ID 041e:4058)
> in the 3.1 and 3.2 kernels.  The bug has all the various output from
> dmesg, lsusb, etc.
> 
> I'm wondering if there is anything further we can do to help diagnose
> what might be going wrong here.
> 
> josh

---

### Post by jonbonjovi on 2012-10-24
I have the same problem with Ubuntu 12.10 32 bit. Any solution?

---

