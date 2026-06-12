---
title: "Hack an animal RFID tag reader"
date: 2015-01-13
forum: Hardware
---

### Post by coldraven on 2015-01-13
This may be a long shot but here goes..
I just bought one of these 
[http://dthinkrfid.en.ec21.com/Low_Frequency_Handheld_Reader_for--6571154_6571155.html](http://dthinkrfid.en.ec21.com/Low_Frequency_Handheld_Reader_for--6571154_6571155.html)

The software it comes with is for Windows but I would like to be able to use it with Ubuntu.
When plugged in dmesg shows the following ouput
```
[ 6501.960088] usb 3-1: new full-speed USB device number 3 using ohci-pci
[ 6502.129136] usb 3-1: New USB device found, idVendor=10c4, idProduct=ea60
[ 6502.129151] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 6502.129158] usb 3-1: Product: CP2102 USB to UART Bridge Controller
[ 6502.129165] usb 3-1: Manufacturer: Silicon Labs
[ 6502.129171] usb 3-1: SerialNumber: 0001
[ 6502.206384] usbcore: registered new interface driver usbserial
[ 6502.206434] usbcore: registered new interface driver usbserial_generic
[ 6502.206477] usbserial: USB Serial support registered for generic
[ 6502.235978] usbcore: registered new interface driver cp210x
[ 6502.236097] usbserial: USB Serial support registered for cp210x
[ 6502.236196] cp210x 3-1:1.0: cp210x converter detected
[ 6502.372162] usb 3-1: reset full-speed USB device number 3 using ohci-pci
[ 6502.535470] usb 3-1: cp210x converter now attached to ttyUSB0
```

A friend who has Windows managed to sniff some data and sent me this:
> As an example, without the serial negotiation etc 

If you want to retrieve the stored tags

AA BB 06 00 00 00 02 03 02 03 AA is sent

BB 06 02 77 77 02 03 00 is returned (77 77) is the scanner ID

then

022BD0B361130085010100008538
022BD0B36113008501016113854A
022BD0B361130085010100008538
022BD0B361130085010100008538
022BD0B361130085010100008538
022BD0B361130085010100008538
022BD0B361130085010100008538
022BD0B361130085010100008538
022BD0B361130085010100008538
022BD0B361130085010100008538

is spat back - these are the 10 stored tags all the same but there is an offset or XOR happening on the second entry.

I cannot afford to pay him to develop a Linux version so I thought that I may try myself. I opened the case but the chips have been sanded, no identification is possible.
I added myself to group dialout.
I tried using gtkterm via /dev/ttyUSB0 to send the string that would retrieve the stored tags but I think that  the interface needs to be initialized to make it work.
I extracted the Windows executables and dlls, browsed through them with a hex editor but did not find anything that looked like initialization strings.

Has anybody tried this before? Any links would be appreciated, thanks.
I'll tag your pet for free if you bring it around here. It might register as a cow but at least you won't be able to lose it :)

---

### Post by QIII on 2015-01-13
Hello!

Sounds like quite the project!

If your intent is to actually use it, it would simply be easier to use Windows.

If your intent is to see if it can be done, it will likely be quite a chore.  Best wishes with that!  It might be useful for others!

---

### Post by sffvba[e0rt on 2015-01-13
Best of luck with the project, I am sure that you may find some clued up people on this forum but I would also suggest trying the Arch community as well (and as a final note I have found that things designed for Windows often work best in... Windows :p)

---

### Post by coldraven on 2015-01-14
Sorry but I've been busy all day.
I did not want to get all functionality, just to be able to extract the stored tags.
I'm new to Wireshark and sniffing but I did not think that it would be too difficult. Searching the web I've seen Python scripts that interrogate similar devices. I just need to learn Python now :) I have done some programming in the past so it's not entirely infeasible.

---

### Post by oldfred on 2015-01-14
Quick search found this:

