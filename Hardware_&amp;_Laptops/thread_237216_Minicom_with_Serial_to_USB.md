---
title: "Minicom with Serial to USB"
date: 2006-08-15
forum: Hardware &amp; Laptops
---

### Post by cburwell on 2006-08-15
I am trying to connect to a Sun Netra X1 using my laptop. I do not have any serial port on my laptop (Compaq V2000 Turion), so I purchased a serial to USB adaptor.

The problem is I do not know what the location of the USB to serial converter is. I searched, and most places say that it should be something like/dev/ttyUSB0, but I do not have that on my install.

Any help would be appreciated.

---

### Post by cburwell on 2006-08-16
I guess this is a topic that not many people have had experience with.

Using dmesg and tail -f /var/log/messages I see that the device is detected, and is shows what bus the device is connected to. However, I do not see anything that indicates that the device has been "mounted". 

I can explore to the /dev folder, but that does not work. For example, dmesg shows that the device is on bus 002 device 009. I point minicom to that device location and it just says "disconnected". Maybe I just don't know how to use Minicom?

---

### Post by webdr on 2006-10-02
try minicom -s
then set the serial device as ttyUSB0

-RacerX

---

### Post by webdr on 2006-10-02
also...
dmesg |grep usb
then look at last line
it may indicate that the usb/serial converter is on ttyUSB1


-RacerX

---

### Post by mzembe on 2006-10-02
I just tried it on my laptop - plugged the adapter in, checked DMESG and got the node, started minicom -s & configured it for /dev/ttyUSB0 and it initialised a serial modem connected to my USB.

After plugging in the adapter and waiting for the hd LED to settle dmesg logged detection and assignment of this type of adapter cable:
[17232327.020000] usb 1-1: new full speed USB device using uhci_hcd and address
2
[17232328.204000] usbcore: registered new driver usbserial
[17232328.208000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[17232328.208000] usbcore: registered new driver usbserial_generic
[17232328.208000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[17232328.224000] drivers/usb/serial/usb-serial.c: USB Serial support registered for pl2303
[17232328.224000] pl2303 1-1:1.0: pl2303 converter detected
[17232328.228000] usb 1-1: pl2303 converter now attached to ttyUSB0
[17232328.228000] usbcore: registered new driver pl2303
[17232328.228000] drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver

---

### Post by mzembe on 2006-10-02
I had to examine minicom's exit message to realise the terminal was h0rked and was clobbering my '/' unless I counted the backspaces while reconfiguring minicom for USB0 - it's a laptop thing I guess. You could watch the cursor and type backspace*3 with /dev/ttyS0 to make it 'look' right on the screen but by carefully backspacing only twice and configuring minicom for what appeared to be '/dev/SUSB0' only worked. lol, good luck.

---

### Post by mzembe on 2006-10-02
I was thinking about this (it just sunk in) what the ??? is a 'bus 002 device 009' - what was the dmesg output again? Thats a lot different from what I got..

---

### Post by AussieLakerFan on 2006-10-10
I actually searched the forum for minicom, because I was having a hard time getting it all up and running, and also trying to create a launch button from the task bar...

I am new to linux, but I worked it out with a little help from a friend and from this forum!  I just throught I would put what I did because it worked first try.

Custom task bar launch, command "sudo minicom", added an icon, works no probs.

ran "dmesg" from terminal, found the usb-serial interface, was the last entry, said it was at "/dev/ttyUSB0"

entered that into the config menu of minicom along with flow speeds, etc and it is perfect.

:KS

---

