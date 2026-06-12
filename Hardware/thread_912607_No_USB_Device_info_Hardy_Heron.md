---
title: "No USB Device info Hardy Heron"
date: 2008-09-06
forum: Hardware
---

### Post by rfrenkel123 on 2008-09-06
Got a scanner and plugged it in (usb). Listed in scan.d config, so it should have worked. But didn't. Light came on on scanner, so it's communicating.  

lsusb returns:

root@ibfx-eas1:/etc/sane.d# lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Amusing, not even the working usb mouse I'm using is shown. But not very informative.

lspci -v gives:

root@ibfx-eas1:/etc/sane.d# lspci -v|grep HCI
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])


OK, I'm a computer user, not a hacker. I'd like my scanner to work. I've seen a fair number of posts with similar issues, but after lots of helpful (at least attempted) back and forth, no solution. 

Is there someone out there with a solution? I'll settle for a definitive "no", (for example based on the hardware). I'm just being anal about not plugging the scanner into my Windows laptop :) But I'd like to know...

---

### Post by IntuitiveNipple on 2008-09-06
The scanner light coming on might just be in response to the power, it doesn't necessarily mean the PC and the scanner are communicating.

The output from 'lsusb' is of concern if it isn't displaying other USB devices too since it hints are more fundamental issues on the PC.

As an experiment monitor the kernel log whilst connecting the scanner and see if the kernel detects the connection:
```

tail -f /var/log/kern.log

```
When it is finished use Ctrl+C to stop the monitoring. If it reports anything please copy it here.

---

### Post by rfrenkel123 on 2008-09-06
Ah, I can see messages about the usb mouse and keyboard. When I unplug and plug the scanner I get:

Sep  6 22:31:23 ibfx-eas1 kernel: [1417553.120478] usb 5-8: USB disconnect, address 34
Sep  6 22:31:31 ibfx-eas1 kernel: [1417561.124199] usb 5-8: new high speed USB device using ehci_hcd and address 36
Sep  6 22:31:31 ibfx-eas1 kernel: [1417561.261291] usb 5-8: configuration #1 chosen from 1 choice

---

### Post by rfrenkel123 on 2008-09-06
Ah, I can see messages about the usb mouse and keyboard. When I unplug and plug the scanner I get:

Sep  6 22:31:23 ibfx-eas1 kernel: [1417553.120478] usb 5-8: USB disconnect, address 34
Sep  6 22:31:31 ibfx-eas1 kernel: [1417561.124199] usb 5-8: new high speed USB device using ehci_hcd and address 36
Sep  6 22:31:31 ibfx-eas1 kernel: [1417561.261291] usb 5-8: configuration #1 chosen from 1 choice

---

### Post by IntuitiveNipple on 2008-09-06
Can you compress and attach the start-up log file?
```

cat /var/log/dmesg | gzip >dmesg.gz

```
There could be something more going on here as I said before. 'lsusb' should be reporting something.

---

### Post by rfrenkel123 on 2008-09-06
Oddly, lsusb is now reporting the mouse and keyboard. Maybe unplugging and plugging the scanner kicked something. Still no sign of the scanner:

root@ibfx-eas1:/etc/sane.d# lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 007: ID 10d5:000d Uni Class Technology Co., Ltd 
Bus 002 Device 006: ID 046d:c03f Logitech, Inc. UltraX Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

dmesg attached.

---

### Post by IntuitiveNipple on 2008-09-07
The dmesg log doesn't show anything unusual and now you have 'lsusb' reporting something at least.

Do you see any clues in daemon.log or kern.log when connecting the scanner now? Run two terminal sessions and put each of these commands in their own terminal so they run at the same time:
```

tail -f /var/log/kern.log

tail -f /var/log/daemon.log

```
What make and model is the scanner? Is it connected directly or via a hub? Do you have an alternate cable to try it with?

Also, try monitoring for udev events when the scanner is connected:
```

sudo udevmonitor --environment

```

---

### Post by rfrenkel123 on 2008-09-07
Hi thanks for the help and lesson in debugging. I'll get this for you tomorrow AM. The scanner is a new Fujitsu ScanSnap S510 and I used it instead from my Windows laptop with no issues with the same cable. The fact that the lsusb showed no entries originally is suggestive of something :)

---

### Post by rfrenkel123 on 2008-09-10
OK, this AM plugged in a USB printer and same thing happens. Here are the kernel and daemon tails. The kernel sees the new device, daemon doesn't (I unplugged it and plugged it back - last few records):

```
Sep 10 07:53:43 ibfx-eas1 kernel: [1710410.675677] ppdev0: registered pardevice
Sep 10 07:53:43 ibfx-eas1 kernel: [1710410.723488] ppdev0: unregistered pardevice
Sep 10 07:53:43 ibfx-eas1 kernel: [1710411.118604] ppdev0: registered pardevice
Sep 10 07:53:43 ibfx-eas1 kernel: [1710411.160123] ppdev0: unregistered pardevice
Sep 10 07:53:43 ibfx-eas1 kernel: [1710411.238861] ppdev0: registered pardevice
Sep 10 07:53:43 ibfx-eas1 kernel: [1710411.288568] ppdev0: unregistered pardevice
Sep 10 07:55:14 ibfx-eas1 kernel: [1710502.899071] usb 1-2: USB disconnect, address 2
Sep 10 07:58:02 ibfx-eas1 kernel: [1710670.282084] usb 1-2: new full speed USB device using uhci_hcd and address 3
Sep 10 07:58:02 ibfx-eas1 kernel: [1710670.476158] usb 1-2: configuration #1 chosen from 1 choice

```

```
Sep 10 07:20:05 ibfx-eas1 ntpd[16107]: time reset -0.573116 s
Sep 10 07:24:45 ibfx-eas1 ntpd[16107]: synchronized to 91.189.94.4, stratum 2
Sep 10 07:35:31 ibfx-eas1 ntpd[16107]: time reset -0.563494 s
Sep 10 07:45:50 ibfx-eas1 ntpd[16107]: synchronized to 91.189.94.4, stratum 2
Sep 10 07:46:40 ibfx-eas1 ntpd[16107]: synchronized to 132.236.56.250, stratum 2
Sep 10 07:54:11 ibfx-eas1 ntpd[16107]: time reset -0.639111 s
```


And here is what lsusb shows with a usb mouse (working) a usb keyboard (working) and the usb printer (not working, since we can't see it):

```
rich@ibfx-eas1:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
rich@ibfx-eas1:~$ 

```

---

### Post by forger on 2008-09-10
(Use simple user, not root, use sudo only where it's necessary)
- Try adding yourself in scanner group:
```
sudo adduser $USER scanner
```
- Log out and log in again.
- Reply with the output of these commands:
```
id
sudo sane-find-scanner
sane-find-scanner
scanimage -L
```

---

### Post by forger on 2008-09-10
- Also do this:
```
sudo update-pciids
sudo update-usbids
```
- Reboot
- Post the reply of:
```
lspci
lsusb
```

---

