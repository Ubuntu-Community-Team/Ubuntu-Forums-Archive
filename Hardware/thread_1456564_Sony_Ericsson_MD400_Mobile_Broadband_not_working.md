---
title: "Sony Ericsson MD400 Mobile Broadband not working"
date: 2010-04-17
forum: Hardware
---

### Post by Noccy on 2010-04-17
I am still having troubles with my MD400 mobile broadband modem. It worked in 9.04, but then it stopped working in 9.10 and still isn't working in 10.04. 

I have tried using usb_modeswitch and wvdial but i can't seem to manage to connect. Besides, in 10.04 the modeswitch is only temporary as the device seem to revert (and /dev/ttyACMx goes away) after like 15 seconds. 

Are there any ideas or suggestions? 

Output from dmesg:
[INDENT][ 6879.004322] udev: starting version 151
[ 8851.945105] usb 1-3: new high speed USB device using ehci_hcd and address 3
[ 8852.080925] usb 1-3: configuration #1 chosen from 1 choice
[ 8853.684293] Initializing USB Mass Storage driver...
[ 8853.684596] usb-storage: device ignored
[ 8853.684734] usbcore: registered new interface driver usb-storage
[ 8853.685357] USB Mass Storage support registered.
[ 8874.809192] usb 1-3: USB disconnect, address 3
[ 8893.192083] usb 1-3: new high speed USB device using ehci_hcd and address 4
[ 8893.329622] usb 1-3: configuration #2 chosen from 1 choice
[ 8893.334194] usb-storage: device ignored
[ 8893.335213] usb-storage: device ignored
[ 8893.336469] usb-storage: device ignored
[ 8893.339389] usb-storage: device ignored
[ 8893.340442] usb-storage: device ignored
[ 8893.341460] usb-storage: device ignored
[ 8893.342535] usb-storage: device ignored
[ 8893.344454] usb-storage: device ignored
[ 8893.346274] usb-storage: device ignored
[ 8893.347097] usb-storage: device ignored
[ 8893.556997] cdc_acm 1-3:2.1: ttyACM0: USB ACM device
[ 8893.569898] cdc_acm 1-3:2.3: ttyACM1: USB ACM device
[ 8893.570764] usbcore: registered new interface driver cdc_acm
[ 8893.570778] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[ 8893.577040] cdc_wdm 1-3:2.5: cdc-wdm0: USB WDM device
[ 8893.577266] cdc_wdm 1-3:2.6: cdc-wdm1: USB WDM device
[ 8893.579448] usbcore: registered new interface driver cdc_wdm
[ 8893.741084] usbcore: registered new interface driver cdc_ether
[ 8893.761165] usb 1-3: unsupported MDLM descriptors
[ 8893.761249] usbcore: registered new interface driver zaurus
[ 8924.368847] usb 1-3: USB disconnect, address 4
[ 8924.370172] ehci_hcd 0000:00:1d.7: dma_pool_free buffer-2048, d31ff000/131ff000 (bad dma)
[ 8924.370402] ehci_hcd 0000:00:1d.7: dma_pool_free buffer-2048, d31ff080/131ff080 (bad dma)
[ 8942.757114] usb 1-3: new high speed USB device using ehci_hcd and address 5
[ 8942.905709] usb 1-3: configuration #1 chosen from 1 choice
[ 8942.912687] usb-storage: device ignored[/INDENT]

---

### Post by GeorgeVita on 2010-04-17
Hi **Noccy**,
from Ubuntu 9.10 modem-manager is used to detect and setup 3g modems. Some modems worked fine some others not. Also  [bug#492772]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/492772") exists.

Can you supply more info from the following procedure (just in case we can think/make a workaround)?

1. boot without modem

2. from terminal:
```
sudo stop network-manager
sudo killall modem-manager
sudo dmesg -c
```

3. attach modem, **wait** 20 seconds

4. from terminal:
```
dmesg
lsusb
ls /dev/ttyA* /dev/ttyU*
uname -a
```

5. post results of step#4 which shows system activity after attaching modem, all usb peripherals, any tty port created for the modem and kernel version

Regards,
George

P.S. suppose you will use an updated 9.10 (or even 10.04) for the tests, please state.

---

### Post by Noccy on 2010-04-19
Hi, thanks for your reply. Managed to collect some information, although I never went through the process of killing the network manager.

Attaching the dmesg output since it's long, 

[INDENT] * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.3 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 Found default devices (1)
Accessing device 003 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached

Received inquiry data (detailed identification)
-------------------------
  Vendor String: SEMC
   Model String: MMC Flash Card
Revision String:    0
-------------------------

Device description data (identification)
-------------------------
Manufacturer: Sony Ericsson
     Product: MMC Flash Card
  Serial No.: 3578650243097390
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Trying to send Sony control message
 OK, control message sent, waiting for device to return ...
##############################
 After 30 seconds: device still gone, cancelling
-> switching was not completed. Bye.
[/INDENT]

lsusb output:
[INDENT]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0fce:d0e1 Sony Ericsson Mobile Communications AB 
Bus 001 Device 002: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/INDENT]

