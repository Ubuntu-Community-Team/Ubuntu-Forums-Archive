---
title: "Help setting up a mail server"
date: 2005-11-15
forum: General Help
---

### Post by losslesshead on 2005-11-15
Well, I am trying to set up a mail server in Ubuntu and am having no luck.  I have tried going through a guide at [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) (i just could not get it).  Is there any easier way to set one up?

---

### Post by losslesshead on 2005-11-15
Hello?

---

### Post by brickbat on 2005-11-16
Postfix setup is really a pain but I don't know an easy way. Sorry. I wish I did.

ciao
bb

---

### Post by jliedeka on 2005-11-16
Postfix is fairly easy.  It would help if you tell us what you are trying to do and what isn't working.  Just installing Postfix gives you pretty good functionality out of the box.

     Jim

---

### Post by losslesshead on 2005-11-17
What I am trying to do is set up a mail server (IMAP) that would have webmail (SQUIRRELMAIL).  I just really cannot get it.  I have a dowmain hosted with 1and1.com and I am really unsure about MX Records, etc...

---

### Post by jliedeka on 2005-11-17
I don't actually get mail directly on my box, I use fetchmail to pull it from my ISP.  I know you have to have smtp enabled in master.cf and probably some options in main.cf for the postfix part.  There's some good documentation at postfix.org with recipes for setting things up.

If you want to run Courier IMAP, you need your mail to be stored in Maildirs.  You enable that in postfix in main.cf with "home_mailbox = Maildir/".  You don't have to call it maildir but the trailing slash is a signal to postfix that it is a maildir.

I've been considering running some webmail service but it's sort of overkill for me since I can just as easily SSH in and run mutt.

Some other issues to consider.  When you say your domain is hosted, do you mean you are setting stuff up on a remotely hosted system or are they just registering your domain and providing DNS stuff?

If you are talking about a server in your home and you are connected through cable or DSL, you might have port 25 blocked at the ISP.  You would have to work around that by listening on another port number.  I haven't tried it so I can't tell you all the issues involved.  Also, your outbound mail may need to be relayed through your ISP and you may not be able to use your registered domain name.  That's due to some mail servers using reverse DNS which wouldn't turn up your registered domain.  E.g, I have the domain jimliedeka.com.  I can look that up to get the actual IP address but when I look up the IP I get whatever my ISP, tds.net, uses for residential addresses.  In other words, cable and DSL are not "real" internet connections in the sense of being a peer on the net.

     Jim

---

### Post by casper_2095 on 2005-11-18
[QUOTE=losslesshead]Well, I am trying to set up a mail server in Ubuntu and am having no luck.  I have tried going through a guide at [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) (i just could not get it).  Is there any easier way to set one up?[/QUOTE]

Well, it's a lot of work.  

As you can see from that howto there are a lot of concepts and quite a lot of systems to get going and dancing to the same tune.  You'll need lots of patience, it's not going to happen in one sitting.  I won't hesitate to criticise the howto for providing a vast stream of steps without a single test until its latter parts.  You really need to do small things and test them as you go; that way you'll not only verify what works but gain an understanding of how it works.

You should be able to send an email to yourself. Have you got that far?
```
$ mail your_login_name_here
Subject: Hello
Testing.
.
Cc:
$ tail /var/log/mail.log
Nov 18 17:55:32 localhost postfix/pickup[24773]: 809E3FADC5: uid=1000 from=<you>
Nov 18 17:55:32 localhost postfix/cleanup[26260]: 809E3FADC5: message-id=<20051118065532.809E3FADC5@localhost.localdomain>
Nov 18 17:55:32 localhost postfix/local[26262]: 809E3FADC5: to=<you@localhost.localdomain>, orig_to=<you>, relay=local, delay=0, status=sent (delivered to mailbox)
$ mail
Mail version 8.1.2 01/15/2001.  Type ? for help.
"/var/mail/you": 1 message 1 new 0 unread
>N  1 you@localhost.lo  Fri Nov 18 17:55   14/483   Hello
& 

```

