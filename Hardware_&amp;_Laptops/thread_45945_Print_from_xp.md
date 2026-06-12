---
title: "Print from xp"
date: 2005-07-02
forum: Hardware &amp; Laptops
---

### Post by asimon623 on 2005-07-02
Hi. I have set up my printer (deskjet 5650) on my ubuntu desktop and want to network it wirelessly so the other computers in my house, all windows xp home computers, can print to it. I really don't know what I need to do. If you can help, I'd really appreciate it. 

Thanks
Alex

---

### Post by asimon623 on 2005-07-02
well ive found some info on the web...and apparently I need to edit a file called smb.conf  I really don't know how to do that anyways, but my problem is it's READ ONLY...and I can't figure out how to edit it. I am on the supposed to be master account..."alex" but the owner of these files I need to edit are root...I tried logging on as root..but it won't let me. I've always been able to use "root terminal" but I can't change anything in these files. 

thanks

---

### Post by skirkpatrick on 2005-07-02
My Ubuntu machine has my HP 5550 on it and the rest of the house is XP and one 98 machine.  I did find out something in trying to get them to all print through my Ubunut machine:  Win98 print response is faster using Samba and XP print response is faster using Cups.  Since you have all XP machines, I'd recommend using Cups.  Use "sudo gedit /etc/cups/cupsd.conf" to edit your Cups configuration.  Search for "Port".  The part of my file looks like this:
[quote
#Port 80
#Port 443
Port 631
#
#Listen 127.0.0.1:631
[/quote]
You want to make sure "Port 631" is uncommented.  This means that Cups will listen to all all print requests from port 631.

You'll need to know the name of your printer.  You can find this out from System->Administration->Printing.  Mine is called "DeskJet-5550".  You'll also need to know the name of your machine.  You can find that from System->Administration->Networking and go to the General tab.  My machine is called "PapaBear".

Now, in XP, add a new printer.  Tell it that it's a network printer and select the third option, "Connect to a printer on the Internet or on a home or office network".  In the URL box, you'll need to put the network path to your printer.  For my machine, it's "http://PapaBear:631/printers/DeskJet-5550".  Substitute your machine's name and the name of your printer.  Unless your XP machines have already installed the printer driver before, you'll need the driver disk to complete the installation.

That should be it.  Like I said, my XP machines get a faster response from the printer going directly through Cups but the Win98 machine works better with Samba.

---

### Post by asimon623 on 2005-07-02
hey thanks, but it still doesn't work. the name of my computer is "lounge" and the name of printer is DeskJet-5650

if i go to my browser on my ubuntu and put in [http://lounge;631](http://lounge;631) it opens up the printer config page...if I do this in firefox it doesnt work, and firefox does that google thing and brings me to betalounge.com haha

I dont know if my router is blocking any ports, but I made sure I turned off all of my firewalls on the computers (sp2 is really pissed at me now).

thanks

---

### Post by skirkpatrick on 2005-07-02
Well, if your Ubuntu machine has a static IP, you can use that for the URL:
> 
[http://192.168.0.100:631/printers/DeskJet-5560](http://192.168.0.100:631/printers/DeskJet-5560)


Now when I say URL, that doesn't mean to put that in to a web-browser.  That means use it in the Windows printer setup.

[IMG]http://webpages.charter.net/clan_kirkpatrick/sok/printer1.jpg[/IMG]

[IMG]http://webpages.charter.net/clan_kirkpatrick/sok/printer2.jpg[/IMG]

---

### Post by asimon623 on 2005-07-02
haha im well aware of that...I did that and it couldn't find the printer...

---

### Post by skirkpatrick on 2005-07-02
Then try using the Ubuntu machine's IP address.  Another machine shouldn't find it unless it's in a DNS somewhere or in the Windows hosts file.  To be honest, I'm not sure how mine found the printer machine.  Possibly because I've got Samba setup on it as well.

---

### Post by asimon623 on 2005-07-03
No, that still doesn't work

---

### Post by skirkpatrick on 2005-07-03
Can your XP machine go to [http://lounge:631](http://lounge:631) and see the Cups admin page?

I forgot something in the Cups config.  You need to make sure the Locations section allows outside access in /etc/cups/cupsd.conf:
> 
<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.*
</Location>

This allows IP's 192.168.0.0 - 192.168.0.255 to have access to Cups.  You'll also need to restart Cups anytime you change the config file:
> 
sudo /etc/init.d/cupsys restart


---

