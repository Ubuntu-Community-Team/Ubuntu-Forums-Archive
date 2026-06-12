---
title: "Photosmart C6160 Printer"
date: 2006-12-24
forum: Hardware &amp; Laptops
---

### Post by k2pow on 2006-12-24
I have a HP C6150 Photosmart Printer that is wired to my router. I really have no idea where to start in trying to set this up if anyone can help me that would be much appreciated.

---

### Post by cilynx on 2006-12-24
Is your router a computer or a Linksys box or something like it?  Give some details of the network and we'll work from there --

---

### Post by k2pow on 2006-12-24
Yes my router is a Linksys Broadband router and the printer is hardwired directly to it.

---

### Post by cilynx on 2006-12-25
Alrighty...and the hope is to print to this printer from an Ubuntu machine?

Does the router see the printer when you look in its web config?

Does the router provide the printer drivers or does it expect the client to do that?

---

### Post by k2pow on 2006-12-25
Yes I want to print from the Ubuntu machine. I have other windows computers that have printed from the printer (its all set up with the network). The printer came with a disc for the windows drivers so I had to install those on the other comps. The router doesnt supply the drivers.

---

### Post by cilynx on 2006-12-25
Alrighty...

System->Administration->Printing
New Printer
Network Printer

Most likely, you're looking at "Windows Printer"

Give it the same URI you gave the Windows boxen that can print to it.

If that doesn't work, give me the model number of your router and I'll seek further.

---

### Post by k2pow on 2006-12-26
First off is their a good way to figure out what my URL is for the printer? And its asking for all these passwords.

---

### Post by cilynx on 2006-12-26
The URI should be something along the lines of:
192.168.0.1/printers/Photosmart-C6160

It all depends on how your router does things.  What model is your router?

The only password Ubuntu should be asking you for is the sudo password.  It's because you're doing administration.

---

### Post by k2pow on 2006-12-26
Its a Linksys WRT54GS, The printer has a IP address [http://192.168.1.108/](http://192.168.1.108/) would that be it?

So I proceeded assuming that information is correct. First for the kind of printer I selected windows (smb), then for host I put, [http://192.168.1.108/](http://192.168.1.108/), and now what do I put for the printer tab? Also for some reason it did ask me for passwords for other comps on the network and some random other things.

Also side note I just looked at my printers settings and in it it says Host Name- Main Print. Would this be what I put under host (but what goes under printer, and what about that url)

---

### Post by cilynx on 2006-12-26
Ok, so as opposed to the Linksys being a print server, it's just a router and the Printer has its own Network interface.  I gotcha.  

```

hp-makeuri 192.168.1.108

```
should give you the URI of the printer.  Once you've got that, input it into the printer setup wizard

---

### Post by k2pow on 2006-12-26
So I just did that, and I typed [http://192.168.1.108/](http://192.168.1.108/) as the host name, now what should I do about the printer name(it doesnt give me anything suggesting something)

---

### Post by jmeuf on 2007-01-15
Hi.
I jump on this thread because I have the same problem.

My PC is loaded with Ubuntu 6.06 (but I will soon upgrade to 6.10). I use a WiFi router Netgear VGR614v6. My printer HP Photosmart 2575 (all-in-one) is wired connected to the router. Everything works when I run Windows XP instead (using SAMBA).

In the wizard I used network printer / CUPS and got the uri from hp-makeuri which returns:
hp:/net/Photosmart_2570_series?ip=192.168.1.2
(192.168.1.2 is effectively the address of the printer, confirmed by the router).
After copying this in the ipp field, I get:
ipp://hp:/net/Photosmart_2570_series?ip=192.168.1.2

My printer remains desperately silent ...

hplip, the recommended driver, is installed (checked in Synaptic)

1) shall I use CUPS or Windows in the wizard?
2) the tooltip in the wizard shows an uri of the form: ipp//nom_d'hote/printers/<name>, which doesn't look like what I got ...

What shall I do ?

Thanks.

---

### Post by akbrian on 2007-02-05
Take a look at;
[http://hplip.sourceforge.net/index.html](http://hplip.sourceforge.net/index.html)
I can't offer any first hand experience on this yet, as I'm still researching the C6150

---

### Post by zebulonevans on 2007-02-25
Take a look at my directions on post:
[http://ubuntuforums.org/showthread.php?p=2213087#post2213087]("http://ubuntuforums.org/showthread.php?p=2213087#post2213087")

I just got my printer working tonight.

Good luck!

---