dmesg output from when plugging in the modem:
[INDENT][12710.356209] usb 1-1: new high speed USB device using ehci_hcd and address 3
[12710.492329] usb 1-1: configuration #1 chosen from 1 choice
[12711.329182] Initializing USB Mass Storage driver...
[12711.329451] usb-storage: device ignored
[12711.329583] usbcore: registered new interface driver usb-storage
[12711.329594] USB Mass Storage support registered.[/INDENT]

dmesg output from the modeswitching:
[INDENT][12754.047568] usb 1-1: USB disconnect, address 3
[12772.424222] usb 1-1: new high speed USB device using ehci_hcd and address 4
[12772.560645] usb 1-1: configuration #2 chosen from 1 choice
[12772.563727] usb-storage: device ignored
[12772.564944] usb-storage: device ignored
[12772.566575] usb-storage: device ignored
[12772.567812] usb-storage: device ignored
[12772.568937] usb-storage: device ignored
[12772.570409] usb-storage: device ignored
[12772.571424] usb-storage: device ignored
[12772.572520] usb-storage: device ignored
[12772.573423] usb-storage: device ignored
[12772.576216] usb-storage: device ignored
[12772.836726] cdc_acm 1-1:2.1: ttyACM0: USB ACM device
[12772.892310] usbcore: registered new interface driver cdc_ether
[12772.914551] cdc_acm 1-1:2.3: ttyACM1: USB ACM device
[12772.916294] usbcore: registered new interface driver cdc_acm
[12772.916309] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[12772.918118] cdc_wdm 1-1:2.5: cdc-wdm0: USB WDM device
[12772.918180] usb 1-1: unsupported MDLM descriptors
[12772.918260] usbcore: registered new interface driver zaurus
[12772.920397] cdc_wdm 1-1:2.6: cdc-wdm1: USB WDM device
[12772.920475] usbcore: registered new interface driver cdc_wdm[/INDENT]

ports and system:
[INDENT]noccy@noccy-laptop:~$ ls /dev/ttyA* /dev/ttyU*
ls: cannot access /dev/ttyU*: No such file or directory
/dev/ttyACM0  /dev/ttyACM1
noccy@noccy-laptop:~$ uname -a
Linux noccy-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
noccy@noccy-laptop:~$ [/INDENT]

If I right-click the network manager I can tick the "Enable mobile broadband" option. I can't connect however, and the second the modem flips back the option goes away.

On a sidenote, modeswitching worked in 9.04 without any problems. It didn't however in 9.10 which is why I stayed at 9.04 for so long. I was hoping this bug to be sorted out with 10.04 but it turned out not to be the case. 


Regards
Chris

---

### Post by GeorgeVita on 2010-04-20
Hi **Noccy**,
ports seem to be created. There is a possibility the reason to be the  [bug#492772]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/492772") 

Read the following link and consider trying wvdial or gnome-ppp method:
[http://ubuntuforums.org/showthread.php?t=1169513](http://ubuntuforums.org/showthread.php?t=1169513)

Consider also to try Ubuntu 10.04 when will be released (by the end of this month).

To try wvdial or gnome-ppp you have to install them using any other connection (ethernet or wireless): ```
sudo apt-get install gnome-ppp
```

After installation:
1. for wvdial method follow instructions from above link.
2. to use the 'GUI' alternative, open a terminal window and run gnome-ppp as 'sudo':
(Note: At this time we use sudo to skip possible 'user-dial-permission' problems. Later if we succeed connection we can 'allow' a normal user to 'use modems' and 'dial' from System > Administration > User and Groups)

```
gksudo gnome-ppp
```

A window will appear, click **Setup**

[img]http://acomelectronics.com/GeorgeVita/various/gPPP_0.jpg[/img]

Type your modem port (most possible /dev/ttyACM0)

[img]http://acomelectronics.com/GeorgeVita/various/gPPP_1.jpg[/img]

Setup your APN (ask your provider or find 'default' via network manager icon). To edit Init3 line you must click on line to 'select', click again to enter 'edit mode', type appropriate data and press enter to accept changes

[img]http://acomelectronics.com/GeorgeVita/various/gPPP_2.jpg[/img]

Check 'networking' tab and adjust 'options' (stupid mode = enabled)

[img]http://acomelectronics.com/GeorgeVita/various/gPPP_3.jpg[/img]  

[img]http://acomelectronics.com/GeorgeVita/various/gPPP_4.jpg[/img]

Click 'close', enter your username and password for the mobile broadband connection and also the dialing number (most cases *99#). By pressing 'log' you can find more info about connection or error condition.

[img]http://acomelectronics.com/GeorgeVita/various/gPPP_5.jpg[/img]  [img]http://acomelectronics.com/GeorgeVita/various/gPPP_6.jpg[/img]

>> If unfortunately you did not make the connection, use 'sudo stop network-manager', 'sudo killall modem-manager' and try again.

Good luck!
George

---

