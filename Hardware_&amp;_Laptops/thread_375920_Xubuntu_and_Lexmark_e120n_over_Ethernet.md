---
title: "Xubuntu and Lexmark e120n over Ethernet"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by frapzzt on 2007-03-04
Hi,
i've bought an Lexmark e120n and intergrated him with ethernet in our network but how can my laptop with xubuntu print there. it is an post script printer but i couldnt get it work
greetz
frapzzt

---

### Post by frapzzt on 2007-03-04
Ok now the Printer Runs but every Time i became a failure 
```
ERROR: configurationerror
OFfEndING COMMAND:

STACK:
```
What can i do

---

### Post by spd106 on 2007-05-06
I'm not sure what steps you took before getting that error message, but the open printing database has a page on this printer [http://openprinting.org/show_printer.cgi?recnum=Lexmark-E120n](http://openprinting.org/show_printer.cgi?recnum=Lexmark-E120n)

On Edgy I use the HP LaserJet Series PCL 4/5 driver.

On Feisty this printer is autodetected, but I it uses the wrong driver. You are better off searching for another model that uses the pxlmono driver as specified in the link above. That's what got it working for me.

---

### Post by sorgud on 2008-02-23
Thanks,
I have just bought  Lexmark E120n.
My Kubuntu Feisty autodetected, but as you said, It uses a wrong driver.
After googling, I found your posting. I followed the installation instructions in your link, downloading the .ppd. 
Everything works fine, now.
I have only change the 80 port in the instructions for the 631 (cups typical?) port.

thanks a lot

talueguito
raul

---

