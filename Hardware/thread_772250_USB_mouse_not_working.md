---
title: "USB mouse not working"
date: 2008-04-28
forum: Hardware
---

### Post by Hauru on 2008-04-28
Hi recently installed Hardy, but the USB mouse is not working. It works on my dualboot windows though. 

typing dmesg | grep usb

[   44.607542] usbcore: registered new interface driver usbfs
[   44.607594] usbcore: registered new interface driver hub
[   44.634434] usbcore: registered new device driver usb
[   44.735738] usb usb1: configuration #1 chosen from 1 choice
[   44.838696] usb usb2: configuration #1 chosen from 1 choice
[   44.942589] usb usb3: configuration #1 chosen from 1 choice
[   45.058253] usb usb4: configuration #1 chosen from 1 choice
[   46.128966] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   51.317598] usb 1-2: string descriptor 0 read error: -110
[   51.317826] usb 1-2: configuration #0 chosen from 1 choice
[   51.317831] usb 1-2: config 0 descriptor??
[   56.313028] usb 1-2: can't set config #0, error -110
[ 2736.073953] usb usb4: USB disconnect, address 1
[ 9166.670335] usb 1-2: USB disconnect, address 2
[ 2748.989170] usb 1-2: new low speed USB device using uhci_hcd and address 3
[ 9199.496699] usb 1-2: device descriptor read/64, error -110
[ 2767.652288] usb 1-2: device descriptor read/64, error -110
[ 4261.220860] usb 1-2: new low speed USB device using uhci_hcd and address 4
[ 9251.426833] usb 1-2: device descriptor read/64, error -110
[ 2781.893355] usb 1-2: device descriptor read/64, error -110
[ 2782.109115] usb 1-2: new low speed USB device using uhci_hcd and address 5
[ 9305.329985] usb 1-2: device not accepting address 5, error -110
[ 9305.441967] usb 1-2: new low speed USB device using uhci_hcd and address 6
[ 4305.196015] usb 1-2: device not accepting address 6, error -110
[ 9850.521819] usb 1-1: new low speed USB device using uhci_hcd and address 7
[ 2960.062653] usb 1-1: device descriptor read/64, error -110
[ 9908.663550] usb 1-1: device descriptor read/64, error -110
[ 2970.357788] usb 1-1: new low speed USB device using uhci_hcd and address 8
[ 9928.070443] usb 1-1: device descriptor read/64, error -110
[ 9954.912019] usb 1-1: device descriptor read/64, error -110
[ 9955.127908] usb 1-1: new low speed USB device using uhci_hcd and address 9
[ 4605.961264] usb 1-1: device not accepting address 9, error -110
[ 4606.073238] usb 1-1: new low speed USB device using uhci_hcd and address 10
[ 2998.984163] usb 1-1: device not accepting address 10, error -110
[ 3014.531970] usb 1-1: new low speed USB device using uhci_hcd and address 11
[ 3029.560673] usb 1-1: device descriptor read/64, error -110
[ 3044.662804] usb 1-1: device descriptor read/64, error -110
[ 3044.878573] usb 1-1: new low speed USB device using uhci_hcd and address 12
[ 4709.726591] usb 1-1: device descriptor read/64, error -110
[ 3072.305523] usb 1-1: device descriptor read/64, error -110
[ 3072.521280] usb 1-1: new low speed USB device using uhci_hcd and address 13
[ 3082.378785] usb 1-1: device not accepting address 13, error -110
[ 3082.490678] usb 1-1: new low speed USB device using uhci_hcd and address 14
[ 4758.795095] usb 1-1: device not accepting address 14, error -110


Would appreciate any help with this issue! Thanks!

---

### Post by alex sun on 2008-05-21
Similar problem.
Mouse worked in Gusty, but it doesn't in Hardy.
In my grep there are only 2 mouse-related strings:

[   18.457701] input: A4Tech PS/2+USB Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input2
[   18.472509] input,hidraw0: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:0b.0-1

