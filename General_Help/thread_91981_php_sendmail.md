---
title: "php sendmail"
date: 2005-11-18
forum: General Help
---

### Post by jabb0 on 2005-11-18
heya,

I have setup my ubuntu box with apache-php-mysql as described in the ubuntuguide. :p

however when i try to use the mail() function in any of my php scripts nothing happens. :confused:
I cannot seem to find any kind of error msg, and this would be so handy as i develop code on my local box, and as it stands, to test any mail() functinality i have to upload to a remotely hosted server, which can get extremely tedious. :-x

How can i set it so that the mail() function will send an email from within a php script runnin on my local machine? :?:

---

### Post by mgor on 2005-11-18
check /var/log/mail.log.

you want to send mail to a local account or via Internet?

i *think* postfix is installed when you install mysql or some php package, so check /etc/postfix/main.cf and add your ISP's mailserver to 'relayhost'. you might also want to change /etc/mailname to a real domain.

try it out and check the above log for errors.

---

### Post by jabb0 on 2005-11-18
Ok i have added my ISP's mailserver to 'relayhost'.
Then i have reset my php.ini file to default.

My mail.log entries started on 11NOV and ended on 14NOV this is 18NOV, still no new entries after changes.
However mail.info did some complaining before, but now seems happy as there is the following entry every time i send a mail :
```
Nov 18 20:42:18 localhost postfix/pickup[14929]: 2E9D6207226: uid=33 from=<www-data>
Nov 18 20:42:18 localhost postfix/cleanup[16051]: 2E9D6207226: message-id=<20051118204218.2E9D6207226@localhost.localdomain>
```
i take this is a good thing, could u explain a litlle about what it means plz?

however there still seems to be a slight problem in that i am not receiving any emails yet?

cheers

PS i know things have definitly moved forward on this solution as previously the mail function was always returning false, now its giving a true... thats bound to be good :D

---

### Post by mgor on 2005-11-18
hm, was there only two lines in the log? should be more, please post atleast the last 10 lines.

how long have you waited? it can take couple of minutes before you'll recive any mail.

---

### Post by jabb0 on 2005-11-18
sorry

