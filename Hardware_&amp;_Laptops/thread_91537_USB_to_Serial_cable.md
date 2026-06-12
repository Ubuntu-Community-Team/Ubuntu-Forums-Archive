---
title: "USB to Serial cable?????"
date: 2005-11-17
forum: Hardware &amp; Laptops
---

### Post by gra_ulv on 2005-11-17
I have a little Dell Latitude LT [P2 266, 64 Mb Ram] that I use for consoling into my switches and routers at work.  I just put Ubuntu on it and love it. (its also on the PC on my workbench that I do my Network monitoring and scanning from)  Does anyone know if I can get a USB to serial cable to work?

newb here, so I'll need details if its possible.

here is a link to the cable I have.  [http://www.radioshack.com/product/index.jsp?productId=2036258](http://www.radioshack.com/product/index.jsp?productId=2036258)

---

### Post by ranf on 2005-11-17
[QUOTE=gra_ulv]Does anyone know if I can get a USB to serial cable to work?

newb here, so I'll need details if its possible.

here is a link to the cable I have.  [http://www.radioshack.com/product/index.jsp?productId=2036258](http://www.radioshack.com/product/index.jsp?productId=2036258)[/QUOTE]
I'd just try it. 
- open a terminal
- enter `tail -f /var/log/messages'
- hit <Enter> a few times to get some blank lines
- plug your converter into the USB port
- post the lines that should have appeared now

---

### Post by gra_ulv on 2005-11-17
it is now connected to ttyUSB0. (why don't I ever just plug something in, oh well)  How would I console to a switch using that?

---

### Post by ranf on 2005-11-18
[QUOTE=gra_ulv]it is now connected to ttyUSB0. (why don't I ever just plug something in, oh well)  How would I console to a switch using that?[/QUOTE]
Install `minicom'  for instance. Maybe you need the `universe' repository enabled (search the wiki on how to do it).
You will need to adjust the serial port to /dev/ttyUSB0. And the serial settings need to fit. Most likely it is 9600 8N1.

---

### Post by gra_ulv on 2005-11-18
[QUOTE=ranf]Install `minicom'  for instance. Maybe you need the `universe' repository enabled (search the wiki on how to do it).
You will need to adjust the serial port to /dev/ttyUSB0. And the serial settings need to fit. Most likely it is 9600 8N1.[/QUOTE]

coolness, thanks.  going to try it now.

---

### Post by gra_ulv on 2005-11-18
[QUOTE=gra_ulv]coolness, thanks.  going to try it now.[/QUOTE]

thank you very much, works great.  had to change flow control. hardware: off, software:on.  YAY!!  I can manage my Cisco Aironet again.  lol

---

### Post by JustAboutRealJAR on 2007-09-17
how do I configure the serial connection (ie set baud rate, flow control, FIFO, etc)

---

### Post by Dinox on 2007-09-17
use gtkterm.

then select tttyusb0 something like that.

open gtkterm
>configuration>port>/dev/ttyUSB0

it cool!:lolflag:

---

### Post by JustAboutRealJAR on 2007-09-18
thanks... the serial port works for the term now... but still isn't getting along with my Basic Stamp Programmer (which I tested in windows)... anybody have an idea why this is?

---

### Post by JustAboutRealJAR on 2007-09-18
Ok thanks for all the help guys... I got the real serial port to work... so I'm going to move the BASIC Stamp problem to a new thread: [http://ubuntuforums.org/showthread.php?p=3385051#post3385051]("http://ubuntuforums.org/showthread.php?p=3385051#post3385051")

---

### Post by dlynch912 on 2007-11-05
I'm sorry to resurrect this old thread, but I have this same converter and i'm having a hell of a time getting it to work.  

When I plug it in, all dmesg spits out is:

[ 2519.016000] usb 2-1: new full speed USB device using uhci_hcd and address 5
[ 2519.176000] usb 2-1: configuration #1 chosen from 1 choice

and lsusb says:

Bus 002 Device 005: ID 05ad:0fba Y.C. Cable U.S.A., Inc. 



Based on everything I've read online about ubuntu and this device, it should just work and attach itself to something like /dev/ttyUSB*

Am I missing a package or something??

This is a fresh install of Gutsy.

Thanks in advance for any and all help.

---

### Post by VeeDubbss on 2007-11-26
I am also having difficulty with this.  I had this exact USB --> Serial cable working before - not sure when it stopped working - I would guess going to 7.10 might have affected it.  Anyways...here is what I see when I plug it in.

Nov 26 14:45:38 3452mmcgrath kernel: [ 1936.464000] usb 2-2: new full speed USB device using uhci_hcd and address 9
Nov 26 14:45:38 3452mmcgrath kernel: [ 1936.660000] usb 2-2: configuration #1 chosen from 1 choice
Nov 26 14:45:38 3452mmcgrath kernel: [ 1936.664000] ftdi_sio 2-2:1.0: FTDI USB Serial Device converter detected
Nov 26 14:45:38 3452mmcgrath kernel: [ 1936.664000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/ftdi_sio.c: Detected FT232BM
Nov 26 14:45:38 3452mmcgrath kernel: [ 1936.664000] usb 2-2: FTDI USB Serial Device converter now attached to ttyUSB0
Nov 26 14:45:41 3452mmcgrath kernel: [ 1939.516000] usb 2-2: usbfs: interface 0 claimed by ftdi_sio while 'brltty' sets config #1
Nov 26 14:45:41 3452mmcgrath kernel: [ 1939.520000] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
Nov 26 14:45:41 3452mmcgrath kernel: [ 1939.520000] ftdi_sio 2-2:1.0: device disconnected

As you can see - it gets detected and installed - but then it disconnects itself.  Not sure what is going on...any help is appreciated!!!

---

### Post by VeeDubbss on 2007-11-26
Nevermind - I got it to work.  I had to uninstall brltty for it to work.  brltty must have gotten reinstalled with the upgrade to 7.10.

---

