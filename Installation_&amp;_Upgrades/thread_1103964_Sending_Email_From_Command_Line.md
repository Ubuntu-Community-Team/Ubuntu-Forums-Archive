---
title: "Sending Email From Command Line"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by mgarl10024 on 2009-03-23
Hi all,

First time post.  I'm quite new to Linux so please be gentle!

In short, I'm trying to set up **email from the command line** so that I can be notified in the event of hardware issues (e.g. a drive failure in my RAID1 array).  I've got smartmontools monitoring the drive ok, now just the email sending bit to do...

I started off trying **ssmtp** and found it easy to set up and get working, however I think I need something slightly more robust.  If ssmtp cannot send your mail right then (so, network issue, internet problem, or even on boot where it is initialised before the network) it fails and I wouldn't know there was an issue.
What I need is it to retry continuously until it gets through (perhaps trying every few minutes or so).

Some forums recommend **exim4**, but that seems overkill for what I need.  The manuals also look baffling.  

Some forums recommend **sendmail**.  The config also looks quite complicated, and it slows down the boot of my machine by 10-15 seconds!  Just feels overkill again.

I'm guessing there must be something lightweight out there.  I don't need anything fancy, I don't need mailboxes, I don't want persistent (database) queues, just something light, in memory, that keeps trying to send my mail instead of giving up first time.   Something like ssmtp with a queue would be ideal, and ease of configuration is a bonus!

Suggestions welcome...  :)

Thanks in advance,

MG

---

### Post by PhrankDaChickenGeek on 2009-03-23
I do it with Mutt and an external smtp email server 

```
sudo apt-get install mutt
``` 


Edit the muttrc configuration file accordingly: 
```
nano ~/.muttrc
``` 

Edit (You'll only need SMTP stuff for sending): 
```
 
set pop_user = "EMAIL@WHEREVER.com" 
set pop_delete = yes # We'll delete the messages once we download them 
set pop_pass = "EMAIL PASSWORD" 
set pop_host = "MAIL.WHEREVER.COM" 

set smtp_url = "smtp://USERNAME@mail.WHEREVER.com:PORT/" 
set smtp_pass = "EMAIL PASSWORD" 
set from = "EMAIL ADDRESS" 
set realname = "WHATEVER YOU WANT" 
``` 

Test and make sure you can send a receive emails from within Mutt. "G" to check email, "m" to send 


Send an email via the command line 
```
echo "message body" | mutt -s "subject" user@mail.com
```

---

### Post by mgarl10024 on 2009-03-28
Hi PhrankDaChickenGeek,

Thanks very much for your response.

You would not believe the amount of grief that sending emails from the command line has caused me (a Linux newbie).  I was thinking that sending emails would be sooo simple as it's such a common thing to do, but boy was I wrong.

As an update,
I tried ssmpt - but it wasn't robust (explained earlier).
I tried sendmail - but that was a full blown mail server and slowed my machine up no end.
I tried exim - and that really looked promising - was easy(ish) to set up and promised queues.  However, apparently with mail, the handshake is encrypted but the email isn't.  But with my mail server, the whole communication is encrypted (ssl) and exim said that was "non standard" and wouldn't work with it.  To get around that, I needed to put stunnel on to set up a secure tunnel....  and this was just too much.

Perhaps mutt is the answer...?

In a move that will really appaul the Linux gurus, I resorted to Java (I'm a dev).  In a few minutes, I wrote a quick class, using the JavaMail API, which sent my email secured.  Job done.  This is how easy it should be.  
I'm thinking this may be the way I stick to, as I am not sure I can face the pain of losing another evening to something that should be so easy!  :)

Thanks once again,

MG

---

### Post by IcarusR on 2009-07-23
Hi, if you are interested I use a command line email tool for raid array status notification. 
 sendEmail [http://caspian.dotconf.net/menu/Software/SendEmail/]("http://caspian.dotconf.net/menu/Software/SendEmail/")
Its a Very simple program to use, highly recommended.

---

