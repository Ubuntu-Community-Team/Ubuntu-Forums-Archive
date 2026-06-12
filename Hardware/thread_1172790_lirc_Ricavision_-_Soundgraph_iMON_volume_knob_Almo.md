---
title: "lirc Ricavision - Soundgraph iMON volume knob Almost working !"
date: 2009-05-28
forum: Hardware
---

### Post by ear9mrn on 2009-05-28
I almost have these two working (did work a kernel or two ago).

The kernel modules these use.

Ricavision (internal usb IR receiver) -> lirc_mseusb2

Dmesg:

lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[ 1734.852086] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[ 1734.964019] usb 7-2: reset full speed USB device using uhci_hcd and address 3
[ 1735.116212] lirc_dev: lirc_register_plugin: sample_rate: 0
[ 1735.120211] lirc_mceusb2[3]: Ricavision eHome Infrared Transceiver on usb7:3


Soundgraph iMON Multimedia IR/VFD w/imon -> lirc_imon (VFD working) volume knob

Dmesg

[ 1748.537508] lirc_imon: Driver for Soundgraph iMON MultiMedia IR/VFD w/imon pad2keys patch, v0.3p2k
[ 1748.537516] lirc_imon: Venky Raju <dev@venky.ws>
[ 1748.537551] lirc_imon: imon_probe: found IMON device
[ 1748.537556] lirc_dev: lirc_register_plugin: sample_rate: 0
[ 1748.539658] lirc_imon: imon_probe: Registered iMON plugin(minor:1)
[ 1748.539738] lirc_imon: imon_probe: iMON device on usb<7:2> initialized


So far so good.

I then do 'cat /dev/lirc0' (the IR receiver) I get the following:

&#65533;&#65533;&#65533; &#65533;&#65533; &#65533; &#65533; &#65533;&#65533; (crud)

Same for 'cat /dev/lirc1' The volume knob.


&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; (crud)

I try 'mode2 -d /dev/lirc0' & 'mode2 -d /dev/lirc1' and get the following.

mode2: could not get hardware features
mode2: this device driver does not support the LIRC ioctl interface
mode2: make sure you use a current version of the driver

and with 
irw,irw /dev/lirc0 and /dev/lirc1

Connection refused.....

mythbuntu 2.6.27-14-generic on a 64bit machine. Any suggestions to get these to work with lirc would be great.

Thanks,

Pete.

---

