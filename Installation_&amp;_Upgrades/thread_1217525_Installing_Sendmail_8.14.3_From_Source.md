---
title: "Installing Sendmail 8.14.3 From Source"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by joncotes on 2009-07-19
(I don't know if I put this in the correct forum. Please feel free to move it)

I have installed sendmail from source, but it is having some issues.
I am running Ubuntu 9.04 (Jaunty)

Install steps:
----------------------------------------------------
groupadd smmsp
useradd -g smmsp smmsp

wget ...
cd sendmail-8.14.3/
sh ./Build
sh ./Build install

cd cf/cf/
cp generic-linux.mc sendmail.mc
sh ./Build sendmail.cf
sh ./Build install-cf

mkdir /var/spool/mqueue
touch /etc/mail/aliases
touch /etc/mail/local-host-names
----------------------------------------------------

At this point, I can start sendmail with

```
sendmail -bd -q20m
```Sending mail works perfectly, but receiving mail does not appear to work. the mailq command shows mail that cannot be delivered because of an Operating system error.

I get the following errors in /var/log/mail.err

```
Jul 19 13:16:04 myhostname sendmail[7920]: n6JJv331007262: SYSERR(root): Cannot exec /usr/bin/procmail: No such file or directory
Jul 19 13:16:04 myhostname sendmail[7918]: n6JJv331007262: SYSERR(root): putbody: write error: Broken pipe
```It's looking into /usr/bin/procmail, which is definitely not there because I haven't installed it. I don't think I want procmail, but I am new to this so I don't know what packages most standard mail configurations use. All I want is mail delivered.

Your thoughts are appreciated. Thanks.

---

### Post by andrevanzuydam on 2009-08-05
I have the same problem from apt-get install sendmail configuration, it accepts email but refuses to deliver with this message

putbody: write error: Broken pipe
Operating system error

---

