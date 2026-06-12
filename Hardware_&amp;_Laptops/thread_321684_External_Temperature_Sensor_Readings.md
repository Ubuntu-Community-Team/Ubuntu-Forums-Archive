---
title: "External Temperature Sensor Readings"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by blakegrover on 2006-12-19
We are looking for a external temperature sensor we can connect to our linux box and get readings from it.  It is for our server room to make sure the air conditioner is working.  We have had the air condition stop working for some reason now 2 times and we would like to know when it decides to stop working so we can go and reset it in the mean time while we figure out why it stops working.

I am looking for a usb/serial device that I would be able to read the values of the temperature through perl or a command line program.  If anyone has any experience or ideas I would appreciate them.

Thanks
Blake

---

### Post by blakegrover on 2008-01-26
Any suggestions

---

### Post by Whiffle on 2008-01-26
I've used a dallas 1-wire bus for this exact thing, even to go as far as control an air conditioner/heater with a linux box.  I almost left it that way (the place with the setup is in another state and people aren't there 24/7), but I was afraid the hardware I pulled out of a junk pile might catch fire or something.  So I'm looking for better hardware...

Anyway...
[http://www.aagelectronica.com/aag/index.html](http://www.aagelectronica.com/aag/index.html) is where I got my stuff.  I have the DS9097U adapter and a TAI8540D 1-Wire Humidity Module.  Works quite well.  It takes some scripting and such to get it working.  I use digitemp ([http://www.digitemp.com/](http://www.digitemp.com/)) to take the readings.

---