I don't know how squirrel retrieves mail but looks like you'll need to get apache2 up and running, plus mysql, so you're going to be busy for a while.  

Are you sure that "squirrelmail" is the requirement and not simply "ability to check and send email remotely"?

---

### Post by losslesshead on 2005-11-18
Right now I do not even have postfix properly set up, so I cannot send email to myself using it.  Squirrelmail is webmail, it gives you the ability to check email remotely.

---

### Post by SeaWolf on 2005-11-18
You sound like I did at the beginning of the summer.  (OK, I've got ten packages installed and nothing works! Which one's broken? ](*,)) I felt like I was trying to make a pie and the instructions say "Make the crust." but don't tell you how. 

The best advice I found was on the Postfix site itself:  Start small.  

I'd start with the documentation on [www.postfix.org](www.postfix.org).  Start by getting Postfix up and running by itself, accepting and delivering mail for users that have an account on the server by authenticating againist local files.  Make sure you use MailDir's for mail boxes.  Next create a virtual domain with virtual users that don't need an account on the box.  Again, keep authenticating againist local files.  Once that is working, then you can add MySQL or PostgreSQL to the mix and start authenticating againist it.

From there, just keep building, Always doing it one step at a time.

Of course, I couldn't find a single document that tells you how to do this.  I started a *.odt (OpenOffice 2.0) document about how I set up Postfix.  It's extremely incomplete and geared towards Gentoo (which I've used for a while, I've just started using Ubuntu because of the edubuntu project.) but I'll e-mail it to you if your are interested.  If you find it helpful, then maybe I'll keep working on it.

---

### Post by casper_2095 on 2005-11-19
[QUOTE=losslesshead]Right now I do not even have postfix properly set up, so I cannot send email to myself using it.[/quote]
How'd you go with that little test?  It works for the default install.  So if that doesn't go, so far you're suceeding in going backward.

> Squirrelmail is webmail, it gives you the ability to check email remotely. ](*,) 
There are quicker and easier ways to check email remotely than squirrel.  The most obvious is pop/imap, or ssh into the box, or even vnc or a vpn.  What is it about squirrel that makes it the best answer for your needs?  Why not use someone else's webmail? eg fastmail.fm.  Not that I don't think squirrel is a nice and admirable goal.  Just suggesting that given the sounds you're making you're biting off more than you can chew.

---

### Post by Neg127 on 2005-11-19
You might take a look at [http://www.qmailrocks.org/]("http://www.qmailrocks.org/")

It has a very comprehensive how-to on installing and setting up qmail which I think is a better mail server then postfix.  You can all so get a good qmail book/documentation from [http://lifewithqmail.org]("http://lifewithqmail.org").

You do not have to set up qmail with all the options at the qmailrocks setup but it will make administrating the mail server simpler.  It well all so give you some good spam blocking tools, user management, mail analysis, and many other features.

I have used his how to on debian to install qmail and start my familiarizing with it. The main difference between the debian install and the ubuntu install would be ubuntu does not install exim by default like debian.  so you would have to do a couple of changes from there but it should be pretty straight forward.

There are all so lots of other good webmail clients.  [Horde]("http://www.horde.org/") which can be very difficult to install, but it is very feature rich and has many addons.  One of the more recent webmail applications I have run across is [RoundCube]("http://www.roundcube.net/").  It’s more of a modern webmail client and has a pretty good feature base, and it is very visually appealing.  Squirrelmail is all so a pretty good choice depending on the features you require in your webmail application.

I wish you the best of luck and hope you lean a lot from your project.

---

### Post by losslesshead on 2005-11-19
I cannot do anything more with postfix for now (since I am about to leave for a Bar-Mitzvah).  I am going to try again later.  BTW, SquirrelMail is not something that is hard to set up at all, I already have set it up on a shared 1&1 web server.

---

