---
title: "Whats wrong with my iPod connection?!!!"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by dynasty144 on 2007-08-19
[  358.420000] usb 3-4: new high speed USB device using ehci_hcd and address 3
[  358.564000] usb 3-4: configuration #1 chosen from 2 choices
[  358.752000] usbcore: registered new interface driver libusual
[  358.780000] Initializing USB Mass Storage driver...
[  358.780000] scsi0 : SCSI emulation for USB Mass Storage devices
[  358.780000] usbcore: registered new interface driver usb-storage
[  358.780000] USB Mass Storage support registered.
[  358.780000] usb-storage: device found at 3
[  358.780000] usb-storage: waiting for device to settle before scanning
[  363.780000] usb-storage: device scan complete
[  363.784000] scsi 0:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[  510.864000] sda: Spinning up disk.....not responding...
[  855.928000] sda : READ CAPACITY failed.
[  855.928000] sda : status=1, message=00, host=0, driver=08
[  855.928000] sd: Current: sense key: Not Ready
[  855.928000]     Additional sense: Logical unit is in process of becoming ready
[  855.928000] sda: Write Protect is off
[  855.928000] sda: Mode Sense: 68 00 00 08
[  855.928000] sda: assuming drive cache: write through
[  855.928000] sd 0:0:0:0: Attached scsi removable disk sda
[ 1052.032000] sda: Spinning up disk.....not responding...
[ 1397.160000] sda : READ CAPACITY failed.
[ 1397.160000] sda : status=1, message=00, host=0, driver=08
[ 1397.160000] sd: Current: sense key: Not Ready
[ 1397.160000]     Additional sense: Logical unit is in process of becoming ready
[ 1397.160000] sda: Write Protect is off
[ 1397.160000] sda: Mode Sense: 68 00 00 08
[ 1397.160000] sda: assuming drive cache: write through
[ 1544.176000] sda: Spinning up disk.....not responding...
[ 1889.632000] sda : READ CAPACITY failed.
[ 1889.632000] sda : status=1, message=00, host=0, driver=08
[ 1889.632000] sd: Current: sense key: Not Ready
[ 1889.632000]     Additional sense: Logical unit is in process of becoming ready
[ 1889.636000] sda: Write Protect is off
[ 1889.636000] sda: Mode Sense: 68 00 00 08
[ 1889.636000] sda: assuming drive cache: write through


above is the dmesg of when i attempted connecting my iPod, the iPod still works, however i can't manage songs, videos, photos, or anything.  Whats wrong?!  I get the do not disconnect picture on my iPod when its connected to the computer.  But i can't do anything about it... i would even go as far to reformat it, but i dont know how to do that without connecting through the computer... any suggestions!?

---

### Post by linuxwizard on 2007-08-19
look over might be something that will help you

[https://help.ubuntu.com/community/PortableDevices/iPod](https://help.ubuntu.com/community/PortableDevices/iPod)

---

### Post by dynasty144 on 2007-08-19
I currently have Banshee and gtkpod, i used to use these apps to manage my iPod, however this last problem came up, and now there's no icon that appears on my desktop.  it appears to be a mounting problem... but i could be wrong.  thats why i connected the "dmesg" from the terminal.

the last link didn't help... thanks though... any other suggestions?

---

### Post by linuxwizard on 2007-08-19
Looks like alot of mounting problems try this if don't help try search in forum
[http://ubuntuforums.org/showthread.php?t=456687&highlight=iPod+connection](http://ubuntuforums.org/showthread.php?t=456687&highlight=iPod+connection)

---

