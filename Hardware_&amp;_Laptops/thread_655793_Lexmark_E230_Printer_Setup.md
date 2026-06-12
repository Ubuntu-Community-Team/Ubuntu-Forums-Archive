---
title: "Lexmark E230 Printer Setup"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by c0met on 2008-01-01
I had some problems getting my Lexmark E230 laser printer to work in Ubuntu. I'm putting my solution to the problem here in the forums in case it might help someone else.

My solution is a combination of different peoples ideas and I'd like thank all those who posted guidelines here in various forums that helped me solve the issue.
[LIST]
[*]Lexmark do not make an E230 driver for Linux :(
[*]As long as "SmartSwitch" is enabled on the printer, it will emulate an HP LaserJet using the "pxlmono" driver. Fortunately, SmartSwitch seems to be the default setting of the printer as it wasn't necessary for me to switch this on :)
[*]In Ubuntu 7.10, I found "pxlmono" by installing my printer as given below.
[/LIST]

[LIST=1]
[*]go to **[COLOR="DarkRed"]System>Administration>Printing[/COLOR]**
[*]enter your password if prompted. In each of the steps below, click on **[COLOR="DarkRed"]foward[/COLOR]** when prompted.
[*]click on **[COLOR="DarkRed"]New Printer[/COLOR]**
[*]choose printer port - for me is was LPT 1
[*]choose [COLOR="DarkRed"]**HP**[/COLOR] from the makes
[*]scroll down to[COLOR="DarkRed"]** LaserJet 2100**[/COLOR] (you'll see that **[COLOR="DarkRed"]pxlmono[/COLOR]** is an option on the [COLOR="DarkRed"]**right-side list**[/COLOR])
[*]install from there
[/LIST]

P.S. It might also be worthwhile looking at the OpenPrinting Database at
[INDENT][[COLOR="Purple"]**http://openprinting.org/printer_list.cgi**[/COLOR]]("http://openprinting.org/printer_list.cgi")[/INDENT]

---

### Post by Shockwav on 2008-04-26
I can confirm that this works. 

Thanks to the info - you made my day!

\\:D/

---

