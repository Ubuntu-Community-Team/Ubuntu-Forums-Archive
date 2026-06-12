---
title: "USB FTDI devices work only sometimes on 14.04.1"
date: 2014-08-28
forum: Hardware
---

### Post by Marie_Johansson on 2014-08-28
Hi,

I'm a real newbie to Linux and new to this forum and I hope that you could help me with a really frustrating problem.

I use Ubuntu Server 14.04.1 LTS and I have three Argolis Smargo Smartreaders V2 which I use with a program called OSCam. When I boot Ubuntu and launch OSCam, then about 50% of the times the Smartreader isn't working with OSCam.

When it doesn't work - then it doesn't work during that "boot" EVER (stopping/starting OSCam never helps) until I either reboot (and get a new 50% chance of it to work) or if I run this script I found on another forum (to kind of reset the USB devices?):

```
for i in $(ls /sys/bus/pci/drivers/ehci-pci/|grep :)
  do echo $i >/sys/bus/pci/drivers/ehci-pci/unbind
done

for i in $(ls /sys/bus/pci/drivers/uhci_hcd/|grep :)
  do echo $i >/sys/bus/pci/drivers/uhci_hcd/unbind
  echo $i >/sys/bus/pci/drivers/uhci_hcd/bind
done
```

When I run that script it's exactly the same as if I would reboot - I get a new 50% chance of it to work.

When it DOES work - then it works all the time during that "boot" (I can stop/start OScam 100 times - it works all the time) until I reboot or run the script.

I've tried this with each of the three different Smartreaders, always only with one at a time and in different USB ports. I've even tried with a USB hub with external power and I always get this result with a 50% chance of it to work.

The manufacturer offers a tool to determine the readers currently connected and the result is like this:

```
Looking for smartreader compatible devices...
bus 003, device 002 : 0403:6001 Smartreader2 plus (type=SRv2, in_ep=02, out_ep=81; insert in oscam.server 'device = SRv2;Serial:card1     ')
```

It always look exactly like this, the only thing that sometimes changes is the bus 003 to 004 after a reboot/running my script but there is no relation to when it's working or not. Both bus 003 work and won't work (the same with bus 004).

I think the Smartreaders have a USB to Serial FTDI chip in them(?). I've also got a USB keyboard connected which works all the time.

Thank you!

---

### Post by Marie_Johansson on 2014-08-29
Edit: my suggested solution didn't work after all - only worked for more times in a row than than "usual". :mad:

---

### Post by Mikulas_Jancsika on 2014-12-22
Same problem here.
It was working without problem on Debian 7. But now on Ubuntu 14.04.1 .... 

dmesg says no problem at boot:

[    1.576097] usb 4-1: new full-speed USB device number 2 using uhci_hcd
[    1.751833] usb 4-1: New USB device found, idVendor=0403, idProduct=6001
[    1.751838] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.751842] usb 4-1: Product: Smartreader2 plus
[    1.751846] usb 4-1: Manufacturer: Argolis BV
[    1.751849] usb 4-1: SerialNumber: myredr76
...
[   11.572215] usbcore: registered new interface driver ftdi_sio
[   11.572232] usbserial: USB Serial support registered for FTDI USB Serial Device
[   11.572308] ftdi_sio 4-1:1.0: FTDI USB Serial Device converter detected
[   11.572342] usb 4-1: Detected FT232BM
[   11.572344] usb 4-1: Number of endpoints 2
[   11.572347] usb 4-1: Endpoint 1 MaxPacketSize 64
[   11.572349] usb 4-1: Endpoint 2 MaxPacketSize 64
[   11.572351] usb 4-1: Setting MaxPacketSize 64
[   11.574902] usb 4-1: FTDI USB Serial Device converter now attached to ttyUSB0


after I plug it out and back ... it works ...:

[12401.636104] usb 4-1: USB disconnect, device number 2
...
[13017.292042] usb 3-2: new full-speed USB device number 2 using uhci_hcd
[13017.471068] usb 3-2: New USB device found, idVendor=0403, idProduct=6001
[13017.471074] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[13017.471078] usb 3-2: Product: Smartreader2 plus
[13017.471081] usb 3-2: Manufacturer: Argolis BV
[13017.471084] usb 3-2: SerialNumber: myredr76
[13017.477142] usb 3-2: Detected FT232BM
[13017.477146] usb 3-2: Number of endpoints 2
[13017.477150] usb 3-2: Endpoint 1 MaxPacketSize 64
[13017.477153] usb 3-2: Endpoint 2 MaxPacketSize 64
[13017.477156] usb 3-2: Setting MaxPacketSize 64
[13017.479134] usb 3-2: FTDI USB Serial Device converter now attached to ttyUSB0

---

### Post by Mister_SMS on 2015-04-07
Hello [**[COLOR=#000000]Marie_Johansson[/COLOR]**]("http://ubuntuforums.org/member.php?u=1942409"),

did you found a solution of your smartreader v2 usb problem?

thanks

---

### Post by Marie_Johansson on 2015-04-08
No, unfortunately I did not. I think the readers where broken or something. I changed to PC/SC card reader instead.

---

