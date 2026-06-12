---
title: "Fingerprint Reader not working."
date: 2019-06-19
forum: Hardware
---

### Post by NahuelMS on 2019-06-19
I am running 18.0.4.2After 3 nigths figthing to make my fingerprint reader work i gave up. For some reason i think the official libfprint that is hosted in ubuntu official channel doesn't support the ELAN fingerprint readers. Support for this hardware have been developed here [https://gitlab.freedesktop.org/libfprint/fprintd](https://gitlab.freedesktop.org/libfprint/fprintd).
Tried to install that version but failed as instructions are not good and i am just an amateur user.
My fingerprint model is supported in the list but when i try to enroll the fingerprint with fingerprint-gui or fprintd keeps telling me that no hardware is detected. In lsub it shows the device but not as a fingerprint reader in particular, just says Elantech. Any solution? Can anyone give me a detailed why of making it work? Thanks a lot!

lsusb: Bus 001 Device 005: ID 04f3:0c03 Elan Microelectronics Corp.

PD: In Ubuntu 16 it didn't work neither but at least it detected it i think.

---

### Post by TheFu on 2019-06-20
[https://bugs.launchpad.net/ubuntu/+source/libfprint/+bug/1641290](https://bugs.launchpad.net/ubuntu/+source/libfprint/+bug/1641290)
If you aren't a C developer with fingerprint coding knowledge, then I would probably move on based on that bug report.

---

