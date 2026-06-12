---
title: "external mail from php script"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by polarbearcv on 2009-10-16
Hello,
 
I have installed a Ubuntu 8.04 server recently.
I'm trying to send emails from a php-script using the mail-function.
This is no problem for internal emailaddresses (own domain) but mails send to external mail addresses never arrive.
Since I'm a newbie at linux I have no idea where to start looking to solve this problem.
 
Thanks in advance and best regards,
 
Marc

---

### Post by phillw on 2009-10-16
Hi,

A lot of mail engines won't allow mail from 'private' IP's

If you check in the returned (failed) mail area it may have a message there.

Phill.

---

### Post by falconindy on 2009-10-16
@OP: you need to install an MTA (mail transport agent) such as Postfix or Exim.

> **phillw said:**
> Hi,A lot of mail engines won't allow mail from 'private' IP's
Not really true. There's no such thing as a registrar for MX hosts and MTAs. How would a mail engine know if the IP is "private" or "public"?

---

### Post by phillw on 2009-10-16
> Not really true. There's no such thing as a registrar for MX hosts and MTAs. How would a mail engine know if the IP is "private" or "public"?

Well, AOL's mail servers certainly know a private IP address. 

I can send email with the Works, business, internet - but not with the one at home, which is for domestic use. I'm guessing they're looking at the info for the originating IP address and filtering that way.

I was just informing the OP of something that may be stopping his emails. 
Hotmail, for example, does not seem to like some of the IP addresses that google-apps use if you use their email system on your site (I do & know !!!).

Phill.

---

### Post by phillw on 2009-10-16
> @OP: you need to install an MTA (mail transport agent) such as Postfix or Exim.And, if you want to install, a secure MTA .... Here's a good place..

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

Be aware, that the authors' idea of 'easy' is not the same as 'quick' !!!

It is, however, one mother of a mail-server. Well, protected with firewall, anti-spam - AV filtering for our poor windows bretheren etc.

Set aside a weekend to get it all done, tho. It does, however, run like a dream :)

Oh, and if you don't want to use **vi ***filename* for the editing of the files you can use **gksudo gedit** *filename*
Which is the more friendly gedit text editor.

Phill.

---

