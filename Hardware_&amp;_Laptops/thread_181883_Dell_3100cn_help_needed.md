---
title: "Dell 3100cn help needed"
date: 2006-05-24
forum: Hardware &amp; Laptops
---

### Post by dgkulzer on 2006-05-24
I have a Dell 3100cn color laser printer I am trying to get set up.  The printer is Linux compatible and is also network compatible.  I have the printer set up to my router and my desktop is able to print fine and if I hook my laptop up to the router I can print in WinXP just fine.  The problem is that I can not get it working in Ubuntu yet.

My printer came with a install cd containing "Dell-Laser-Printer-3100cn-1.2-1.noarch.rpm".  I used Alien on this file and made a "Dell-Laser-Printer-3100cn-1.2-1_all.deb" file.  I right clicked on this file and selected 'Open with Gdebi Package Installer'.  I then install the package and everything looks fine.

If I go to System->Admin->Printing a little window pops up.  I went under Global Settings and put a check mark next to Detect LAN Printers.  I then click on Add Printer and a new window opens up.  In this window I selected Network Printer but am I supposed to select "Unix Printer LPD" or "Cups Printer IPP"??  I think its Unix Printer LPD but if so is Host the printers IP and what should be put under Queue?

Anyone have any tips for me?

The readme files with the Dell installation cd only cover installing to Suse and RedHat.

---

### Post by digi_al on 2006-08-02
Hi,

I actually followed your instructions to install my printer.

You do select 'Unix Printer LPD', the host is the printer's IP and you leave the queue field blank, then on the next screen you select Dell and then the printer model. And i think that was it.

It all installed perfectly - so thanks

I do love Ubuntu and these forums - regularly i find answers to problems here, so i thought i'll add the above in case someone else got this problem.

Alan.

---

### Post by chrismyers on 2006-08-22
The  Dell 3100cn uses the same driver as the Lexmark Optra Color 1200.

The Lexmark printer is natively supported in Ubuntu Dapper. I should get the developers to add this in to the next release :-)

---

### Post by zielina on 2007-09-24
I try what you said to my Dell 3100cn and Ubuntu 7.03 it is networked. No luck. Any thoughts? Are you on a network?

---

