---
title: "Corrupted usb stick"
date: 2012-05-24
forum: Hardware
---

### Post by ChoPnGo on 2012-05-24
Hi
I've got usb stick that is not working neither on Ubuntu nor on Win.

On connect:
```

May 24 18:08:55 vovanb-laptop kernel: [ 7318.732690] usb 2-1.1: new high-speed USB device number 18 using ehci_hcd
May 24 18:08:55 vovanb-laptop kernel: [ 7318.827978] usb-storage 2-1.1:1.0: Quirks match for vid 058f pid 6387: 400
May 24 18:08:55 vovanb-laptop kernel: [ 7318.828028] scsi14 : usb-storage 2-1.1:1.0
May 24 18:08:55 vovanb-laptop mtp-probe: checking bus 2, device 18: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1"
May 24 18:08:55 vovanb-laptop mtp-probe: bus: 2, device: 18 was not an MTP device
May 24 18:09:17 vovanb-laptop kernel: [ 7340.513364] usb 2-1.1: reset high-speed USB device number 18 using ehci_hcd
May 24 18:09:17 vovanb-laptop kernel: [ 7340.701149] usb 2-1.1: reset high-speed USB device number 18 using ehci_hcd
May 24 18:09:23 vovanb-laptop kernel: [ 7346.868826] usb 2-1.1: reset high-speed USB device number 18 using ehci_hcd
May 24 18:09:23 vovanb-laptop kernel: [ 7347.036460] usb 2-1.1: reset high-speed USB device number 18 using ehci_hcd
May 24 18:09:23 vovanb-laptop kernel: [ 7347.220117] usb 2-1.1: reset high-speed USB device number 18 using ehci_hcd
May 24 18:09:23 vovanb-laptop kernel: [ 7347.313940] scsi 14:0:0:0: Device offlined - not ready after error recovery

```disconnect
```
May 24 18:10:12 vovanb-laptop kernel: [ 7395.690143] usb 2-1.1: USB disconnect, device number 18
```It is corectly shown by lsusb. Silence from fdisk. /dev/sdb is not created.
How can I fix it with/without losing data?

---

### Post by 2F4U on 2012-05-24
There are some freeware utilities available, such as PC Inspector, depending on the filesystem on the stick and the operating system you want to use. You can also look for professional help.

---

### Post by km3952 on 2012-05-24
Before attempting to recover anything from the pendrive, make a copy using a block copying program like dd, then work on the copy.

---

### Post by sudodus on 2012-05-24
> **km3952 said:**
> Before attempting to recover anything from the pendrive, make a copy using a block copying program like dd, then work on the copy.
+1
dd or ddrescue.

And on the copy you can try to restore the file system, for example in Windows with ```
chkdsk /f
``` or some special rescue disk as suggested before. You can also try to recover file data directly using ***PhotoRec*** (you find descriptions and tutorials on the internet).

---

### Post by ChoPnGo on 2012-05-25
How can I use dd or chkdsk when I can't specify the device to copy from or the drive to check?
Other utilities (like testdisk for example) ask me to choose the drive too. But there is only sda (hard drive) in list.

---

### Post by sudodus on 2012-05-25
> **ChoPnGo said:**
> How can I use dd or chkdsk when I can't specify the device to copy from or the drive to check?
Other utilities (like testdisk for example) ask me to choose the drive too. But there is only sda (hard drive) in list.

I see. I was not reading your first post carefully enough. Yes, those programs need that the system can see the drive (for example as /dev/sdb).

I found another thread about a similar issue. Maybe you can try if the solution of the thread works for you too.
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1586206_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1586206")
(I found it searching the internet for ***fdisk cannot see usb***)

---

