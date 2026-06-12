---
title: "Can't print duplex with Brother HL-2270DW"
date: 2012-10-06
forum: Hardware
---

### Post by intercept on 2012-10-06
I'm trying to set up my new printer, Brother HL-2270DW, connected by USB. It's got duplex capability which works in Windows, but I can't duplex in ubuntu. 

When I print a document like this ```
lp -d Brother_HL-2270DW_series -o sides=two-sided-long-edge test.pdf 

``` the document prints one-sided.


I have the drivers installed. My output for ```
dpkg -l | grep Brother
``` is 


```
ii  cupswrapperhl2270dw:i386               2.0.4-2                                 Brother HL2270DW CUPS wrapper driver
ii  hl2270dwlpr:i386                       2.1.0-1                                 Brother HL-2270DW LPR driver
ii  printer-driver-ptouch                  1.3-3ubuntu0.1                          printer driver Brother P-touch label printers

```

Any help is greatly appreciated.

---

### Post by pdc on 2012-10-06
paste this into a spare browser window

[http://localhost:631/printers/](http://localhost:631/printers/)

..it is the CUPS interface for your computer ...........

left-click on your printer; work through the options

.......select......administration.........set default options....

......for my canon printer, with duplex options, that is where I set it

---

### Post by intercept on 2012-10-06
Thanks for your response. In the "set default options" pages, there aren't any apparent duplex options.

---

### Post by pdc on 2012-10-07
OK:

well open Printing from Administration

select your Brother;

right-click;

select Properties;

...... 4 down.......Printer Options....

.....can you set duplex there?

---

### Post by intercept on 2012-10-07
That was a great tip pdc! In the GUI I didn't see any duplex options, but I noticed that the printer "make and model" had the wrong printer. I had to change that to "Brother HL2270DW for CUPS" which I downloaded from Brother.

Duplex works great now! Thanks for all your help!

---

### Post by pdc on 2012-10-07
thanks: 

in your first post when you said

> cupswrapperhl2270dw:i386               2.0.4-2                                 Brother HL2270DW CUPS wrapper driver
ii  hl2270dwlpr:i386                       2.1.0-1 

.........I took it you had downloaded and installed what you needed...

when you say

> I noticed that the printer "make and model" had the wrong printer

..........which "wrong" printer was there please?

........we all get these problems; and linux is a great place for learning; .....there is an unlimited amount I have no idea about in linux!!

---

### Post by intercept on 2012-10-07
I don't know the name of the printer it had selected, but it wasn't one that I own.

---

