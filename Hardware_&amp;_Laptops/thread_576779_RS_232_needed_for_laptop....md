---
title: "RS 232 needed for laptop..."
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by PsycoGeek on 2007-10-15
I now (finally, after all these years of wishing they would just go away) once again need RS 232 on my new laptop, which of course did not come with a com port.  

What is the best method of doing this?  I have looked at PCMCIA Type 2 cards, but was as of yet unable to find any info on compatibility with Linux.  Serial to USB may not work because of the application, which is remotely controlling a telescope.  

Here are some of the PCMCIA cards that I was looking at:

[SIIG JJ-PCM012-S2]("http://www.siig.com/ViewProduct.aspx?pn=JJ-PCM012-S2")

[Syba SD-PCB-1S]("http://www.syba.com/Product/Info/Id/82")

SIIG also makes a CF to serial converter ([SIIG JJ-CFTS11]("http://www.siig.com/ViewProduct.aspx?pn=JJ-CFTS11")

I have not found any other (decent quality)cards yet, so if you know of any that will work with Ubuntu please post them here.

---

### Post by daller on 2007-11-07
What exactly is the problem with USB to Serial converters?

They are cheap, and almost all supported under linux.

Most PCMCIA cards even use a virtual layer!

There should be no problem using these things...

The address will be /dev/ttyUSB0 or something...

---

### Post by happy-hippo on 2007-11-07
I use a USB to serial converter to connect my laptop with a Garmin GPS and it worked out-of-the-box.
No experience regarding PCMCIA cards, sorry.

---

### Post by gfxguy on 2007-11-07
I'll third giving a USB to Serial converter... used one for a very specific home (office built, I suppose) built application, and it worked exactly like an serial port would.

---

### Post by juhl on 2007-11-08
If you find a card which is RS-232 to whatever, then you can use the program `socat' to pipe the data to whatever you want (STD-I/O, TCP-UDP/IP, PIPES..etc.).

I'm using a WLAN <-> RS-232 module for a wireless application.

---

### Post by Bartender on 2007-11-08
Sabrent SBT-USC1M cable.
[http://www.newegg.com/Product/Produc...&Tpk=SBT-USC1M\](http://www.newegg.com/Product/Produc...&Tpk=SBT-USC1M\)

Can't guarantee this will work in your unique application but it worked like a champ in Ubuntu 7.04 for a US Robotics serial modem.  The modem was detected at /dev/ttyACMO

---

