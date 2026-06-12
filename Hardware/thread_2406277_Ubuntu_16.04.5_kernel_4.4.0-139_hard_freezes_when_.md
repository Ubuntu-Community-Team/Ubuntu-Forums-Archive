---
title: "Ubuntu 16.04.5 kernel 4.4.0-139 hard freezes when unmounting USB drive"
date: 2018-11-18
forum: Hardware
---

### Post by kpatz on 2018-11-18
I have a machine running as a file server on Ubuntu 16.04.5.  After the latest kernel update (4.4.0-139-generic #165-Ubuntu SMP Wed Oct 24 10:58:50 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux) I am having a problem.

I backup this server by mounting an external 4 TB external USB HDD, which is formatted with LUKS encryption and ext4.  It mounts fine, I can do my backup, but when I unmount it (by right clicking the icon in the task bar and clicking Safely Remove), the entire system freezes hard... no mouse, no keyboard, Ctrl-Alt-Del doesn't work, etc.  I have to hit the reset button to reboot.

I normally run these backups weekly and this is the first time I've had this problem, so I think it's related to the latest kernel update.  I backup to two of these external drives, I'm trying the other one now to see what happens, but I'll have to post this before I attempt to unmount since I'll lose my post if the machine freezes again.

With the drive mounted, lsusb returns:
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 002: ID 0411:0257 BUFFALO INC. (formerly MelCo., Inc.) 
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 002: ID 051d:0003 American Power Conversion UPS
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```The **Bus 009 Device 002: ID 0411:0257 BUFFALO INC. (formerly MelCo., Inc.) ** is the external drive.

dmesg | grep usb returns:

```
[  439.851502] usb 9-2: new SuperSpeed USB device number 2 using xhci_hcd
[  439.871513] usb 9-2: New USB device found, idVendor=0411, idProduct=0257
[  439.871522] usb 9-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  439.871527] usb 9-2: Product: HD-LCU3
[  439.871531] usb 9-2: Manufacturer: BUFFALO
[  439.871535] usb 9-2: SerialNumber: 000000090000A83E
[  439.903822] usb-storage 9-2:1.0: USB Mass Storage device detected
[  439.904059] scsi host6: usb-storage 9-2:1.0
[  439.904656] usbcore: registered new interface driver usb-storage
[  439.907133] usbcore: registered new interface driver uas

```

Once again, mounting isn't the issue.  Unmounting is causing the hard freeze.  I'm going to try manually unmounting, closing the LUKS volume, and then unplugging the drive and see what happens.

---

### Post by kpatz on 2018-11-18
Update:  Manually unmounting etc. worked.  But when I right clicked and chose Safely Remove, which just disconnects the USB driver, the GUI hung but i could still access the server via SSH.  I tried remounting the drive but with the GUI hung it didn't mount automatically.  I then unplugged the drive and the kernel hard hung again.

I manually booted the previous kernel (4.4.0-138) and the USB drive mount/dismount work correctly again.  So it's an issue with the -139 kernel.

Anyone else seeing similar problems with 4.4.0-139?

---

### Post by ciniset on 2018-11-18
same thing with ubuntu 14.04 kernel 4.4.0-139 but only on usb 3.0. 
on usb 2.0 things are OK.

---

### Post by j-k-vanamerongen-uu on 2018-11-26
Same thing here with ubuntu 16.04 and kernel 4.4.0-139

---

### Post by kreuvf on 2018-11-28
This appears to be a kernel bug. There is a [bug report on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1803929"), so this will hopefully get fixed with the next kernel. But adding some heat to that bug probably won't hurt ... ;)

---

### Post by kpatz on 2018-12-08
From reading it appears that 4.4.0-140 still has the issue.  Have to wait impatiently for 4.4.0.141 I guess.

In the meantime I've uninstalled 4.4.0-139 and am not installing 4.4.0-140.

I used the command **sudo apt-mark hold 4.4.0-138-generic** to stay at 138 until this issue is resolved.

---

### Post by alien62 on 2018-12-30
The same problem here withUbuntu 16.04.5 LTS, kernel **4.4.0-141 :(**

---

### Post by MartyBuntu on 2018-12-30
Same problem persists with the **4.4.0-141-lowlatency** kernel using Ubuntu Studio 14.04. Seems to only affect USB 3.0 ports.

---

### Post by isagarran2 on 2019-01-11
Hello,
I got the same issue whatever the USB drive is. I have a Lenovo P50.
```
~$ uname -a
Linux HanaYoriDango 4.4.0-141-generic #167-Ubuntu SMP Wed Dec 5 10:40:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

~$ uname -r
4.4.0-141-generic

~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.5 LTS
Release:    16.04
Codename:    xenial
```

I didn't try unmounting using command line but if it is a bypass, it will fit for a while. I'll try.
If you are aware of any patch, I'll be glad too :)
Isagarran

---

### Post by djao on 2019-01-15
One workaround is to install a newer kernel such as the HWE kernel:
```
apt-get install --install-recommends linux-generic-hwe-16.04
```
(or linux-lowlatency-hwe-16.04, etc. if you need something else)

---

### Post by kpatz on 2019-02-10
Looks like 4.4.0-142 finally fixes this.  Updated last night, did my weekly backup to my 2 USB 3.0 drives, and I can unmount them without locking up.

---

