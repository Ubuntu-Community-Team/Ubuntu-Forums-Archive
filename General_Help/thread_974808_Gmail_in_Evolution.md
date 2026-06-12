---
title: "Gmail in Evolution?"
date: 2008-11-07
forum: General Help
---

### Post by TheHerb on 2008-11-07
I open evolution put in the pop setting, make it pop.gmail.com and then smtp.gmail.com and my login info but i can't send or recieve emails :S how do i fix it?

---

### Post by Quarg on 2008-11-07
Make sure that you told it that they took encryption (the pop and smtp servers) below the "server" part I think it is SSL encryption. Make sure the ports are also set correctly. Here's a good looking tutorial: [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/41552-complete-guide-using-gmail-thunderbird-mozilla-mail-evolution-kmai.html]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/41552-complete-guide-using-gmail-thunderbird-mozilla-mail-evolution-kmai.html")

---

### Post by fragos on 2008-11-08
incoming should be imap.gmail.com:993 and outgoing smtp.gmail.com:465. There's help in Gmail's settings.

---

### Post by Chunky Dunk on 2008-11-08
This may be of some help... [http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/](http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/)
and
[http://mail.google.com/support/bin/answer.py?answer=13287&topic=12810](http://mail.google.com/support/bin/answer.py?answer=13287&topic=12810)

---

### Post by rlunger on 2008-12-12
> **TheHerb said:**
> I open evolution put in the pop setting, make it pop.gmail.com and then smtp.gmail.com and my login info but i can't send or recieve emails :S how do i fix it?

I got gmail & evolution to work with these settings:

Incoming:  server type = pop3
           server = pop.gmail.com
           username = [email]myaccount@gmail.com[/email]
           authentication type = password
           secure connection = ssl

Outgoing:  server = smtp.gmail.com:25
           secure connection = tls
           authentication type = plain
           username = [email]myaccount@gmail.com[/email]

Good Luck.

---

