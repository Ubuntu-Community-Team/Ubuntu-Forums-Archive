---
title: "Printer recommendation"
date: 2011-09-29
forum: Hardware
---

### Post by mijdrawoh on 2011-09-29
To avoid the seemingly constant problems in using my HP1020 printer, I am planning to replace it with one that doesn't have all the CUPS and HPLIP issues. I would appreciate the identification of light-duty, home printers that work flawlessly with Ubuntu. Thanks in advance.

---

### Post by MartyBuntu on 2011-09-29
> **mijdrawoh said:**
> ... all the CUPS and HPLIP issues.

What CUPS and HPLIP issues? HP printers are well supported.

FWIW, my Samsung printer works great with the Unified drivers in 10.04 LTS.

---

### Post by BlinkinCat on 2011-09-29
I have had no problems with my HP 2120 - I have had it for a few years now,

Cheap too, but they really get you for the cost of the cartridges - ugh

---

### Post by collisionystm on 2011-09-29
> **mijdrawoh said:**
> To avoid the seemingly constant problems in using my HP1020 printer, I am planning to replace it with one that doesn't have all the CUPS and HPLIP issues. I would appreciate the identification of light-duty, home printers that work flawlessly with Ubuntu. Thanks in advance.

What problems are you having? I have always stood behind HP printers with Ubuntu. The HPLIP utility is the best I have seen so far.

Did you install the actual HPLIP toolbox or are you just using what came with Ubuntu?

---

### Post by mijdrawoh on 2011-09-29
My problems with the 1020 happened after, I believe, an update of CUPS; I couldn't get it to print. In trying to restore functionality, I apparently deleted the required plug-in. Then I found, when I tried to download a replacement, that the plug-in file was corrupted.  I got a plug-in that a Ubuntu user made available on the net, installed it and got the 1020 working. A day later when I tried to print, it again was not functional.  Doing a search showed that 1020 users in almost all distros had continuing problems with that printer. I'm trying to find a printer that just works.

---

### Post by RH9R on 2012-04-20
FWIW, I've given up on Ubuntu w/ HP1020 and would like to know about one that plugs in and prints also. This isn't the first round of difficulty w/ HP. Lucid/HPLIP can probably be made to work but too many hours of heartburn have gone buy to stay w/ HP.
The one user mentioned a Samsung model. Are there others?

---

### Post by kurt18947 on 2012-04-20
I've had pretty good luck with Brother.  An older no longer available one - MFC-7820N - installs itself, at least the print function.  Brother's install instructions are not the best; they seem to be based on 8.04 or thereabouts and Ubuntu has changed since then, mostly for the better.  But I've had decent luck with a few models.  Be sure to read the "pre-installation" section and install both the lpd & CUPS drivers, lpd first.

You might take a look at the printer database here:
[http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/databaseintro](http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/databaseintro)
I don't know how current it is.  I too thought HP was about the best when it came to "just working" in Linux but I guess not with the 1000 series.

---

### Post by mastablasta on 2012-04-21
what are you looking for? what kind of printer? laser, inkjet? b&W, color? scanner, no scanner? fax? net printer or plug into computer printer? wireless (wi-fi) printer?

HP's are the most supported ones since HP works on linux support. 1020 should work flawlesly. i am not sure what you were doing...

Samsung have drivers, but their own are rubish. a community made patch makes some of them run flawlesly.

some people use Brother.

cannon is a no-no.

---

### Post by rewyllys on 2012-04-21
> **mastablasta said:**
> . . . . cannon is a no-no.
I have to disagree, at least with respect to an older Canon S900 that I used to use, and with respect to the newer Canon Pixma MG5220 that I now use.  

All I had to do was download and install the pertinent Linux drivers from Canon's Asian Website:

[http://support-asia.canon-asia.com/?personal]("http://support-asia.canon-asia.com/?personal")

---

### Post by RH9R on 2012-07-11
It appears the solution is to deny the issue. Disappointing.

---

### Post by Mikeb85 on 2012-07-12
I have an HP F4480 (printer/scanner), it works flawlessly with both Ubuntu 12.04 and openSUSE 12.1.  Unfortunately I don't have any experience with non-HP printers to give any other recommendation.

---

### Post by efflandt on 2012-07-12
Your best bet might be a network printer.  I have never used a USB printer, just parallel ports in the printcap days before cups, and network printers.  Once you point Ubuntu at the IP address of the printer it usually automatically finds a driver.

While you probably want to stay away from Lexmark ink jet printers, their laser printers are fairly standard.  Even an inexpensive do everything X204n I got at work to temporarily substitute for a dead HP printer at work does HP PCL and postscript, and was only $150 at the time.

Although, I have not actually tried printing on the X204n from Linux (or scanning), I have a Lexmark C543dn color laser at home (which also does HP PCL and postscript), and it works great with Ubuntu, including duplexing.  Before Ubuntu had a driver for it, it worked with an older C534 driver.  So with a network printer you just need any driver that speaks the same printer control language.

---

