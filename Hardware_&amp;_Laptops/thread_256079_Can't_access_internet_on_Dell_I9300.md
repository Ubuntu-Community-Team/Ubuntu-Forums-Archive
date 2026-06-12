---
title: "Can't access internet on Dell I9300"
date: 2006-09-12
forum: Hardware &amp; Laptops
---

### Post by jcaulley on 2006-09-12
I have the most recent version of Ubuntu. Installation went fine. I opened Firefox and typed in a web address and it timed out. I can not get any web page to show up. I tried synaptic and it couldn't dowload anything either. I also tried the updater and it was unable as well. So it does not appear to be limited to a program. I can ping any IP adress or web address from within a terminal. Here is a summary of everything I know right now:

Qwest DSL
Actiontec GT701-WS moden
Linksys WRT54GS router
Dell I9300 w/Intel 2200 wireless

I can access the admin page of the router.
I can access the admin page of the modem.
I can ping any IP address and recieve responses.
I can ping a web address and it resolves through the DNS servers to the correct IP address and returns responses.
It is not limited to just Firefox, Synaptic can't download packages, and the update can't either.
The only thing that seems to be able get past the modem is a ping.
I have tried using alternate DNS servers and that didn't work.
I don't use any form of proxy server.
The modem uses PPPoA and the username and password is stored in the modem. All the other computers that have attached to my network only needed to DHCP from the router and had instant connection.

Can someone please help me? I am going out of my mind here

---

### Post by David Corrales on 2006-09-12
Are you connecting with a cable or wireless? Did you already try both?
Please post the output of the command **route** to see if the problem could be from a missing route (though your comments kinda imply it's not).
Try running **sudo pppoeconf** to see if that will help you.

---

### Post by jcaulley on 2006-09-12
OK, for the first time I am posting from a Linux installation.  I activated the wireless built into my DSL modem and was able to connect using that wireless.  It still won't connect using the wireless on my Linksys router but I'll live with what I've got.  I had to disable IPV6 to get firefox to work but it is working like a champ now.

But I still have a problem.  I cannot download any software upates and I can't download anything with synaptic.  It just sits there and does nothing and then times out.  Any suggestions on why these programs wouldn't be able to retrieve any information?

---

### Post by David Corrales on 2006-09-13
Hmmm dns issues?

---

