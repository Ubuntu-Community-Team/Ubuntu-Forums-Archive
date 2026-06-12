---
title: "Laptop DVD-ROM problem"
date: 2008-04-29
forum: Hardware
---

### Post by spectrevk on 2008-04-29
I had tried to recycle a thread I was using in the Absolute Beginner forum, but I think that was the wrong place for it, as it was a bit off-topic for a thread about power management issues.

Powertop has left me with a rather odd problem. After making a change involving my DVD-ROM drive's power useage, my drive no longer works in Ubuntu. I think it's no longer loading the driver correctly. The error message says "Cannot mount volume." Details say:

```
mount: block device /dev/scd0 is write-protected, mounting read-only mount: wrong fs type, bad option, bad superblock on /dev/scd0, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg|tail or so
```

So I tried that, but dmesg|tail gives me this:

```
[ 3272.820421] psmouse.c: Failed to reset mouse on isa0060/serio1
[ 3272.834021] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3272.841706] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3272.844075] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3272.846269] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 3272.856010] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 3272.856020] psmouse.c: issuing reconnect request
[ 3272.965843] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input10
[ 3272.997724] psmouse.c: Failed to enable mouse on isa0060/serio1
[ 3276.074717] UDF-fs: No fileset found

```

---

### Post by spectrevk on 2008-04-30
Can anyone just point me in the right direction for undoing changes to my configuration related to the DVD-ROM drive? Ubuntu 7.10 had a  device manager that showed all of the hardware devices in the machine, but that program no longer appears in the menus. Now the Hardware Manager is just that program that deals with proprietary drivers. Actually, some way of rolling back to an earlier configuration would work as well.

---

### Post by spectrevk on 2008-04-30
Just bumping this in hopes of getting some help. I'm sure there's a config file somewhere that'll fix this, I just don't know where it is.

---

### Post by spectrevk on 2008-05-02
Bumping again, hoping someone will see this.

---