On connecting\disconnecting mouse during work grep retunes nothing.

Help please!

---

### Post by nicedude on 2008-05-21
try running the two command  below the first will update your systems USB known device list and the second will then list the devices detected. Paste the output of the second command so someone can see what is up with your USB devices

Update for USB device list

sudo update-usbids

Command to list USB devices

lsusb

In addition to output of command #2 please give your USB mouse brand & model as well as what version of Xubuntu or other OS is the one you are running.

Please answer those and I or others can better help figure out why your device isn't working

nicedude

---

### Post by alex sun on 2008-05-21
Updated USB device list with sudo update-usbids.
lsusb returns:
```

Bus 001 Device 007: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 006: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 001 Device 005: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 001 Device 003: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 0000:0000 

```
I'm running Ubuntu Hardy Heron 64bit and have tried A4-TECH OP-35D mouse and several other ones (Asus, Acer and HP) with same results.
In previous version of Ubuntu (Gusty 64bit) everything worked.

In log by grep there are only 2 mouse-related strings:
```

[ 18.457701] input: A4Tech PS/2+USB Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input2
[ 18.472509] input,hidraw0: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:0b.0-1

```
On connecting\disconnecting mouse during work grep returns nothing.

---

### Post by szako on 2008-08-01
> **nicedude said:**
> 

Update for USB device list

sudo update-usbids



stopped working in hardy a min ago, so googled ;)

worked!

thanks

---

### Post by lycopenehead on 2008-08-15
i was trying to connect my nokia 6100 ,its playing dead when i connect it,nothing happenes 

just as follows:

ale@adam:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


in the system log the following msgs just appeared when i connected the phone

Aug 15 23:41:57 adam kernel: [ 8969.671824] usb 2-2: new low speed USB device using uhci_hcd and address 11
Aug 15 23:41:57 adam kernel: [ 8969.791808] usb 2-2: device descriptor read/64, error -71
Aug 15 23:41:57 adam kernel: [ 8970.015776] usb 2-2: device descriptor read/64, error -71
Aug 15 23:41:57 adam kernel: [ 8970.231750] usb 2-2: new low speed USB device using uhci_hcd and address 12
Aug 15 23:41:58 adam kernel: [ 8970.351738] usb 2-2: device descriptor read/64, error -71
Aug 15 23:41:58 adam kernel: [ 8970.575751] usb 2-2: device descriptor read/64, error -71
Aug 15 23:41:58 adam kernel: [ 8970.791680] usb 2-2: new low speed USB device using uhci_hcd and address 13
Aug 15 23:41:58 adam kernel: [ 8971.204965] usb 2-2: device not accepting address 13, error -71
Aug 15 23:41:59 adam kernel: [ 8971.316886] usb 2-2: new low speed USB device using uhci_hcd and address 14
Aug 15 23:41:59 adam kernel: [ 8971.727543] usb 2-2: device not accepting address 14, error -71
Aug 15 23:43:37 adam kernel: [ 9077.681086] usb 2-2: new low speed USB device using uhci_hcd and address 15
Aug 15 23:43:37 adam kernel: [ 9077.801024] usb 2-2: device descriptor read/64, error -71
Aug 15 23:43:37 adam kernel: [ 9078.024986] usb 2-2: device descriptor read/64, error -71
Aug 15 23:43:37 adam kernel: [ 9078.241049] usb 2-2: new low speed USB device using uhci_hcd and address 16
Aug 15 23:43:37 adam kernel: [ 9078.360946] usb 2-2: device descriptor read/64, error -71
Aug 15 23:43:37 adam kernel: [ 9078.584923] usb 2-2: device descriptor read/64, error -71
Aug 15 23:43:38 adam kernel: [ 9078.800898] usb 2-2: new low speed USB device using uhci_hcd and address 17
Aug 15 23:43:38 adam kernel: [ 9079.448493] usb 2-2: device not accepting address 17, error -71
Aug 15 23:43:38 adam kernel: [ 9079.560478] usb 2-2: new low speed USB device using uhci_hcd and address 18
Aug 15 23:43:39 adam kernel: [ 9079.968424] usb 2-2: device not accepting address 18, error -71

