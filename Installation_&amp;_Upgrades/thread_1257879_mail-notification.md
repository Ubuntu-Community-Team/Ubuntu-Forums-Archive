---
title: "mail-notification"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by jaikzelf on 2009-09-04
I installed [ mail-notification ] through Synaptic
Went : System-Preferences-Mail Notification and filled out the necessary data concerning UID's/Passwd's
Gmail and my POP3 accounts work fine
Yahoo!Mail produces [ unknown fetchyahoo failure ] even after installing fetchyahoo by sudo apt-get install fetchyahoo or by Synaptic

Looking on the net I found only that I needed fetchyahoo installed but to no avail.
One post mentions that one needs a paying Yahoo account to be able to use fetchyahoo ???

Anybody any ideas

---

### Post by kerry_s on 2009-09-04
are you using the free yahoo mail? the free does not come with pop unless you hack it. then you can set it up for pop.
[http://picobit.wordpress.com/2009/04/10/yahoo-mail-free-pop-access/](http://picobit.wordpress.com/2009/04/10/yahoo-mail-free-pop-access/)

---

### Post by stevo1977 on 2009-10-18
I followed the directions on the site listed above (thanks, kerry_s) and have turned on POP3 access for my Yahoo account.  I also switched back to 'Classic' mode (another thread suggested this).  I then went back and completely uninstalled Mail Notification and fetchyahoo and reinstalled them.

I am still getting the same "unknown fetchyahoo failure" when it tries to check my mail.  Any other ideas or helpful hints?  Thanks.

---

### Post by JMLM70 on 2010-11-29
I had a problem with my pop3 accounts and solved it by putting the port on front of the pop server, like: "pop.server.domain:123". Just google for yahoo ports and give it a try...

---

### Post by I2k4 on 2011-04-24
This set up works for me with a (paid) Yahoo Plus account - I had the same "fetchyahoo" problem with a secondary free Yahoo account, but can forward its mail into the paid account:

General:  
Mailbox type		POP3

Account			
Server			plus.pop.mail.yahoo.com
Username		its.me
PW			pw

Connection
Type			Standard Port 110
Authentication		Autodetect

Details
Name			its.me

If there is a way to get the free yahoo mail into the notification app it would be nice to know.  (No problems with a Google Gmail account.)

---

