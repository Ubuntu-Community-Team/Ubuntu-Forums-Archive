---
title: "Using Gmail as SMTP server Eaton UPS"
date: 2013-01-04
forum: Hardware
---

### Post by incindre on 2013-01-04
Hey All,

I just bought an Eaton Evolution 850VA UPS and I'm very pleased with it so far. I've installed the Eaton Intelligent Power Protector software onto my Ubuntu 12.04 server and connected with USB cable.

The software is great and gives me a fairly powerful web interface.
The problem is though that I want to configure it to send me an email when an event happens (critical battery, loss of connection, etc.) and was trying to get it to work with Gmail's SMTP server (as I couldn't get postfix & dovecot to play nice last time I tried to configure them).

I've dropped a picture in of the Web UI's dialog for this specific option. Can anyone sort out what I've done wrong? (or if it's even possible for this application).
[URL="http://s442.beta.photobucket.com/user/Incindre/library/"]
[IMG]http://s442.beta.photobucket.com/user/Incindre/library/[/IMG][/URL][IMG]http://i442.photobucket.com/albums/qq145/Incindre/UPS1_zps3bddf4ad.jpg[/IMG]

Cheers!

~Incindre

[IMG]http://s442.beta.photobucket.com/user/Incindre/library/[/IMG]

---

### Post by Fahim Abdun-Nur on 2013-01-04
Maybe try port 25?

[http://support.google.com/mail/bin/answer.py?hl=en&answer=78775](http://support.google.com/mail/bin/answer.py?hl=en&answer=78775)

587 vs. 465....can't seem to dig up Gmail help documentation indicating which port to use

---

### Post by incindre on 2013-01-04
I tried Port 25, but that hasn't made any difference.
Theoretically, it should work shouldn't it? I just need to get the details right.

---

### Post by tgalati4 on 2013-01-04
Gmail servers take port 25 with SSL, port 465 with TLS, and port 587 with SSL.  It's possible that the Eaton smtp server uses no encryption and sends the message in the clear.  If that is the case, then you would have to send it to yourself within the machine using dovecot or postfix and then send from that server to gmail using TLS/SSL.

Perhaps an email to Eaton tech support is in order.  We need a good laugh for the day.

---

### Post by Isti2002 on 2013-01-30
mail from EATON:

           "At the moment, all the e-mail notifications we can perform with our softwares and connectivity components use the TCP/IP port 25. Hence, the settings smtp.gmail.com:587 is converted to smtp.gmail.com The coming firmwares (if not exactly the next one, the one after the next one) will include the feature for use of secured SMTP servers (using TCP/IP #587 port). 

For the moment, no possible solution.

Bav  "

Isti

---

