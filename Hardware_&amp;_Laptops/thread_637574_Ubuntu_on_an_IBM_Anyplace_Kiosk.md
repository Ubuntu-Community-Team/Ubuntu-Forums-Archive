---
title: "Ubuntu on an IBM Anyplace Kiosk"
date: 2007-12-11
forum: Hardware &amp; Laptops
---

### Post by Mrwasab1 on 2007-12-11
Hi guys,
I have recently been given an IBM Anyplace Kiosk and thought it would be a good idea to get rid of windows and install Ubuntu on it.

Now, these devices have a built in barcode scanner and are mainly used for price checking at retail stores.

Essentially what i want to do is the same that windows could do, but without having to pay for millions of licences to use windows embeded...

i have Ubuntu installed, i got the touchscreen working, the only problem is i cant get the barcode scanner to work.
It is on, and when a barcode is placed over the laser, it beeps. apart from that it does nothing. I have searched all over for a solution and cant seem to find one.

Eventually i will set up a small database and when a barcode is scanned, it will search that barcode in a database and spit out a price...

But for now i want to get this scanner working. 

Does anyone have any ideas or any direction as to where i can start?

---

### Post by Mrwasab1 on 2007-12-13
sureley someone must know something about getting a barcode scanner to read a barcode and output it as if it were typed by a keyboard...
ive heard of a keyboard wedge but i havent seen much about them on linux. any direction would be welcome

---

### Post by joecrappa on 2007-12-27
I am also looking for input on this problem. I tried modprobe usbkbd to no avail. 

Someone please chime in!

---

### Post by joecrappa on 2007-12-27
OK...lol...I just figured it out.

Here are the things that I did: 

-modprobe usbkbd
-input another input device in my xorg.conf as usbkbd with dev name as barcodescanner0

None of which worked. 

So...I reprogrammed the scanner leaving out some of the options they give you. And low and behold, it worked. 

So, if you're using a generic barcode scanner and can't get it to output as a keyboard, the problem may not be with Ubuntu or your drivers or settings, but a problem with the scanner's programming.

Play around with the settings and hopefully you'll get lucky like myself!

---

### Post by ecoolman on 2008-04-26
Hello there, do you recall what you needed to do to get the touchscreen working on the anyplace kiosk?

---

