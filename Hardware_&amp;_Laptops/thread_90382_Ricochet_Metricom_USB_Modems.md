---
title: "Ricochet Metricom USB Modems"
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by hawaiione on 2005-11-14
Hello everyone, I am new to the Ubuntu forums, I have just switch from Microsucks to Suse to Ubuntu. No problems so far until today. Lost my broadband connection, and it's so hard to go back to dialup. I dug out my ricochet Metricom USB modem and tried to setup an Internet connection. No luck, did some research, found out that it is possible to setup the modem for use in Redhat, can anyone help me with Ubuntu? If you are not sure what an Ricochet modem is, it is an wireless modem that is connected by cell phone technology, connection is by USB, and it supports 2.0 Download speeds are between 148-220kbps, and it is only available in a few areas. For more info, go to [www.ricochet.com](www.ricochet.com)  It works well with windows, it should work great with Linux. Help anyone....:confused:

---

### Post by Scunizi on 2006-06-03
Hopefully by posting here it will help this thread stay alive.  I've just introduce Ubuntu to a friend and his only access to the net is through the richochet product.  Anyone?  Anyone?

---

### Post by srf21c on 2006-10-25
I've managed to get a novatel wireless Merlin for Ricochet PC card working under Dapper 6.06, although it's excruciatingly slow.  Think it might have to do with a bug in the serial driver, which was supposedly fixed in kernel 2.4.4.  

[http://homepages.nyu.edu/~gmp216/nrm6842/](http://homepages.nyu.edu/~gmp216/nrm6842/)

---

### Post by morbid_bean on 2007-03-10
I need to set up my modem in linux too...has anyone found a way yet??

---

### Post by tomwg123 on 2007-04-08
Hi Guys,

I installed Ubuntu yesterday and with minimal tweaking got it working with my Ricochet USB modem.

I'm going off memory, but basically what I did was:

1) Plugged modem into usb port and turned it on.  Was then able to verify in the device manager that it detected the modem.

2) In the device manager I looked at the serial port sub-device under the modem and saw it said the device file was /dev/ttyACM0

3) After a little digging I found that it looked like I needed to install a PPP dialer.  In the package manager I installed Knome PPP.  I had internet access through my network at this point - if you don't, you may have to burn it to a CD or something.

4) In Knome PPP went into Setup, set the device to what I saw in device manager (/dev/ttyACM0).  I then hit the Detect button and it changed the type to Analog and the speed to 460800.

5) At this point I tried to connect but it failed.  Looking at the log it showed the modem complaining about the init string.  To fix that I clicked the Init String button, and trimmed the first entry (Init 2) to be just ATQ0

6) The last thing I did was enter the same phone number as was setup on my Windows PC (3333) and put in a random username / password.  I was then able to hit connect and was online.  It seemed to run the same speed as on Windows.


Hope this helps.  I'm not sure if it's the best way to do it, but it worked for me.

---

### Post by airbornespent on 2008-03-23
I've been looking for a few ricochet modems (usb or serial) for experimenting with, preferably the GT or GS models. They are dirt cheap on Ebay but come up rarely. If anyone has one or more to spare I'm willing to offer something reasonable for them, like $20 plus shipping. I want to use them for point to point connections between computers.

---

