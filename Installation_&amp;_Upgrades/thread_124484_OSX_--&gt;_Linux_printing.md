---
title: "OSX --&gt; Linux printing"
date: 2006-02-01
forum: Installation &amp; Upgrades
---

### Post by WelterPelter on 2006-02-01
This should be easy to set up, but for some reason it's not going well for me.

Runnning Tiger on a Powerbook.

An HP printer off Breezy Badger. Can't get the Mac to see the printer on the network. The printer itself works fine when just configured as local for the ubuntu box. But I need to to be *shared*. 

I assume the answer lies somewhere in CUPS. Any ideas?

---

### Post by mips on 2006-02-01
[http://ubuntuforums.org/showthread.php?t=78976](http://ubuntuforums.org/showthread.php?t=78976)
[http://ubuntuforums.org/showthread.php?t=82039](http://ubuntuforums.org/showthread.php?t=82039)
[http://www.ifelix.co.uk/tech/index.html](http://www.ifelix.co.uk/tech/index.html)  #Above thread said same as setup for WinXp printer ?

---

### Post by WelterPelter on 2006-02-01
Thanks for the links. I've tried doing what they said (as well as the tricks from several other posts) and nothing is working. 

There has got to be an easier way to do this. I can set up this printer in under 30 seconds in Mandriva. I'm wasting hours and hours trying to get ubuntu to allow network printing -- it should be simple. 

:mad: - very frustrated...

In an attempt to do something useful, here is my current CUPS configuration file, which I've now edited so many times, I'm not sure about at all:

DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.1.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.1.*
</Location>

MORE INFORMATION: The error log keeps saying that "get_printer_attrs: resource name '/' no good!" and "Destination printer does not exist!"
Hmm.... how to get the resource name right...

---

### Post by WelterPelter on 2006-02-01
For those having this CUPS weirdness, these two articles set me straight:

[http://www.enterprisenetworkingplanet.com/netos/article.php/2233051](http://www.enterprisenetworkingplanet.com/netos/article.php/2233051)
[http://www.enterprisenetworkingplanet.com/netos/article.php/2236011](http://www.enterprisenetworkingplanet.com/netos/article.php/2236011)

Just a hint: Don't use the System > Administration > Printers UI. Use the cups.conf file instead.

---

