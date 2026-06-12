---
title: "USB Bluetooth Not Recognized?"
date: 2008-10-24
forum: Hardware
---

### Post by raynedanser on 2008-10-24
Like an idiot, I forgot to order bluetooth when I ordered my laptop, so tonight I grabbed a Targus USB Receiver and can't get the lappy to recognize it. 

I tried following [*this*]("http://www.gnomefiles.org/app.php/blueman") and [*this*]("http://ubuntuforums.org/newthread.php?do=newthread&f=332") and rebooted (old Windows habit, I know, but one of them said it might help, too) - and it still isn't recognized. 

If I click Inquiry in Blueman, it tells me that it failed to start inquiry because the device is busy. 

Help?

---

### Post by melojo on 2008-10-24
open a terminal and post the output of

lsusb

---

### Post by raynedanser on 2008-10-24
Bus 007 Device 004: ID 0781:5406 SanDisk Corp. Cruzer Micro 4GB Flash Drive
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 0a5c:2154 Broadcom Corp. 
Bus 004 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 004 Device 003: ID 0a5c:4502 Broadcom Corp. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 046d:c526 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Where Logitech is my wireless mouse. *sigh* It isn't reading it at ALL and it's plugged in and "restarting" it through terminal didn't help earlier.

---

### Post by melojo on 2008-10-24
is your usb ports 2.0 capatable or just 1.1?  How old is the machine?

not sure whether this will help to get lsusb to see the device but its worth a try.

/etc/init.d/dbus restart


Then try lsusb again.

---

### Post by raynedanser on 2008-10-24
Ports are all 2.0 - machine is a little over 2 months old. 

Did the restart and got this. lsusb gets same result as it did before.

 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon avahi-daemon                               Failed to open PID file: Permission denied
                                                                         [ OK ]
 * Stopping System Tools Backends system-tools-backends                         start-stop-daemon: warning: failed to kill 5569: Operation not permitted
                                                                         [ OK ]
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Stopping network connection manager NetworkManager                    [ OK ] 
 * Stopping system message bus dbus                                             start-stop-daemon: warning: failed to kill 5526: Operation not permitted
                                                                         [ OK ]
