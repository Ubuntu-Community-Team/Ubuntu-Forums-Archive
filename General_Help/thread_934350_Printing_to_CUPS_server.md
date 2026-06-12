---
title: "Printing to CUPS server"
date: 2008-09-30
forum: General Help
---

### Post by colinnwn on 2008-09-30
Hi All,

I have searched the docs [https://help.ubuntu.com/](https://help.ubuntu.com/) and google, but most of what I find is about setting up a CUPS server on Ubunutu.  I need help printing from Ubuntu to another CUPS server.

I have a little server (a NSLU2) running CUPS and hosting a HP F4180 printer.  I can print to it fine in Windows if I install a network printer with the address [http://192.168.1.4:631/printers/HPF4180](http://192.168.1.4:631/printers/HPF4180) or [http://slug3:631/printers/HPF4180](http://slug3:631/printers/HPF4180).  

I have been unable to print to it at all from the same dual booting computers on Ubuntu Hardy.  One of the Printing Admin panels can't find any non-local printers, and frequently locks up when I try to connect to the server or browse for printers.  The other computer I tried changing the device URI for that same locally installed printer to the server.  When I click browse (or whatever it is), it finds the slug3 server, and seems to connect to the printer, but nothing happens when I try printing with it.

Can anyone give me some pointers or show me a good troubleshooting guide?

Thanks.

---

### Post by phidia on 2008-09-30
The Ubuntu wiki [here]("https://help.ubuntu.com/community/HpAllInOne") is for HP printers specifically and gives guidence on installing networked printers.

---

### Post by bcom on 2008-09-30
I'm not sure I can be of mulch help.  I use Ubuntu to print to Linksys print server. 


When I installed the printers, I made use of LPD and for the Device URL I used: lpd://192.168.1.78/L2.  L2 is the queue (port) that one of the printers is connected to on the print server.  For the other printer, I changed the Device URL to lpd://192.168.1.78/L1.

---

### Post by colinnwn on 2008-10-02
Hi,

Per the wiki, I tried running 
*sudo hp-setup*

It didn't discover the printer and exited.  This is probably because I haven't got HPLIP working on the server connected to the printer, **and HPLIP needs to be running on the server and client for this to work?**  I am currently getting 
[COLOR="Red"]"error: HPMUDEXT could not be loaded. Please check HPLIP installation" [/COLOR]
when I run any of the hp-* tools on the server.  I am working through this on the NSLU2 forum.

I researched LPD printing on the internet, and it seems you must have the HP tools working on the computer attached to the printer to find the queue name for the LPD URL.  **Is this true? ** If there is an alternate way to find the queue name, I could try it.

It seems wierd I can print fine with the printer attached locally to the Ubuntu computer, and I can print fine with the printer on the server using CUPS and Windows as the client, but I can't get the printer to work with CUPS and Ubuntu as the client.  Perhaps I don't understand something fundamentally different with the Linux printing infrastructure though.

Thanks.

---

### Post by bcom on 2008-10-02
> **colinnwn said:**
> Hi,


I researched LPD printing on the internet, and it seems you must have the HP tools working on the computer attached to the printer to find the queue name for the LPD URL.  **Is this true? ** If there is an alternate way to find the queue name, I could try it.



I am printing to two HP printers via a Linksys print server.  I did not have to do anything with HP tools.  

The queue name is is L1 for one port on the print server and L2 for the second port (might have to try l1 or l2, i.e without the capital letter).

So, in your case, if your print server has only one connection to your printer the queue is either L1 or l1; that is the queue name.  If your print server had another connection to a different printer, the queue name would be L2 or l2 and so on.

---

### Post by colinnwn on 2008-10-13
Man I am red faced I read all those CUPS docs and didn't put this together sooner.  But by the same token, I think there is substantial room for improvement in the CUPS docs and Ubuntu Wiki.  I am a reasonably savvy computer user and it took me probably 5 hours of research / trial to figure this out.

To print from a Ubuntu client computer to a printer on a server running CUPS, do the following on the client (Ubuntu) computer.

[LIST]
In a web browser go to [http://localhost:631](http://localhost:631)[/LIST]
[LIST]Click home>add printer
If at any time you are asked for your username and password, use the same one you use to log onto Ubuntu[/LIST]
[LIST]Enter anything you want for the name, location, and description[/LIST]
[LIST]Choose http printer[/LIST]
[LIST]Enter the address of your printer on the server.  You can get this address from the CUPS webpage on the server.  It should look like
[http://ServerIP:631/printers/PrinterNameInCUPS](http://ServerIP:631/printers/PrinterNameInCUPS)[/LIST]
[LIST]Select the make and model of your printer or upload the ppd file.  This must be a known working combination for your printer.[/LIST]
All done, you should now have this printer installed on your local computer if you go to administration>printing control panel.

It is always best to test the make and model number combination by installing the printer locally on your usb port first.  That way you immediately know if it doesn't work you have a CUPS config problem.  For example I have a HP F4180 printer, but they don't make a driver for it, I must use the HP F4100 driver.

If you don't know the address to the printer on the server, you can go to [http://ServerIP:631/printers](http://ServerIP:631/printers) to see all the names of available printers.

---

