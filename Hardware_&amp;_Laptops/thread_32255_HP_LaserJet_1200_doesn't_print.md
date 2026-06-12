---
title: "HP LaserJet 1200 doesn't print"
date: 2005-05-06
forum: Hardware &amp; Laptops
---

### Post by dworzec.net on 2005-05-06
well, strange thing - I chose my printer from the list - driver seems to be ok, but when I choose "print" I get the message "printer ready"/"printing" and nothing happens... control light on my printer just flashes like it's going to print something, but it doesn't...
what's even stranger is that I managed to print one page after waiting a few minutes, but it was only once... I don't even know where might be a problem?

---

### Post by kleeman on 2005-05-06
I have exactly this printer under hoary and it works really well. How do you have it connected? I have mine set up with the jet direct server off my router and installed it as a network printer.

---

### Post by dworzec.net on 2005-05-06
connected via usb

---

### Post by kleeman on 2005-05-06
OK so different connection. If the light is going that means data is getting there. Have a look in /var/log/cups/error_log to see if there is anything interesting. What does lsusb show?

---

### Post by patrick.inderkum on 2007-05-27
Hello 

While searching for a solution for my not printing HP Laserjet 1200 (but connected via parallel port). I found your dialogue.  In /var/log/cups/error_log I found the following:

E [27/May/2007:12:42:25 +0200] cupsdAuthorize: Local authentication certificate not found!

Guess this is my problem. But how to solve it??

Thanks for any help.

Patrick

---

### Post by kleeman on 2007-05-27
May be this bug:
[https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/45099](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/45099)

A lot of these problems occurred with Dapper and were resolved in Feisty......

---

### Post by patrick.inderkum on 2007-05-27
Hi kleeman

Thanks for quick response. So far I understood my problem relates to granting access rights to the printer. Non of your suggested bug reports helped to much.

First of all: I have already feisty installed. Therefore your mentioned bugs from drapper should be resolved on that version.

I tried to add a user in Printers Tab in the configuration Page of Cups. The configuration web-gui told me something like "successfully added user".  The error_log of cups tells me something different:
E [27/May/2007:16:09:19 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [27/May/2007:16:09:25 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [27/May/2007:16:10:59 +0200] CUPS-Set-Default: Unauthorized
E [27/May/2007:16:11:12 +0200] CUPS-Add-Modify-Printer: Unauthorized

Do you have a clue about that??

Thanks anyway
Patrick

---

### Post by patrick.inderkum on 2007-05-27
Hi kleeman

Finally I resolved my problem. 
1. Remove everything in connection with cups which is not needed with the Synoptic Package Manager. (In Add/Remove program it tells you if you can remove)

2. Install the Printer manually without the suggested printer choice.

That's it. Magic!

Thanks for help.
Patrick

---

### Post by kleeman on 2007-05-27
Hmmm wild guess but one possibility is that you are not a member of the lpadmin group. Open the Users and Groups dialogue (under System---> Administration) and then click on manage groups and check who the members of the group are....

---

### Post by patrick.inderkum on 2007-05-28
Hello kleeman

No I am member of the group lpadmin. Thinking deeper on my yesterdays successful wild trial one of the main changes are I haven't chosen the default setting for the Printer Port (something like "device=parport0). I chose directly LPT1. 
My guess was that parport0 means the very same parallel Port (LPT1). Seems that assumption was wrong. Is it possible that I've chosen  a port from the USB?

Patrick

---

### Post by kleeman on 2007-05-28
In complicated situations like this appears to be I prefer the kde print tool which can be installed with

sudo apt-get install kdeprint

It may install a whole lot of kde stuff however....

You use it from the commandline with

gksu kprinter

---

### Post by snkk on 2007-12-02
I have the same scenario, but I am a novice when it comes to Ubuntu.
I jsut installed last night, and I have not been able to get the damn 1200 printing.
It is recognized, says that it is idle, then stops.  
Sometimes, I cannot even stop the print que without a restart.
Can anyone help that can speak BASIC language to me?
I have attempted the above....I am in fear that I am doing more damage than good.,
Thanks for any replies...

---

### Post by secular on 2007-12-07
My apologies for jumping in, but I think I have the same problem and can add my own detail:

I can click on System, Administration, Printing and get the Printer Configuration window. In that window, I can click on the Policies tab and check Enabled. This gets my printer working for a while.

If the computer is idle for an hour or so, I can't print any more, so I do the above to print again.

I wonder if there's a way to make this check stick.

---

### Post by kleeman on 2007-12-08
> **snkk said:**
> I have the same scenario, but I am a novice when it comes to Ubuntu.
I jsut installed last night, and I have not been able to get the damn 1200 printing.
It is recognized, says that it is idle, then stops.  
Sometimes, I cannot even stop the print que without a restart.
Can anyone help that can speak BASIC language to me?
I have attempted the above....I am in fear that I am doing more damage than good.,
Thanks for any replies...

Go to a terminal (Applications---> Accessories----> Terminal) and type

cat /var/log/cups/error_log

Post the output here....

---

