---
title: "vgaswitcheroo isn't working anymore"
date: 2012-05-18
forum: Hardware
---

### Post by forbidden404 on 2012-05-18
I always used vgaswitcheroo to turn off my discrete graphic, I did a script to turn off in boot, but now, vgaswitcheroo isn't working anymore, I don't know why... look

```
forbidden404@forbidden404-Inspiron-N5110:~$ ls -l /sys/kernel/debug/vgaswitcheroo/switch
ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: Permission denied
forbidden404@forbidden404-Inspiron-N5110:~$ grep -i switcheroo /boot/config-*
/boot/config-3.2.0-20-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-3.2.0-23-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-3.2.0-24-generic:CONFIG_VGA_SWITCHEROO=y
forbidden404@forbidden404-Inspiron-N5110:~$ sudo su
[sudo] password for forbidden404: 
root@forbidden404-Inspiron-N5110:/home/forbidden404# echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
bash: /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
root@forbidden404-Inspiron-N5110:/home/forbidden404# ls -l /sys/kernel/debug/vgaswitcheroo/switch
ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
```

---

### Post by brainwash on 2012-05-18
> **forbidden404 said:**
> I always used vgaswitcheroo to turn off my discrete graphic, I did a script to turn off in boot, **but now**, vgaswitcheroo isn't working anymore, I don't know why... look

Please provide more information. Did you install the proprietary driver for your discrete GPU?

---

### Post by forbidden404 on 2012-05-18
> **brainwash said:**
> Please provide more information. Did you install the proprietary driver for your discrete GPU?

I did, but never worked, so I'm using the open source one

---

### Post by brainwash on 2012-05-18
Please attach the content of your custom script and the output of this command:
```
dmesg | egrep 'radeon|switcheroo'
```

---

### Post by forbidden404 on 2012-05-18
> **brainwash said:**
> Please attach the content of your custom script and the output of this command:
```
dmesg | egrep 'radeon|switcheroo'
```

```


[   22.857997] [drm] radeon defaulting to kernel modesetting.
[   22.858001] [drm] radeon kernel modesetting enabled.
[   22.858013] VGA switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle


```

I guess is all configured fine, I don't know why isn't working.

---

