---
title: "USB broadband connection"
date: 2005-10-21
forum: Hardware &amp; Laptops
---

### Post by coolclassic on 2005-10-21
I am trying to install the eagle drivers for the sagem usb modem but I am having the following error when I try to connect the modem using eaglectrl -w or -d
-----
Sending options to device /proc/bus/usb/002/002
Unable to send options to driver: Unknown error 512
Failed to send options to device /proc/bus/usb/002/002
-----
I have installed this modem under hoary with success.

---

### Post by aceJacek on 2005-10-30
I got the same.

I did recompile module eagle-usb for my kernel (2.6.12-9-686), apparently it doesn't help.

Try follow this: [http://forum.ubuntu.pl/viewtopic.php?t=1494](http://forum.ubuntu.pl/viewtopic.php?t=1494)
It doesn't work for me either...

---

### Post by dumbbeatnix on 2006-03-17
Hello aceJacek

I have broadband at home.  Believe me it wasn't the most easiest thing to do at the time, but when finished it was so simple it wasn't funny.

Now I set my modem up using ethernet, so I dont know much about USB.  But it shouldn't matter, they are almost the same.

The reason for this post is to check for something that you might not know about, your modem settings.  This may sound silly, but you can access your modem by using Firefox.  For me it was just typing 10.0.0.138 into the url box, and up came all the defaults for the modem.  Thus allowing me to set them up.

Maybe you should look at the manual and see if there is any setup parameters that you need to fix this way.  Such information is usually in the FAQ pages of your manual, as most modem companies use WinBlow software for the installation of devices.

I hope this helps.  Enjoy your time with Linux, as it is the best as far as communication software goes.  And oh yes Ubuntu is the best linux that I have ever used, believe me I have tried a lot of flavours.

Cheers
Peter Greenfield
:-k

---

