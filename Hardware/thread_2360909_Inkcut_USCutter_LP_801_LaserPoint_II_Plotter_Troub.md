---
title: "Inkcut USCutter LP 801 LaserPoint II Plotter Trouble"
date: 2017-05-09
forum: Hardware
---

### Post by TMundo on 2017-05-09
Hi all,

     I Have a USCutter LP 801 LaserPoint II Plotter, and can't seem to get the plotter to respond when I send graphics to it through Inkcut. I'm runinng Ubuntu 14.04. I installed Inkcut sucessfully, but the plotter doesn't respond to a test cut nor does it cut any of the selected graphics I attempted to send to it.

     For your info...

code:

dmesg | tail
output:

[FONT=Verdana][277885.978058] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0[/FONT]
[FONT=Verdana][277885.978065] usb 4-2: Product: USB <-> Serial[/FONT]
[FONT=Verdana][277885.978070] usb 4-2: Manufacturer: FTDI[/FONT]
[FONT=Verdana][277885.984143] ftdi_sio 4-2:1.0: FTDI USB Serial Device converter detected[/FONT]
[FONT=Verdana][277885.984227] usb 4-2: Detected FT232BM[/FONT]
[FONT=Verdana][277885.984235] usb 4-2: Number of endpoints 2[/FONT]
[FONT=Verdana][277885.984241] usb 4-2: Endpoint 1 MaxPacketSize 64[/FONT]
[FONT=Verdana][277885.984247] usb 4-2: Endpoint 2 MaxPacketSize 64[/FONT]
[FONT=Verdana][277885.984251] usb 4-2: Setting MaxPacketSize 64[/FONT]
[FONT=Verdana][277885.986155] usb 4-2: FTDI USB Serial Device converter now attached to ttyUSB0
[/FONT]




code:

lsusb
output:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 006: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 004: ID 04b4:0033 Cypress Semiconductor Corp. Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



I think I have the required dependencies installed:



[LIST]
[*]pygtk and gtk
[*]pyserial
[*]librsvg2-common
[/LIST]


Although I was a little uncertain as to weather or not I had located the correct programs in the software center when I installed [COLOR=#333333][FONT=verdana]pygtk and gtk[/FONT][/COLOR].  Everything else looked good though.

Any help you could give me would be great as I have work coming my way and would like to get the plotter going ASAP.

---

### Post by pdc on 2017-05-09
this programme Tux Plot [http://securetech-ns.ca/tuxplot.html](http://securetech-ns.ca/tuxplot.html) seems to be very helpful in getting things to work; it links inkscape to the hardware 

It was mentioned in a Mint forum [https://forums.linuxmint.com/viewtopic.php?f=51&t=240180&p=1282102&hilit=vinyl+cutter#p1282102](https://forums.linuxmint.com/viewtopic.php?f=51&t=240180&p=1282102&hilit=vinyl+cutter#p1282102)

---

