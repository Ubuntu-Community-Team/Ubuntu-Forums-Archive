---
title: "fsck runs after hibernation, resume info is lost"
date: 2012-07-16
forum: Hardware
---

### Post by tkzv on 2012-07-16
When I switch the computer on after hibernation, often the disk is checked for errors, as if it was not unmounted correctly. After that the computer is rebooted again, and previous state is not restored. What is wrong?

Observed in Ubuntu 10.10 and 12.04. Worked correctly in 10.04. Computer is Asus EEE 701, with Intel video and SILICONMOTION SM223AC solid state disk. Partitions: 3.0 gigabyte ext2 as /, 700 megabyte swap. The bug seems more likely to occur when working with a 3G USB modem (Huawei E620).

There are the following errors in /var/log/pm-suspend.log:

```

Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.

```

and then

```

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 HDIO_DRIVE_CMD failed: Input/output error

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level      = off

/dev/sda:
 setting standby to 36 (3 minutes)

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.

```

How do I make it hibernate correctly?

---

### Post by tkzv on 2012-07-16
Looks like the bug only reproduces if I hibernate with Chromium running.

Tried the same with Firefox. 2 hibernations, no disk errors so far.

---

