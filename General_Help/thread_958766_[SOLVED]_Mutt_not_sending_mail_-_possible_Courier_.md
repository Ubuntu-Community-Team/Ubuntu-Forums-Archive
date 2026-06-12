---
title: "[SOLVED] Mutt not sending mail - possible Courier problem?"
date: 2008-10-25
forum: General Help
---

### Post by sampablokuper on 2008-10-25
Hi folks,

I recently set up two servers running Ubuntu 8.04.1 server LTS. On one of them, Mutt works fine. On the other, it doesn't. Both were set up around the same time, but at different locations. Both are behind home routers with NAT, and seem to be having no problems with their other functions.

On the server that's having the problem with Mutt, if I use
```
mutt -x
``` and then enter my personal email address, a subject ("Testing") and a message ("Foo bar"), followed by a full stop on a line by itself, Mutt drops me back to the command line as though everything's fine. But when I log in (on a different PC) to my personal email account, the email hasn't arrived. Yet if I do the same thing using the other Ubuntu server, the email arrives in my inbox as it should.

I've never had a problem with Mutt before, so don't really know how to troubleshoot it, but the Mutt website suggests investigating the MTA. When I installed mdadm on the machine previously, it installed Courier (I don't know why - seems odd for RAID software to require a particular MTA), and since I haven't installed any other MTA software myself, I figure Mutt is trying to use Courier as the MTA.

Sure enough, ```
tail /var/log/syslog
```gives:```
Oct 25 23:17:02 shelleysoldbox courierd: Initializing dsn
Oct 25 23:17:02 shelleysoldbox courierd: Started ./courieruucp, pid=5434, maxdels=4, maxhost=4, maxrcpt=16
Oct 25 23:17:02 shelleysoldbox courierd: Started ./courierlocal, pid=5435, maxdels=10, maxhost=4, maxrcpt=1
Oct 25 23:17:02 shelleysoldbox courierd: Started ./courierfax, pid=5436, maxdels=1, maxhost=1, maxrcpt=1
Oct 25 23:17:02 shelleysoldbox courierd: Started ./courieresmtp, pid=5437, maxdels=40, maxhost=4, maxrcpt=100
Oct 25 23:17:02 shelleysoldbox courierd: Started ./courierdsn, pid=5438, maxdels=4, maxhost=1, maxrcpt=1
Oct 25 23:17:02 shelleysoldbox courierd: queuelo=200, queuehi=400
Oct 25 23:17:02 shelleysoldbox courierd: Purging /var/lib/courier/msgq
Oct 25 23:17:02 shelleysoldbox courierd: Purging /var/lib/courier/msgs
Oct 25 23:17:02 shelleysoldbox courierd: Waiting.  shutdown time=Sun Oct 26 00:17:02 2008, wakeup time=Sat Oct 25 23:44:59 2008, queuedelivering=1, inprogress=0
```

The "queuedelivering=1" part looks like it might be referring to the email I tried to send with Mutt, but I'm not sure.

I'd be grateful for any advice here!

Many thanks in advance,

spk

---

### Post by dcstar on 2008-10-25
> **sampablokuper said:**
> Hi folks,

I recently set up two servers running Ubuntu 8.04.1 server LTS. On one of them, Mutt works fine. On the other, it doesn't. Both were set up around the same time, but at different locations. Both are behind home routers with NAT, and seem to be having no problems with their other functions.
.........
I'd be grateful for any advice here!

Many thanks in advance,

spk

Try installing **postfix**, it is simple to set up and I find it a reliable MTA.

---

### Post by sampablokuper on 2008-10-25
> **dcstar said:**
> Try installing **postfix**, it is simple to set up and I find it a reliable MTA.

Thanks for the suggestion, but installing another MTA is going to be a last resort, I think, because I don't want to have two MTAs running, and it looks like mdadm requires Courier (correct me if I'm wrong!).

---

### Post by sampablokuper on 2008-10-25
OK, following the advice at [this]("http://markmail.org/message/z7jze6mlgxjhyqtf#query:+page:1+mid:q6gt4gt2qbu76baw+state:results") mailing list post, I tried
```
host -t mx uclmail.net
```
and then
```
telnet barracuda.aluminati.org 25
```
both of which seemed to work fine, so that at least hopefully means I probably don't have a network configuration problem or an esmtpd settings problem...

What's the next diagnostic step to take?

---

### Post by sampablokuper on 2008-10-26
Thanks to some folks on the Courier mailing list, this problem has now been solved.

Basically, it involved ensuring that /etc/hosts and /etc/courier/me had the correct domains in them. The problem was that courier was trying to send from the address sam@shelleysoldbox, which isn't a valid email address and was therefore being rejected by the receiving mail server.

---

