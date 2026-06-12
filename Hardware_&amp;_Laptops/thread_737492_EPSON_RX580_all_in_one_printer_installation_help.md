---
title: "EPSON RX580 all in one printer installation help"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by Brigitte Seib on 2008-03-27
I checked and  found no answers. Did anybody get it to work?
Please let me know
Thank you 
Brigitte

It is in this list:

[http://openprinting.org/test/show_driver.cgi?driver=test-3](http://openprinting.org/test/show_driver.cgi?driver=test-3)

and is listed in there as supported here:
[http://www.linux-foundation.org/en/OpenPrinting/Database/SuggestedPrinters#Which_to_buy.3F](http://www.linux-foundation.org/en/OpenPrinting/Database/SuggestedPrinters#Which_to_buy.3F)

see multifunction devices 
it says there you just need to install the parts as separate USB devices (scanner, printer) 

So I tried this however, I do not find EPSON RX580 in my printer list:
I am on Feisty 7.04 and I used Systerm -> Printing: New Printer

The printer was turned on and connected on a local usb port
and something was connected to it.

I found some EPSON Stylus Photo RX printers  [COLOR="Red"]however not RX580[/COLOR] (from RX400 to RX700) in my list.
I configured it as RX600 and tried to print a test page .. it run through empty pages <deep sigh)


 Please help!!  Thanks If I cannot get it to work I need to return it soon.

Do I need a different version of Gutenprint? It uses High Quality Image (Gutenprint CUPS) version 5.0.0.99.1

---

### Post by linuxwizard on 2008-03-27
You can get driver > Stylus Photo RX560/RX580/RX590 >  here > [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do) >  should be a howto install there also

---

### Post by Brigitte Seib on 2008-03-28
> **linuxwizard said:**
> You can get driver > Stylus Photo RX560/RX580/RX590 >  here > [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do) >  should be a howto install there also
Thank you for your answer.

I found this link also and an unanswered question from a user. This package includes compiled code which did not get integrated  into her 64 bit processor code. I could have the same problem .. I have a AMD64 Dual processor and I am using the 686 code.

uname -a
Linux piano 2.6.20-16-generic #2 SMP Tue Feb 12 05:41:34 UTC 2008 i686 GNU/Linux


The RX580 is listed in the Gutenprint list .. however this Gutenprint is not built for Ubuntu yet.
I am on Feisty 7.04 do you know which Version of Gutenprint is included with version 7.10?

What do you suggest?
let me know
Thank you again
Brigitte

---

### Post by linuxwizard on 2008-03-29
You didn't state in your first post you are using 64bit system. Can't help you there.
Is this what you are looking for >
[http://packages.ubuntu.com/search?keywords=Gutenprint&searchon=names&suite=gutsy&section=all](http://packages.ubuntu.com/search?keywords=Gutenprint&searchon=names&suite=gutsy&section=all)

---

### Post by Brigitte Seib on 2008-03-30
I realized that I am not running my AMD64 in 64 bit mode ..

So I followed your initial suggestion and installed pipslite 

I found this thread
[http://ubuntuforums.org/showthread.php?t=377092](http://ubuntuforums.org/showthread.php?t=377092)
to help me 
and this website to convert the down loaded  rpm
[http://stefan.samaflost.de/blog/en/personal/infra](http://stefan.samaflost.de/blog/en/personal/infra)

I had to install alien  then it converted  rpm converted it into debian etc ..

Thank you again for your help
Brigitte

P.S.: Any suggestions how I can get the scanner part to work in Ubuntu?

---

