---
title: "USB stick not recognized after incorrect unplug"
date: 2017-03-22
forum: Hardware
---

### Post by pehuenr on 2017-03-22
Hi, I've been looking around and I haven't been able to find a possible solution to this.

I've got an usb stick which might have been incorrectly unplugged; causing it to stop being recognized. 

I already tried shutting the PC down, disconnect from the power source, and then power back on. But that doesn't work; I would not say it is not a power supply issue cause I've tried different ports, different PC. So it seems to be somehow corrupted. **I'm wondering if it can be fixed, by forcing the USB to be recognized and formatted**. Or maybe it's bricked and that's all there is to it.

lsblk shows only sda (main HD on an Dell Inspiron), sdb (the hybrid SDD part) and sr0 (guess it's the DVD?).

```
sda      8:0    0 465,8G  0 disk 
&#9500;&#9472;sda1   8:1    0   500M  0 part /boot/efi
&#9500;&#9472;sda2   8:2    0    40M  0 part 
&#9500;&#9472;sda3   8:3    0   128M  0 part 
&#9500;&#9472;sda4   8:4    0   490M  0 part 
&#9500;&#9472;sda5   8:5    0 341,5G  0 part 
&#9500;&#9472;sda6   8:6    0   450M  0 part 
&#9492;&#9472;sda7   8:7    0 122,7G  0 part /home
sdb      8:16   0  29,8G  0 disk 
&#9500;&#9472;sdb1   8:17   0     8G  0 part 
&#9500;&#9472;sdb2   8:18   0   513M  0 part 
&#9500;&#9472;sdb3   8:19   0  17,4G  0 part /
&#9492;&#9472;sdb4   8:20   0     4G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom
```

There's a portion of dmesg which raises after I plug the USB in. I know because same happens when I plug the usb on terminal mode (ctrl alt f1):

```
[ 1231.145133] usb 3-1: new full-speed USB device number 2 using xhci_hcd[ 1231.257177] usb 3-1: device descriptor read/64, error -71
[ 1231.473071] usb 3-1: device descriptor read/64, error -71
[ 1231.689087] usb 3-1: new full-speed USB device number 3 using xhci_hcd
[ 1231.801043] usb 3-1: device descriptor read/64, error -71
[ 1232.017047] usb 3-1: device descriptor read/64, error -71
[ 1232.233038] usb 3-1: new full-speed USB device number 4 using xhci_hcd
[ 1232.233348] usb 3-1: Device not responding to setup address.
[ 1232.437283] usb 3-1: Device not responding to setup address.
[ 1232.640994] usb 3-1: device not accepting address 4, error -71
[ 1232.752982] usb 3-1: new full-speed USB device number 5 using xhci_hcd
[ 1232.753272] usb 3-1: Device not responding to setup address.
[ 1232.957260] usb 3-1: Device not responding to setup address.
[ 1233.160908] usb 3-1: device not accepting address 5, error -71
[ 1233.160961] usb usb3-port1: unable to enumerate USB device
```

---

### Post by vanadium on 2017-03-22
That could be a failing USB stick. I currently have a 2 GB USB hard drive that sometimes is not recognized, with similar error messages: I probably will need to replace it.

---

### Post by jeff666 on 2017-03-23
i would say bricked i think the setup addresses is the first point in memory where the usb is told to write to, to start the boot strap process to "unofficially" mount in the kernel. good thing they are cheap! It could just have a bad crystal or capacitor as well, causing it to fail a usb is a simple computer. hdparm is a utilite that might be able to repair devices but im not sure how it interfaces does 'lsusb' yeild anything although you still might be out of luck it needs to mount in the kernel to produce /dev/sdb and with out that i don't think hdparm will do much

---

### Post by sudodus on 2017-03-23
Are there important data on the USB stick that you want to recover? Or would you be happy to create a new partition table and file system on the drive? There are different things to do depending on the answer to those questions.

See these links for more details,

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

