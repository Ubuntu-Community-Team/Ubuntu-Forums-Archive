---
title: "[Fujitsu Siemens Li2727] - Wifi Activation"
date: 2010-07-09
forum: Hardware
---

### Post by jagie_259 on 2010-07-09
Hello,

Can anyone possible to a step by step guide for me to turn on the wifi in ubuntu. I have the the latest ubuntu installed via wubi.

I just want to know how to activate it and get it working. I have no idea how to.

If someone possibly knows, could they at all just write a quick step by step guide for me. I would appreciate it.

Thanks

---

### Post by psavva on 2010-07-09
> **jagie_259 said:**
> Hello,

Can anyone possible to a step by step guide for me to turn on the wifi in ubuntu. I have the the latest ubuntu installed via wubi.

I just want to know how to activate it and get it working. I have no idea how to.

If someone possibly knows, could they at all just write a quick step by step guide for me. I would appreciate it.

Thanks

See This Article
[http://swiss.ubuntuforums.org/showthread.php?t=986288](http://swiss.ubuntuforums.org/showthread.php?t=986288)

---

### Post by jagie_259 on 2010-07-09
Got it working.

If anyone has a fujitsu siemens li2727 laptop do the following:

Go to

[]("http://support.ts.fujitsu.com/com/support/linkapplication.html?LNG=EN&ProductID=25387")[http://support.ts.fujitsu.com/com/support/linkapplication.html?LNG=EN&ProductID=25387](http://support.ts.fujitsu.com/com/support/linkapplication.html?LNG=EN&ProductID=25387)

untick the box marked 'Show only  supported operating systems' 

this will open up a disclaimer  click on the 'Close Information' arrow

(you may need to wait for  options to appear)

click on the + sign next to 'Other Operating  System' 

(you may need to wait for options to appear)

then  select the 'Embedded Operating System' radial button 

(you need  to wait for options to appear) 

then click the + symbol next to  'Flash Bios' 

The latest one is at the top 'current BIOS V. 1.10:  Solved problems: - WLAN RF will be automatically turned off after  rebooting.  

There are options for applying the update: 

You  can make a floppy disk (not sure how you use it without a floppy disk  drive, unless you have a usb one of course), 

or a bootable cd  image which you can burn then boot your pc with, 

or use the  windows flash utility install and run it on your pc. 

I used the  windows flash utility as it is a 32 bit windows application that runs  just fine on Vista so is therefore the easiest way IMHO. 

This is  a pretty straight forward activity if you are competent pc user. 

Just  follow the instructions for the BIOS flash in the file readme.txt  

Make  sure the AC power is plugged in as if you run out of power or if you  mess it up or stop it halfway through you may render your machine  inoperable.

-------------

I got this off the fujitsu siemens forums. It updates the BIOS so that it automatically activates your wifi. It works perfectly. If your on windows 7 it works too. I downloaded he flash utility one from the website, and ran it. Within a minute, the bios had updated and works fine. No codes to put into ubuntu.

Hope this helps everyone.

---

