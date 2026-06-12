---
title: "USBtoSERIAL Mapping?"
date: 2010-02-16
forum: Hardware
---

### Post by kaspar_silas on 2010-02-16
Hi all,

I have a serial to USB convertor I am trying to get working with some hardware. So far I have:

Plugged in the serial to usb converter and typed
$lsusb

which gave (amongst other stuff) this line:
Bus 004 Device 012: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port

so using the vendor ID and partNumber I typed
$sudo modprobe usbserial vendor=0x067b product=0x2303

I then checked with 
$dmesg 

and sure enough the last line was 
usb 4-2: pl2303 converter now attached to ttyUSB0

So far all good. Plus the serial converter is now working at this stage, however the program I am using will only connect to ttyS0,ttyS1,ttyS2,or ttyS3. I don't have access to the programs code to alter this. 

Hence I was wondering if anyone knows how to either change the initial connection point to ttyS0 or knows if it's safe to make a symbolic/hard link. I mean something like:
$ sudo cp /dev/ttyS0 /dev/ttyS0.bkup
$ sudo rm /dev/ttyS0
$ sudo ln-s /dev/ttyUSB0 /dev/ttyS0

Thanks for any help.
(Incidentally if there is a better place for this inquiry feel free to move this post.)

---

### Post by intel on 2010-02-16
use cutecom  apt-get install cutecom  which h/w are you trying the serial port on? is it that seagate HDD fiasco?  -intel

---

### Post by kaspar_silas on 2010-02-16
Cheers for the reply. No unfortunately nothing to do with HDDs. I am trying to communcate with a Galil Motion controller. Basically some hardware to control three motors. 

The card uses it's own propetary Galil language. However helpfully Galil provides a c++ communication wrapper for it's own language. I can thus write my own programs in c++ calling the Galil code when I need to move the motors. This works a treat on my desktop computer which has a serial port.

In a nutshell I have this line.
Galil::addresses();
in the code. It retreives available addresses to connect to.
This lists:
/dev/ttyS0
/dev/ttyS1
/dev/ttyS2
/dev/ttyS3
On my desktop (with a built in serial) I connect to the first and everything works. 

I was hoping I could use my laptop which has no serial ports by using a usb to serial lead. Unfortunately Galil::addresses() doesn't recognize /dev/ttyUSB0 as a valid port. That is why I was asking about linking ttyUSB0 to ttyS0 

I tried cutecom it also did not recognize /dev/ttyUSB0 as a port.

---

### Post by efflandt on 2010-02-17
Make sure you get the correct device for your symlink.  In your first post you mentioned tty0 (which I think is a console as in **t**ele**ty**pe).  ttyS0 is a serial port.

---

### Post by kaspar_silas on 2010-02-17
Yeah good spot. 

I did mean ttyS* but I'll edit the first post to stop others making this mistake.

---

### Post by GeorgeVita on 2010-02-17
Hi **kaspar_silas**,
after creating the /dev/ttyUSB0 port you can create a 'symbolic link' for your /dev/ttyS3 port:
```
sudo ln -sf /dev/ttyUSB0 /dev/ttyS3

```
I used /dev/ttyS**3** as 0 and 1 possibly exist as h/w ports.

**EDIT: ** no need to use 'modprobe' on Ubuntu 9.10 (just tested)
> [11311.552047] usb 2-3: new full speed USB device using ohci_hcd and address 3
[11311.756248] usb 2-3: configuration #1 chosen from 1 choice
[11311.759275] pl2303 2-3:1.0: pl2303 converter detected
[11311.794261] usb 2-3: pl2303 converter now attached to ttyUSB3

Regards,
George

---

