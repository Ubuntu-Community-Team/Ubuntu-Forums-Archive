---
title: "BRFAX brother MFC fax  wrongly set to  lp0 via DRIVER INSTALL TOOL - quick to fix"
date: 2015-09-17
forum: Hardware
---

### Post by Li_Wu on 2015-09-17
on recent live distros such as mint 17.2 and others, users of brother MFC - xxxx 4 in 1 machines with fax will probably run into a problem:

The brother will not connect BRFAX via USB.

This is because brother's DRIVER INSTALL TOOL 


[TABLE]
[TR]
[TH]Title[/TH]
[TH]Description[/TH]
[TH]Release Date
(Version)[/TH]
[TH]Size[/TH]
[/TR]
[TR]
[TD]*[Driver Install Tool]("http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=mfc7440n_all&os=128&dlid=dlf006893_000&flang=4&type3=625")*[/TD]
[TD]The tool will install LPR, CUPSwrapper driver and scanner driver (for scanner models).
 
[...more]("http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7440n_all&os=128#more")[/TD]
[TD="class: text-center"][I]03/12/2014
(2.0.0-1)[/I][/TD]
[TD="class: text-center"][I]0.02
MB[/I][/TD]
[/TR]
[/TABLE]



[TABLE]
[TR]
[/TR]
[TR]
[TD="class: text-center"][/TD]
[/TR]
[/TABLE]

in combination with

[TABLE="class: normal-table"]
[TR]
[TH]Title[/TH]
[TH]Description[/TH]
[TH]Language[/TH]
[TH]Release Date
(Version)[/TH]
[TH]Size[/TH]
[/TR]
[TR]
[TD]*FAXmodem Driver (Ubuntu 11.04)*[/TD]
[TD] FAX modem driver for Ubuntu 11.04[/TD]
[TD="class: text-center"]*English*[/TD]
[TD="class: text-center"][I]06/29/2011
(1.1.3-1)[/I][/TD]
[TD="class: text-center"][I]0.03
MB[/I][/TD]
[/TR]
[/TABLE]





puts it on connection   usb:/dev/usb/lp0
while lp1 would be better.

correct setting is

 **usb://Brother/MFC-7440N?serial=000111111111**

(using your model & serial names). Then the fax can be talked to by the filters.


One cannot fax anything in this situation, you will never hear the audible dialling of the fax unit after printing to BRFAX via "OpenOffice Writer".


**):PThe fix is easy:**  ):P
In the printer setting GUI (from menu : system settings, printers)   RECONFIGURE the connection ! With a USB cable plugged in and MFC powered on, you will be offered an autodetected setting involving a "usb://Brother/MFC-   .....   serial=00000" string.  Click on OK and everything will be fine. :p

Or has anyone managed to get USB via  lp0 working (etc/printcap) ? seems unlikely to me.

The BRFAX install used to work properly before in earlier versions and it can be tricky to actually find a solution if you start looking in the wrong places, e.g. DEBUG=4 .

Also it sukks that efax used to work with a brother, but now the AT-commands by efax cannot properly give the right AT commands anymore and efax returns error with nothing actually faxed at all. A case of software rot. One must use debuglevel 4 on BRFAX and find out the proper AT commands but then efax is of little use anyway unless special features are added.

---

