---
title: "dell inspiron 9400 bluetooth"
date: 2006-07-06
forum: Hardware &amp; Laptops
---

### Post by nibblesmx on 2006-07-06
I just bought a dell inspiron 9400 and ubuntu is great.

I know the installation detected my bluetooth card, 'cuz it installed bluetooth administrator and some other BT tools, but they just don't work.

When i execute gnome-bluetooth-manager from console, i get this:
```

Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/gnomebt/manager.py", line 274, in ?
    BTManager ().main ()
  File "/usr/lib/python2.4/site-packages/gnomebt/manager.py", line 85, in __init__
    if not self.btctl.is_initialised():
gobject.GError: Can't get device id of hci0
```

also, sudo hciconfig -a gives me nothing.

Here is the output of a sudo lspci -v

```
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
        Subsystem: Dell: Unknown device 01cd
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] #09 [5109]

0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: dd000000-dfefffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cff00000
        Capabilities: [88] #0d [0000]
        Capabilities: [80] Power Management version 2
        Capabilities: [90] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [a0] #10 [0141]

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Dell: Unknown device 01cd
        Flags: bus master, fast devsel, latency 0, IRQ 50
        Memory at dfffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] #10 [0091]

0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
        Capabilities: [40] #10 [0141]
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
        Memory behind bridge: dcf00000-dcffffff
        Capabilities: [40] #10 [0141]
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: dcc00000-dcefffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d0100000
        Capabilities: [40] #10 [0141]
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 01cd
        Flags: bus master, medium devsel, latency 0, IRQ 233
        I/O ports at bf80 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 01cd
        Flags: bus master, medium devsel, latency 0, IRQ 50
        I/O ports at bf60 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 01cd
        Flags: bus master, medium devsel, latency 0, IRQ 58
        I/O ports at bf40 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 01cd
        Flags: bus master, medium devsel, latency 0, IRQ 66
        I/O ports at bf20 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell: Unknown device 01cd
        Flags: bus master, medium devsel, latency 0, IRQ 233
        Memory at ffa80000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #0a [20a0]

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        Memory behind bridge: dcb00000-dcbfffff
        Capabilities: [50] #0d [0000]

0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
        Subsystem: Dell: Unknown device 01cd
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] #09 [100c]

0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01) (prog-if 80 [Master])
        Subsystem: Dell: Unknown device 01cd
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 177
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at bfa0 [size=16]
        Capabilities: [70] Power Management version 2

0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Dell: Unknown device 01cd
        Flags: medium devsel, IRQ 5
        I/O ports at 10c0 [size=32]

0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0298 (rev a1) (prog-if 00 [VGA])
        Subsystem: Dell: Unknown device 019b
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at de000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at ef00 [size=128]
        Expansion ROM at dfe00000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [78] #10 [0001]

0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
        Subsystem: Dell: Unknown device 01cd
        Flags: bus master, fast devsel, latency 64, IRQ 177
        Memory at dcbfe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2

0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832 (prog-if 10 [OHCI])
        Subsystem: Dell: Unknown device 01cd
        Flags: bus master, medium devsel, latency 64, IRQ 185
        Memory at dcbfd800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [dc] Power Management version 2

0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) (prog-if 01)
        Subsystem: Dell: Unknown device 01cd
        Flags: bus master, medium devsel, latency 64, IRQ 74
        Memory at dcbfd400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
        Subsystem: Dell: Unknown device 01cd
        Flags: bus master, medium devsel, latency 0, IRQ 9
        Memory at dcbfd500 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

0000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: Dell: Unknown device 01cd
        Flags: medium devsel, IRQ 9
        Memory at dcbfd600 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)        Subsystem: Dell: Unknown device 01cd
        Flags: medium devsel, IRQ 9
        Memory at dcbfd700 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

0000:0c:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)        Subsystem: Intel Corporation: Unknown device 1020
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at dcfff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] #10 [0011]
```

Can anyone help me? It's the only glitch that's keeping ubuntu from being perfect

---

### Post by venico on 2006-09-21
I have the same problem..

have you the solution?

---

### Post by kejava on 2006-12-13
sorry for the late response.  i just joined the forum.  i ran into a similar problem a while back.  i'm still learning too ;-)  this is the typical quick and dirty way to get things rolling:

sudo /etc/init.d/./bluez-utils start
hcitool scan
sudo hidd --search

