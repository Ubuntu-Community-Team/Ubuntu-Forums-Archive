---
title: "vga switcheroo"
date: 2012-03-27
forum: Hardware
---

### Post by umkonst on 2012-03-27
Hey people, 
I'm new in the linux.
I have tm2t with switchable graphic card.
When i'm doing this it's mean that kernel knows this module:

```
grep -i switcheroo /boot/config-3.0.0-16-generic 
CONFIG_VGA_SWITCHEROO=y
```


but:

```
ls -l /sys/kernel/debug/vgaswitcheroo/switch
ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
```

What i have to do, for switching between cards.
thank's/

---

### Post by brainwash on 2012-03-27
Hey,

please attach the output of
```
cat /proc/cmdline
```

---

### Post by umkonst on 2012-03-27
```
cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=eaeda052-d386-4eb5-a007-25c6a0e89a33 ro quiet splash vt.handoff=7

```

---

### Post by brainwash on 2012-03-27
Nothing suspicious. The output of
```
lspci | grep VGA
lsmod | grep radeon
```
might be helpful here.

---

### Post by umkonst on 2012-03-27
```
root@cu-HP-TouchSmart-tm2-Notebook-PC:/home/cu# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5400 Series]
root@cu-HP-TouchSmart-tm2-Notebook-PC:/home/cu# lsmod | grep radeon
root@cu-HP-TouchSmart-tm2-Notebook-PC:/home/cu# 

```
"lsmod | grep radeon" do not give output as u see.
thank's for helping me

---

### Post by brainwash on 2012-03-27
So you likely installed the **fglrx** driver (via Additional Drivers) or you put the default **radeon** driver on a blacklist. The radeon driver is required for vgaswitcheroo to work!

If you downloaded the extra one, you might want to check this thread for some details on how to switch the GPU:

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

---

### Post by umkonst on 2012-03-27
Oh! Great!!! It works!!!! I'S ALIVE!!!!!
Thank's a lot!

---

