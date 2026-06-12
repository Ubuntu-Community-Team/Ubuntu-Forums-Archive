---
title: "Dell 7212 web cam problem"
date: 2019-05-07
forum: Hardware
---

### Post by mspezia on 2019-05-07
Hi,
 I have a Dell 7212 extreme tablet pc that work correctly with Ubunt but not see two camera that are present. I verify that are present more video device but any of this work:

crw-rw----+ 1 root video 81, 0 mag  7 07:11 ./video0
crw-rw----+ 1 root video 81, 1 mag  7 07:11 ./video1
crw-rw----+ 1 root video 81, 2 mag  7 07:11 ./video2
crw-rw----+ 1 root video 81, 3 mag  7 07:11 ./video3
crw-rw----+ 1 root video 81, 4 mag  7 07:11 ./video4
crw-rw----+ 1 root video 81, 5 mag  7 07:11 ./video5
crw-rw----+ 1 root video 81, 6 mag  7 07:11 ./video6
crw-rw----+ 1 root video 81, 7 mag  7 07:11 ./video7
crw-rw----+ 1 root video 81, 8 mag  7 07:11 ./video8
crw-rw----+ 1 root video 81, 9 mag  7 07:11 ./video9

I checked that ipu3-imgu are loaded

00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 08)
    Subsystem: Dell Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers
    Kernel driver in use: skl_uncore
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07)
    Subsystem: Dell UHD Graphics 620
    Kernel driver in use: i915
    Kernel modules: i915
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 08)
    Subsystem: Dell Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
    Kernel driver in use: proc_thermal
    Kernel modules: processor_thermal_device
00:05.0 Multimedia controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Imaging Unit (rev 01)
    Subsystem: Dell Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Imaging Unit
    Kernel driver in use: ipu3-imgu
    Kernel modules: ipu3_imgu
00:13.0 Non-VGA unclassified device: Intel Corporation Sunrise Point-LP Integrated Sensor Hub (rev 21)
    Subsystem: Dell Sunrise Point-LP Integrated Sensor Hub
    Kernel driver in use: intel_ish_ipc
    Kernel modules: intel_ish_ipc
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
    Subsystem: Dell Sunrise Point-LP USB 3.0 xHCI Controller
    Kernel driver in use: xhci_hcd
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
    Subsystem: Dell Sunrise Point-LP Thermal subsystem
    Kernel driver in use: intel_pch_thermal
    Kernel modules: intel_pch_thermal
00:14.3 Multimedia controller: Intel Corporation Device 9d32 (rev 01)
    Subsystem: Dell Device 07d3
    Kernel modules: ipu3_cio2
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
    Subsystem: Dell Sunrise Point-LP Serial IO I2C Controller
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)
    Subsystem: Dell Sunrise Point-LP Serial IO I2C Controller
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:15.2 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #2 (rev 21)
    Subsystem: Dell Sunrise Point-LP Serial IO I2C Controller
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
    Subsystem: Dell Sunrise Point-LP CSME HECI
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:1c.0 PCI bridge: Intel Corporation Device 9d13 (rev f1)
    Kernel driver in use: pcieport
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
    Kernel driver in use: pcieport
00:1d.0 PCI bridge: Intel Corporation Device 9d1b (rev f1)
    Kernel driver in use: pcieport
00:1f.0 ISA bridge: Intel Corporation Intel(R) 100 Series Chipset Family LPC Controller/eSPI Controller - 9D4E (rev 21)
    Subsystem: Dell Intel(R) 100 Series Chipset Family LPC Controller/eSPI Controller - 9D4E
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
    Subsystem: Dell Sunrise Point-LP PMC
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
    Subsystem: Dell Sunrise Point-LP HD Audio
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
    Subsystem: Dell Sunrise Point-LP SMBus
    Kernel driver in use: i801_smbus
    Kernel modules: i2c_i801
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)
    Subsystem: Dell RTS525A PCI Express Card Reader
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci
02:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981
    Subsystem: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981
    Kernel driver in use: nvme
    Kernel modules: nvme
03:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)
    Subsystem: Dell QCA6174 802.11ac Wireless Network Adapter
    Kernel driver in use: ath10k_pci
    Kernel modules: ath10k_pci



ubuntu version 19.04

If I execute, for example, Cheese program, this see ipu3-imgu device but not work. Other, Webcamoid, not see any webcam.
Could you any suggest to me where investigate please?
Thank you
By
Marco

---

