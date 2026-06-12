---
title: "USB Dongle device name?"
date: 2008-07-14
forum: General Help
---

### Post by jonlemur on 2008-07-14
Hey, I'm trying to use a USB dongle to connect to a remote device running linux with a [BlueSMiRF bluetooth]("http://www.sparkfun.com/commerce/product_info.php?products_id=582") modem on it.  I'm trying to adapt a [howto for Windows]("http://www.lynxmotion.com/images/html/build125.htm") that deals with this particular bluetooth modem.  

The main thing that I'm having trouble figuring out is Step 15.  It seems that in Windows, the module gets assigned to COM7, and the terminal that communicates with the BlueSMiRF uses that.  

In Ubuntu however, I can't figure out what the device is called.  I've compared /dev with and without the dongle plugged in, and these are the lines that are different: > < usbdev1.3_ep00
< usbdev1.3_ep81
< usbdev1.4_ep00
< usbdev1.4_ep02
< usbdev1.4_ep03
< usbdev1.4_ep04
< usbdev1.4_ep81
< usbdev1.4_ep82
< usbdev1.4_ep83
< usbdev1.4_ep84
I was hoping for something along the lines of ttyUSB0, like I use for my RS232-USB adapter that I'm using for testing purposes before I get the bluetooth dongle working.  Then in minicom, I just use /dev/ttyUSB0 for the connection, and I can communicate with the remote device.

Any ideas on what I need to do to connect with the device and send shell commands across it?  For the time being, I'm looking for anything to get it working, but in the future, I want to be able to write a C++ program that will send the commands across Bluetooth to the remote device.  So if you have any ideas on how to do that, I'd appreciate any tips you can give.

---

### Post by jonlemur on 2008-07-14
bump

---

### Post by bushda on 2008-07-14
Type dmesg and hit enter at a command prompt. Then paste the contents here please.

---

### Post by jonlemur on 2008-07-15
I don't have the dongle with me, but I'll post it tomorrow morning.  Thanks for the suggestion.

---

### Post by jonlemur on 2008-07-15
dmesg is such a long file, that I did ```
dmesg > without
dmesg > with
diff with without 
```to get the following```
~$ diff with without
546,562d545
< [  235.113011] usb 1-1: new full speed USB device using uhci_hcd and address 2
< [  235.120464] usb 1-1: configuration #1 chosen from 1 choice
< [  235.130105] hub 1-1:1.0: USB hub found
< [  235.131241] hub 1-1:1.0: 3 ports detected
< [  235.416516] usb 1-1.1: new full speed USB device using uhci_hcd and address 3
< [  235.431713] usb 1-1.1: configuration #1 chosen from 1 choice
< [  108.909054] usb 1-1.2: new full speed USB device using uhci_hcd and address 4
< [  108.952041] Bluetooth: HCI USB driver ver 2.9
< [  108.968419] usb 1-1.2: configuration #1 chosen from 1 choice
< [  236.198918] usb 1-1.3: new full speed USB device using uhci_hcd and address 5
< [  236.211704] usb 1-1.3: configuration #1 chosen from 1 choice
< [  236.249728] usbcore: registered new interface driver hci_usb
< [  236.269409] usbcore: registered new interface driver hiddev
< [  109.127319] usbcore: registered new interface driver usbhid
< [  109.127326] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
< [  109.212541] usb 1-1.2: USB disconnect, address 4
< [  109.358526] usb 1-1.3: USB disconnect, address 5
```

---

### Post by jonlemur on 2008-07-15
```
tail -f /var/log/messages
```produces```
Jul 15 09:11:58 user-name kernel: [  271.030304] usb 1-1: new full speed USB device using uhci_hcd and address 6
Jul 15 09:11:58 user-name kernel: [  271.035268] usb 1-1: configuration #1 chosen from 1 choice
Jul 15 09:11:58 user-name kernel: [  125.173422] hub 1-1:1.0: USB hub found
Jul 15 09:11:58 user-name kernel: [  125.175247] hub 1-1:1.0: 3 ports detected
Jul 15 09:11:59 user-name kernel: [  271.330995] usb 1-1.1: new full speed USB device using uhci_hcd and address 7
Jul 15 09:11:59 user-name kernel: [  271.343057] usb 1-1.1: configuration #1 chosen from 1 choice
```when I plug in the dongle.

---

### Post by jonlemur on 2008-07-15
I figured it out.  By running blueman, I was able to set up a serial connection.  Then it established rfcomm0 in /dev, which I was able to use in minicom.  Now just to figure out how to automate everything with c++ instead of manually doing stuff in minicom :)

---

