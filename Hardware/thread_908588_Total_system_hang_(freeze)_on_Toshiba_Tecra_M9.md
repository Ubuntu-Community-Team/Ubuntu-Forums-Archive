---
title: "Total system hang (freeze) on Toshiba Tecra M9"
date: 2008-09-02
forum: Hardware
---

### Post by alecz20 on 2008-09-02
I successfully installed Ubuntu 8.04.1 on a Toshiba Tecra M9 (Nvidia Quadro NVS 130M).

The problem is that the system completely hangs anywhere between 2-5 minutes after logging in. I searched for solutions, but couldn't find anything other than people having trouble with hibernate/suspend.

I just want to be able to use it for more than 5 minutes.

---

### Post by alecz20 on 2008-09-02
I got around the freeze using the modifications described here:
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

The proprietary driver was disabled. I re-installed the driver, so I can use higher resolutions. However, now I can't dim the screen anymore, and some other special keyboard keys do not work (such as "pad-lock")

---

### Post by vgyo on 2008-09-02
more specifically, the freezing occurs when the Nvidia driver is disabled and I use the Fn + F6 to dim the screen; a few minutes after the system freezes.
  If I enable the driver , there is no system freezing but then none of the Fn + F1 through F12  work (Icannot dim the screen,or lock the touchpad or the wireless, etc)

---

