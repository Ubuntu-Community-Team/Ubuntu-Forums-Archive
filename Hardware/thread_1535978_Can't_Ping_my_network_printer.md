---
title: "Can't Ping my network printer"
date: 2010-07-21
forum: Hardware
---

### Post by unckybob on 2010-07-21
Can someone please help me? I'm at my wit's end. 

I am trying to get my network printer an HP Laserjet 8000N working. It has HP JetDirect. 

I set it up with the cups printing utility found at "System" ->  Administration" -> "Printing". From my configuration page my network printer's address is 192.168.0.2. I can't ping it, so I can't print to it. 

Can someone please help?

---

### Post by PresenceofMind on 2010-07-21
Greetings,

Have you got any firewall installed?...anything like gufw?

I would suggest using HPLIP. It's developed by HP to enable HP printers print in Linux and I have connected my printer HP 8500a Officejet through that rather than use the printing utility. I did try using the printing utility but I got no results.

---

### Post by unckybob on 2010-07-21
Thanks for getting to me!

I'm a little new. How can I check for firewalls?

---

### Post by unckybob on 2010-07-21
And if it's not too much trouble could you give me a link to a site that tells how to use it?

---

### Post by PresenceofMind on 2010-07-21
Go to the Administration menu..... If you have any graphical user-interface firewalls installed it should show up there (sometimes firewalls are also found in your Applications menu)

Unfortunately, I don't use the cups printer utility anymore, as such I've lost or have no familiarity with it. If you haven't set it up properly you can find yourself unable to ping or print (which is what happened me....and yourself as well).

Later on, I began to use HPLIP with my HP printers cos I found that program works the best for HP.

Here, have a look in here:

[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

I also found this from another post in this forum, which involves CUPS. You might find this useful:

[http://ubuntuforums.org/showthread.php?t=1535679](http://ubuntuforums.org/showthread.php?t=1535679)

---

### Post by unckybob on 2010-07-21
According to this link: 

[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_8000_series.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_8000_series.html) 

The HP Laserjet 8000 series won't work with HPLIP for network or parallel interfaces. It will work for USB. Unfortunately, I don't have the card that goes in the printer that accepts a USB connection. 

Thanks for your help just the same!

---

### Post by PresenceofMind on 2010-07-21
> **unckybob said:**
> According to this link: 

[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_8000_series.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_8000_series.html) 

The HP Laserjet 8000 series won't work with HPLIP for network or parallel interfaces. It will work for USB. Unfortunately, I don't have the card that goes in the printer that accepts a USB connection. 

Thanks for your help just the same!

No problem. I feel bad now......

Here are my final two links, which may help you out as it has stuff about using HP JetDirect with CUPS. Feel free to have a look if you wish:

[http://www.hlug.org/presentations/cups/printing.html](http://www.hlug.org/presentations/cups/printing.html)

[http://www.ehow.co.uk/how_6208908_add-printer-linux-hp-jetdirect.html](http://www.ehow.co.uk/how_6208908_add-printer-linux-hp-jetdirect.html)

Just out of interest, how old is the 8000N?

---

### Post by unckybob on 2010-07-21
When the people that I got that thing bought it, I think people were still using Windows 98! 

I'll check out those two websites later and post something here if I can do anything with them.

Thanks again!

---