### Post by yaazzz on 2019-05-08
Good Morning, I am not sure to have enough skill to support but for ipu3 it seems that 2 drivers drivers are needed : [LEFT][COLOR=#000000][FONT=serif]ipu3_csi2 and ipu3_imgu. I experience the same issue on my Galaxy Book 12.
The output of :
```
lsmod |grep ipu3 
``` 
```
ipu3_imgu             208896  0
ipu3_cio2              32768  0
v4l2_fwnode            28672  1 ipu3_cio2
videobuf2_dma_sg       16384  2 ipu3_cio2,ipu3_imgu
videobuf2_v4l2         24576  2 ipu3_cio2,ipu3_imgu
videobuf2_common       49152  3 ipu3_cio2,videobuf2_v4l2,ipu3_imgu
videodev              200704  5 v4l2_fwnode,ipu3_cio2,videobuf2_v4l2,videobuf2_common,ipu3_imgu
media                  53248  5 videodev,ipu3_cio2,videobuf2_v4l2,videobuf2_common,ipu3_imgu

```

```
dmesg |grep ipu3

```[/FONT][/COLOR]
[/LEFT]

```
[    5.563256] ipu3-cio2 0000:00:14.3: enabling device (0000 -> 0002)
[    5.563425] ipu3-cio2 0000:00:14.3: device 0x9d32 (rev: 0x1)
[    5.565987] ipu3-cio2 0000:00:14.3: Entity type for entity ipu3-csi2 0 was not initialized!
[    5.566048] ipu3-cio2 0000:00:14.3: Entity type for entity ipu3-csi2 1 was not initialized!
[    5.566096] ipu3-cio2 0000:00:14.3: Entity type for entity ipu3-csi2 2 was not initialized!
[    5.566138] ipu3-cio2 0000:00:14.3: Entity type for entity ipu3-csi2 3 was not initialized!
[    5.575796] ipu3_imgu: module is from the staging directory, the quality is unknown, you have been warned.
[    5.575871] ipu3_imgu: module verification failed: signature and/or required key missing - tainting kernel
[    5.576620] ipu3-imgu 0000:00:05.0: enabling device (0000 -> 0002)
[    5.580831] ipu3-imgu 0000:00:05.0: device 0x1919 (rev: 0x1)
[    5.580854] ipu3-imgu 0000:00:05.0: physical base address 0x00000000df000000, 4194304 bytes
[    5.703308] ipu3-imgu 0000:00:05.0: loaded firmware version irci_irci_ecr-master_20161208_0213_20170112_1500, 17 binaries, 1212984 bytes


```

I am not sure it seems to be related to ipu3-csi2. I try to find documentation on how to initialize it but without success.

---

### Post by mspezia on 2019-05-08
Hi,
 thank you so much for your support. I checked  and the situation is the same of yours.

> 
mspezia@extreme:~$ sudo lsmod |grep ipu3
[sudo] password for mspezia: 

ipu3_cio2              32768  0
v4l2_fwnode            28672  1 ipu3_cio2
ipu3_imgu             208896  0
videobuf2_dma_sg       16384  2 ipu3_cio2,ipu3_imgu
videobuf2_v4l2         24576  2 ipu3_cio2,ipu3_imgu
videobuf2_common       49152  3 ipu3_cio2,videobuf2_v4l2,ipu3_imgu
videodev              200704  5 v4l2_fwnode,ipu3_cio2,videobuf2_v4l2,videobuf2_common,ipu3_imgu
media                  53248  5 videodev,ipu3_cio2,videobuf2_v4l2,videobuf2_common,ipu3_imgu

mspezia@extreme:~$ dmesg |grep ipu3

[    3.075208] ipu3_imgu: module is from the staging directory, the quality is unknown, you have been warned.
[    3.075304] ipu3_imgu: module verification failed: signature and/or required key missing - tainting kernel
[    3.079786] ipu3-imgu 0000:00:05.0: enabling device (0000 -> 0002)
[    3.084420] ipu3-imgu 0000:00:05.0: device 0x1919 (rev: 0x1)
[    3.084442] ipu3-imgu 0000:00:05.0: physical base address 0x00000000df000000, 4194304 bytes
[    3.094678] ipu3-cio2 0000:00:14.3: enabling device (0000 -> 0002)
[    3.095727] ipu3-cio2 0000:00:14.3: device 0x9d32 (rev: 0x1)
[    3.096129] ipu3-cio2 0000:00:14.3: Entity type for entity ipu3-csi2 0 was not initialized!
[    3.096236] ipu3-cio2 0000:00:14.3: Entity type for entity ipu3-csi2 1 was not initialized!
[    3.096295] ipu3-cio2 0000:00:14.3: Entity type for entity ipu3-csi2 2 was not initialized!
[    3.096340] ipu3-cio2 0000:00:14.3: Entity type for entity ipu3-csi2 3 was not initialized!
[    3.195909] ipu3-imgu 0000:00:05.0: loaded firmware version irci_irci_ecr-master_20161208_0213_20170112_1500, 17 binaries, 1212984 bytes




When start cheese program, in the syslog fie is presente:

> 
May  8 22:30:23 extreme kernel: [ 1212.813374] pcieport 0000:00:1d.0: AER: Corrected error received: 0000:00:1d.0
May  8 22:30:23 extreme kernel: [ 1212.813382] pcieport 0000:00:1d.0: PCIe Bus Error: severity=Corrected, type=Data Link Layer, (Transmitter ID)
May  8 22:30:23 extreme kernel: [ 1212.813385] pcieport 0000:00:1d.0:   device [8086:9d1b] error status/mask=00001000/00002000
May  8 22:30:23 extreme kernel: [ 1212.813387] pcieport 0000:00:1d.0:    [12] Timeout               
May  8 22:30:25 extreme gnome-shell[1472]: g_environ_setenv: assertion 'value != NULL' failed
May  8 22:30:25 extreme dbus-daemon[1321]: [session uid=1000 pid=1321] Activating service name='org.gnome.Cheese' requested by ':1.13' (uid=1000 pid=1472 comm="/usr/bin/gnome-shell " label="unconfined")
May  8 22:30:25 extreme dbus-daemon[1321]: [session uid=1000 pid=1321] Successfully activated service 'org.gnome.Cheese'
May  8 22:30:25 extreme /usr/lib/gdm3/gdm-x-session[1311]: (II) modeset(0): EDID vendor "SHP", prod id 5257
May  8 22:30:25 extreme /usr/lib/gdm3/gdm-x-session[1311]: (II) modeset(0): Printing DDC gathered Modelines:
May  8 22:30:25 extreme /usr/lib/gdm3/gdm-x-session[1311]: (II) modeset(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.6 kHz eP)
May  8 22:30:25 extreme kernel: [ 1214.515485] ipu3-imgu 0000:00:05.0: required queues are disabled
May  8 22:30:25 extreme kernel: [ 1214.515488] ipu3-imgu 0000:00:05.0: required queues are disabled
May  8 22:30:25 extreme kernel: [ 1214.516012] ipu3-imgu 0000:00:05.0: required queues are disabled
May  8 22:30:25 extreme kernel: [ 1214.516015] ipu3-imgu 0000:00:05.0: required queues are disabled
May  8 22:30:25 extreme org.gnome.Shell.desktop[1472]: Window manager warning: last_focus_time (1214337000) is greater than comparison timestamp (1214630).  This most likely represents a buggy client sending inaccurate timestamps in messages such as _NET_ACTIVE_WINDOW.  Trying to work around...
May  8 22:30:25 extreme kernel: [ 1214.571618] ipu3-imgu 0000:00:05.0: required queues are disabled
May  8 22:30:25 extreme kernel: [ 1214.571622] ipu3-imgu 0000:00:05.0: required queues are disabled
May  8 22:30:25 extreme kernel: [ 1214.594710] ipu3-imgu 0000:00:05.0: required queues are disabled
May  8 22:30:25 extreme kernel: [ 1214.604180] ipu3-imgu 0000:00:05.0: required queues are disabled
May  8 22:30:25 extreme kernel: [ 1214.604183] ipu3-imgu 0000:00:05.0: required queues are disabled
May  8 22:30:25 extreme kernel: [ 1214.619685] ipu3-imgu 0000:00:05.0: required queues are disabled
May  8 22:30:25 extreme cheese[9544]: Device '/dev/video2' has no supported format: gstv4l2object.c(3748): gst_v4l2_object_set_format_full (): /GstCameraBin:camerabin/GstWrapperCameraBinSrc:camera_source/GstBin:bin18/GstV4l2Src:v4l2src1:#012Call to TRY_FMT failed for NV12 @ 640x480: Invalid argument


Device is found but there is a not supported format problem. This problem is the same for other video device (from /dev/video0 to /dev/video9)

Does cams of your Galaxy Book 12 work correctly?
Bye
Marco

---

### Post by yaazzz on 2019-05-10
No the webcam of my GB12 is not working. So we are in the same situation.

---

### Post by mspezia on 2019-05-11
[FONT=DejaVu Sans]I have installed again Windows 10 for abstains details about these webcams because I didn't found anything on web. So, there are the following two cam:
  
OV5670
OV8858

[/FONT]

---

### Post by waterhead on 2019-05-16
I have a Thinkpad X1, with a similar problem. Until recently no driver was loading. After a kernel upgrade the ipu3-imgu module showed up, and a series video devices also were created. But the camera still doesn't work.

I found an old bug report ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1812114)](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1812114)) about this module it states that this driver is new and still under development. Apparently a driver "stack" is being developed for these type of embedded devices.

[https://www.libcamera.org/](https://www.libcamera.org/)

---

### Post by mspezia on 2019-05-16
I see that in the kernel 5.1.1 is present driver for OV5670 (not compiled) but not for OV8858. This is present in Linux kernels 4.12&#8211;4.14 ([https://cateee.net/lkddb/web-lkddb/VIDEO_OV8858.html](https://cateee.net/lkddb/web-lkddb/VIDEO_OV8858.html))
So, now modify my kernel insert OV5670 and after this I'll check if  at least one cam will work....

---

### Post by mspezia on 2019-05-16
...for ov8858 I see that It currently only works with the atomisp driver that is present but non compiled

---

### Post by waterhead on 2019-05-17
I should have mentioned, these are the devices that Windows lists are on my Thinkpad:
OV2740
OV8858

---

