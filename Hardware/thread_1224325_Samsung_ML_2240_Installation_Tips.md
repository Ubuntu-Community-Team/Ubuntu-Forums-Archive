---
title: "Samsung ML 2240 Installation Tips"
date: 2009-07-27
forum: Hardware
---

### Post by kaashif on 2009-07-27
Hey Everyone,

Had some problems setting up the Samsung ML 2240 but got it working so I thought I'd share how.

After connecting the printer first time, Ubuntu brought a driver installation wizard. Default selections were mostly good:

[IMG]http://img194.imageshack.us/img194/1010/driveroption.gif[/IMG]


No ML 2240 listed but the Samsung ML-2250 Foomatic/gdi [en] worked fine. The recommended option (first one) did not work.


[IMG]http://img194.imageshack.us/img194/4285/choosedriver.gif[/IMG]

I had to restart my printer (unplug, plug back in) to get the printer to work. Not sure if this is the case with every printer but if it is, it would be helpful to have mentioned it in the "choose driver" screen.

If the foomatic/gdi one doesn't work for you, try the others. Remember to restart the printer after selecting a new driver.

---

### Post by brookiemonsta on 2009-09-02
I confirm this works.

Output using kaashif's method on karmic (sorry it's too late now for me to try it on jaunty) is different to that using the Samsung supplied driver (which requires using the binary only rastertosamsungspl filter - see [http://www.openprinting.org/show_printer.cgi?recnum=Samsung-ML-2240](http://www.openprinting.org/show_printer.cgi?recnum=Samsung-ML-2240) for details). 

First, the downside. The test page using kaashif's method prints about 3.5 - 4 mm further up the page (A4) meaning you lose some detail right at the top of the print area.

Second, the upside. kaashif's method produces output with slightly lighter grayscale shades. This actually enables you to observe a difference between the 90% and 100% black boxes on the test page, whereas with the Samsung supplied driver there is no visible difference. 10% black is still visibly different to 0% black (ie. white).

I think I'll avoid the Samsung supplied driver and it's binary only filter from now on.

Thanks kaashif!

---

### Post by andresv on 2009-12-03
just to confirm your solution also works for me ... thank you !

---

### Post by NiCopy on 2010-06-14
Thank you for this. VERY helpfull! :)

I tried searching trough all the different drivers without any luck. Now my printer works like a charm..

Once again: THANK YOU

---

### Post by john.kreelman on 2010-08-27
Kaashif, thank you so much for this. I'm very new to Ubuntu, have tried it before & given up everytime as far too many complications for a novice. 
This time around I have all working nicely save for the ML2240 & the epson 4180 scanner.

This knocks the problem with the printer out the window, I can't thank you enough. Now just the scanner, cheers a million.

JK

---

### Post by lazyacre on 2010-09-26
Thanks saved me hours of messing around and my stopped my printer from learning to fly.....your solution worked a treat :D

---

### Post by sikilpaake on 2011-01-02
thanks a million, Kaashif!! :p

---

### Post by thoughto on 2011-09-12
kaashif, thanks a lot! Your post is still helping people! This is what makes Ubuntu work.

---

### Post by fabien29200 on 2011-11-19
Does someone try the ML-2240 with Ubuntu 11.10 ?

I have one and with the Official Samsung Unified Driver, when I try to print more than one page in LibreOffice Writer, I have an error page printed.

Do you have this problem ?

---

### Post by GeoMag on 2011-12-20
I can confirm this works on 11.10

Was a very usefull tip, easy to apply as well

I think the main problem as mentoined is that the reccomended driver doesn't work... So you just need to turn into the recommended from kaashif one

After installing a different driver you have to unplug and plug in again your printer.

Many thanks to Kaashif

---

