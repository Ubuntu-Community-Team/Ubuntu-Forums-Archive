---
title: "USB doesn't work at all"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by azurewraith on 2007-06-15
I have a USB printer, an iPod and a memory stick, none of which work. I've tried lsusb, which outputs nothing. Sorry I have so little information. I've tried googling for it but I couldn't find anything.

---

### Post by mrphantastic on 2007-06-15
for the printer, go to >system>administration>printing  and set it up from there with the on screen prompts with the proper drivers...  Also, if you just installed ubuntu, you need to have updated AND restarted after each and every update, it really does help.  the ipod, well, that depends on the music player you use...i like "Listen" music player from >applications>add/remove>sound and video, the mem stick...well, what kind is it?

---

### Post by bigken on 2007-06-15
check you bios to see if usb is enabled

---

### Post by mrphantastic on 2007-06-15
secondly, is your ipod, an ipod video or what?  cuz i've had issues with the big fancy ones...

---

### Post by azurewraith on 2007-06-15
bigken > I'm dual booting with Windows and USB works there, so I assume it is. Though, truth be told, I couldn't find where in the BIOS to find if USB is enabled.

mrphantastic > My problem isn't that I don't know how to configure these, but that USB isn't (seemingly) detected. Sorry for the confusion

---

### Post by bigken on 2007-06-16
hmmm strange go to system/preferences hardwarew information and look to see if there is anything about usb

---

### Post by heldal on 2007-06-16
The most common problems are:

1. That you've got USB controller hardware that isn't detected. Try the command "dmesg | grep -i usb". That should give some indication as to what USB hardware is detected during boot. You should see messages such as these:

```
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
USB Universal Host Controller Interface driver v3.0
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
new USB bus registered, assigned bus number 2
ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
```


2. Your USB devices may not be supported. Each type if device has a unique ID which has to be associated with the right drivers to controll it. Launch the command "sudo tail -f /var/log/messages" in a terminal window, then watch the messages that pops up as you disconnect and reconnect your USB devices.

---

### Post by azurewraith on 2007-06-16
dmesg | grep -i outputs:
```
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
USB Universal Host Controller Interface driver v3.0
```

Given that /var/log/messages doesn't output anything new either nor can I find anything in the Device Manager.

---

### Post by IntuitiveNipple on 2007-06-16
Try running this command to discover what USB hardware was probed:
```
$ sudo lspci -v | awk 'BEGIN { usb=0; } { if($0 ~ /^[0-9a-f]/) { if($0 ~ /USB/) { usb=1; } else { usb=0; } } if(usb==1) { print $0;} }'
```
On my system the output gives:
```
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1840 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Sony Corporation Unknown device 81ef
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at d2304000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port
```
To get more details on each device increase the number of **v**'s in the options of lspci. For example:

lspci -vv
lspci -vvv

---

### Post by azurewraith on 2007-06-16
```
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: 66MHz, medium devsel
        Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: 66MHz, medium devsel
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a26
        Flags: 66MHz, medium devsel
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

```

---

### Post by IntuitiveNipple on 2007-06-16
That report doesn't show any I/O ports or IRQs allocated to the USB devices.

What does this command report?
```
$ lsmod | grep hci
hci_usb                18204  3 
bluetooth              55908  9 rfcomm,l2cap,hci_usb
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
uhci_hcd               25360  0 
ehci_hcd               34188  0 
usbcore               134280  9 hsfosspec,uvcvideo,hci_usb,r5u870,usb_storage,libusual,uhci_hcd,ehci_hci
```
I think you need to carefully read the output dmesg log to see if you can identify what it is doing when it detects the USB devices.

Here's a little bit from the beginning of the dmesg log on this system so you know the kind of thing to expect:
```
[    2.256000] usbcore: registered new interface driver usbfs
[    2.256000] usbcore: registered new interface driver hub
[    2.256000] usbcore: registered new device driver usb
[    2.260000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[    2.260000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    2.260000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.260000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.260000] ehci_hcd 0000:00:1d.7: debug port 1
[    2.260000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    2.260000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd2304000
[    2.264000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.264000] usb usb1: configuration #1 chosen from 1 choice
[    2.264000] hub 1-0:1.0: USB hub found
[    2.264000] hub 1-0:1.0: 8 ports detected
[    2.268000] USB Universal Host Controller Interface driver v3.0
```

---

### Post by bigken on 2007-06-16
just a though have you run all the updates 

you never know it might just fix it

---

### Post by azurewraith on 2007-06-16
```
lsmod | grep hci
uhci_hcd               25360  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
ehci_hcd               34188  0 
ohci_hcd               22532  0 
usbcore               134280  4 uhci_hcd,ehci_hcd,ohci_hcd

```

I thought that this was a little suspicious but I can't tell:

```
[   20.058300] PCI: No IRQ known for interrupt pin A of device 0000:00:13.2. Probably buggy MP table.
[   20.058305] ehci_hcd 0000:00:13.2: Found HC with no IRQ.  Check BIOS/PCI 0000:00:13.2 setup!
[   20.058313] ehci_hcd 0000:00:13.2: init 0000:00:13.2 fail, -19

```

---

### Post by dentaku65 on 2007-06-21
I'm in trouble with usb2 too, mainly with external hard drive and usb tv stick; my fix is:

```
sudo modprobe -r ehci_hcd && sudo modprobe ehci_hcd
```

After this everything works perfect (Kubuntu Feisty). I don't know if there is something wrong in the module itself, in the kernel, in the hal or god knows... I got this annoying usb2 issue since Feisty.

---

