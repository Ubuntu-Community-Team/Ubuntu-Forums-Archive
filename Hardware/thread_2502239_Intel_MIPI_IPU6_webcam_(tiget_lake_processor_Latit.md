---
title: "Intel MIPI IPU6 webcam (tiget lake processor Latitude 7320 detachable)"
date: 2024-11-06
forum: Hardware
---

### Post by kswenson on 2024-11-06
Hello folks, I'm trying to get my webcam to work in my Dell laptop.  I bought it about 4 years ago with Windows installed, and I immediately switched to Ubuntu.  I've never gotten the webcam to work, but I see that these days there are several examples of Ubuntu working with this type of webcam.

I'm running 24.10 Oracular.

Basically, I've followed the (vague) instructions at [https://wiki.ubuntu.com/IntelMIPICamera]("https://wiki.ubuntu.com/IntelMIPICamera") and installed all the packages in the "OEM Solutions Group" PPA [https://launchpad.net/~oem-solutions-group/+archive/ubuntu/intel-ipu6]("https://launchpad.net/~oem-solutions-group/+archive/ubuntu/intel-ipu6").

There are also signs that the thing is recognized by the system:
```

=> v4l2-ctl --list-devices
ipu6 (PCI:pci:pci0000:00):
	/dev/video1
	/dev/video2
	/dev/video3
	/dev/video4
	/dev/video5
	/dev/video6
	/dev/video7
	/dev/video8

ipu6 (pci:pci0000:00):
	/dev/media0

Intel MIPI Camera (platform:v4l2loopback-000):
	/dev/video0

```
```

=> sudo lshw -C multimedia
[sudo] password for kms: 
  *-multimedia:0            
       description: Multimedia controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm bus_master cap_list
       configuration: driver=intel-ipu6 latency=0
       resources: iomemory:600-5ff irq:169 memory:6052000000-6052ffffff

```

There is also an error message, which I'm not sure is relevant, because it's buried in other encouraging messages:
```

=> sudo dmesg | grep ipu
[    3.303953] intel-ipu6 0000:00:05.0: enabling device (0000 -> 0002)
[    3.304649] intel-ipu6 0000:00:05.0: Device 0x9a19 (rev: 0x1)
[    3.304674] intel-ipu6 0000:00:05.0: physical base address 0x6052000000
[    3.304676] intel-ipu6 0000:00:05.0: mapped as: 0x00000000f288b33b
[    3.306354] intel-ipu6 0000:00:05.0: IPU in secure mode
[    3.306358] intel-ipu6 0000:00:05.0: IPU secure touch = 0x0
[    3.306360] intel-ipu6 0000:00:05.0: IPU camera mask = 0xff
[    3.322283] intel-ipu6 0000:00:05.0: IPC reset done
[    3.323855] intel-ipu6 0000:00:05.0: Direct firmware load for intel/ipu6_fw.bin failed with error -2
[    3.329435] intel-ipu6 0000:00:05.0: FW version: 20230925
[    3.331259] intel-ipu6 0000:00:05.0: Found supported sensor OVTI8856:00
[    3.331264] intel-ipu6 0000:00:05.0: Connected 1 cameras
[    3.332219] intel-ipu6 0000:00:05.0: Sending BOOT_LOAD to CSE
[    3.353910] intel-ipu6 0000:00:05.0: Sending AUTHENTICATE_RUN to CSE
[    3.425513] intel-ipu6 0000:00:05.0: CSE authenticate_run done
[    3.425707] intel-ipu6 0000:00:05.0: IPU6-v0 driver version 1.0
[    4.295772] intel-ipu6-psys intel-ipu6-psys0: pkg_dir entry count:8
[    4.306081] intel-ipu6-psys intel-ipu6-psys0: psys probe minor: 0

```

When I do `ffplay /dev/video0` the terminal output looks good, but there just a black video screen:
```
Input #0, video4linux2,v4l2, from '/dev/video0':B sq=    0B 
  Duration: N/A, start: 1481.490208, bitrate: 442368 kb/s
  Stream #0:0: Video: rawvideo (YUY2 / 0x32595559), yuyv422, 1280x720, 442368 kb/s, 30 fps, 30 tbr, 1000k tbn

```

If anyone has input on debugging, I would love to hear your advice!

---

