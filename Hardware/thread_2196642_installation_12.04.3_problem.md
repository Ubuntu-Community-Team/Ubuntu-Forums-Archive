---
title: "installation 12.04.3 problem"
date: 2013-12-30
forum: Hardware
---

### Post by buktoria92 on 2013-12-30
after installation ubuntu(64 bit) i looked logs(/var/log/installer/syslog) it contains errors
```
Dec 30 20:55:28 ubuntu ubiquity: WARNING:root:modinfo for module wl failed: ERROR: modinfo: could not find module wl
Dec 30 20:55:28 ubuntu ubiquity: 
Dec 30 20:55:28 ubuntu ubiquity: WARNING:root:modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet
Dec 30 20:55:28 ubuntu ubiquity: 
Dec 30 20:55:28 ubuntu ubiquity: WARNING:root:modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci
Dec 30 20:55:28 ubuntu ubiquity: 
Dec 30 20:55:28 ubuntu ubiquity: WARNING:root:modinfo for module fglrx_experimental_12 failed: ERROR: modinfo: could not find module fglrx_experimental_12
Dec 30 20:55:28 ubuntu ubiquity: 
Dec 30 20:55:30 ubuntu ubiquity: WARNING:root:modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates
Dec 30 20:55:30 ubuntu ubiquity: 
Dec 30 20:55:32 ubuntu ubiquity: WARNING:root:modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9
Dec 30 20:55:32 ubuntu ubiquity: 
Dec 30 20:55:33 ubuntu ubiquity: WARNING:root:modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
Dec 30 20:55:33 ubuntu ubiquity: 
Dec 30 20:55:36 ubuntu ubiquity: WARNING:root:modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
Dec 30 20:55:36 ubuntu ubiquity: 
Dec 30 20:55:39 ubuntu ubiquity: WARNING:root:modinfo for module fglrx_experimental_13 failed: ERROR: modinfo: could not find module fglrx_experimental_13
Dec 30 20:55:39 ubuntu ubiquity: 
Dec 30 20:55:40 ubuntu ubiquity: WARNING:root:modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx
Dec 30 20:55:40 ubuntu ubiquity: 
Dec 30 20:55:40 ubuntu ubiquity: WARNING:root:modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr
Dec 30 20:55:40 ubuntu ubiquity: 
Dec 30 20:55:41 ubuntu ubiquity: WARNING:root:modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304
Dec 30 20:55:41 ubuntu ubiquity: 
Dec 30 20:55:44 ubuntu ubiquity: WARNING:root:modinfo for module nvidia_304_updates failed: ERROR: modinfo: could not find module nvidia_304_updates
Dec 30 20:55:44 ubuntu ubiquity: 
Dec 30 20:55:48 ubuntu ubiquity: WARNING:root:modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates
Dec 30 20:55:48 ubuntu ubiquity: 
Dec 30 20:55:48 ubuntu ubiquity: WARNING:root:modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304
Dec 30 20:55:48 ubuntu ubiquity: 
Dec 30 20:55:48 ubuntu ubiquity: WARNING:root:modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current
Dec 30 20:55:48 ubuntu ubiquity: 
Dec 30 20:55:48 ubuntu ubiquity: WARNING:root:modinfo for module nvidia_319 failed: ERROR: modinfo: could not find module nvidia_319
Dec 30 20:55:48 ubuntu ubiquity: 
Dec 30 20:55:50 ubuntu ubiquity: WARNING:root:modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173
Dec 30 20:55:50 ubuntu ubiquity: 
Dec 30 20:55:54 ubuntu ubiquity: WARNING:root:modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates
Dec 30 20:55:54 ubuntu ubiquity: 
Dec 30 20:56:01 ubuntu ubiquity: WARNING:root:modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310
Dec 30 20:56:01 ubuntu ubiquity: 
Dec 30 20:56:01 ubuntu ubiquity: WARNING:root:modinfo for module nvidia_319_updates failed: ERROR: modinfo: could not find module nvidia_319_updates
Dec 30 20:56:01 ubuntu ubiquity: 
Dec 30 20:56:03 ubuntu ubiquity: WARNING:root:modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96
Dec 30 20:56:03 ubuntu ubiquity: 
Dec 30 20:56:05 ubuntu ubiquity: WARNING:root:modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates
Dec 30 20:56:05 ubuntu ubiquity: 
Dec 30 20:56:07 ubuntu ubiquity: WARNING:root:modinfo for module fglrx_experimental_13 failed: ERROR: modinfo: could not find module fglrx_experimental_13
Dec 30 20:56:07 ubuntu ubiquity: 
Dec 30 20:56:08 ubuntu ubiquity: WARNING:root:modinfo for module fglrx_experimental_12 failed: ERROR: modinfo: could not find module fglrx_experimental_12
Dec 30 20:56:08 ubuntu ubiquity: 
Dec 30 20:56:09 ubuntu ubiquity: WARNING:root:modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9
Dec 30 20:56:09 ubuntu ubiquity: 
Dec 30 20:56:10 ubuntu ubiquity: WARNING:root:modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates
Dec 30 20:56:10 ubuntu ubiquity: 
Dec 30 20:56:13 ubuntu ubiquity: WARNING:root:modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
```
In System settings>Additional drivers
[IMG]http://s29.postimg.org/v2kxk5bg7/Screenshot_from_2013_12_31_02_24_58.png[/IMG]

How to activate driver?This driver is suitable for steam games? Or do I need to install the latest driver from the official website of AMD (with its installation I have problems, too)?

my hardware:
mb: Asrock p55 pro
cpu: i7 860
gpu: hd7850 (Asus HD7850-DC-1GD5)

---

### Post by QIII on 2013-12-30
Hello!

Is your machine a laptop with hybrid Intel/ATI graphics, by chance?

---

### Post by buktoria92 on 2013-12-30
Hello.
No. i am updated my post and writed hardware specifications. my machine is a desktop PC without integrated videocard

---

### Post by buktoria92 on 2013-12-30
i checked my usb flash drive (sudo badblocks -v /dev/sdb) - 0 errors. I checked md5 sum of iso - it's ok. Now I try to burn the image via dd(sudo dd if=/home/boris/ubuntu-12.04.3-desktop-amd64.iso of=/dev/sdb). before recorded via unebootin under windows. I will write about the results after reinstalling system

---

### Post by buktoria92 on 2013-12-30
I reinstalled ubuntu. the problem persists.
installation log (/var/log/installer/syslog)
[http://pastebin.com/Xe6sPABL](http://pastebin.com/Xe6sPABL)


what can i try to resolve this problem?

---

