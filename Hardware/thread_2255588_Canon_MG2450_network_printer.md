---
title: "Canon MG2450 network printer"
date: 2014-12-06
forum: Hardware
---

### Post by a4r on 2014-12-06
I installed LUBUNTU 14.10 64 bit on my laptop and 32 bit on another. My family printer is USB Canon MG2450. It is connected to my router  via Networking Server box that communicates betweem Ethernet to USB. In Win7 environment all computer connected to my network and have Networking software installed, may take control over this printer/scanner (one each time). It works flawless.
In Lubuntu - it doesn't at all. I have installed drivers provided with packages, then drivers dowlowded from Canon's Asia site (.deb), but the best I can get is the first "movement" of the printer when a job is sent to it. It starts forwarding a page, then stops, and after maybe half an hour, the page get out with a partial frame printed on it, but never with the content it should have on it. I'm quite desperate since I have tried almost all suggestions found on the Net for this problem: different ways of installation (command line, authomatic), different drivers, including 32 or 64 bit, different versions of it, whatever.. THe best I got is what is described above.

Can anyone say if this is a bug, or I make something wrong from the beginning? I start looking for other Linux distributions, or just to give the Linux up and to uninstall: I can't go to Windowseach time I need to print a page...
Thanks !

---

### Post by Enigma12 on 2014-12-06
Since no one else has answered this yet, I will offer my still-a-newbie advice. First, I would back up any data you want to save, including the downloaded drivers you have. Second, since 14.10 is still new and others have reported various bugs, I would install Lubuntu 14.04 LTS, then upgrade it to 14.04.1 and see if you can get that to work. If someone gives you better advice, go with that instead.

---

### Post by mörgæs on 2014-12-06
I would stay with 14.10. 
First, are you able to print if you connect directly (not through network)?

---

### Post by QIII on 2014-12-06
Reinstallation is not a solution, but a desperate act of last resort.  This should never be a first recommendation, so please be careful of that.

This post is only ten hours old.  It is far to early to assume it will not be answered.  Also, a non-solution answer has removed it from the population of threads found by the "unanswered posts" query that many here use to find threads such as this to help with.

---

### Post by pdc on 2014-12-07
so if we check some things on the Lubuntu install please

___________________________________________

can you in turn copy the commands; so for each command, open a terminal; and paste the command into a terminal; and then copy the result; and paste it back here please

```
dpkg -l | grep cnijfilter
```

```
/usr/sbin/lpinfo -v
```

______________________