rm: cannot remove `/var/run/dbus/pid': Permission denied

---

### Post by melojo on 2008-10-24
sry try sudo /etc/init.d/dbus restart

---

### Post by Yellow Pasque on 2008-10-24
Also, run this to make sure you have the latest usb id's:
```
sudo update-usbids
```

---

### Post by raynedanser on 2008-10-24
> **Temüjin said:**
> Also, run this to make sure you have the latest usb id's:
```
sudo update-usbids
```

I did, thank you.

Still no change:

Bus 005 Device 006: ID 0a5c:2154 Broadcom Corp. 
Bus 005 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 005 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 005 Device 003: ID 0a5c:4500 Broadcom Corp. 
Bus 005 Device 002: ID 046d:c526 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/2/4GB Flash Drive
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


Unless - could Broadcom be it?

---

### Post by melojo on 2008-10-24
> **raynedanser said:**
> I did, thank you.

Still no change:

Bus 005 Device 006: ID 0a5c:2154 Broadcom Corp. 
Bus 005 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 005 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 005 Device 003: ID 0a5c:4500 Broadcom Corp. 
Bus 005 Device 002: ID 046d:c526 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/2/4GB Flash Drive
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


Unless - could Broadcom be it?

did you restart after sudo update-usbids or
sudo /etc/init.d/dbus restart

---

### Post by raynedanser on 2008-10-24
> **melojo said:**
> did you restart after sudo update-usbids or
sudo /etc/init.d/dbus restart

Both. I entered the command in the terminal and then it also zapped my wireless (and I couldn't remember where to reset it), so I rebooted as well and then redid lsusb

Still zilch. Am starting to wonder if this one is just not going to work for my system. :/

---

### Post by Yellow Pasque on 2008-10-25
I think it is recognized as the Broadcom device. The next step is seeing what driver it uses:
```
sudo lshw -C network
```

---

### Post by raynedanser on 2008-10-25
*-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:5a:96:05
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:a1:c2:c0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.3 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g


(also, I am going out of town today, so I may not get any more replies until late tomorrow or Monday, but I didn't want it to see like I was ignoring you. *g*)

---

### Post by rjonesx on 2008-10-28
unplug and plug back in your usb adapter, then run

> dmesg

chances are at the end of dmesg output you will see that your USB adapter is being interpreted as an HID compliant mouse/keyboard rather than an HCI device.

That is where I am stuck. And yes, the Broadcom 45xx listings are the USB device...

This problem appears to be pretty common, it just seem to be high up on the list of priority fixes.

---

### Post by raynedanser on 2008-10-28
I wussed out. LOL I ended up taking it back, mostly because I don't need it *that* badly - but it would read something as a mouse because I have a cordless mouse with a micro-receiver. 

But thank you (everyone) for the help!

---

### Post by joe_geek on 2008-11-09
> **rjonesx said:**
> unplug and plug back in your usb adapter, then run

> dmesg

chances are at the end of dmesg output you will see that your USB adapter is being interpreted as an HID compliant mouse/keyboard rather than an HCI device.

That is where I am stuck. And yes, the Broadcom 45xx listings are the USB device...

This problem appears to be pretty common, it just seem to be high up on the list of priority fixes.

This is where I'm stuck too.  I've got a Rocketfish Bluetooth dongle.  Seems this is why bluetooth-applet won't recognize the dongle as a bluetooth adapter.

Output of dmesg if this helps:
[16377.153007] usb 2-2: new full speed USB device using uhci_hcd and address 29
[16377.328558] usb 2-2: configuration #1 chosen from 1 choice
[16377.332130] hub 2-2:1.0: USB hub found
[16377.336961] hub 2-2:1.0: 3 ports detected
[16378.022345] usb 2-2.2: new full speed USB device using uhci_hcd and address 30
[16378.164568] usb 2-2.2: configuration #1 chosen from 1 choice
[16378.172291] input: Broadcom Corp BCM2045B3 ROM as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2.2/2-2.2:1.0/input/input32
[ 6543.630878] input,hidraw3: USB HID v1.11 Keyboard [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:1d.1-2.2
[ 6543.839768] usb 2-2.3: new full speed USB device using uhci_hcd and address 31
[12284.288130] usb 2-2.3: configuration #1 chosen from 1 choice
[12284.298972] input: Broadcom Corp BCM2045B3 ROM as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2.3/2-2.3:1.0/input/input33
[ 6543.992902] input,hidraw4: USB HID v1.11 Mouse [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:1d.1-2.3

---

### Post by joe_geek on 2009-01-03
Figured I'd give this thread another ping to see if some fresh eyes could help.  lsusb -v lists 3 Broadcom devices: one keyboard, one mouse, one full speed hub.

bluetooth-applet still won't recognize it as a bluetooth dongle so I can't try pairing anything with it.  I don't even get hci0 anywhere, and hcitool commands result in "no such device" errors.

---

### Post by cong06 on 2009-01-05
I'm having a similar [problem on my Intrepid laptop](http://ubuntuforums.org/showthread.php?p=6496985).
I'm trying to detect a Creative Zen Micro mp3 player.

lsusb gives no change when it's plugged in, yet /var/log/messages changes when it's plugged in:
```

Jan  5 02:30:52 dirac kernel: [ 1906.040198] usb 5-1: new full speed USB device using uhci_hcd and address 7
Jan  5 02:30:52 dirac kernel: [ 1906.248836] usb 5-1: configuration #1 chosen from 1 choice
Jan  5 02:30:54 dirac kernel: [ 1908.280257] usb 5-1: USB disconnect, address 7
```

I tried restarting after:
```
sudo update-usbids
```
But that did nothing.

Incidentally, I accidentally booted my live disk, and decided to try it there, and it worked. (Intrepid live disk) Or rather it was listed, I couldn't go about installing programs on the live disk, so I couldn't actually test copying files to it.

---

