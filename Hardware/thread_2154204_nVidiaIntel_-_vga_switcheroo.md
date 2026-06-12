---
title: "nVidia/Intel - vga switcheroo"
date: 2013-06-13
forum: Hardware
---

### Post by trove on 2013-06-13
I got the same problem like **umkonst **right [HERE]("http://ubuntuforums.org/showthread.php?t=1947819") but with nVidia card so I don't even read this thread [AMD/Intel Hybrid Graphics works]("http://ubuntuforums.org/showthread.php?t=1930450&highlight=nvidia+dedic") regarding to what it says:
> If you do not own a AMD hybrid graphic card, please leave this thread.


I'm getting
```
ls -l /sys/kernel/debug/vgaswitcheroo/switch
ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
```
and I'm stuck, cause I can't find anywhere any solution.

Any suggestions?

```
aleksander@Lenovo:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-34-generic root=UUID=df37bcf0-4573-4f83-88a2-304b67934126 ro quiet splash

```
```
aleksander@Lenovo:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0fd4 (rev a1)
```
```
aleksander@Lenovo:~$ lsmod | grep nvidia
nvidia               9367981  0
```

---

### Post by Yellow Pasque on 2013-06-14
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by trove on 2013-06-14
How do I *replace linux-headers-generic with linux-headers-generic-lts-quantal*?

Updated kernel to 3.9.6. When trying to install bumblebee I receive information that there's no such package.


SOLVED

After reinstalling Ubuntu 12.04 and doing everything like instructions said everything works nice.

---

