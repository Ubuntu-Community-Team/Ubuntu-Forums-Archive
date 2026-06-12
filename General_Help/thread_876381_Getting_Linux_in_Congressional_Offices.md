---
title: "Getting Linux in Congressional Offices"
date: 2008-07-31
forum: General Help
---

### Post by ultrapuma on 2008-07-31
Without going into too much detail about my job, but I'm in a unique position to get a full Linux environment set up in various congressional offices.
Ive already worked out most of the details and almost everything that they need come in the base install. 

Basically, the two things Id have to work out is getting an outlook type software (it needs to be as close to outlook as possible AND be fully integrated with exchange) and some sort of black berry integration (wine doesn't seem to support it).

Unfortunately, I'm no Linux developer. So I need the help of you guys, the largest Linux community on the internet to help by spreading the word, building support for this, and encouraging development.

Getting Linux in just one congressional office is a HUGE opportunity for the community to finally be taken seriously in the market. We all know that its basically MADE for office environments but we need to take steps to get it out there. And I think that getting a congressional office or two would get digg and reddit attention in a heartbeat. Then its only a matter of time before larger new outlets hear about it.

Before I write up my proposal I'd like to work out those last two kinks. So what Im asking, is spread the word and gain support. This is more than a dream, its completely achievable goal that I need to see happen.

---

### Post by rbmorse on 2008-07-31
Evolution with exchange connector will take care of the Outlook clone part...if you can figure out how to make the crackberry part work, I'd love to hear it because I'm facing the same problem here.

---

### Post by bodhi.zazen on 2008-07-31
For replacing outlook I suggest you look at Thunderbird. You can install thunderbird on Windows and try it out b4 you migrate to Linux.

You might also want to have people convert from IE -> firefox

Nothing quite beats being familiar with these applications when you introduce Ubuntu.

This thread may help with blackberry : 

[http://ubuntuforums.org/showthread.php?t=190938](http://ubuntuforums.org/showthread.php?t=190938)

Next step, plan for migration, expect to migrate in stages.

---

### Post by rbmorse on 2008-07-31
You're not going to get people who are (or believe they are) dependent on Outlook's scheduling and group coordination features to settle for Thunderturd.  Mail is the smallest part of the equation.

---

### Post by bodhi.zazen on 2008-07-31
I guess it depends on the needs of the OP.

All the same, no need to use that kind of language rbmorse.

---

### Post by rbmorse on 2008-07-31
Sorry, it was a typo, honest.

---

### Post by DGortze380 on 2008-07-31
> **rbmorse said:**
> You're not going to get people who are (or believe they are) dependent on Outlook's scheduling and group coordination features to settle for Thunderturd.  Mail is the smallest part of the equation.

You can add an Outlook type scheduler to Thunderbird.

---

### Post by 3rods on 2008-07-31
I think what he means is, basically, the Congressional offices already have M$ Exchange as part of the infrastructure and working a rack full of servers in to the deal is not an option at this point. Unless I'm wrong, in which case I'd check out this:

[http://www.open-xchange.com/en/products/open-xchange-express-editon-en/webmail]("http://www.open-xchange.com/en/products/open-xchange-express-editon-en/webmail")

When you find the email client that integrates with M$ Exchange server, provides the same scheduling, meeting requests and mail features as Outlook 2003 or 2007- call me and I'll buy you a 6 pack of whatever beer you want. 

Sorry folks, I love Thunderbird and use it at home and on my flash drive, but it just doesn't cut it in the workplace.

---

### Post by rbmorse on 2008-08-01
In additional to the functional requirements you might check with the Sergeant at Arms' office and see if there any special administrative, legal and security certification requirements for software. 

I know the archiving and accountability requirements are pretty stiff on the Executive side, but I'm not sure what (if anything) is required on the Hill.

---

### Post by ultrapuma on 2008-08-05
Went out of town for a bit... but I already found a workaround for the blackberry issue.


Yea, mail alone isnt enough. they need contacts, and a decent scheduling app.  The house is in recess now so Im going to start conducting surveys to see what feature they NEED, what they like but could do without, and what they use a good deal.

I dont use outlook for anything other than setting up meetings and getting mail so if anyone here has some good survey questions have at it.


Ive had offices approach  me in the past about getting a linux server set up and I know other offices have linux servers, sooooooo this isnt that far fetched an idea!

---

### Post by ByteJuggler on 2008-08-05
> **3rods said:**
> When you find the email client that integrates with M$ Exchange server, provides the same scheduling, meeting requests and mail features as Outlook 2003 or 2007- call me and I'll buy you a 6 pack of whatever beer you want.

So Evolution with the [Exchange connector]("http://www.go-evolution.org/Exchange_Architecture") doesn't cut it then?  (Or alternatively, possibly Evolution -> [Brutus server]("http://www.42tools.com/node/1") + Exchange server.  Also keep an eye on [OpenChange]("http://www.openchange.org/index.php?option=com_content&task=view&id=15&Itemid=49") )

---

### Post by mike2357 on 2008-08-05
I'd like to add another perspective.  If I understand things correctly, you're about to embark on a major Information Technology deployment in a critical organization and you're getting your consulting advice from an online forum, skilled as it is.

You may be biting off more than anyone could chew without some serious consulting assistance.

Whatever you do, take it slowly.  A gradual deployment is easier on everyone's nerves, and will allow you to correct errors more quickly.  Also be sure to have a failsafe strategy, so if you go to production and things don't work out you can revert to the old system and then figure out what went wrong.

I hope I don't sound like I'm down on Linux (I love it) or anyone's advice, but it's in your interest to make sure nothing is overlooked.

---

### Post by ultrapuma on 2008-08-05
I mean, were not going to jump right in. Baby steps of course. I have a couple offices willing to give it a shot.

First step: an intern machine. Maybe a staff assistant as well. Revitalizing their old PCs is at the top of my list tho.

---

### Post by Ingenue on 2008-08-05
You might want to get in touch with your local LUG, Linux User Group. Most likely you can Google: Linux User Group (your town),(your state). They are a wealth of information and it could end up being someone you can talk to in person. Maybe they even have knowledge of a large office that has migrated and you can learn from their mistakes. You never know...

---

