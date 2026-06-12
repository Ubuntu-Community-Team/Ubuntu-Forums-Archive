---
title: "USB ports stopped working"
date: 2008-07-30
forum: Hardware
---

### Post by cw2008 on 2008-07-30
Hi all.

I have been running Hardy Heron 8.04 for a few months now on a new system with a Gigabyte GA-MA78GM-SH2 motherboard.

My USB ports used to work, flash drives would auto mount and I had a USB mouse. Then, suddenly, they all stopped working.  The mouse actually stopped working while I was using it. I can't remember if I had just completed an update at the time.

Now, when I plug a flash drive into my USB ports, absolutely nothing happens, except on one particular port where dmesg shows the following: 

"[ 2131.996652] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?"

I have also tried plugging in an MP3 player which charges its battery from a USB port, but the battery does not charge.

Has anyone had anything like this before?
Does it sound like a hardware problem?

Thanks for any help in advance!

---

### Post by Altur on 2008-07-30
Are you using wireless at all?  I had the same symptoms when I made a mistake setting up my wireless on my laptop.

---

### Post by cw2008 on 2008-07-31
No, I'm not using wireless.

Can I re-install the USB drivers? Does anyone have any advice on how to do that?

---

### Post by ModelM on 2008-07-31
You might get a few clues by typing into a terminal:

```
dmesg | grep -i hci

```
To help interpret the results: EHCI is the USB 2.0 driver. UHCI & OHCI are USB 1.1 drivers.

---

### Post by cw2008 on 2008-08-03
Hi ModelM, I did as you suggested and got the following output:

```
[   28.995840] pci 0000:00:11.0: set SATA to AHCI mode
[   31.669433] ahci 0000:00:11.0: version 3.0
[   31.669518] ahci 0000:00:11.0: controller can't do PMP, turning off CAP_PMP
[   31.675221] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   32.668469] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   32.668474] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pio slum part 
[   32.668791] scsi0 : ahci
[   32.669008] scsi1 : ahci
[   32.669112] scsi2 : ahci
[   32.669209] scsi3 : ahci
[   34.571003] ehci_hcd 0000:00:12.2: EHCI Host Controller
[   34.571234] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[   34.571275] ehci_hcd 0000:00:12.2: debug port 1
[   34.571290] ehci_hcd 0000:00:12.2: irq 18, io mem 0xfe02c000
[   34.581911] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.684824] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   34.684843] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[   34.684877] ehci_hcd 0000:00:13.2: debug port 1
[   34.684892] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
[   34.697690] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.801692] ohci_hcd 0000:00:12.0: OHCI Host Controller
[   34.801711] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[   34.801729] ohci_hcd 0000:00:12.0: irq 20, io mem 0xfe02e000
[   34.965289] ohci_hcd 0000:00:12.1: OHCI Host Controller
[   34.965310] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[   34.965323] ohci_hcd 0000:00:12.1: irq 20, io mem 0xfe02d000
[   35.125003] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   35.125024] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[   35.125042] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02b000
[   35.284709] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   35.284726] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[   35.284739] ohci_hcd 0000:00:13.1: irq 16, io mem 0xfe02a000
[   35.493811] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fdcff000-fdcff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   36.578464] ohci_hcd 0000:00:14.5: OHCI Host Controller
[   36.578493] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[   36.578508] ohci_hcd 0000:00:14.5: irq 16, io mem 0xfe028000
[   98.639475] Bluetooth: HCI device and connection manager initialized
[   98.639479] Bluetooth: HCI socket layer initialized

```

Any idea what the 'debug port 1' above referrs to? Is that normal?

Thanks for the help!

---

### Post by kahlil88 on 2008-08-03
It may very well be a hardware problem. A few months ago, I was unable to mount my flash drives. The only way to make it work was by disabling the USB-2.0 kernel modules, which meant I was using it in USB 1.0 mode (VERY slow). For awhile I thought it was maybe a bad kernel update, but eventually I stumbled on a forum that said I had classic symptoms of a southbridge chip gone bad. Put in a new motherboard, works fine.

---

### Post by mb_webguy on 2008-08-03
It's probably a hardware problem.  I had the same thing happen to me last year, and knew it was a hardware problem since I was dual-booting with Windows XP, and I couldn't get my USB ports to work with either OS.

---

### Post by ATMOS_SKY on 2008-08-06
> **ModelM said:**
> You might get a few clues by typing into a terminal:

```
dmesg | grep -i hci

```
To help interpret the results: EHCI is the USB 2.0 driver. UHCI & OHCI are USB 1.1 drivers.

Hey, Would anyone get me started for fixing my usb port problems?

I have a hp tx1000 that has 2 usb ports in the back and 1 more on the right side of the laptop.


%% Problem Description Start: 

I used NDISWRAPPER to get my wireless working, and I did get it working but sacrificed my USB ports working correctly.  

The logitech mouse is only getting power when it starts in a usb port from start up. If I was to take the mouse out and then plug it back into the same port the mouse does not power back up.  While my Dell keyboard does not get power at all even when it is in from start up.  With power the ubuntu (Hardy) does not recognize my mouse like it did before the NDISWRAPPER.

I dual boot with vista tablet and these keyboards and mouses work on that.