and then if click on this link [http://localhost:631/printers/](http://localhost:631/printers/) and look in the right-hand column; that should be headed **Make and Model** and tell us what it says for your Canon printer please

---

### Post by a4r on 2014-12-07
Not yet tried... I will and report.

---

### Post by a4r on 2014-12-07
> **pdc said:**
> so if we check some things on the Lubuntu install please

___________________________________________

can you in turn copy the commands; so for each command, open a terminal; and paste the command into a terminal; and then copy the result; and paste it back here please

```
dpkg -l | grep cnijfilter
```

```
/usr/sbin/lpinfo -v
```

______________________

and then if click on this link [http://localhost:631/printers/](http://localhost:631/printers/) and look in the right-hand column; that should be headed **Make and Model** and tell us what it says for your Canon printer please

OK I get this in terminal:
j@j-ASUS:~$ dpkg -l | grep cnjfilter
j@j-ASUS:~$ /usr/sbin/lpinfo -v
network socket
network ipp14
network ipp
network lpd
network http
network ipps
network https
network dnssd://Canon%20MG2400%20series-803f39._printer._tcp.local/

and in the [http://localhost:631/printers/](http://localhost:631/printers/) I've got:
[TABLE="class: list"]
[TR]
[TH][&#9660; Queue Name &#9660;]("http://localhost:631/printers/?QUERY=&WHICH_JOBS=&FIRST=%7BFIRST%7D&ORDER=dec")[/TH]
[TH]Description[/TH]
[TH]Location[/TH]
[TH]Make and Model[/TH]
[TH]Status[/TH]
[/TR]
[TR]
[TD][Canon-MG2400-series]("http://localhost:631/printers/Canon-MG2400-series")[/TD]
[TD]Canon MG2400 series[/TD]
[TD][/TD]
[TD]Canon MG2400 series - CUPS+Gutenprint v5.2.10[/TD]
[TD]Idle[/TD]
[/TR]
[/TABLE]

That's I saw before, but the printer is just frozen... When I print a test page it shows Printer Connected for 2-3 minutes, then it is Spooling Job with 0% of done forever...

---

### Post by a4r on 2014-12-07
> **mörgæs said:**
> I would stay with 14.10. 
First, are you able to print if you connect directly (not through network)?

I did. Connected directly via USB it prints just OK without any problem.

---

### Post by weatherman2 on 2014-12-07
I would go back to a Windows machine that can print to it over the network, right-click on the printer, do "Printer Properties," and click on the "Ports" tab.  See how the port is defined in Windows.  Then try to replicate that in Ubuntu.

I had a USB printer attached to my router, and I could print to it over the network using this Device URI in Ubuntu:

```
socket://192.168.1.1:9100
```

where 192.168.1.1 is the address of my router.  Of course, your router may have a different scheme of sharing the printer than mine does.  But Ubuntu could not automatically detect the printer otherwise.

---

### Post by a4r on 2014-12-08
> **weatherman2 said:**
> I would go back to a Windows machine that can print to it over the network, right-click on the printer, do "Printer Properties," and click on the "Ports" tab.  See how the port is defined in Windows.  Then try to replicate that in Ubuntu.

I had a USB printer attached to my router, and I could print to it over the network using this Device URI in Ubuntu:

```
socket://192.168.1.1:9100
```

where 192.168.1.1 is the address of my router.  Of course, your router may have a different scheme of sharing the printer than mine does.  But Ubuntu could not automatically detect the printer otherwise.

How do I replicate it in Ubuntu?  Where should I put it in?  Please give me some details,  I am not familiar with Ubuntu or Linux.

---

### Post by weatherman2 on 2014-12-09
I'm using Ubuntu 12.04.2 with Gnome Fallback.  When I go to the "Gear" in the top right corner and choose "Printers" from the menu, I find my printer, right-click the icon and choose "Properties" and then I can change Device URI.  That's where you could put "socket://192.168.1.1:9100" in for the printer you've already installed.

---

### Post by a4r on 2014-12-12
> **weatherman2 said:**
> I'm using Ubuntu 12.04.2 with Gnome Fallback.  When I go to the "Gear" in the top right corner and choose "Printers" from the menu, I find my printer, right-click the icon and choose "Properties" and then I can change Device URI.  That's where you could put "socket://192.168.1.1:9100" in for the printer you've already installed.

It didn't help...

---

### Post by guillermo-fink on 2015-06-07
Hello: I run Ubuntu 14.04 LTS. I have a TP Link TL-WDR3600 running factory firmware. I've tried all options, to print using print server on router and get the same errors depicted here. Any clues? Best, Willy

---

### Post by pdc on 2015-06-08
Hi guillermo; welcome to the forum

it is not clear from your description what sort of a setup that you have; 

have a read at this [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu) and tell us which of the options applies to you; and perhaps the wiki might give you some guidance too; 

if you can open a terminal; (type the word into the Dash search option ..................)

and if you can copy this command, and paste it into the terminal: hit the ENTER key after the paste; and if you can please copy the result; and paste it back in your reply please

```
/usr/sbin/lpinfo -v
```

---

### Post by aikishugyo on 2015-06-08
Nice to see you are using gutenprint, and that you can print via USB but not over network. So there is no problem with the gutenprint driver, which to me is good news.
A similar problem was reported on the gimp-print mailing list with a different printer model, so if a solution is developed in this thread, it will bea good reference for others.

I don't see any mention of CUPS debugging logs yet, which surely should be a primary consideration.

---

