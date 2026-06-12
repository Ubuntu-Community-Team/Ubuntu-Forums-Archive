---
title: "16gb USB Drive Not Recognised in Ubuntu"
date: 2011-08-15
forum: Hardware
---

### Post by lazyboy994 on 2011-08-15
Hi there.
I've been looking up this problem for a while and have reformatted many times with still no result.

The problem is that I have a 16gb USB flash drive, and when i plug it into my computer running Ubuntu, it doesn't show up under lsusb or gparted or disk manager. However, in the same port and using the same key, when I reboot into Windows XP, it comes up straight away and i can use it fine.
This is the first case where i cannot open something in ubuntu, but i can in Windows, it's normally the other way around.

Please help as I really would like my USB to work in Ubuntu, not just Windows.
Thanks

---

### Post by varunendra on 2011-08-16
Try usbmount program. It is in the repositories.

Does the same port work with other usb devices, other flash drives in particular? To detect any possible error during its detection/mounting, enter this command in a terminal (after plugging in the flash drive in question, and waiting for 5-10 sec.) and post back its output in your new post:
```
dmesg | grep -i usb
```

---

### Post by lazyboy994 on 2011-08-16
I installed usbmount but I do not know how to run it... i installed using:
```
sudo apt-get install usbmount
```Yes the same port does work fine with every usb device I plug into it, other flash drives and massive external hardrives, they all work just fine. I'll insert the output from my terminal:
```
caleb@caleb-GA-MA74GM-S2:~$ dmesg | grep -i usb
[    0.567071] usbcore: registered new interface driver usbfs
[    0.567071] usbcore: registered new interface driver hub
[    0.567071] usbcore: registered new device driver usb
[    0.992914] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.993138] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.040054] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.040180] hub 1-0:1.0: USB hub found
[    1.040399] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.060050] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.060173] hub 2-0:1.0: USB hub found
[    1.060296] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.060459] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.124175] hub 3-0:1.0: USB hub found
[    1.124387] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.184173] hub 4-0:1.0: USB hub found
[    1.184398] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.244194] hub 5-0:1.0: USB hub found
[    1.244408] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.304181] hub 6-0:1.0: USB hub found
[    1.304399] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.364185] hub 7-0:1.0: USB hub found
[    1.364301] uhci_hcd: USB Universal Host Controller Interface driver
[    1.680231] usb 3-2: new full speed USB device using ohci_hcd and address 2
[    1.940130] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input2
[    1.940217] generic-usb 0003:046D:C52E.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:12.0-2/input0
[    1.944403] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.1/input/input3
[    1.944546] generic-usb 0003:046D:C52E.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:12.0-2/input1
[    1.944561] usbcore: registered new interface driver usbhid
[    1.944562] usbhid: USB HID core driver
[  132.750113] usb 2-6: new high speed USB device using ehci_hcd and address 2
[  133.073030] usbcore: registered new interface driver uas
[  133.098747] Initializing USB Mass Storage driver...
[  133.099069] scsi6 : usb-storage 2-6:1.0
[  133.099551] usbcore: registered new interface driver usb-storage
[  133.099557] USB Mass Storage support registered.
[  165.200190] usb 2-6: reset high speed USB device using ehci_hcd and address 2
[  196.200088] usb 2-6: reset high speed USB device using ehci_hcd and address 2
[  227.240102] usb 2-6: reset high speed USB device using ehci_hcd and address 2
[  258.200111] usb 2-6: reset high speed USB device using ehci_hcd and address 2
[  289.240073] usb 2-6: reset high speed USB device using ehci_hcd and address 2
[  320.200103] usb 2-6: reset high speed USB device using ehci_hcd and address 2
[  351.160106] usb 2-6: reset high speed USB device using ehci_hcd and address 2
caleb@caleb-GA-MA74GM-S2:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0011:7788  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
caleb@caleb-GA-MA74GM-S2:~$ 

```Any other ideas would be appreciated.
Thanks

---

### Post by lazyboy994 on 2011-08-16
I just reeealised that when i have my flash drive plugged in, i see this output:
```
caleb@caleb-GA-MA74GM-S2:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0011:7788  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
Yet when I unplug it, i see this output:
```
caleb@caleb-GA-MA74GM-S2:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
I don't know what this means, but there is one less entry after I unplug it.
Ideas?

---

### Post by varunendra on 2011-08-16
see if this helps (follow the heading- "Automatically Mounting USB Devices"): [http://lcorg.blogspot.com/2009/03/project-building-all-text-linux_11.html](http://lcorg.blogspot.com/2009/03/project-building-all-text-linux_11.html)

By the way, since all other devices, including other flash drives, are already able to get automounted, it means there's nothing wrong with ubuntu's inbuilt automount function. So I doubt if usbmount is going to help.

As for the difference in lsusb output, it definitely indicates the detection of a new device, but beyond that it's incomprehensive to me.

---