[http://rfidiot.org/](http://rfidiot.org/)
RFIDIOt is an open source python library for exploring RFID devices

And it mentions this:
> The EM4x05 range implement the animal tagging standard [ISO-11784]("http://en.wikipedia.org/wiki/ISO_11784_%26_11785") 'Radio-frequency identification of
 animals - Code structure' and ISO-11785 'Radio-frequency identification of animals - Technical concept' (also known as FDX-B).  These chips are ID-only transponders, operating at 134.2kHz and storing 128 bits of data, 64 bits of which are the ID:
 
   Bit 1:              'Animal Flag' - Animal or Non-Animal application indicator
   Bits 2 - 15:      Reserved Field - RFU
   Bit 16:             Data Block Flag - Indicates if more detailed data is also stored on this chip
   Bits 17 - 26:    Country Code - 3 digit country code as defined by [ISO-3166]("http://en.wikipedia.org/wiki/ISO_3166"), or manufacturer code by [icar.org]("http://www.icar.org/pages/manufacturer_codes.htm")
   Bits 27 - 64:    National ID - Unique ID assigned by manufacturer / supplier

---

### Post by coldraven on 2015-01-22
Thanks oldfred, I found this python utility that will interrogate a CP2102 chip but I had some problems getting to work (error: module util not found).
[http://cp210x-program.sourceforge.net/](http://cp210x-program.sourceforge.net/)

I have given the project to a friend who is much better at these sort of things and I will report back if he comes up with the goodies.

---

### Post by tgalati4 on 2015-01-22
Remember the cuecat?  It was a bar code scanner that you scanned magazine articles that had a cuecat barcode.  This was before smartphones and QR codes.  I would bet that the RF-reader is based on a simple barcode reader.  So I would search for the bar code reader libraries that work with linux and use that as a basis for coding.

Sanding the chips makes it harder to reverse engineer, which means it uses standard logic chips.  If it was a custom ASIC, then there would be no need to sand it because it would be a proprietary design.  Sanding == Off-the-Shelf components.

---

### Post by coldraven on 2015-01-23
> **tgalati4 said:**
> Sanding the chips makes it harder to reverse engineer, which means it uses standard logic chips.  If it was a custom ASIC, then there would be no need to sand it because it would be a proprietary design.  Sanding == Off-the-Shelf components.

That is interesting, I would not have thought of that.

P.S. Sorry Mods if this thread is in the wrong place, feel free to move it. Maybe we need an RFID subsection ):P

---

### Post by oldfred on 2015-01-23
Since it now is more support than discussion, moving to hardware sub forum.

---

### Post by tgalati4 on 2015-01-23
I bought a no-name metal detector.  Being curious, I opened it up and found a foreign school of electrical engineering printed on the circuit board.  All the chips were socketed (which is both rare, and nice) and all of the chips were sanded.  It seemed to be a class (reverse) engineering project that was turned into a commercial product.  I presume that the chips were sanded to avoid revealing where the design came from.  It had features of some really high-end metal detectors.

So I conclude that sanded chips == off-the-shelf.  With a logic probe and some patience, you can usually figure out the design.  If you are dealing with a black epoxy blob covering a custom chip, then your chances of revealing the design is more difficult.

Why don't you post a detailed picture of both sides of the circuit board?  That is if you don't mind voiding your warranty.

---

### Post by coldraven on 2015-01-24
> Why don't you post a detailed picture of both sides of the circuit board?  That is if you don't mind voiding your warranty.
To see the bottom of the circuit board I would have to remove the aerial coil which is hot glued in place.
I don't think it's necessary, I'm sure that my pal can hack it. 
See here: [https://picasaweb.google.com/102130182469464429363/X10?authuser=0&feat=directlink](https://picasaweb.google.com/102130182469464429363/X10?authuser=0&feat=directlink)


I found this pdf which has some good info. The SPPyQt utility is no longer on googlecode. 
**Do not try to run any of the so called "clones". They are just malware serving HTML files!**
[https://sppyqt.googlecode.com/files/Python%20for%20Serial%20Communication.pdf](https://sppyqt.googlecode.com/files/Python%20for%20Serial%20Communication.pdf)

Also this python utility should be able to get the data that I need but I could not get it to work.
If you look at the output from dmesg (in my first post) it shows that the chip is a CP2102
[http://cp210x-program.sourceforge.net/](http://cp210x-program.sourceforge.net/)

---

### Post by tgalati4 on 2015-01-24
I can't count the pins on the 3 chips because the resolution of the photo is too low.  What frequency is printed on the crystal?  That's the metal, oblong can on the right side of the ribbon cable.

The CP2102 is just the serial driver.  If your computer had a real serial port, you could use that, but you are going through a USB port, so it requires a driver that converts USB to a standard serial communication that the microcontroller can understand.  Once you get serial communications established, you typically send single string commands to the device and it sends back packets of data--presumably the animal ID information as described in the standards documents.

If you get a data stream with the same ID# as shown in the display, then that is success.  I didn't see any errors in your *dmesg*, so now we have to figure out the commands to send to the serial port.

Here's an example of a command set that I am talking about (page 17) [http://www.ti.com/lit/ug/scbu001/scbu001.pdf](http://www.ti.com/lit/ug/scbu001/scbu001.pdf)

Open a terminal:

```
echo somemeaningfulstringofbytes > /dev/ttyUSB0
```

Send the "Query" command so that it spits back what type of scanner it is.  That gives you more information.

The other way to approach the problem is to capture the output from the Windows reader program.  Decode that to simple codes that resemble the standard RFID command protocol.  Then duplicate that with a simple linux program (a script or a Python program) to send the same commands and receive the data and display it.

Here's some hard core reverse engineering:  [http://www.bunniestudios.com/blog/?p=4297](http://www.bunniestudios.com/blog/?p=4297)

This is an example of reverse-engineering a reverse-engineered product--not unlike your RFID reader.

---

