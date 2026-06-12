---
title: "Lenovo 500 low brightness"
date: 2016-06-30
forum: Hardware
---

### Post by helektron on 2016-06-30
Hi, I'm using ubuntu 16.04 for lenovo z500 laptop (3rd intel hd graphics / 3D controller: NVIDIA Corporation GK208M [GeForce GT 740M]). I don't have issues with drivers but the problem it's not fully bright. I tried xcalib and xbacklight but i can't increse brightness or contrast because it is already 100%. White color seems to be grey. I'ts working fine using Windows 10 but I want to use Ubuntu :)

Some info:

```
helektron@helektron-laptop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-4.4.0-28-generic root=UUID=7326329b-56fc-4136-8a79-8a1747f603dc ro quiet splash

```

```
helektron@helektron-laptop:~$ lspci -k | grep -A3 VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: Lenovo 3rd Gen Core processor Graphics Controller
    Kernel driver in use: i915
    Kernel modules: i915

```

```
helektron@helektron-laptop:~$ lspci -k | grep -A3 NVIDIA
01:00.0 3D controller: NVIDIA Corporation GK208M [GeForce GT 740M] (rev a1)
    Subsystem: Lenovo GK208M [GeForce GT 740M]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_361

```

```
helektron@helektron-laptop:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; cat $i/actual_brightness; done
/sys/class/backlight/intel_backlight
976
976
976

```

```
helektron@helektron-laptop:~$ pastebinit /var/log/Xorg.0.log
http://paste.ubuntu.com/18159486/

```


Can you please help me?

Thanks a lot.

---

