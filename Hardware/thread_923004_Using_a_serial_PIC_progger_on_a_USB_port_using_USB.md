---
title: "Using a serial PIC progger on a USB port using USB2SERIAL"
date: 2008-09-17
forum: Hardware
---

### Post by Hakachukai on 2008-09-17
Hi, I've been searching around and I haven't found the answer to this question yet... 

I have Ubuntu hardy, and my laptop has no serial ports, but it does have 4 USB ports. 

I have a serial PIC-PG2C programmer, and Piklab along with GPasm installed.

I need to know which USB2SERIAL cable to buy, because I'm told that only certain ones will work for PIC programming because of "bitbanging".

Has anyone else done this? 
Which cables work? (I'm looking for cheapest simplest one because I'm a very poor college student :-P )

How do I set it up to work with the USB2SERIAL module?
What tool chain do I need to use to actually write the hex file to the programmer?

Thanks in advance! I'd really love to get this fully working in Linux :-)

---

### Post by ModelM on 2008-09-18
One of the best chips in these cables is the PL2303 from Prolific Technology. A cable using that chip is recognized as soon as you plug it in & is set up as /dev/ttyUSB0. It then behaves just as a serial port would including hardware or software handshaking and higher speeds than an old fashioned serial port, 230400 or greater.

Unfortunately most of the cables aren't labeled as to what chip they contain.

The one I use is an OEM I bought locally for $19 & even included an adapter so it works with 9 or 25 pin connectors. It has the PL2303 chip but I didn't know that when I bought it - I just got lucky. It would be easy to recognize, though, if you came across it. The cable is silver shielded covered in clear plastic & the plugs are clear blue like all the peripherals for the original iMac were. And, as I said, it includes a DB9 to DB25 adapter - I would think that most don't.

---

