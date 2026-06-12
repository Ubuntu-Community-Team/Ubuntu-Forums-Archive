---
title: "Lexmark S405 Wifi - Printer Installed But Won't Print"
date: 2013-09-15
forum: Hardware
---

### Post by arkan01d on 2013-09-15
[COLOR=#333333][FONT=UbuntuRegular]I went to **Lexmark** and downloaded the 64bit driver for my **Ubuntu** **12.04** 64bit. I have followed 4 different guides so far. They all say pretty much the same thing. Add the printer, install the driver, and* it works!* For me, I add the printer, install the driver, and it says **Processing** for about 6 minutes then **Stopped**.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I've tried it the wizard way, that installs the drivers automatically, and the more hands on approach. There are 2 driver versions and I have tried them both. I the printer works if you print from other devices; so I know it's something to do with this one PC...[/FONT][/COLOR]

[COLOR=#333333][FONT=UbuntuRegular]I ran the troubleshooting wizard. I've attached the diagnostic log. TL;DR Printer came up in **Ready** Status and **Available to Print**, but nothing printed.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][Wizard's Diagnosis]("https://docs.google.com/file/d/0B5tKJWPQD_OQMUp6R3lwY2xjX00/edit?usp=sharing")
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I followed [this guide]("https://wiki.ubuntu.com/DebuggingPrintingProblems#Network_printer") under the **Network Printer** link. I'll attach a log of the output for that as well. The **/usr/lib/cups/backend/snmp 192.168.0.8** came up with nothing and both **avahi-browse** commands did not show the printer. If that helps...
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][Command Prompt Diagnosis]("https://docs.google.com/document/d/1KYztCP7-S75mkkYvbeejt_G_mH300jrk18154tNOyZM/edit?usp=sharing")

[B]_Update:_

[/B][/FONT][/COLOR][SIZE=2][FONT=arial narrow]My machine dual boots to **Windows**. I loaded **Windows** up, installed the drivers, and it prints just fine. The only thing that could be a potential problem is my color cartridges are empty. When I print from **Windows** it tells me this first and I select Print in ***Black & White***. I attempted printing a simple text file from **Ubuntu** and made sure to select to print in ***Black & White***, but it still will not print. Could this be the reason? If I buy new color cartridges and it still doesn't work I've blown half the money I could have used buying a printer that is sure to work with **Ubuntu**. Or if it's a system side issue I could buy the cartridges  then a new printer, and be out all that money. *Could anyone help me?*[/FONT][/SIZE]

---

### Post by arkan01d on 2013-09-19
Bump

---

### Post by arkan01d on 2013-09-25
-Bump - any help at all, even the least, is most appreciated. Right now I'm using Ubuntu for everything, then I have to boot to Windows just to print, it's a bit sad really.

---

### Post by kurt18947 on 2013-09-25
In view of the fact that Lexmark has discontinued inkjet printers and is closing the supplies factory in 2015 the last I read, I wouldn't spend too much money on your existing machine.
[http://www.pcworld.com/article/261564/lexmark_exits_the_inkjet_market_are_printers_doomed_.html](http://www.pcworld.com/article/261564/lexmark_exits_the_inkjet_market_are_printers_doomed_.html)

---

### Post by arkan01d on 2013-09-25
I did not know that. Thanks for the advice. I can boot to Windows for now. I'll be on the lookout for a decent printer/scanner combo w/ Linux support,

---

### Post by kurt18947 on 2013-09-26
IME, HP & Brother are pretty good bets.  I think HP is easier to set up, Brother has cheaper ink.  You can also get refillable cartridges for some Brother machines so you use bulk ink.  Other brands may be good as well but I have no experience with them.  I see Brother's MFC-J430 go on sale for $59 pretty often.  If I didn't print very often, at least 1 page every 10 - 14 days, I'd probably favor the HP 'print head as part of the cartridge' approach.  Ink Jet print heads can plug if they're not used periodically.  If the print head is part of the cartridge, just buy another cartridge.  If the print head is separate and it plugs to where cleaning cycles don't work, it's probably going to be cheaper to buy another printer.  Be aware that some HPs have a separate print head as well.  Head plugging is probably not an issue if you remember to run at least one page a week even if it's a test page.

---

### Post by arkan01d on 2013-09-26
Thank you for the good advice! I will keep that in mind :D

---

