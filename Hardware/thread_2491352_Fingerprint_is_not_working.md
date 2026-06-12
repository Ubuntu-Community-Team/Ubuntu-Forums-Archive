---
title: "Fingerprint is not working"
date: 2023-10-05
forum: Hardware
---

### Post by gopal337 on 2023-10-05
i cannot able to use fingerprint in my ubuntu. Help me to fix. The hardware is detecting the fingerprint sensor But it does not showing in setting menu.
here's the hardware information.

(base) gopal@Gopal-Laptop:~$ fprintd-enroll
Impossible to enroll: GDBus.Error:net.reactivated.Fprint.Error.NoSuchDevice: No devices available
(base) gopal@Gopal-Laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 27c6:5e0a Shenzhen Goodix Technology Co.,Ltd. FingerPrint
Bus 003 Device 002: ID 2b7e:b514 SunplusIT Inc 720p HD Camera
Bus 003 Device 004: ID 8087:0aaa Intel Corp. Bluetooth 9460/9560 Jefferson Peak (JfP)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by readableauthor on 2023-10-05
Doesn't seem to be supported by Linux:
[https://linux-hardware.org/?id=usb:27c6-5e0a](https://linux-hardware.org/?id=usb:27c6-5e0a)
[https://gitlab.freedesktop.org/libfprint/libfprint/-/issues/457](https://gitlab.freedesktop.org/libfprint/libfprint/-/issues/457)

---

