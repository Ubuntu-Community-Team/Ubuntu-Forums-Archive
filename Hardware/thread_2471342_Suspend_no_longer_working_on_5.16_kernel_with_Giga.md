---
title: "Suspend no longer working on 5.16 kernel with Gigabyte gaming X / z690 / Nvidia GPU"
date: 2022-01-27
forum: Hardware
---

### Post by monpoke on 2022-01-27
This is relatively new hardware: z690 chipset (motherboard gigabyte gaming X ddr4, bios F6) + i7-12700kf + nvidia GPU

Ubuntu 21.10

uname -a
Linux xpc 5.16.2-051602-generic #202201200936 SMP PREEMPT Thu Jan 20 10:20:55 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

With 5.13 and 5.15 kernels suspend and resume to S3 works. (one has to unload 'intel_lpss_pci' otherwise system hangs on resume)

But with 5.16 on Ubuntu, the system no longer fully suspends - screen goes dark, one can hear the disks stop spinning, but the CPU/GPU fans are still spinning... only way to recover is power-off / power-on

This is specific to Ubuntu. On Manjaro suspend/resume with 5.16 kernel works as does 5.15

I have tried suspending with pm_trace enabled and this is what shows up

[    3.645453] PM:   Magic number: 0:707:508
[    3.645455] PM:   hash matches drivers/base/power/main.c:1206
[    3.645490] pcieport 0000:00:01.0: hash matches

(have repeated 2 times and both times it is consistent)

Is pcieport 0000:00:01.0 the same as 01:00.0 in below (the GPU?) or is it the 00:01.0 PCI bridge?

x@xpc:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 4668 (rev 02)
00:01.0 PCI bridge: Intel Corporation Device 460d (rev 02)
00:06.0 PCI bridge: Intel Corporation Device 464d (rev 02)
00:0a.0 Signal processing controller: Intel Corporation Device 467d (rev 01)
00:14.0 USB controller: Intel Corporation Device 7ae0 (rev 11)
00:14.2 RAM memory: Intel Corporation Device 7aa7 (rev 11)
00:15.0 Serial bus controller [0c80]: Intel Corporation Device 7acc (rev 11)
00:15.1 Serial bus controller [0c80]: Intel Corporation Device 7acd (rev 11)
00:15.2 Serial bus controller [0c80]: Intel Corporation Device 7ace (rev 11)
00:15.3 Serial bus controller [0c80]: Intel Corporation Device 7acf (rev 11)
00:16.0 Communication controller: Intel Corporation Device 7ae8 (rev 11)
00:17.0 SATA controller: Intel Corporation Device 7ae2 (rev 11)
00:19.0 Serial bus controller [0c80]: Intel Corporation Device 7afc (rev 11)
00:19.1 Serial bus controller [0c80]: Intel Corporation Device 7afd (rev 11)
00:1c.0 PCI bridge: Intel Corporation Device 7ab8 (rev 11)
00:1c.2 PCI bridge: Intel Corporation Device 7aba (rev 11)
00:1f.0 ISA bridge: Intel Corporation Device 7a84 (rev 11)
00:1f.3 Audio device: Intel Corporation Device 7ad0 (rev 11)
00:1f.4 SMBus: Intel Corporation Device 7aa3 (rev 11)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Device 7aa4 (rev 11)
01:00.0 VGA compatible controller: NVIDIA Corporation GV100 [TITAN V] (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 10f2 (rev a1)
02:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8125 2.5GbE Controller (rev 05)

Also have tried going through pm_test tests:

- freezer works
echo freezer >/sys/power/pm_test 

- devices works
echo devices >/sys/power/pm_test 

- platform hangs during suspend (same as normal suspend)

i have tried to collect ubuntu-bug linux - but it fails with 'package not installed' 

Nvidia GPU drivers were 495, but also tried with 470 and also beta 510 - no difference. In Manjaro 495 works ok with any kernel. Also on Ubuntu any version works with 5.13 and 5.15

5.17rc1 doesn't seem to be building in mainline yet, so have not tested it yet.

Looking for help / advise how to troubleshoot / fix suspend

---

### Post by linuxgnuru on 2022-03-23
I found one "fix" but the side effects are unknown; if you remove the intel_lpss_pci module then the system can wake from suspend `sudo rmmod intel_lpss_pci`

---

