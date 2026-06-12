---
title: "Trying to get spamassassin to work with ubuntu"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by anthony_audi on 2009-08-18
I downloaded Ubuntu Server 8.04 and installed the gui now it boots up as Xubuntu

Hey guys !
So I'm going to try and make this as simple as possible I hope I get some good information!

I am trying to get a spambox working here for my company. I'm very new to Ubuntu but I think I can get the hang of it pretty easily. 

My problem currently is I can send mail internally and send mail to any external address however I can't receive any mail from external mail addresses like gmail.

I am pretty sure it has something to do with my configuration but I really have no idea where I could have a problem.

From what I can  tell I have the latest versions of

CLAMAV
PostFix
Amavisd-new
Spamassassin

If I knew exactly how to check my versions I would be able to be 100% sure but from what I can tell I added the repositories to my sources.list and when I did apt-get install spamassassin or clamav or postfix or amavis it told me that I had the latest versions. 

Can anyone give me maybe a how-to on how to get mail coming into my inbox?

I did change a few things in the conf files such as spamassassin like
the bayes score I set to 6.3
bayes auto learn = 1


i set to use pyzor
use razor

I didn't  really do MUCH configuration after upgrading I just want to know what files I have to update and what kind of updating i need to do in order to get mail to come in.


Eventually (after I actually do have mail coming in I want to configure apache to connect to my active directory and have my users log into [http://x.x.x.x:8443](http://x.x.x.x:8443) and see whatever spam they are getting)

Can anyone help me out!
thanks!

---

### Post by anthony_audi on 2009-08-18
nothing at all? :(

---

### Post by ptn107 on 2009-08-18
All you need to get spamassasin working is the following:
```
sudo aptitude install spamassasin -y
sudo sed -i 's/ENABLED=0/ENABLED=1/' /etc/default/spamassasin
sudo /etc/init.d/spamassassin start
```

---

