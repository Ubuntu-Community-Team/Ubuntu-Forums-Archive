---
title: "Optimize ssd hard drives with hdparm / laptop-mode"
date: 2009-10-08
forum: Hardware
---

### Post by Axx83 on 2009-10-08
Hi guys, I bought this new ssd hard drive Kingston SSDNow Series V 64Gb and I was trying to optimize it like I did with my old non solid hard drive.

What parameters should I play with in hdparm/laptop-mode ? (I use the latter, but functions are almost the same)

For the moment I just partitioned with ext4, attached noatime to /etc/fstab, and vm.swappiness=0 to to /etc/sysctl.conf but I'm sure there are commands that will put my ssd to idle more often. The following commands are from laptop-mode.conf

```

LM_BATT_MAX_LOST_WORK_SECONDS=600
LM_AC_MAX_LOST_WORK_SECONDS=360

CONTROL_READAHEAD=1

LM_READAHEAD=3072
NOLM_READAHEAD=128

CONTROL_NOATIME=1

USE_RELATIME=0

CONTROL_HD_IDLE_TIMEOUT=1

LM_AC_HD_IDLE_TIMEOUT_SECONDS=240
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=20
NOLM_HD_IDLE_TIMEOUT_SECONDS=7200

CONTROL_HD_POWERMGMT=1

BATT_HD_POWERMGMT=1
LM_AC_HD_POWERMGMT=254
NOLM_AC_HD_POWERMGMT=254

CONTROL_HD_WRITECACHE=0

NOLM_AC_HD_WRITECACHE=1
NOLM_BATT_HD_WRITECACHE=0
LM_HD_WRITECACHE=0

CONTROL_MOUNT_OPTIONS=1

LM_DIRTY_RATIO=90
NOLM_DIRTY_RATIO=40

LM_DIRTY_BACKGROUND_RATIO=1
NOLM_DIRTY_BACKGROUND_RATIO=10

```

Thanks for the help guys !

---

