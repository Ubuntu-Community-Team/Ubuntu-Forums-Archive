---
title: "I don't see my USB ports in Ubuntu 9.10"
date: 2009-12-27
forum: Hardware
---

### Post by rva1945 on 2009-12-27
I know I have to mount them or something like that (new to Linux, sorry).

I'd appreciate any help.

Thanks

---

### Post by rva1945 on 2009-12-27
> **rva1945 said:**
> I know I have to mount them or something like that (new to Linux, sorry).

I'd appreciate any help.

Thanks

Well, to be true, when I insert a USB pend drive, it appears in Media window, I can see it listed by lsusb command. If I connect the digital camera to another the USB port, the USB pen drive disappears. I see the camera listed by lsusb but can't access to its files.

It seems as if I have to mount the camera, maybe because it's a different USB port?

---

### Post by chewearn on 2009-12-27
It should be completely plug'n play.  Gone are the days when you have to type cryptic mount command line to get access USB devices.

Something is not quite right, somewhere.  It would be helpful if you could:

1. tell us the make/model of the said digital camera.

Plug in the camera, wait a few seconds:
2. post the output of lsusb
3. post the output of command:

```

dmesg | tail -n 20

```

---

### Post by rva1945 on 2009-12-27
> **chewearn said:**
> It should be completely plug'n play.  Gone are the days when you have to type cryptic mount command line to get access USB devices.

Something is not quite right, somewhere.  It would be helpful if you could:

1. tell us the make/model of the said digital camera.

Plug in the camera, wait a few seconds:
2. post the output of lsusb
3. post the output of command:

```

dmesg | tail -n 20

```

Well it seems to be plug'n play...excepto for the camera.
When I connect my 512 MB Kingston, the FIle Browser pops up showing the folders in it.
Then this is the output of lsusb:
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0930:6533 Toshiba Corp. 512M Stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2624 Pixart Imaging, Inc. WebCam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Then I connect the Sony W55 to another  USB port: no file browser pop up, it simply vanishes, and this is the lsusb output:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 054c:0010 Sony Corp. DSC-S30/S70/S75/F505V/F505/FD92/W1 Cybershot/Mavica Digital Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2624 Pixart Imaging, Inc. WebCam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

But I can't acces it. Then I unplug the camera, the Kingston (which I didn't unplug) doesn't return, and this is the lsusb output:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2624 Pixart Imaging, Inc. WebCam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

No Kingston pen drive, no Sony Camera. But if I now plug the pen drive to the same USB port I used for the camera, the pen drive is again detected.

Of course I switched ports, but with the same result: the Kingston pen drive is detected, not the Sony Camera. And if I plug the camera while the Kingston is plugged, this is "logically unplugged".

By the way, I installed the Tux Commander, I love those two panels style file managers, but can't see the hard disk (to access WXP file system) or the pen drive, when pllugged.

Thanks. I'm loving Ubuntu since I installed it, yesterday.

Robert

---

### Post by chewearn on 2009-12-27
Could you also post the output of:

```

dmesg | tail -n 20

```

This will show the messages from the kernel when the Sony camera is plugged in.


As for the second question: the automount of USB drives will shown up under directory: /media

---

### Post by chewearn on 2009-12-27
Found this thread:
[http://ubuntuforums.org/showthread.php?t=463711](http://ubuntuforums.org/showthread.php?t=463711)

Basically, set the camera to use either "USB mass storage" or "PTP" mode.

---

### Post by rva1945 on 2009-12-27
> **chewearn said:**
> Could you also post the output of:

```

dmesg | tail -n 20

```This will show the messages from the kernel when the Sony camera is plugged in.


As for the second question: the automount of USB drives will shown up under directory: /media

Here it goes:
robert@rvasystem:~$ dmesg | tail -n 20
[ 3013.640217] sd 4:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 3013.640220] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3013.649456] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3013.649466]  sdb: sdb1
[ 3013.661593] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3013.661603] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 3088.888040] usb 1-7: new high speed USB device using ehci_hcd and address 8
[ 3089.022424] usb 1-7: configuration #1 chosen from 2 choices
[ 3090.212182] usb 1-4: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 128 rq 6 len 1000 ret -110
[ 3090.532051] usb 1-4: reset high speed USB device using ehci_hcd and address 7
[ 3090.601645] ehci_hcd 0000:00:1d.7: port 4 reset error -110
[ 3090.601666] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 3090.804167] usb 1-4: USB disconnect, address 7
[ 3106.256179] usb 1-7: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 33 rq 102 len 0 ret -110
[ 3122.256186] usb 1-7: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 33 rq 102 len 0 ret -110
[ 3138.256188] usb 1-7: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 33 rq 102 len 0 ret -110
[ 3264.260846] usb 1-7: USB disconnect, address 8
[ 4783.396488] usb 1-4: new high speed USB device using ehci_hcd and address 9
[ 4783.534550] usb 1-4: configuration #1 chosen from 2 choices
[ 4799.900962] usb 1-4: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 33 rq 102 len 0 ret -110
robert@rvasystem:~$

---

### Post by chewearn on 2009-12-27
As mentioned, try setting the camera to USB mass storage mode.  If that doesn't work, try PTP mode.

As a last resort, you probably need to remove and access the camera's flash card via a card reader.

---

### Post by rva1945 on 2009-12-27
> **chewearn said:**
> As mentioned, try setting the camera to USB mass storage mode.  If that doesn't work, try PTP mode.

As a last resort, you probably need to remove and access the camera's flash card via a card reader.

Do you mean I have to alter the camera settings, in the camera? Well, at least it works in WXP, I expected to access it the same way, as a storage device.

---

### Post by chewearn on 2009-12-27
Yes, if you read the thread I mentioned, you need to go into the camera settings and change it from "auto".

Why is this not needed in WinXP?  Well, probably Sony wrote the driver for WinXP to be able to handle "auto".  But the Linux guys don't have such help and have to rely on generic USB mass storage or PTP, which were well documented protocols.

---

