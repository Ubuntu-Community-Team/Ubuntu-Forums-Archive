---
title: "Postfix Will Not Start!"
date: 2008-08-13
forum: General Help
---

### Post by DevilChild on 2008-08-13
Hi all, I'm new to Ubuntu.. but i have experience with computers ( windows ) so hopefully i'll be able to understand any replies :)

Okay, a couple days ago I installed the new Ubuntu Server Edition and added the Desktop.  It's going to be the server for my business, so I need this to work desperately...

I can't get my mail server to work!

I followed a full guide on how to set up a server at [http://flurdy.com/docs/postfix/edition5.html](http://flurdy.com/docs/postfix/edition5.html), but for some reason now postfix won't even start :confused:

It used to before I followed the guide, so I tried re-installing postfix, which didn't help, and also putting everything in main.cf back to its default, still no help.

When I run: sudo /etc/init.d/postfix start it outputs
"Starting Postfix Mail Transport Agent postfix"
"postfix/postfix-script: fatal: usage: postfix start ( or stop, reload, abort, flush, check, status, set-permissions, upgrade-configuration )

postfix status says that postfix is not running.

I've tried re-booting multiple times, I have no other mail systems installed other than courier-pop/courier-imap/courier.. and I cannot get this to work at all.

I've 'googled' time and time again with no success.

Any ideas guys?  Would be much apreciated!

BTW: I checked in the /var/log/mail.log / mail.err and nothing is being written...

( Sorry for such a long post )

---

