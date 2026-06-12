---
title: "Pad PSX to Parallel port - Not working"
date: 2016-03-13
forum: Hardware
---

### Post by bastpos on 2016-03-13
Hi. I use the operating system Ubuntu 14.04 (64 bit)
> 
$ uname -a
Linux x 3.13.0-74-generic #118-Ubuntu SMP Thu Dec 17 22:52:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


I connected Pad PSX to Parallel port. 
> 
Schematic:
[IMG]http://www.raphnet.net/electronique/psx_adaptor/images/psx.gif[/IMG]

[http://www.raphnet.net/electronique/psx_adaptor/psx_adaptor_en.php](http://www.raphnet.net/electronique/psx_adaptor/psx_adaptor_en.php)


Parallel port controller is not integrated with the motherboard. But is on the card plugged into a PCI slot
> 
0e:02.0 Parallel controller: MosChip Semiconductor Technology Ltd. PCI 9865 Multi-I/O Controller (prog-if 03 [IEEE1284])
    Subsystem: Device a000:2000
    Flags: bus master, medium devsel, latency 32, IRQ 18
    I/O ports at be00 (size=8)
    I/O ports at bd00 (size=8)
    Memory at fbcfe000 (32-bit, non-prefetchable) [size=4K]
    Memory at fbcfd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: parport_pc

0e:02.2 Parallel controller: MosChip Semiconductor Technology Ltd. PCI 9865 Multi-I/O Controller (prog-if 03 [IEEE1284])
    Subsystem: Device a000:2000
    Flags: bus master, medium devsel, latency 32, IRQ 17
    I/O ports at bc00 (size=8)
    I/O ports at bb00 (size=8)
    Memory at fbcfc000 (32-bit, non-prefetchable) [size=4K]
    Memory at fbcfb000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: parport_pc


My First step - turned off the printing
> 
$ sudo modprobe -r lp


Activation joydev
> 
$ sudo modprobe joydev


Two PSX Pads in Parport0
> 
$ gc=parport0,pad1,pad2


> 
$ sudo modprobe gamecon gc=0,7,0,0,0,0
modprobe: ERROR: could not insert 'gamecon': No such device

$ sudo modprobe map=0,7,0,0,0,0
modprobe: FATAL: Module map=0,7,0,0,0,0 not found.

(0,7,0,0,0,0 -> Where the first 0 is the first Parallel port and "7" is a PSX Pad controller)

Device "PSX Pad to PC" working in Windows, so this device is done correctly. But not working in Linux. Please help me solve this problem

---

### Post by bastpos on 2016-03-13
Okay, I worked it out :)\\:D/

First step is installation gamecon from [this]("http://www.niksula.hut.fi/~mhiienka/Rpi/gamecon-gpio-rpi-dkms_0.9_all.deb")

Next step is installation joystick
> 
$ sudo apt-get install joystick


Disable lp from modules and add both lines "joydev" and "gamecon map=0,7"
> 
$ cat /etc/modules
parport_pc
parport
[COLOR=green]#lp[/COLOR]
rtc
vhba
[COLOR=green]joydev
gamecon map=0,7[/COLOR]


Finally testing PSX Pad
> 
$ jstest /dev/input/js0

```

Driver version is 2.1.0.
Joystick (PSX controller) has 6 axes (X, Y, Rx, Ry, Hat0X, Hat0Y)
and 12 buttons (BtnX, BtnY, BtnTL, BtnTR, BtnTR2, BtnSelect, BtnStart, BtnMode, BtnThumbL, BtnThumbR, ?, ?).
Testing ... (interrupt to exit)
Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:-32767  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:-32767  3:-32767  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:-32767  3:-32767  4:-32767  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:-32767  3:-32767  4:-32767  5:-32767 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5:-32767 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:-32767  5:-32767 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:-32767 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:-32767  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:-32767  1:-32767  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:-32767  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1: 32767  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:-32767  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:-32767  1:-32767  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:-32767  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:-32767  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:-32767  1: 32767  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1: 32767  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0: 32767  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0: 32767  1: 32767  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1: 32767  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:-32767  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2: -4096  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2: -9012  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2: -7100  3:     0  4:     0  5:     0 Buttons:  0:ofAxes:  0:     0  1:     0  2:-10650  3:     0  4:     0  5:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off 

```

Done :):D

---

