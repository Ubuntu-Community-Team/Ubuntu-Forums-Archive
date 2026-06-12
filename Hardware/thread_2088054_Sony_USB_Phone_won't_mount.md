---
title: "Sony USB Phone won't mount"
date: 2012-11-25
forum: Hardware
---

### Post by Thyrosis on 2012-11-25
Hello all,

I've been searching all over the internet the whole day, and can't seem to find a definitive answer. If I missed a post somewhere and you know of it, please tell me off and refer me to the post :)

Anyway, the problem is this: I'm running Xubuntu and want to connect my Sony Experia U phone via USB to transfer files. But, whatever I try, and can't seem to get it to work. Plugging in the phone gives me the following outputs:

syslog during startup
```

Nov 25 16:26:28 MrtHP kernel: [    1.700034] usb 2-3: new high-speed USB device number 2 using ehci_hcd
Nov 25 16:26:28 MrtHP kernel: [    1.832956] usb 2-3: Dual-Role OTG device on non-HNP port
Nov 25 16:26:28 MrtHP kernel: [    1.833452] usb 2-3: New USB device found, idVendor=0fce, idProduct=0171
Nov 25 16:26:28 MrtHP kernel: [    1.833455] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov 25 16:26:28 MrtHP kernel: [    1.833457] usb 2-3: Product: SEMC HSUSB Device
Nov 25 16:26:28 MrtHP kernel: [    1.833460] usb 2-3: Manufacturer: SEMC
Nov 25 16:26:28 MrtHP kernel: [    1.833462] usb 2-3: SerialNumber: BX9030QJRS

// And, after disconnect/connect as described below:
Nov 25 16:46:26 MrtHP kernel: [ 1216.815782] Initializing USB Mass Storage driver...
Nov 25 16:46:26 MrtHP kernel: [ 1216.815864] usbcore: registered new interface driver usb-storage
Nov 25 16:46:26 MrtHP kernel: [ 1216.815866] USB Mass Storage support registered.
Nov 25 16:46:40 MrtHP kernel: [ 1230.532016] usb 2-3: USB disconnect, device number 2
Nov 25 16:46:59 MrtHP kernel: [ 1249.700038] usb 2-3: new high-speed USB device number 3 using ehci_hcd
Nov 25 16:46:59 MrtHP kernel: [ 1249.832963] usb 2-3: Dual-Role OTG device on non-HNP port
Nov 25 16:46:59 MrtHP kernel: [ 1249.833087] usb 2-3: New USB device found, idVendor=0fce, idProduct=0171
Nov 25 16:46:59 MrtHP kernel: [ 1249.833091] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov 25 16:46:59 MrtHP kernel: [ 1249.833094] usb 2-3: Product: SEMC HSUSB Device
Nov 25 16:46:59 MrtHP kernel: [ 1249.833096] usb 2-3: Manufacturer: SEMC
Nov 25 16:46:59 MrtHP kernel: [ 1249.833099] usb 2-3: SerialNumber: BX9030QJRS

```

dmesg
```

[    1.700034] usb 2-3: new high-speed USB device number 2 using ehci_hcd
[    1.832956] usb 2-3: Dual-Role OTG device on non-HNP port
[    1.833452] usb 2-3: New USB device found, idVendor=0fce, idProduct=0171
[    1.833455] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.833457] usb 2-3: Product: SEMC HSUSB Device
[    1.833460] usb 2-3: Manufacturer: SEMC
[    1.833462] usb 2-3: SerialNumber: BX9030QJRS

```

or, after inserting extra modules (using modprobe hid, usbhid and usb_storage) followed by disconnecting and connecting:
```

[ 1216.815782] Initializing USB Mass Storage driver...
[ 1216.815864] usbcore: registered new interface driver usb-storage
[ 1216.815866] USB Mass Storage support registered.
[ 1230.532016] usb 2-3: USB disconnect, device number 2
[ 1249.700038] usb 2-3: new high-speed USB device number 3 using ehci_hcd
[ 1249.832963] usb 2-3: Dual-Role OTG device on non-HNP port
[ 1249.833087] usb 2-3: New USB device found, idVendor=0fce, idProduct=0171
[ 1249.833091] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1249.833094] usb 2-3: Product: SEMC HSUSB Device
[ 1249.833096] usb 2-3: Manufacturer: SEMC
[ 1249.833099] usb 2-3: SerialNumber: BX9030QJRS

```

lsusb
```

// on startup
Bus 002 Device 002: ID 0fce:0171 Sony Ericsson Mobile Communications AB 

// after disconnect/connect
Bus 002 Device 003: ID 0fce:0171 Sony Ericsson Mobile Communications AB 

```


```

# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000fc2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   304357375   152177664   83  Linux
/dev/sda2       304359422   312580095     4110337    5  Extended
/dev/sda5       304359424   312580095     4110336   82  Linux swap / Solaris


```

The only thing I haven't tried is mounting the phone, purely for the fact that I don't know where to mount it from.

As you can see, I have done my homework. The most frustrating thing is that it works fine on my Fedora machine at work, but as I don't like Fedora that much and want to reinstall that PC too, I need to know whether connecting my phone is possible under Xubuntu too...

Can anyone give me any pointers towards the right direction?

Many thanks in advance!

---

### Post by TheMrWoodyGuy on 2012-12-13
As I understood Xperia U like many last produced Smartphones or tablets connect to PC as an multimedia device not as flash drive and you unable to connect it as a drive untill you have rooted device and installed "ROM Manager" than you have to do like that guy [http://www.youtube.com/watch?v=JQi8AORrZjI&feature=g-hist](http://www.youtube.com/watch?v=JQi8AORrZjI&feature=g-hist) 
Second way is to use Wifi and access your android by ftp connection using "wifi transfer" on android and "FileZilla" on Kubuntu
Third way is to install gMTP from [http://gmtp.sourceforge.net/#Downloads](http://gmtp.sourceforge.net/#Downloads) that program, works slowly but throught cable.
I use second way ))) it is the easiest one

---

### Post by Thyrosis on 2012-12-15
> **TheMrWoodyGuy said:**
> As I understood Xperia U like many last produced Smartphones or tablets connect to PC as an multimedia device not as flash drive and you unable to connect it as a drive untill you have rooted device and installed "ROM Manager" than you have to do like that guy [http://www.youtube.com/watch?v=JQi8AORrZjI&feature=g-hist](http://www.youtube.com/watch?v=JQi8AORrZjI&feature=g-hist) 
Second way is to use Wifi and access your android by ftp connection using "wifi transfer" on android and "FileZilla" on Kubuntu
Third way is to install gMTP from [http://gmtp.sourceforge.net/#Downloads](http://gmtp.sourceforge.net/#Downloads) that program, works slowly but throught cable.
I use second way ))) it is the easiest one

TheMrWoodyGuy, apologies for the late reply. I'd given up on this thread and hadn't spotted the notification.

That aside, as of now,  you are my hero! I've used the WiFi way you recommended, and got it working straight away! (Apart from the fact that the one I used doesn't seem to support FTP  transfers, or at least I haven't figured out how to connect it, but I won't mention it.) (Oh, I just mentioned it...)

Unfortunately, it works rather slow via the web-interface. And I'm talking 3kb/s kinda slow. That might be due to the fact that my router is downstairs and I'm on the first floor, so possibly it doesn't like going down the stairs only to go up again, but hey.  It's transferring, so I'm not complaining :D

Thanks again for the tip!

// Edit, installed a different app, FTPDroid. Have a guess what that supports... Still very slow though, but I'll live. Although getting 1.7GB of pictures at 1.1kb/s is rather, err... slow

---

