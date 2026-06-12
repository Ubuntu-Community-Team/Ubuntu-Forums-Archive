---
title: "built-in webcam - Not supported in 12.04?"
date: 2012-10-28
forum: Hardware
---

### Post by vecnu on 2012-10-28
Hi everyone. I am having problems making the built-in webcam in my laptop work.
```

Bus 001 Device 004: ID 0ac8:c002 Z-Star Microelectronics Corp. Visual Communication Camera VGP-VCC1

```In kubuntu 10.04, it worked loading the gspca_vc032x module, and running skype like this:
```

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

```Recently, I have made a clean Xubuntu 12.04 install. The path to vdl1compat.so has been moved. I am trying
```

LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype

```But that doesn't work. I've also tried with cheese, kamerka and others.

It looks like the problem is that webcam is not supported in 12.04:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/990749](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/990749)

Do you think there is anything I can do to make it work?

---

