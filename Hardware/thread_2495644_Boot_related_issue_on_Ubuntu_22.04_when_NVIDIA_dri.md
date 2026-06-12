---
title: "Boot related issue on Ubuntu 22.04 when NVIDIA driver is installed"
date: 2024-02-25
forum: Hardware
---

### Post by alvinjinsung on 2024-02-25
[COLOR=#0C0D0E][FONT=-apple-system]I have booting related issue everytime I install NVIDIA-driver on Ubuntu 22.04 So the main problem is everytime I boot, Ubuntu would either[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system](1) boot fine (25% of the time)[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system](2) boot takes long time(about 2 min) (50% of the time)[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system](3) boot fails (25% of the time)[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]This symptom disappears when I uninstall NVIDIA driver so I'm pretty sure it is related to NVIDIA driver but I don't know how to fix it.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]For case (2) (boot takes long time), black screen with
[/FONT][/COLOR]
```
'/dev/nvme0n1p6: clean, *** files, *** blocks'
```

[COLOR=#0C0D0E][FONT=-apple-system]hang for a long time.

[/FONT][/COLOR][COLOR=#0C0D0E][FONT=-apple-system]For case (3) (boot fails), blackscreen with[/FONT][/COLOR]
```
'iwlwifi : invalid buffer destination'
'ACPI BIOS Error (bug): could not resolve symbol [\_TZ.ETMD], AE NOT_FOUND'
'ACPI Error: Aborting method \_SB.IETM._OSC due to previos error (AE_NOT_FOUND)'
'Bluetooth: hci0: Malformed MSFT vendor event: 0x02'
'INFO: task plymouthd: *** blocked for more than *** seconds'
'"echo 0 > /prc/sys/kernel/hung_task_timeout_secs" disables this message'
'INFO: task gpu-manager: *** blocked for more than *** seconds' 
'"echo 0 > /prc/sys/kernel/hung_task_timeout_secs" disables this message'

```

[COLOR=#0C0D0E][FONT=-apple-system]This screen appears and doesn't boot or blackscreen with cursor appears and doesn't boot. It happens quite randomly and it really is frustrating and want to resolve this issue. I've tried various things but it didn't work out. Here are some things I tried

[/FONT][/COLOR]
[LIST]
[*]deleting and reinstalling NVIDIA driver with 'purge, autoremove, apt install'
[*]Installing different driver version(525, 535, 545)
[*]trying boot-repair program
[*]disabling nouveau by modifying /etc/modprobe.d/blacklist.conf
[*]'nomodeset' by modifying /etc/default/grub (made it worse.. all boot fails....)
[*]tried various kernel version with various Ubuntu version (my laptop is very new device so 20.04 had issues with touchpad, wifi, etc, therefore I mainly tried 22.04)
[/LIST]
[FONT=inherit][COLOR=#0C0D0E][FONT=-apple-system]However none of them seemed to resolve the problem I am facing. It showed different symptoms time-to-time but mostly all of them were boot-related. I am using a dualboot with windows[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I am kind of lost and kindly ask for help. Here are some of the specification that would be helpful

Laptop: lenovo legion pro 7 16irx8h

[/FONT][/COLOR]
```
$ uname -a
Linux alvin-Legion-Pro-7-16IRX8H 6.5.0-21-generic 
#21~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Fri Feb  9 13:32:52 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

$ lspci
00:00.0 Host bridge: Intel Corporation Device a702 (rev 01)
00:01.0 PCI bridge: Intel Corporation Device a70d (rev 01)
00:02.0 VGA compatible controller: Intel Corporation Raptor Lake-S UHD Graphics (rev 04)
00:04.0 Signal processing controller: Intel Corporation Raptor Lake Dynamic Platform and Thermal Framework Processor Participant (rev 01)
00:06.0 PCI bridge: Intel Corporation Raptor Lake PCIe 4.0 Graphics Port (rev 01)
00:0a.0 Signal processing controller: Intel Corporation Raptor Lake Crashlog and Telemetry (rev 01)
00:14.0 USB controller: Intel Corporation Raptor Lake USB 3.2 Gen 2x2 (20 Gb/s) XHCI Host Controller (rev 11)
00:14.2 RAM memory: Intel Corporation Raptor Lake-S PCH Shared SRAM (rev 11)
00:14.3 Network controller: Intel Corporation Raptor Lake-S PCH CNVi WiFi (rev 11)
00:15.0 Serial bus controller: Intel Corporation Raptor Lake Serial IO I2C Host Controller #0 (rev 11)
00:15.1 Serial bus controller: Intel Corporation Raptor Lake Serial IO I2C Host Controller #1 (rev 11)
00:15.2 Serial bus controller: Intel Corporation Raptor Lake Serial IO I2C Host Controller #2 (rev 11)
00:16.0 Communication controller: Intel Corporation Raptor Lake CSME HECI #1 (rev 11)
00:19.0 Serial bus controller: Intel Corporation Device 7a7c (rev 11)
00:19.1 Serial bus controller: Intel Corporation Device 7a7d (rev 11)
00:1a.0 PCI bridge: Intel Corporation Raptor Lake PCI Express Root Port #25 (rev 11)
00:1b.0 PCI bridge: Intel Corporation Raptor Lake PCI Express Root Port #17 (rev 11)
00:1b.5 PCI bridge: Intel Corporation Device 7a45 (rev 11)
00:1d.0 PCI bridge: Intel Corporation Raptor Lake PCI Express Root Port #9 (rev 11)
00:1f.0 ISA bridge: Intel Corporation Device 7a0c (rev 11)
00:1f.3 Audio device: Intel Corporation Raptor Lake High Definition Audio Controller (rev 11)
00:1f.4 SMBus: Intel Corporation Raptor Lake-S PCH SMBus Controller (rev 11)
00:1f.5 Serial bus controller: Intel Corporation Raptor Lake SPI (flash) Controller (rev 11)
01:00.0 VGA compatible controller: NVIDIA Corporation AD104M [GeForce RTX 4080 Max-Q / Mobile] (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 22bc (rev a1)
06:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller PM9A1/PM9A3/980PRO
07:00.0 PCI bridge: Intel Corporation Device 1133 (rev 02)
08:00.0 PCI bridge: Intel Corporation Device 1133 (rev 02)
08:01.0 PCI bridge: Intel Corporation Device 1133 (rev 02)
08:02.0 PCI bridge: Intel Corporation Device 1133 (rev 02)
08:03.0 PCI bridge: Intel Corporation Device 1133 (rev 02)
09:00.0 USB controller: Intel Corporation Device 1134
3d:00.0 USB controller: Intel Corporation Device 1135
76:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet Controller (rev 15)

$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd000027E0sv000017AAsd00003B64bc03sc00i00
vendor   : NVIDIA Corporation
driver   : nvidia-driver-535-open - distro non-free
driver   : nvidia-driver-525 - distro non-free recommended
driver   : nvidia-driver-535-server-open - distro non-free
driver   : nvidia-driver-545 - distro non-free
driver   : nvidia-driver-525-open - distro non-free
driver   : nvidia-driver-545-open - distro non-free
driver   : nvidia-driver-535-server - distro non-free
driver   : nvidia-driver-525-server - distro non-free
driver   : nvidia-driver-535 - third-party non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

$ nvidia-smi
Mon Feb 26 12:51:30 2024       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 525.147.05   Driver Version: 525.147.05   CUDA Version: 12.0     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   39C    P3    N/A /  80W |      6MiB / 12282MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      2048      G   /usr/lib/xorg/Xorg                  4MiB |
+-----------------------------------------------------------------------------+
```[/FONT]

[COLOR=#0C0D0E][FONT=-apple-system]I am a newby and it would be kind if you suggest some action I should try with command-line code with it.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Thank you for your help in advance![/FONT][/COLOR]

---

### Post by MAFoElffen on 2024-02-26
Ensure SecureBoot is disabled. NVidia modules are not self-signed.

---

### Post by alvinjinsung on 2024-02-26
Secure boot is already disabled

---

