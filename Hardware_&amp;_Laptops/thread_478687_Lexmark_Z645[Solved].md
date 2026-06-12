---
title: "Lexmark Z645[Solved]"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by AlexMono94 on 2007-06-19
I need some help. I'm quite new to Linux and I cannot get my Lexmark Z645 printer to work. Is there any way I can!? :(

---

### Post by hummingbird59 on 2007-06-19
It will probably be difficult.  See [http://openprinting.org/show_printer.cgi?recnum=Lexmark-z645](http://openprinting.org/show_printer.cgi?recnum=Lexmark-z645).  But, just try different drivers - you might get lucky!

---

### Post by Epperly on 2007-10-02
Ever get it Alex?

---

### Post by AlexMono94 on 2007-10-20
Actually I did! :)

I just followed a tutorial here for Z600 printers but it works fine with a Z645.
[http://finebushpeople.net/LexmarkZ600](http://finebushpeople.net/LexmarkZ600)

---

### Post by Parsec on 2007-10-25
Thank you all. I'm a super-newbie  and i was almost giving up Ubuntu because i could not get this printer to work.

I  followed AlexMono94 link and it did not work... but i came across with a useful info in other forum ( [http://forums.linux-foundation.org/read.php?29,419](http://forums.linux-foundation.org/read.php?29,419) - thanks to Dan): 
> The lexmark Z640 uses the z600 driver found on this site but you have to install libstdc++-33 to get it to print, with out the lib it will just hold everything in queue.

The solution is:  follow the tutorial provided by  AlexMono94 (many thanks) and make sure you have libstdc++-33 installed.


My thanks to all!

---

### Post by Galls on 2008-01-11
Hi, super newbie here.  Running 7.10 on a 32 bit system.

Where do I download the cups file to for this sequence to work?  As in what directory.  I downloaded the file to the desktop but no dice.

Is it possible for someone to really dumb this down this process down for me?  I know I am asking a lot but I am in a time sensitive and tough situation right now where I cannot physically go out and buy a new printer.

---

