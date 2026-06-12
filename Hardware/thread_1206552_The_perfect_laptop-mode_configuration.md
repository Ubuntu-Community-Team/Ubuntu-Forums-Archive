---
title: "The perfect laptop-mode configuration"
date: 2009-07-07
forum: Hardware
---

### Post by Axx83 on 2009-07-07
Hello guys. I need your help setting up laptop-mode to be just PERFECT.
Perfect means that I'll be saving the most power when on battery and reducing the most tear when on ac, right now I believe the default conf of laptop-mode doesn't do that. This is my slightly tuned /etc/laptop-mode/laptop-mode.conf (i'm using jaunty)

I removed the comments and descriptions and printed only the relevant commands.

```

VERBOSE_OUTPUT=0

ENABLE_LAPTOP_MODE_ON_BATTERY=1

ENABLE_LAPTOP_MODE_ON_AC=1

ENABLE_LAPTOP_MODE_WHEN_LID_CLOSED=0

MINIMUM_BATTERY_CHARGE_PERCENT=3

DISABLE_LAPTOP_MODE_ON_CRITICAL_BATTERY_LEVEL=1

HD="/dev/[hs]d[abcdefgh]"

PARTITIONS="auto /dev/mapper/*"

ASSUME_SCSI_IS_SATA=1





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

Thank you for the help, let me know what your numbers are.

---

### Post by shatterblast on 2009-07-07
While not in my personal experience, it is in my understanding that the Remix version of Ubuntu provides the majority of needed options towards power-saving.  I have not verified how good the information tests out, and compatibility issues with power-saving exist I think on a few hardware platforms.

---

### Post by Axx83 on 2009-07-08
You mean the "ubuntu-netbook-remix-default" package ? It says "This package provides common configuration files and gconf-defaults for
Ubuntu Netbook Remix".

Does someone know what exactly are the conf in this package ? I don't know if it's a good idea trying it without a completely clean installation of ubuntu.

Thanks

---

### Post by Axx83 on 2009-07-08
I checked the package myself, the only thing useful it does is modify a couple of settings for gnome-power-manager. Besides this it configures appearances to fit with the netbook launcher menu.

Thank you for the tip anyway and keep looking

---

### Post by Axx83 on 2009-07-10
It seems my power consumption goes up if I modify the write cache setting, does someone knows why ?

---