```
Nov 18 20:39:21 localhost postfix/pickup[14929]: 3C38520721C: uid=33 from=<webmaster@example.com>
Nov 18 20:39:21 localhost postfix/cleanup[15996]: 3C38520721C: message-id=<20051118203921.3C38520721C@localhost.localdomain>
Nov 18 20:39:21 localhost postfix/pickup[14929]: 4AD4920721D: uid=33 from=<www-data>
Nov 18 20:39:21 localhost postfix/cleanup[15996]: 4AD4920721D: message-id=<20051118203921.4AD4920721D@localhost.localdomain>
Nov 18 20:39:23 localhost postfix/pickup[14929]: 3E0AF20721E: uid=33 from=<webmaster@example.com>
Nov 18 20:39:23 localhost postfix/cleanup[15996]: 3E0AF20721E: message-id=<20051118203923.3E0AF20721E@localhost.localdomain>
Nov 18 20:39:23 localhost postfix/pickup[14929]: 4360920721F: uid=33 from=<www-data>
Nov 18 20:39:23 localhost postfix/cleanup[15996]: 4360920721F: message-id=<20051118203923.4360920721F@localhost.localdomain>
Nov 18 20:41:23 localhost postfix/pickup[14929]: 6E241207220: uid=33 from=<www-data>
Nov 18 20:41:23 localhost postfix/cleanup[16051]: 6E241207220: message-id=<20051118204123.6E241207220@localhost.localdomain>
Nov 18 20:41:24 localhost postfix/pickup[14929]: 7FF5C207221: uid=33 from=<www-data>
Nov 18 20:41:24 localhost postfix/cleanup[16051]: 7FF5C207221: message-id=<20051118204124.7FF5C207221@localhost.localdomain>
Nov 18 20:41:25 localhost postfix/pickup[14929]: 75276207222: uid=33 from=<www-data>
Nov 18 20:41:25 localhost postfix/cleanup[16051]: 75276207222: message-id=<20051118204125.75276207222@localhost.localdomain>
Nov 18 20:41:26 localhost postfix/pickup[14929]: D51B1207223: uid=33 from=<www-data>
Nov 18 20:41:26 localhost postfix/cleanup[16051]: D51B1207223: message-id=<20051118204126.D51B1207223@localhost.localdomain>
Nov 18 20:41:43 localhost postfix/smtp[16053]: 6E241207220: to=<nobody@jabb0.co.uk>, relay=none, delay=20, status=deferred (Host or domain name not found. Name service error for name=relay.plus.net type=MX: Host not found, try again)
Nov 18 20:41:44 localhost postfix/smtp[16058]: 7FF5C207221: to=<nobody@jabb0.co.uk>, relay=none, delay=20, status=deferred (Host or domain name not found. Name service error for name=relay.plus.net type=MX: Host not found, try again)
Nov 18 20:41:45 localhost postfix/smtp[16061]: 75276207222: to=<nobody@jabb0.co.uk>, relay=none, delay=20, status=deferred (Host or domain name not found. Name service error for name=relay.plus.net type=MX: Host not found, try again)
Nov 18 20:41:46 localhost postfix/smtp[16064]: D51B1207223: to=<nobody@jabb0.co.uk>, relay=none, delay=20, status=deferred (Host or domain name not found. Name service error for name=relay.plus.net type=MX: Host not found, try again)
Nov 18 20:42:15 localhost postfix/pickup[14929]: 6A55E207224: uid=33 from=<www-data>
Nov 18 20:42:15 localhost postfix/cleanup[16051]: 6A55E207224: message-id=<20051118204215.6A55E207224@localhost.localdomain>
Nov 18 20:42:17 localhost postfix/pickup[14929]: EC5EA207225: uid=33 from=<www-data>
Nov 18 20:42:17 localhost postfix/cleanup[16051]: EC5EA207225: message-id=<20051118204216.EC5EA207225@localhost.localdomain>
Nov 18 20:42:18 localhost postfix/pickup[14929]: 2E9D6207226: uid=33 from=<www-data>
Nov 18 20:42:18 localhost postfix/cleanup[16051]: 2E9D6207226: message-id=<20051118204218.2E9D6207226@localhost.localdomain>

```

you can see the last set of entries came in 2s for each email i sent.

wot do you think?

thanx

PS what will changing /etc/mailname to a real domain effect?

---

### Post by mgor on 2005-11-18
let me see the relayhost line in /etc/postfix/main.cf.

---

### Post by jabb0 on 2005-11-18
relayhost = relay.plus.net

which is the same as my evolution smtp setting is, and that is workin no bother.

also why would i change localhost.localdomain in  /etc/mailname to a real domain, when i dont have a real domain to point to it?

---

### Post by mr_niceguy on 2005-11-29
If you'll forgive me, I've had the same problems. Ubuntu is the best desktop going but Fedora certainly never gave me such run-around server wise.

The only way I've found to mail out was using Pear's Mail module and even then to use my ISP's smtp server via Mail's "Factory" method. You can install pear and the Mail module from apt or synaptic.

Would love to hear the real answer to this dilema.

---

### Post by jabb0 on 2005-11-29
Ur not goin to beleive this, but i have it workin and i have completely forgot how - oh gawd im so sorry mate.

It has something to do with postfix, there is a config file with a variable called "relay" which you must set to your outgoing mail server.  The config file had the word "main" in it as far as i can remember.

In my case this was the one from my ISP.

Oh i am such an idiot, cos im gonna have to set that up again someday.  I am not in Ubuntu at the mo, but when i get to it again, ill have a root around and see if i can remember anything... hopefully the Command Console has held onto the commands i entered (it has done every other time ive used it)

If your in a rush you could try googling for Ubuntu + Postfix + Relay.  
I am a little more confident now than at the start of this post, that i can suss this out again mate, at which point ill post back here.

Methinks i followed i walkthrough somewhere.

jees sorry for bein stupid.

---