and it was several pluging and unpluging attempts

please help

---

### Post by wbrown on 2008-08-22
Greetings: 

I am trying to get my Meizu mini player 8Gig to work and so far it doesn't.  I tried sudo update-usbids but that didn't do it. 

from lsusb

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0566:3002 Monterey International Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

and in dmesg

[  212.475170] usb 1-2: new high speed USB device using ehci_hcd and address 3
[  212.524170] usb 1-2: device descriptor read/64, error -71
[  212.618336] usb 1-2: device descriptor read/64, error -71
[  212.710600] usb 1-2: new high speed USB device using ehci_hcd and address 4
[  212.759232] usb 1-2: device descriptor read/64, error -71
[  212.853767] usb 1-2: device descriptor read/64, error -71
[  212.946399] usb 1-2: new high speed USB device using ehci_hcd and address 5
[  213.129100] usb 1-2: device not accepting address 5, error -71
[  213.175459] usb 1-2: new high speed USB device using ehci_hcd and address 6
[  213.357803] usb 1-2: device not accepting address 6, error -71
[  258.263014] usb 1-2: new high speed USB device using ehci_hcd and address 7
[  258.311541] usb 1-2: device descriptor read/64, error -71
[  258.405726] usb 1-2: device descriptor read/64, error -71
[  258.497989] usb 1-2: new high speed USB device using ehci_hcd and address 8
[  258.546514] usb 1-2: device descriptor read/64, error -71
[  316.447707] usb 1-2: new high speed USB device using ehci_hcd and address 9
[  316.496661] usb 1-2: device descriptor read/64, error -71
[  316.590877] usb 1-2: device descriptor read/64, error -71
[  316.683137] usb 1-2: new high speed USB device using ehci_hcd and address 10
[  316.731773] usb 1-2: device descriptor read/64, error -71
[  316.826302] usb 1-2: device descriptor read/64, error -71
[  316.918566] usb 1-2: new high speed USB device using ehci_hcd and address 11
[  317.101594] usb 1-2: device not accepting address 11, error -71
[  317.147956] usb 1-2: new high speed USB device using ehci_hcd and address 12
[  317.330339] usb 1-2: device not accepting address 12, error -71
[  329.269834] usb 1-2: new high speed USB device using ehci_hcd and address 13
[  329.318159] usb 1-2: device descriptor read/64, error -71
[  329.412548] usb 1-2: device descriptor read/64, error -71
[  329.504808] usb 1-2: new high speed USB device using ehci_hcd and address 14
[  329.553439] usb 1-2: device descriptor read/64, error -71
[  329.647669] usb 1-2: device descriptor read/64, error -71
[  329.739932] usb 1-2: new high speed USB device using ehci_hcd and address 15
[  329.922636] usb 1-2: device not accepting address 15, error -71
[  329.969000] usb 1-2: new high speed USB device using ehci_hcd and address 16
[  330.152012] usb 1-2: device not accepting address 16, error -71
[  332.636752] usb 1-2: new high speed USB device using ehci_hcd and address 17
[  332.685074] usb 1-2: device descriptor read/64, error -71
[  332.779605] usb 1-2: device descriptor read/64, error -71
[  332.871873] usb 1-2: new high speed USB device using ehci_hcd and address 18
[  332.920501] usb 1-2: device descriptor read/64, error -71
[  393.242872] usb 1-2: new high speed USB device using ehci_hcd and address 19
[  393.291213] usb 1-2: device descriptor read/64, error -71


Is there some other way I can debug this.  

Thanks for your help. 
Bill.

---

### Post by wbrown on 2008-08-23
Greetings: 

Found this on another thread and it fixed my issue: 

I typed "rmmod ehci-hcd" and everything came back up. Not sure how long this will last but hopefully it helps someone.

HTH
Bill.

---

