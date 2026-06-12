---
title: "ftdi_sio 2-6:1.0: device disconnected &amp; lcdproc"
date: 2008-11-30
forum: Hardware
---

### Post by JedTheHead on 2008-11-30
Hey there!

Ubutnu 8.04 

I am trying to get LCDproc to work with an L.I.S. MCE 2005 VFD display and everything I have read tells me it should work with a few modifications.  I have made those changes to LCDd.conf and when I load it, it continually disconnects and /dev/ttyUSB0 disappears.  Everything I can find via Google points to removing / purging brltty and brltty-x11 - which I have done.  Still, after loading LCDd, I get a the display to change once, then receive the following in dmesg:


ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0
[ 9385.101795] ftdi_sio 2-6:1.0: device disconnected


Anyone else experience this or have any ideas?

Thanks!

---

