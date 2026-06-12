---
title: "Ubuntu 14.04 64 bit Lexmark S605 printer set up"
date: 2014-10-18
forum: Hardware
---

### Post by jaaylwar on 2014-10-18
Just in case anyone else is having difficulty printing from a Lexmark S605 with Ubuntu 14.04 64 bit,
this is what I've done and now have my printer printing.

Firstly I went to 
[http://support.lexmark.com/index?page=driverSupport&locale=EN&userlocale=EN_US](http://support.lexmark.com/index?page=driverSupport&locale=EN&userlocale=EN_US)
and downloaded the 64 bit printer utility and the 64 bit ppd file.
The latest declared version of Ubuntu on the lexmark site was 12, but this still worked.

On download I selected open with Ubuntu software centre.
This installed things here: /usr/local/lexmark/

I then had to change permissions
sudo chmod 755  * 
to all ppds and printerfilter in these directories
/usr/local/lexmark/v3/bin/printfilter
/usr/local/lexmark/v3/etc

I then edited the printer in CUPS
[http://localhost:631/printers/](http://localhost:631/printers/)

I manually set the Connection: to	lxhcp://192.168.x.x (my printer's ip address)
You can do this by selecting Other network printers (Administration->Modify Printer)

And now it's printing.

I hope that's useful to someone.

Jamie Aylward

---

### Post by Waklevören on 2015-02-18
Whoa, that's SO close to making me happy. However, I think I'm doing something wrong or miss out on something important somewhere between "sudo chmod 755 *" in the dirs you mentioned and editing the printer in CUPS. CUPS doesn't find my printer no matter how I try to find it. 

I did

$ sudo chmod 755 /usr/local/lexmark/v3/bin/printfilter 
$ sudo chmod 755 /usr/local/lexmark/v3/etc/*
$ sudo chmod 755 /usr/local/lexmark/v3/bin/*

and went to localhost:631/printers

And there's nothing there.

Where am I going wrong?


-Carl

---

### Post by Waklevören on 2015-02-18
O HAI!

I just noticed I had forgotten to do the actual setup of the printer (attach usb cable and stuff), so as soon as that was done I was back on track! I'm now printing happily over WiFi. Oh, and **I didn't need to modify anything in CUPS.**

Thank you SO much for your initial post, FINALLY I can use my lexmark printer on my own computer again.. I've had to borrow the missus' 12.04 LTS-running laptop when I needed to print for the last two years. Then again, I've almost never needed to print anything, but it nice to know that it's working :D

---

