---
title: "Problem with Ricoh Aficio SP 1100s and ratertosag-gd"
date: 2012-10-07
forum: Hardware
---

### Post by marchborch on 2012-10-07
Hello,
I have a Ricoh Aficio SP 1100s connected to the PC with USB cable.
I installed [ratertosag-gdi]("http://www.openprinting.org/printer/Ricoh/Ricoh-Aficio_SP_1100S") and the printer is recognized correctly by the system.
The problem is that not always the printing is successful. When I launch the print, the writing "Printing" appears on the display, but sometimes the sheet is printed in fact, sometimes appears on tthe display "Please wait" and then returns to "Ready" and nothing is printed.
I can not understand why. Can you give me a hand?
Thanks and greetings
Ubuntu 12.04.1 LTS

---

### Post by paalz on 2012-10-07
hello borch

rastertosag-gdi is located in /usr/lib/cups/filter/

it is a raster cups filter, so it works the following way: cups creates a b/w raster image from any print-output from any program using best available technology (ghostscript for example) and then passes it to the filter's stdin in a special (really very simple) format. i would imagine that cups also monitors the stderr and stdout of its filters, so if something goes wrong during rastertosag-gdi execution, i think cups will log it somewhere - try searching for the information where cups could log errors and filter console output. i would start searching with something like "cups filter log".

if you don't find the logs or logs are not useful - you can still try to debug it yourself: you can easily insert debugging to some file as rastertosag-gdi is fully written in python. as a first step i would suggest you add some output line at the very end of the code just to see if rastertosag-gdi is failing at some point, or it seems to finish execution. then, to do it more precise - add output lines after each block/in each function to detect the place of the failure as precise as possible. after that if you experience problems with deeper debugging feel free to continue this discussion, i'll try to help.

as far as "Ready" printer status is concerned - you should not rely on this. an online printer is always only in one of two states: ready and busy - this is not a real printer drive, so it does not provide any support for  printer status reporting - those statuses are from cups i think and in fact stand for the cups statuses - whether it is idle or busy with sending data over usb bus.

---

