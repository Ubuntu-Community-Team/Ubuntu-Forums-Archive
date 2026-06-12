---
title: "USB Bluetooth Dongle unable to install/detect adapter"
date: 2010-01-10
forum: Hardware
---

### Post by rosier on 2010-01-10
Hi Ive got tow Ubuntu versions running and neither is able to detect the Bluetooth dongle- bought another and neither is able to detect and install the drivers: Ive got karmic and hardy distro's running
Tried purchasing another dongle- still no go.
Only usb device it picks up is the webcam.
Ive tried other ports- no change.                                                                                                                                                                                                                                             

Heres some data
dad@dad-desktop:~$ lsusb
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 003 Device 002: ID 05a9:8519 OmniVision Technologies, Inc. OV519 Webcam
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
dad@dad-desktop:~$ 

here is a report from dmesg report when unplugging and replugging:

 [ 2494.860061] usb 4-1: new full speed USB device using uhci_hcd and address 15
 [ 2494.980029] usb 4-1: device descriptor read/64, error -71
 [ 2495.204035] usb 4-1: device descriptor read/64, error -71
 [ 2495.420036] usb 4-1: new full speed USB device using uhci_hcd and address 16
 [ 2495.836091] usb 4-1: device not accepting address 16, error -71
 [ 2495.948030] usb 4-1: new full speed USB device using uhci_hcd and address 17
 [ 2496.356021] usb 4-1: device not accepting address 17, error -71
 [ 2496.356046] hub 4-0:1.0: unable to enumerate USB device on port 1

Any help apprecited or steps to figure out whats going on. Ive got both systems up to date and have installed bluetooth software but neither detects the adapter.

By the way Fedora installs it no problems...

Thanks for any suggestions..

---

### Post by chaanakya_chiraag on 2010-01-10
Which Ubuntu versions are you using?  From your lsusb, it seems like the only thing plugged in is a webcam...??  Without the info about which versions you're running, it's impossible to get further.

---

### Post by rosier on 2010-01-11
Hi I've included it in my profile- its Hardy heron 8.04 (great distro)! Thanks for any suggestions

---

### Post by rosier on 2010-01-11
also yes the webcam and most USB devices are fine and are listed on the lsusb list.
Can confirm that the dongles are good- runs ok on Windows and fedora.

---

### Post by chaanakya_chiraag on 2010-01-11
What USB Bluetooth dongle are you using (or trying to use)?  Hardy shouldn't be a problem at all.  Try installing the bluetooth packages.  I think it's gnome-bluetooth or something along those lines.  Search for bluetooth in Synaptic and install whatever seems right.  If you're not sure, just copy-paste the descriptions of all of the packages matching bluetooth by running the following command and copying the output:
```
sudo apt-cache search bluetooth
```

---

### Post by rosier on 2010-01-11
Hi from what I can ascertain it seems as thought the adapter is not being registered with Linux- from the kernels perspective the adapter wont accept the address and therefore is not accepting and registering its address- Linux is throwing up an error and therefore all bluetooth utilities i have loaded cannot find the adapter- there is none registered.
Ive tried all kinds of BOIS settings changes- no luck.
Is there anything in the kernel?? or something like that tat may resolve or clarify what the issue is.
Thanks...

---

### Post by chaanakya_chiraag on 2010-01-11
Have you tried installing the bluetooth packages for Hardy Heron??  If you haven't installed those, I don't think Linux will know what the heck the device is.

---

### Post by rosier on 2010-01-12
yes of course Ive installed it- also tried different driver installation wizards etc...still no go.

---

### Post by chaanakya_chiraag on 2010-01-12
Hmmm...it seems weird that Fedora recognizes it but Ubuntu doesn't.  Try the following: ```
sudo /etc/init.d/bluetooth start
``` and see what it says.

---

### Post by rosier on 2010-01-14
Hi ran the code and nothing happened- no automatic pickup of dongle. Manually ran bluetooth utilities...didnt pickup an adapter.
Ran lsusb:
dad@dad-desktop:~$ sudo /etc/init.d/bluetooth start
[sudo] password for dad: 
dad@dad-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 05a9:8519 OmniVision Technologies, Inc. OV519 Webcam
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
dad@dad-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 05a9:8519 OmniVision Technologies, Inc. OV519 Webcam
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
dad@dad-desktop:~$ 

didnt pickup the dongle.

Difference now is that the dongle is accepting an address and being enumerated.

syslog output when plugging in dongle...before it wouldn't accept the address.???

Jan 14 22:39:33 dad-desktop kernel: [ 1654.144032] usb 4-1: new full speed USB device using uhci_hcd and address 6
Jan 14 22:39:33 dad-desktop kernel: [ 1654.704029] usb 4-1: new full speed USB device using uhci_hcd and address 7
Jan 14 22:39:34 dad-desktop kernel: [ 1655.264035] usb 4-1: new full speed USB device using uhci_hcd and address 8
Jan 14 22:39:34 dad-desktop kernel: [ 1655.788032] usb 4-1: new full speed USB device using uhci_hcd and address 9
Jan 14 22:40:33 dad-desktop kernel: [ 1714.249252] usb 4-1: new full speed USB device using uhci_hcd and address 10

Ill keep working on it and will post updates and findings...thanks

---

### Post by chaanakya_chiraag on 2010-01-14
What happened is that the bluetooth service hadn't been started, so Ubuntu didn't know it was supposed to look for a bluetooth dongle.  Hmmm...I'm surprised that lsusb isn't listing the device.

---

### Post by rosier on 2010-02-01
hi just updating how i resolved the problem- bought another one and it worked, say no more.

---

### Post by chaanakya_chiraag on 2010-02-01
Yay!  If this problem is resolved, please mark the thread as solved by going to Thread Tools->Mark as Solved.  Thanks :)

---

