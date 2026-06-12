---
title: "USB Firmware quirk - DViCO"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by moloth on 2007-03-01
I Have a DViCO FusionHDTV DVB-T Dual card and while the pci part loads fine the usb fails to load on ubuntu 6.10 (Edgy).  It is probably a simple solution... possibly it might be an order of loading problem? Anyway from a cold boot I unplug an replug the usb component i get this in dmesg:

```

usb 5-3: USB disconnect, address 2
usb 5-3: new high speed USB device using ehci_hcd and address 3
usb 5-3: config 1 has an invalid descriptor of length 1, skipping remainder of the config
usb 5-3: config 1 has 0 interfaces, different from the descriptor's value: 1
usb 5-3: configuration #1 chosen from 1 choice
```


Looking at the error I noticed ehci_hcd which i think is the usb2.0 driver?!?. So I did this:

rmmod ehci_hcd

then the dmesg said this:

```

ehci_hcd 0000:00:10.4: remove, state 1
usb usb5: USB disconnect, address 1
usb 5-3: USB disconnect, address 3
ehci_hcd 0000:00:10.4: USB bus 5 deregistered
ACPI: PCI interrupt for device 0000:00:10.4 disabled
usb 2-1: new full speed USB device using uhci_hcd and address 2
usb 2-1: config 1 has an invalid descriptor of length 1, skipping remainder of the config
usb 2-1: configuration #1 chosen from 1 choice
dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual USB' in cold state, will try to load a firmware
dvb-usb: downloading firmware from file 'dvb-usb-bluebird-01.fw'
usbcore: registered new driver dvb_usb_cxusb
usb 2-1: USB disconnect, address 2
dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
usb 2-1: new full speed USB device using uhci_hcd and address 3
usb 2-1: configuration #1 chosen from 1 choice
dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual USB' in warm state.
dvb-usb: This USB2.0 device cannot be run on a USB1.1 port. (it lacks a hardware PID filter)
dvb-usb: DViCO FusionHDTV DVB-T Dual USB error while loading driver (-19)
dvb_usb_cxusb: probe of 2-1:1.0 failed with error -22
```

OOh that looks promising! but it is still having errors... uhci_hcd looks like the usb1.1 driver?? and this is a usb2.0 device. Ok we will put the ehci_hcd driver back in.

modprobe ehci_hcd

then dmesg:

```

ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 177
ehci_hcd 0000:00:10.4: EHCI Host Controller
ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
ehci_hcd 0000:00:10.4: irq 177, io mem 0xbb000000
ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb5: configuration #1 chosen from 1 choice
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
usb 2-1: USB disconnect, address 3
usb 5-3: new high speed USB device using ehci_hcd and address 2
usb 5-3: configuration #1 chosen from 1 choice
dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual USB' in warm state.
dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual USB).
DVB: registering frontend 1 (Zarlink MT352 DVB-T)...
input: IR-receiver inside an USB DVB receiver as /class/input/input3
dvb-usb: schedule remote query interval to 150 msecs.
dvb-usb: DViCO FusionHDTV DVB-T Dual USB successfully initialized and connected.
```

So everything is working at this point. If i do a warm reboot and everything works fine because the firmware is loaded and it is getting a correct device id... but from a cold boot i have to do these steps again.

Starting from a cold boot and looking from a lsusb angle:

```

#lsusb

Bus 002 Device 003: ID 07e9:d350

#rmmod ehci_hcd
#lsusb

Bus 001 Device 007: ID 0fe9:db50 DVICO
(Firmware was loaded here because it is getting a true device ID)

#modprobe ehci_hcd
#lsusb

Bus 002 Device 003: ID 0fe9:db51 DVICO
```

After the first rmmod (Changing to Usb 1.0) it looks like the device id has changed and now it knows its a DVICO:db50. After modprobe (Changing to usb 2.0) the device id changed to DIVCO:db51.. which means the firmware must be loaded before the ehci_hcd loads otherwise an incorrect device id is reported.. any idea on how to do this?

---

### Post by moloth on 2007-03-02
*bump*

---

### Post by anonymou38 on 2007-03-08
bumping b/c i am having a similar problem.  my external hard drives all run slowly (ie. usb 1.0 speed) until i "sudo rmmod ehci-hcd", then "sudo modprobe ehci-hcd".  after that they work perfectly, until i shutdown or restart, in which case i have to do it again.  is the ehci-hcd mod just getting loaded at the incorrect time?  is there any way to fix this during booting so i don't have to do this every time? 

thanks a lot.

---

