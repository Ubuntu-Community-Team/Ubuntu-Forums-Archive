---
title: "Does Ubuntu need a Firewall?"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by MrRabbitC on 2006-01-14
Well... Does it?
I read somewhere that it really doesn't. 
Is that true?

---

### Post by Zelut on 2006-01-14
You're going to get mixed replies about that.  Here are my 2c..

If you're behind a router you're fine. (unless you port-forward)
To be safe install firestarter & setup some security.  Can't hurt really, whether we NEED it or not..

---

### Post by jasmuz on 2006-01-14
Linux in general is more secure than Windows, nonetheless....Distributions come with services that are uncalled for, shutting down those services you wont need, reduces the posibility of a break in.

You shouldnt be worried for a firewall unless you are planning to set up a server.

---

### Post by MrRabbitC on 2006-01-14
I'm at the firestarter web pager here and am not sure which to download. I see one for Ubuntu 5.04 but not for 5.10.

---

### Post by Zelut on 2006-01-14
simply install the firestarter package (using apt-get or Synaptic)

---

### Post by Azion on 2006-01-14
As kuyaedz said, if ur behind a hardware firewall you'll be fine.
All the ports will be hidden anyway

---

### Post by MrRabbitC on 2006-01-14
Yep. I'm good in that respect.
I'm just trying to learn Ubuntu the best I can.

I didn't really understand this:

Ubuntu users can install Firestarter by enabling the "universe" repository in the /etc/apt/sources.list file or in synaptic under Settings->Repositories. Having enabled the repository, the procedure is the same as in Debian.

is this something already existing in Ubuntu that I would need to enable?
I found the /etc/apt/sources.list but wasn't sure what exactly to do with it.
As for the "universe" repository.... ?????

Just kind of excited about Ubuntu. Seems pretty cool so far.

---

### Post by Omnios on 2006-01-14
Go to Menu: Sytem / Administration/ Synaptic package manager :open it lol. 

  In synaptic package manager on the top go: settings / Repositories /

 A window pops up in that window click settings  and another pop up. check off showed disabled software sources. CLose and in the window before that you can check off the sources such as restricted universe multiverse etc.

---

### Post by Zelut on 2006-01-15
As per the response above check out this [Wiki]("https://wiki.ubuntu.com/SourcesList") for more information on that..

---

### Post by wanger123 on 2006-01-15
Hi, I use guarddog and am very happy with it. There is a good article about the setup at [http://www.tuxmagazine.com/](http://www.tuxmagazine.com/) issue #5
wanger

---

### Post by Herman on 2006-01-15
Just out of curiosity, if anyone is installing a fiewall, it would be interesting to find out if they pass the firewall tesing at these two sites before and after the firewall is installed. Mine passes them without any firewall, but I have a router. With the computer connected directly to the internet (not going thru' the router temporarily), sygate finds only one port not 100% strealth, but that one was the one I was using to connect to them, and it was 'closed'. All other ports 100% stealth as far as I can tell from these on-line scans. 

[https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")
'Shields Up!'
[http://scan.sygatetech.com]("http://scan.sygatetech.com/")
'Sygate Online Security'

There may be more ways to test our firewalls or tougher tests, I would be interested to learn of them. The best I can tell we don't need a firewall, but each to their own opinion. I may change my mind if shown a good arguement with some evidence. This is an interesting subject. (Herman) :D

---

### Post by moon2js on 2006-01-15
[QUOTE=kuyaedz]You're going to get mixed replies about that.  Here are my 2c..

If you're behind a router you're fine. (unless you port-forward)
To be safe install firestarter & setup some security.  Can't hurt really, whether we NEED it or not..[/QUOTE]

Out of curiosity, what is the danger if ports are forwarded past a firewalling router to a firewall-less ubuntu box?

I mean, the ports that are forwarded are ports that I would have to open on the Ubuntu machine's firewall anyway, aren't they?

Unless I'm worred about something happening from within the LAN, isn't another firewall redundant?

---

### Post by transactionlogfiller on 2006-01-15
You can forward a port from your router to your Ubuntu server and then use the software firewall to restrict connections to a specific host and/or service. Which is what I've done with my SSH server.

---

### Post by MrRabbitC on 2006-01-15
Sorry for my ignorance. I'm new to Ubuntu and I'm still trying to figure out what/where everything is. But I am finding this forum to be very helpful and insightful. Everyone here seems to be very willing to help. That's cool.

---

### Post by MrRabbitC on 2006-01-15
Well.... I think I got firestarter running though I don't see anything. Does it have an interface somewhere I'm not seeing?

---

### Post by Zelut on 2006-01-15
you should be able to find it in Applications > System Tools > Firestarter (or try ALT-F2 gksudo firestarter)

---

### Post by MrRabbitC on 2006-01-15
I got it now. I had to restart to see it.

---