I'm having to use synergy to use a mouse on my laptop from another computer while my tx1000 is in linux please any help is appreciated.

%% Problem Description End: 

I've searched through a lot of these forums and I've found kinda useful information for my tx1000 on this forum pages 79 & 80ish relate to USB stuff
[http://ubuntuforums.org/showthread.php?t=442483](http://ubuntuforums.org/showthread.php?t=442483)

here is the listing of 
            dmesg | grep -i hci 
below that I also listed the output of
            sudo udevcontrol --start_exec_queue
            dmesg | grep usb    

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
in_a_terminal_as_user:~$ dmesg | grep -i hci
[   20.341786] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   20.342437] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   20.342701] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   20.342726] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xc0004000
[   20.502695] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   20.502755] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   20.502792] ehci_hcd 0000:00:0b.1: debug port 1
[   20.502809] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xc0005000
[   20.513876] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.413190] usb 2-2: new high speed USB device using ehci_hcd and address 3
[   22.244584] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   22.776196] usb 1-5: new full speed USB device using ohci_hcd and address 3
[   23.219981] usb 2-2.1: new high speed USB device using ehci_hcd and address 5
[   23.539761] usb 2-2.2: new full speed USB device using ehci_hcd and address 6
[   23.856537] usb 2-2.3: new full speed USB device using ehci_hcd and address 7
[   40.764423] Bluetooth: HCI device and connection manager initialized
[   40.764429] Bluetooth: HCI socket layer initialized
[   44.180188] ohci_hcd 0000:00:0b.0: remove, state 1
[   44.222895] ohci_hcd 0000:00:0b.0: USB bus 1 deregistered


%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
separator, :)
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

in_a_terminal_as_user:~$ sudo udevcontrol --start_exec_queue
in_a_terminal_as_user:~$ dmesg | grep usb
[   28.760170] usbcore: registered new interface driver usbfs
[   28.760195] usbcore: registered new interface driver hub
[   28.761265] usbcore: registered new device driver usb
[   28.776215] usb usb1: configuration #1 chosen from 1 choice
[   29.303665] usb 1-2: new high speed USB device using ehci_hcd and address 3
[   29.437226] usb 1-2: configuration #1 chosen from 1 choice
[   30.261953] usb usb2: configuration #1 chosen from 1 choice
[   30.275880] usb 1-2.1: new high speed USB device using ehci_hcd and address 6
[   30.385521] usb 1-2.1: configuration #1 chosen from 1 choice
[   30.608017] usb 1-2.2: new full speed USB device using ehci_hcd and address 7
[   30.716915] usb 1-2.2: configuration #1 chosen from 1 choice
[   30.937572]  sda1 sda2 sda3 <<6>usb 1-2.3: new full speed USB device using ehci_hcd and address 8
[   31.045314] usb 1-2.3: configuration #1 chosen from 1 choice
[   31.359049] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   31.573001] usb 2-1: configuration #1 chosen from 1 choice
[   31.890649] usb 2-5: new full speed USB device using ohci_hcd and address 3
[   32.133617] usb 2-5: configuration #1 chosen from 1 choice
[   32.446229] usb 2-7: new full speed USB device using ohci_hcd and address 4
[   32.684199] usb 2-7: configuration #1 chosen from 1 choice
[   32.687370] usbcore: registered new interface driver hiddev
[   32.689372] input: eGalax INC. USB TouchController as /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2.3/1-2.3:1.0/input/input2
[   32.706092] input,hiddev96,hidraw0: USB HID v2.10 Pointer [eGalax INC. USB TouchController] on usb-0000:00:0b.1-2.3
[   32.713259] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input3
[   32.722031] input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:0b.0-1
[   32.729231] input: Logitech USB Gaming Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-5/2-5:1.0/input/input4
[   32.738026] input,hidraw2: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:0b.0-5
[   32.749073] hiddev97hidraw3: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:0b.0-5
[   32.749089] usbcore: registered new interface driver usbhid
[   32.749092] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   39.702318] usbcore: registered new interface driver hci_usb
[   39.814878] usbcore: registered new interface driver usbtouchscreen
[   39.927176] usbcore: registered new interface driver uvcvideo
[   43.092384] usbcore: registered new interface driver ndiswrapper
[   52.575113] usb usb2: USB disconnect, address 1
[   52.575116] usb 2-1: USB disconnect, address 2
[   52.612795] usb 2-5: USB disconnect, address 3
[   52.660932] usb 2-7: USB disconnect, address 4

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
thanks in advance

---

### Post by ATMOS_SKY on 2008-08-17
I solved my problem but thank you anyway ubuntu community,

---

### Post by dsm iv tr on 2008-08-18
Glad to see the problem was resolved. I have an alternate solution. I had to

```

sudo rmmod ehci_hcd
sudo mv /lib/modules/2.6.24-19-generic/kernel/drivers/usb/host/ehci_hcd.ko ~
sudo update-initramfs -u

```

then add

```

blacklist ehci_hcd

```

to /etc/modprobe.d/blacklist to actually stop it from loading at all so I could use ohci_hcd as a workaround - it's built into the initramfs, so my hubs/devices would be grabbed by it no matter what. I moved the module back after I rebuilt the initramfs, just in case I found a patched version. But no luck yet.

---

