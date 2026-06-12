---
title: "Fuji Xerox DocuPrint M205 fw  --  No driver under Linux?"
date: 2013-05-27
forum: Hardware
---

### Post by jiapei100 on 2013-05-27
Hi, all:


OS: Ubuntu 12.10

Recently, I purchased a new printer, a Fuji Xerox DocuPrint M205 fw. However, after a double-check on its official website:
[http://www.fujixeroxprinters.com.au/en/Downloads.aspx?product=10404&category=5726&os=32768&dl=1]("http://www.fujixeroxprinters.com.au/en/Downloads.aspx?product=10404&category=5726&os=32768&dl=1")

there seems to be no Linux driver for this particular printer.

> Drivers

Sorry there are no drivers available for this product or match your search criteria


I'm trying to add this printer with a supported driver, but the only thing I've got is: [IMG]http:/visionopen.com/questions/fx_m205fw.png[/IMG]

Can anybody please give me some suggestions on
1) either providing me a driver to replace m205fw ?
2) or providing me an open source driver that supports m205fw?


Thank you very much.



Best Regards
Pei

---

### Post by aikishugyo on 2013-05-28
I do not think there is any solution for a host-based based printer at this time.

---

### Post by Al-Man on 2013-10-01
I have a rpm package for the cm205fw that I got from one of the Asian   Fuji Zerox sites. I converted it to a debian package using Alien. I even  managed to install it. Unfortunately it crashes every time I try to  print anything. If you would like the rpm or deb package let me know and  I will try to find the link. I do not have the time or skill to pursue  this any further but if any one else does it would be great. Hoping someone out there has the required skill to work this out. Cheers Al-Man

---

### Post by dileepa1 on 2013-10-22
Hi Pei,

I also have the DocuPrint M205 FW and have tried different drives but have not been able to get it to print from Ubuntu. Have you been able to get this to work?

Thanks.

---

### Post by aikishugyo on 2013-10-25
Can someone try the foo2hbpl driver and give feedback on whether the printer may be supported:
[http://foo2hbpl.rkkda.com/](http://foo2hbpl.rkkda.com/)

---

### Post by Al-Man on 2014-09-15
Hi aikishugyo, I can confirm that the foo2hbpl driver from [http://foo2hbpl.rkkda.com/](http://foo2hbpl.rkkda.com/)  does indeed work. Just follow the supplied instructions. If you do use this driver please donate to Ralph Richardson at linuxtrade for his sterling work in making this printer work in Linux. Now I only need to find a way to get the scanner working. I can scan from the Fuji-Xerox interface to my network share on ubuntu but I can not get it to login to share folder, If anyone has any ideas I would love to here from you, Thanks. Al-Man.
[TABLE="align: center"]
[TR]
[TD="class: small"] 
[/TD]
[/TR]
[/TABLE]
[TABLE="align: center"]
[TR]
[TD="class: label"][/TD]
[TD][/TD]
[TD="class: small"][/TD]
[/TR]
[/TABLE]

---

