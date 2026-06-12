---
title: "cannot cat /dev/ttyUSB0"
date: 2013-08-13
forum: Hardware
---

### Post by mark1977 on 2013-08-13
Hi,

I have connected a usb device:
```
dmesg|tail
[74358.236055] hid-generic 0003:0458:003A.001A: input,hidraw1: USB HID v1.10 Mouse [Genius Optical Mouse] on usb-0000:00:1d.0-1.3/input0
[74537.192206] usb 2-1.1: new full-speed USB device number 31 using ehci_hcd
[74537.286298] usb 2-1.1: New USB device found, idVendor=10c4, idProduct=ea60
[74537.286305] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[74537.286309] usb 2-1.1: Product: CP2102 USB to UART Bridge Controller
[74537.286312] usb 2-1.1: Manufacturer: Silicon Labs
[74537.286316] usb 2-1.1: SerialNumber: 0001
[74537.287366] cp210x 2-1.1:1.0: cp210x converter detected
[74537.360207] usb 2-1.1: reset full-speed USB device number 31 using ehci_hcd
[74537.453465] usb 2-1.1: cp210x converter now attached to ttyUSB0


```

but when I try to ```
sudo cat /dev/ttyUSB0
``` it just hangs. ```
/dev/ttyUSB0
``` does exist.

Can anyone help? I think it's related to why I can't seem to use the device. I'm on 12.04.

Thanks,

Mark

---

### Post by tgalati4 on 2013-08-13
Try adding read permissions to the device:

```
sudo chmod 777 /dev/ttyUSB0
cat /dev/ttyUSB0
```

Although I see you are using the sudo command already to cat the device.  Perhaps there is another process that has the device tied up.

This looks like an optical mouse with a USB-to-serial converter built in.  Does mouse work correctly when plugged in?

What data are you trying to get?  Mouse coordinates?  Try using *xev* and see if you can see the data that you want.

Because this is an HID device--human interface device--there may be restrictions on the file/device to help prevent malicious intent.

---

### Post by steeldriver on 2013-08-13
If it 'just hangs' that usually just means there is no data to read, no?

Also, the ttyUSB devices should belong to group 'dialout' - so IMHO rather than brute forcing things with sudo or chmod, it's better to add your user to the group

```
$ ls -l /dev/ttyUSB?
crw-rw---- 1 root dialout 188, 0 Aug 13 14:35 /dev/ttyUSB0
$ 
$ cat /dev/ttyUSB0
cat: /dev/ttyUSB0: Permission denied
$ 
$ sudo gpasswd --add steeldriver dialout
Adding user steeldriver to group dialout
```

At this point you either need to log out and back in, or at least spawn a new login shell

```
$ su - steeldriver
Password: 
$ 
$ cat /dev/ttyUSB0
^C
```

---

### Post by mark1977 on 2013-08-14
Thanks for your replies. The device is a multimeter (I think you can ignore the first line from dmesg|tail).

Neither of your suggestions worked, though. However, what has worked is if I run qtdmm (a GUI for multimeters) as root and connect to my device. Only after doing this am I able to cat /dev/ttyUSB0.
Strange...

---

