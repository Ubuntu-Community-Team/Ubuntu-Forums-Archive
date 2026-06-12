---
title: "parallel port card"
date: 2015-05-29
forum: Hardware
---

### Post by aknjusa on 2015-05-29
I have a Dell Vostro 200 machine with an add in card for adding a parallel port to which I connect an HP1100 LaserJet printer for occasional printing.
This works fine in Windows Vista 32-bit Home which was the original OS but I am trying to switch to Ubuntu 14.04 LTS and the parallel port is not available as an option when I try to install the printer using the software from HP.
The card is a black PCB with a large SMD chip (1' square) marked  Extending Future DC0923 L002M003.

A manufacturer (Startech, most likely to have made this card) indicates the below in a installation doc in the troubleshooting section.
However, there is no such file (/proc/pci) in my system.
Is  there any updated procedure similar to this?

=======================================================
From Startech
Q: 
How do I install this card in Linux?
A: 
Once you have physically installed the card in the computer, follow the following steps to 
activate the port(s) in the operating system:
1.
List the resources assigned to the PCI card by typing this command: 
more /proc/pci
 The response will include something similar to the following, however, yours will be 
different:
Bus 0, Device 11, function 0:
Serial controller : Unknown vendor Unknown device (rev 01).
Vendor id=9710, Device id=9715
Medium devsel. Fast back-to-back capable. IRQ 11
I/O at 0xc000 [0xc001] printer port 1
I/O at 0xc400 [0xc401] ECP/EPP config registers 1
I/O at 0xc800 [0xc801] printer port 2
I/O at 0xd000 [0xd001] ECP/EPP config registers 2
I/O at 0xd400 [0xd401] not used
I/O at 0xd800 [0xd801] not used
2.
Unload the paraport_pc.o module by typing in this command:
rmmod paraport_pc.o
3.
Reload the parport_pc.o module to include the new parallel port. The followingexample 
assumes the resources discovered in step 1 and a built-in motherboard parallel port with a 
memory address of 378 and an IRQ setting of 7.
insmod parport_pc.o io=0x378,0xc000,0xc800 irq=7,11,none
The first port assigned will be /dev/lp0, the second will be /dev/lp1, etc. In this case, the built-in 
parallel port will be assigned /dev/lp0, and the port on the PCI parallel card will be
/dev/lp1 (and /dev/lp2 if you are using a two port model

---

### Post by aknjusa on 2015-06-04
I found a similar thread and it indicates use lspci -v command.
In my case the output is as below.


02:00.0 Communication controller: Device 5372:6872 (rev 01)
	Subsystem: LSI Logic / Symbios Logic Device 0012
	Flags: slow devsel, IRQ 21
	I/O ports at df00 [size=8]
	I/O ports at de00 [size=8]
	I/O ports at dd00 [size=8]
	I/O ports at dc00 [size=8]
	I/O ports at db00 [size=8]
	I/O ports at da00 [size=16]
	Kernel driver in use: serial

Can I pick any port for the parallel port driver configuration?
Ubuntu does not seem to identify any as parallel port.
It works fine in Windows Vista 32 bit home edition.

---

### Post by tgalati4 on 2015-06-04
There are several switches for that module:

> parm:           io:Base I/O address (SPP regs) (array of int)
parm:           io_hi:Base I/O address (ECR) (array of int)
parm:           irq:IRQ line (array of charp)
parm:           dma:DMA channel (array of charp)
parm:           verbose_probing:Log chit-chat during initialisation (int)
parm:           init_mode:Initialise mode for VIA VT8231 port (spp, ps2, epp, ecp or ecpepp) (charp)

What was the exact command that you used to load the *parport_pc* module?

Does your PC have a built-in parallel port?

---

### Post by aknjusa on 2015-06-04
I did not use any command to load the parallel port.
The output was from lspci -v

My PC does not have a built-in parallel port so I need to use this add-in card.

---

### Post by tgalati4 on 2015-06-04
So open a terminal:

```
sudo modprobe parport_pc io=0xdf00 io_hi=0xde00 irq=21
```

Check to see if there is a line printer device:

```
ls -la /dev/lp*
```

If /dev/lp0 exists then try sending something to it:

```
cp my_test_file.txt /dev/lp0
```

---

### Post by aknjusa on 2015-06-04
Here is a picture of the chip on the card.
Its name indicates RS232 but I am using a parallel cable to connect the printer.
The printer does not have a serial port.
[http://www.hp.com/ctg/Manual/bpl06115.pdf](http://www.hp.com/ctg/Manual/bpl06115.pdf)

---

