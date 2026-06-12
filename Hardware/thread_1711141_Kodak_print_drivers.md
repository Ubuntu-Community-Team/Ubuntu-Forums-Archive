---
title: "Kodak print drivers"
date: 2011-03-20
forum: Hardware
---

### Post by speedball1 on 2011-03-20
I am using Ubuntu 10.10 Does any one have print drivers for Kodak ESP 9250 ???
My system has no problem recognising and finding the printer and it looks for and finds quite a few possible drivers 40 to be exact but I am not sure what will work so far nothing has !

I know from looking at Kodak web and reading other posting that Kodak does not support Ubuntu .

Any Help would be greatly appreciated !!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by speedball1 on 2011-03-20
Drivers Found ! I hpoe this helps any one else with Kodak ESP 9250 Printer. I first down loaded             A cups filter and ppd file for the kodak ESP 5xxx all in one printer on linux. Likely to work on ESP 3250 ESP 5250 ESP 7 ESP 9
From the Following link:

[http://cupsdriverkodak.sourceforge.net/](http://cupsdriverkodak.sourceforge.net/)

Then: System/Amin/Printing/+Add/Network Printer/Find Network Printer @ this point it did find the kodak ESP 9250 which was hooked up to my wireless router .My computer then Automaticly  made a search for drivers and came up with a list of 40 drivers . I selected the recommended driver which was from some off the wall Manufacture with a 3 letter name ( sorry I don't remember the name). After that the computer then listed more drivers from the selected source I chose the ESP 5500 duplex driver as no ESP 9200 series was listed and It worked !

---

### Post by lunbuntu on 2011-04-03
I have re down loaded this driver and will try again but it did not work with my new Kodak ESP 5250 

yesterday . Ubuntu 10.01

---

### Post by lunbuntu on 2011-04-03
No although I down loaded and re installed the drivers it still does not function ?

          Please any other ideas or suggestions ?

---

### Post by lunbuntu on 2011-04-05
Please I still have not resolved this printer driver problem does anyone have any suggestions , thanks, ?:(

---

### Post by Wayne Thomas on 2011-06-05
I too am facing this dilemma.. Kodak from what I read seems to be trying to be a bit more Linux friendly but still no support for the ESP3250 AIO.


Has anyone came up with a solution to make this printer operate under Natty?
The scanner function would be nice but is not totally mandatory for me as I cam go to a different location to scan a document and would have to anyway considering this is a remote network printer.

I attempted to emulate it to the closest model with available data but I get an error on the machine hosting the printer and halts the print job.


Best Regards,

Wayne
[http://www.smythweather.net](http://www.smythweather.net)

---

### Post by Tootler on 2011-06-07
I just bought a Kodak ESP 310 AiO and found there was a problem with the drivers. The ones from source forge seem to be only partially functional so I took it back and exchanged it for an HP Photosmart so now I have a functional printer and Kodak have lost another sale. 

If enough people do that they might just get their fingers out and do something about providing Linux drivers. It can't be that hard to do as they support Mac and Mac OS is Unix based.

---

### Post by Wayne Thomas on 2011-06-07
Exchanging the printer is unfortunately not an option for me as I have had this one close to a year now..but I do have an HP AIO that works fine so if I can find driver support for that I'll just network it and make it my dedicated nix printer.

I agree with ya though,I wish they( manufacturers) would decide to get into more support for Linux.. I can't see it being an impossible task but the number of users is bound to be increasing every day...


Thanks for the info!


Best Regards,

Wayne Thomas
[http://www.smythweather.net](http://www.smythweather.net)

---

### Post by twowheeler on 2011-08-21
Thank you for the linkage -- the sourceforge driver works great with natty and my ESP 9250.

---

### Post by paulnewall on 2011-10-31
The driver for kodak ESP printers is now in ubuntu 11.10

---

### Post by paulnewall on 2012-01-14
There's now a scanner driver, better with WiFi than USB
here
[http://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/]("http://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/")

---

