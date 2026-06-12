---
title: "Canon PIXMA e500 not scanning or printing in greyscale"
date: 2012-02-04
forum: Hardware
---

### Post by nandan on 2012-02-04
Hello,
I use Ubuntu Lucid 10.04 LTS. I recently bought and installed a Canon PIXMA e500. After some difficulty in setting it up and installing it on my system,I have been able to get my desktop computer to send documents to the printer and get them printed. :)

However, the printer model is a copier, scanner and printer. It does not scan documents. XSane image manager says "no devices available". 

Also, it does not print in greyscale...so I cannot take fast, cheap and environmentally friendly printouts. :P

The printer works very well in WinXP after installing the device drivers.

Could somebody please help? 

Thanks!

---

### Post by jayshomebrew on 2012-02-04
It took me a while to find these for you. I looked at the europe site first, then aus, then finally ....

[http://support-ph.canon-asia.com/P/search?model=PIXMA+E500&menu=download&filter=0&tagname=g_os&g_os=Linux]("http://support-ph.canon-asia.com/P/search?model=PIXMA+E500&menu=download&filter=0&tagname=g_os&g_os=Linux")

---

### Post by nandan on 2012-02-04
> **jayshomebrew said:**
> It took me a while to find these for you. I looked at the europe site first, then aus, then finally ....

[http://support-ph.canon-asia.com/P/search?model=PIXMA+E500&menu=download&filter=0&tagname=g_os&g_os=Linux]("http://support-ph.canon-asia.com/P/search?model=PIXMA+E500&menu=download&filter=0&tagname=g_os&g_os=Linux")

Thanks a lot! I already downloaded and installed it...but apparently it has not helped.

The package is for Ubuntu 10.10 and I am on 10.04. Also, while I get the message that it is successfully installed, I do not see any reflection of it (e.g., in application>Printing, I see the printer, but that's about it. There is no way to change the settings)..Under Start>Graphics, I see CNGPIJMON-MX860, whose status is: Status Monitor for Canon Inkjet Printer driver under CUPS
But when I click on it, all I get is a window with the title "Canon USB" which has the message "Unknown Printer" inside it.

Is there any way in which something can be done so that scanning and greyscale printing can be made possible?



Thanks again...

---

### Post by jayshomebrew on 2012-02-07
I'm using 10.04LTS too, and my pixma is working fine.  Do you have these options under system/admin/printing/printer properties?
[IMG]http://img406.imageshack.us/img406/8937/tmpab87oa.png[/IMG]

The linux drivers from canon are generic linux drivers, not specific to ubuntu 10.04, or 10.10 or any other version.

---

### Post by nandan on 2012-02-07
Hello,
I can see these options, but I cannot print in greyscale.For example, if I go to 'color model', I only see RGB, not Greyscale.I do not see greyscale option anywhere... 

Also, how do I get it to scan?
Thanks again!

---

### Post by jayshomebrew on 2012-02-07
you can scan by running scan gear MP
/usr/bin/scangearmp

then it should allow you to scan.
it looks like this:
[IMG]http://img171.imageshack.us/img171/9904/tmpzujjoq.png[/IMG]



**GREYSCALE**
ohh, whoops greyscale, yeah, that was hidden for me too. I just did this:
1. system/printing, select printer, right click duplicate, then name it "greyscale pixma printer" or whatever you want.
2. right click "greyscale pixma printer", select properties.
3. select job options, scroll down, on the right, to Other Options.
add the option "CNGrayscale" without the quotes, click ADD
[IMG]http://img72.imageshack.us/img72/4586/tmp4t2r8i.png[/IMG]


4. type "TRUE" without quotes into the new box
[IMG]http://img52.imageshack.us/img52/6716/tmpqmmmhh.png[/IMG]


5. click apply.
this is what mine looked like finally:
[IMG]http://img850.imageshack.us/img850/2107/tmpig05.png[/IMG]

Now you should be able to print greyscale with this new printer.

---

### Post by nandan on 2012-02-11
Fantastic!
The grayscale thing is working perfectly...thanks a lot!
Was travelling for a few days, so couldn't reply.
Will try out scanning as well.

---

### Post by nandan on 2012-02-18
Hello,

The scanner is still not working! :(

The error message in scangear is "Cannot find available scanners. Cable may be disconnected or scanner may be turned off.Check the scanner status and then try again."

It works fine in Windows XP, by the way...so I can safely assume that connection, printer being off etc. are not issues.

Could you please help?

---

### Post by nandan on 2012-02-18
OK, I reinstalled and it works fine...thanks once again!

---