the last line depends on what you're trying to connect with.  it finds my iFrogPad and initiates pairing.  from your problem, it seems that the first line is giving you trouble.  i would start there.  if you can't get that going nothing else will work.  it's possible your kernel modules aren't being loaded properly.  Look for info on the "Dell Wireless 350 Bluetooth 2.0 Module" in your 'dmesg' output.

here are some success stories for the 9400:
[http://linux-laptop.net/hosted/dell-inspiron-9400.html](http://linux-laptop.net/hosted/dell-inspiron-9400.html)
[http://www.notpraveen.com/pmwiki.php/ScrapBook/FedoraCore5onInspiron9400](http://www.notpraveen.com/pmwiki.php/ScrapBook/FedoraCore5onInspiron9400)
[http://xoomer.alice.it/sam_psy/soft/ubuntu_install.html](http://xoomer.alice.it/sam_psy/soft/ubuntu_install.html)

---

### Post by gotjam on 2007-05-14
i cant make it search other devices, also when i try to find my computer, i cant

when i type 
sudo /etc/init.d/./bluez-utils start

the response is:
sudo: /etc/init.d/./bluez-utils: command not found

what am i doing wrong?

---

### Post by morgengenuss on 2007-05-14
i assume you don't have bluez-utils installed (since it isn't installed by default).

this should help:
```
sudo apt-get install bluez-utils
```

---

### Post by kejava on 2007-05-14
Hi Gotjam,

Do as morgengenuss says to install it, if you don't have it already.  The name of the service script changed from "bluez-utils" to "bluetooth" on Feisty Fawn.  I believe it should start after you install it but I'm not certain.  Just stop and then start it to be sure, like this:```
sudo /etc/init.d/./bluetooth stop
sudo /etc/init.d/./bluetooth start
```

---

### Post by gotjam on 2007-05-14
i have bluez-utils installed, i have it started, ubuntu detects the bluetooth, but my cellphone doesnt detect it, and i cant send files.

it's very strange, i had followed tutorials, i have installed and reinstalled the aplications with no result.

what else can i do??

thanks,

---

### Post by kejava on 2007-05-15
gotjam,

i'm kinda in the same boat.  i just got a new Samsung sch-u740 phone the other day.  Now I'm trying to obex_test and obexftp to communicate with.  Both the PC and phone can see each other, but I can't pair up from either side.

when you say "ubuntu detects the bluetooth" do you mean that the PC can see the phone?

I'm new to this stuff so I'll do some more searching.  If I get anywhere, I'll report back.

---

### Post by gotjam on 2007-05-15
i mean that ubuntu detect the bluutooth card, when i turn it on a tray appears by a side of the clock, and when i turn it off, it disappears.

my phone doesnt detect the computer, and i cant search devices from my computer, dont know why.

i installed the kde obex, but it doesnt open when i turn on my bluetooth.

[IMG]http://home.galileo.edu/~andresmonge/pantallazo1.png[/IMG]

thats my bluetooth manager, as u see where is "Tipo de dispositivo", (device type), i cant select any thing.

i must be a software hardware compatibility problem, but i cant find it.

---

### Post by gotjam on 2007-05-17
i finally could configure my bluetooth, the problem was the when installed the bluetooth manager, it didnt change the configuration that saids that blue tooth is like enable.

here is my solution,

after install all u need for the bluetooth, 

open a console and type this
$ sudo hciconfig hci0 auth
$ sudo hciconfig hci0 iscan
$ sudo hciconfig hci0 pscan

where hci0 is my bluetooth device, 

to see where is ur device type:

$ sudo hciconfig -a

hope to help u, any question just post it here.

---

### Post by Padre on 2007-07-13
I have same problem.

hciconfig -a
hci0:   Type: USB
        BD Address: 00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
        DOWN
        RX bytes:0 acl:0 sco:0 events:0 errors:0
        TX bytes:0 acl:0 sco:0 commands:0 errors:0

---

### Post by Nanoboy on 2007-07-13
Padre,

Your hci is down, do *hciconfig up* command before anything else.

I am still struggling myself, and I'm quite convinced that I've done absolutely everything I could.  My *hcitool scan* or *hidd --search* just timed out and could never find any device.

---

### Post by Padre on 2007-07-18
not working:

hciconfig up hci0
hci0:   Type: USB
        BD Address: 00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
        DOWN
        RX bytes:0 acl:0 sco:0 events:0 errors:0
        TX bytes:0 acl:0 sco:0 commands:0 errors:0

---

### Post by Nanoboy on 2007-07-18
Try to have a go at following this guide:
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

