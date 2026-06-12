---
title: "Mail Server Problem"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by nara_456 on 2009-07-15
Hi 

Recently I have installed Mail Server in my Ubuntu Machine 
(MTA - postfix , MDA - Courirer , Client - Squirrelmail and outlook)

And configured DNS too. But when i tried to send a mail to yahoo my 
mail.log message shows an error saying that 

Jul 15 20:22:00 ityug postfix/smtp[7205]: 348CED00444: host b.mx.mail.yahoo.com[66.196.82.7] refused to talk to me: 553 Mail from 122.169.248.92 not allowed - 5.7.1 [BL21] [B**_]Connections not accepted from IP addresses on Spamhaus PBL;_[/U]**[/B] see [http://postmaster.yahoo.com/550-bl21.html](http://postmaster.yahoo.com/550-bl21.html) [550]


How to overcome this PBL error?

And I tried nslookup my ip address 

it is redirecting to my ISP domain it is not showing my domain . why ?


Server:		10.0.0.1
Address:	10.0.0.1#53

Non-authoritative answer:
92.248.169.122.in-addr.arpa	name = ABTS-AP-Static-092.248.169.122.airtelbroadband.in.

Authoritative answers can be found from:
248.169.122.in-addr.arpa	nameserver = dnsglobal.mantraonline.com.
248.169.122.in-addr.arpa	nameserver = dnsbom.mantraonline.com.
248.169.122.in-addr.arpa	nameserver = dnsdel.mantraonline.com.
248.169.122.in-addr.arpa	nameserver = aaadel.mantraonline.com.
248.169.122.in-addr.arpa	nameserver = dnsblr.mantraonline.com.
aaadel.mantraonline.com	internet address = 202.56.230.6
dnsblr.mantraonline.com	internet address = 202.56.250.5
dnsbom.mantraonline.com	internet address = 202.56.240.5
dnsdel.mantraonline.com	internet address = 202.56.230.5
dnsglobal.mantraonline.com	internet address = 202.56.230.52


Any body suggest me where I did the mistake ?

---

### Post by dstew on 2009-07-15
I don't think you made a mistake. The problem is that you have put up a mailserver that is not recognized by yahoo as being valid. Your IP address is apparently on the [Spamhaus block list]("http://www.spamhaus.org/sbl/"), which yahoo is using to filter incoming mail. You would have to convice Spamhaus that your mail server is harmless.

---

