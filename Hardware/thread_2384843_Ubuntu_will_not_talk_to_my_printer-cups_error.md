---
title: "Ubuntu will not talk to my printer-cups error"
date: 2018-02-12
forum: Hardware
---

### Post by rapidrob on 2018-02-12
My new Brother 3180CDW color laser-jet printer is seen by unbuntu but  If I plug the printer into my laptop the software never sees it,but sees thumb drives and my cell phone just fine. I get a constant CUPS error if I try to print to it. I am new to Ubentu and know little about its software and commands.
[ATTACH=CONFIG]278509[/ATTACH]
[ATTACH=CONFIG]278510[/ATTACH]

---

### Post by kc1di on 2018-02-13
I would try reinstalling the printer with it plugged in.
download the driver install tool from brother from [here.]("http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hl3180cdw_us_as&os=128")

---

### Post by rapidrob on 2018-02-13
It did not work. The software never reacted to the usb being plugged in. Reloading the software did not help,

---

### Post by kc1di on 2018-02-14
go to[ this page]("https://sites.google.com/site/easylinuxtipsproject/15") and follow the  instructions for installing brother printers.  It is written for mint but should work with Ubuntu also.

---

### Post by pdc on 2018-02-14
so Rob; sorry to hear of these troubles; if this is a usb connection, if you plug the Brother in to your laptop; (which is where all the issues are?) ...... and you open a terminal and type ```
lsusb
```       .... that is asking the computer to LIST what usb devices are connected: does the Brother get listed

________________--

when you said> The software never reacted to the usb being plugged in. ...... which software did you mean please?

________________

In Ubuntu 17.04, airprint compatibility was introduced; as I understand it, if a printer is on this list [https://support.apple.com/en-nz/HT201311](https://support.apple.com/en-nz/HT201311) then Ubuntu should recognise it; and auto-configure it; so one does not need the Brother drivers installed; 

this HL-3180CDW is airprint compatible

many folks are on 16.04 Ubuntu; as a long-term support version; the next one is due mid-April so it will be 18.04 so it should have continued airprint support from 17.04 .............

---

### Post by rapidrob on 2018-02-15
OK, I removed the software (drivers) and reloaded. I hooked up the USB and it appears the laptop "see" the printer. I then downloaded new software and opened it. It looked to be loaded but I get a constant error every time about cups and other errors. I'm not sure why this happens.
Plugging in the printers USB cable the laptop does NOT respond. If I open up "system settings" the printer is shown and is set to primary.
Here are several screenshots as to what is being displayed.I did NOT include all the licenses  baloney.

---

### Post by rapidrob on 2018-02-15
Cont: More screen shots.[ATTACH=CONFIG]278545[/ATTACH][ATTACH=CONFIG]278546[/ATTACH][ATTACH=CONFIG]278547[/ATTACH][ATTACH=CONFIG]278548[/ATTACH]

---

### Post by rapidrob on 2018-02-15
Still more screen shots:[ATTACH=CONFIG]278549[/ATTACH][ATTACH=CONFIG]278550[/ATTACH][ATTACH=CONFIG]278551[/ATTACH]

---

### Post by rapidrob on 2018-02-15
Another unrelated problem is I plugged in external speakers in the head-phone jack. The sound is very loud and badly distorted. There does not seem to be a volume control for the head phones. The on-board speakers work normally.

---

### Post by kurt18947 on 2018-02-17
Pardon me if I missed it but what version of Ubuntu are you using? 16.04, 17.10 or something else? The reason I ask is that I run both versions in a dual boot configuration. 16.04 works perfectly both print and scan, 17.10 works okay for printing but not for scanning. If you're using 17.10, it might be worth installing 16.04 instead or in addition. Rightly or wrongly I regard the non-LTS versions as beta software where Canonical can introduce new stuff and test it before incorporating it into LTS releases. I'm running 17.10 on my main machine but rock solid 16.04 is there is needed.  I would not be surprised if hardware vendors develop and test their machines on LTS releases. I don't know but suspect that to be the case; chasing new versions every 6 months might be a bit much for manufacturers.

---

### Post by rapidrob on 2018-02-17
16.04

---

### Post by rapidrob on 2018-02-20
I was able to get the sound to work normally.
I still could use help on the problem not communicating with the laser printer.

---

### Post by pdc on 2018-02-21
what does ```
lpinfo -v
``` give from a terminal please?

also: if you open the PRINTERS folder; hit the F1 key ..... that opens a trouble-shooting wizard ............. I wonder if running that gives any clues ............

______________-

[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) Ubuntu offer a wiki: if you feel up to it, if you activate the log that records issues; if you do that, if you post some back here; it would also be of use if you report the issue as a bug to Ubuntu

---

### Post by rapidrob on 2018-02-21
Here is a screenshot.[ATTACH=CONFIG]278618[/ATTACH]

---

### Post by rapidrob on 2018-02-21
The program asked to open a command,and I do it. It ask for my password which I enter BUT it says it is wrong? I use it all the time.
[ATTACH=CONFIG]278619[/ATTACH][ATTACH=CONFIG]278620[/ATTACH]

---

### Post by kc1di on 2018-02-21
change su -C in that command to sudo
 su is not used in ubuntu.

---

### Post by pdc on 2018-02-21
that is a strange message about cups .......... I can't remember if you have done the "delete cups ........... install cups " routine .......... sadly these types often seem solved when the poor soul posting the problems just gets fed up and does a clean install; and surprisingly everything now works like it should .. I would need to google on these types of error messages to try and guide you through some possible fix ....... sumfin is broken ...........

---

### Post by kc1di on 2018-02-22
what does the command ```
lpstat -v
``` produce?

---

### Post by rapidrob on 2018-02-22
see post 14 results

---

