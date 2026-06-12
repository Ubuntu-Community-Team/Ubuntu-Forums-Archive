---
title: "[SOLVED] Pidgin and yahoo connection solution (Maybe)"
date: 2008-11-06
forum: General Help
---

### Post by pPrdrm on 2008-11-06
After I've installed Ubuntu 8.10 I had this problem with Pidgin and Yahoo, it wouldn't login unless after a lot of attempts, giving me an error message:

[B]"[account name] disconnected.
Could not establish a connection with the server:
Error resolving scs.msg.yahoo.com
Name or service not known".[/B] 

I've tried many thinks that where suggested in these Forums, for e.g. unistalling and reinstalling Pidgin, with no success. Then I read the error message more carefully and I saw that it had to be something with the resolving of the server address "**scs.msg.yahoo.com**". So I pinged "**scs.msg.yahoo.com**" and it gave me an error, but when I pinged "**66.163.181.173**", which is the numeric address of yahoo's server, there it was.

So, the solution that worked for me, and hadn't failed me yet, is this: In the "**Acounts**" menu choose your yahoo account and select "**Edit Acount**". In the new window that will appear named "**Modify Account**" in the "**Advanced**" tab look for an entry named "**Pager server**". By default its value should be "**scs.msg.yahoo.com**". Change it to "**66.163.181.173**"
If this works for you too, please tell me so I can mark this post Solved and help other people that have the same problem.

---

### Post by realn on 2008-11-07
Maan, you're a wizard. Thanks a lot, it worked 100%.
Anyway, yahoo starts to suck big time. I had a shortage of about 1 month on one of my e-mail accounts. I should gradually get rid of them, don't want my e-mail to be lost because of "cost reductions", "upgrades" and stuff. And they customer care is 0. In fact it's less than 0, is on the negative side. I was sending mail with my problem, and they were answering with surveys about how satisfied I was about their services. Now, that's really something.

---

### Post by pPrdrm on 2008-11-08
Hey there realn,
I am glad it worked for you too. I know it's very frustrating when apps that used to work fine stop to function with no apparent reason. But I don't think that we can blame Yahoo for trying to make a living in the cruel world of High Tech market. And to be honest, I don't like the way that google is coming up to become a monopoly in this area. I think I will stay with Yahoo for as long as I can.

---

### Post by toller99 on 2008-11-08
I just ran into this exact issue this morning.  I did, however, do some hardware upgrades on my home network.  I think it might be the new router causing problems, but I wanted to say thanks because typing in the IP address fixed the issue.  I'm assuming that it is a DNS issue somewhere along the way.  Anyways, thanks for the solution.

Steve Rock
[EMAIL="srock@saurette.com"]
[/EMAIL]

---

### Post by pPrdrm on 2008-11-10
Since this proved to be useful for at least 2 people (3 plus me) I'm marking this thread as Solved. Have fun.

---

### Post by Narvinye on 2008-11-18
This worked for me as well.  Thank you!

---

### Post by ppe on 2008-11-19
Worked for me as well. Thanks!

---

### Post by nguchet on 2008-11-19
omg cool cool, pidgin works like a charm thanks a lot pPrdrm

---

### Post by pPrdrm on 2008-11-20
You are all very welcome! It's nice to know that this worked for all of you too. Thank you for thanking me. :)

---

### Post by DC@DR on 2008-11-21
The trick works for me also, even when I ping scs.msg.yahoo.com, it results unknown host error, weird :-(

---

### Post by psychomichael on 2008-11-21
Thanks! It's nice to have found a quick solution.

---

### Post by NWAdawg on 2008-11-22
Thanks, That fix did the job.

---

### Post by kytribefan21 on 2008-11-22
I have been looking for a solution to this for several weeks and finally found this post.  Mostly I have looked on the pidgin help site, to no avail.  Thanks for the post and I am now back online!

---

### Post by kpothi on 2008-11-23
Hi pPrdrm,

Thank you so much buddy. I had the same issue today. I solved after seeing this post.

Thanks again,

Pothi.

---

### Post by pcm_man on 2008-11-23
This problem has been bothering me on and off for the last 6 months since I converted from Windows XP to Ubuntu.  I tried to find a solution once but all I knew for sure was that the problem was a network issue with Pidgin since I could use Yahoo IM just fine Windows running under VirtualBox.

THIS WAS A WONDERFUL SOLUTION THAT HAS CONTINUED TO WORK.   I would advise that if the problem comes up again ping scs.msg.yahoo.com and see if the IP address has changed and use that new address.

I hope Pidgin will fix this problem in a future release.

---

### Post by spcwingo on 2008-12-04
Worked like a charm!  Thanks a million...this was driving me crazy.

---

### Post by stolenorgans on 2008-12-05
Didn't work for me. Still can't connect to yahoo. :/

---

### Post by spcwingo on 2008-12-05
> **stolenorgans said:**
> Didn't work for me. Still can't connect to yahoo. :/

Try this address: 68.180.217.32

---

### Post by stolenorgans on 2008-12-05
> **spcwingo said:**
> Try this address: 68.180.217.32

Still does not work.

---

### Post by pissedoffdude on 2008-12-05
> **stolenorgans said:**
> Didn't work for me. Still can't connect to yahoo. :/

Yeah, I'm having the same issue too.  But it's not just pidgin.  Meebo and kopete are having the same problem, while the official yahoo ones actually work.

---

### Post by spcwingo on 2008-12-05
Hmmm...mine has now died too.  Anybody have any other suggestions?  I have tried these addresses so far:

68.180.217.32

66.163.181.173

66.163.181.166

scs.msg.yahoo.com

---

### Post by mr.lee on 2008-12-05
Hey I don't get it....

Did I should click the option box Yahoo Japan?

---

### Post by HousieMousie2 on 2008-12-05
This worked for me in Kopete... Yahoo is having 'issues.'

[http://ubuntuforums.org/showpost.php?p=6267682&postcount=5](http://ubuntuforums.org/showpost.php?p=6267682&postcount=5)

Edit your account settings to over ride the default server for Yahoo.

---

### Post by johnlvs2run on 2008-12-06
I've been using Pidgin and Kopete on Sabayon and both have been fine.

Kopete stopped connecting a week ago, and Pidgin stopped connecting today.

As has been mentioned, the issue appears to be with Yahoo.

---

### Post by spcwingo on 2008-12-06
The server cn.scs.msg.yahoo.com works for me, as posted above.  Yahoo needs to get their stuff together.

---

### Post by Pete051 on 2008-12-06
Worked for me too. one odd thing though when I eventually got a connection I found I'd gained a load of dubious female contacts that I'd never heard of.
very odd
Pete

---

### Post by prshah on 2008-12-09
I ran into the same problem as well, but instead of changing the server entries in pidgin, I added a line to my /etc/hosts file```
66.163.181.170 scs.msg.yahoo.com
```

---

### Post by indiana_crook on 2008-12-13
Oh the brilliance of the Linux society!!  Thank you so much works great!

---

### Post by pPrdrm on 2008-12-13
Wow! :shock:
I never could imagine that such a small programming hiccup could affect so many people. I am glad I was able to help some of you to find peace of mind again regarding this problem. Thanks again to all of you for thanking me. Cheers. :grin:

---

### Post by never2far on 2008-12-13
It worked for me too. Thank you

---

### Post by jahin on 2009-06-12
thanks.
also worked for me.

again thank you very much for the solve.:D

---

### Post by vahnx on 2009-06-12
Didn't even know this was a global problem even. Pidgin or Yahoo should fix this :)

---

### Post by ekss on 2009-06-18
thank you

---

### Post by chrone on 2009-06-18
thanks a lot mate. :)

i don't know which to blame here, is it pidgin (ubuntu 8.04 and 9.04) or yahoo server?

the funny thing is gaim (ubuntu 7.04) didn't have this problem at the very same time. :(

---

### Post by stans on 2009-06-19
I'd like to offer thanks also.

---

### Post by colau on 2009-06-19
> **prshah said:**
> I ran into the same problem as well, but instead of changing the server entries in pidgin, I added a line to my /etc/hosts file```
66.163.181.170 scs.msg.yahoo.com
```
Same problem.
Replaced scs.msg.yahoo.com with 66.163.181.170 in Managed Account>Modify>Advanced and it worked.

---

### Post by StarCruiser on 2009-06-19
Fixed it for me as well.  Thanks, this has been driving me nuts! :D

---

### Post by causeitsme on 2009-06-19
Thanks! Worked for me.:popcorn:

---

### Post by nefrin on 2009-06-19
adding the line to the/etc/hosts file worked like a charm for me as well, only had to restart Pidgin, not the system.

Running Ubuntu 9.04

---

### Post by Therion on 2009-06-19
Lots of threads about this problem...

One more solution here:

[http://ubuntuforums.org/showpost.php?p=7480983&postcount=21](http://ubuntuforums.org/showpost.php?p=7480983&postcount=21)

---

### Post by alphacrucis2 on 2009-06-20
A lookup on the ptr record for 66.163.181.170 returns:

cs105.msg.mud.yahoo.com

So you could use that name instead of the IP address. No guarantee that yahoo wont change their dns again though.

---

### Post by okolnost on 2009-06-20
I solved my issue using your help, thanks a lot.

---

### Post by paco85 on 2009-06-20
HEY Thanks .... It has worked for me as well... that was really annoying.... i had to send it from my e-mail page.... Thanks for the info.... NEVER KNEW that forums are soooooo helpful!:KS

---

### Post by lamnk on 2009-06-20
> **pPrdrm said:**
> So, the solution that worked for me, and hadn't failed me yet, is this: In the "**Acounts**" menu choose your yahoo account and select "**Edit Acount**". In the new window that will appear named "**Modify Account**" in the "**Advanced**" tab look for an entry named "**Pager server**". By default its value should be "**scs.msg.yahoo.com**". Change it to "**66.163.181.173**"
If this works for you too, please tell me so I can mark this post Solved and help other people that have the same problem.
It does help ! Thanks a lot.

---

### Post by ktechman on 2009-06-21
pPrdrm,

       Thank you for your work on this one

                                Ktechman:D

---

### Post by nghalion on 2009-06-21
Like a ChaAaAaArm :o
Thanks man..

---

### Post by wncben on 2009-06-23
Changing your server is a temporary bandaid as yahoo is going through bit by bit updating servers and phasing out the older protocols that the version of pidgin that ships with ubuntu uses.  As yahoo "improves" their servers the server patch will not work.  Instead, update pidgin.  the newest version fixes the issue and pidgin has set up a ppa so that ubuntu will automatically update it. I posted instructions here:  
[http://ubuntuforums.org/showpost.php?p=7504859&postcount=10](http://ubuntuforums.org/showpost.php?p=7504859&postcount=10)
~Cheers

---

### Post by TFrog on 2009-06-23
This appears to have resolved the issues I was having with Kopete 0.70.4 under KDE 4.2.4 and Jaunty Jackalope :D

---

### Post by undoIT on 2009-06-23
Does anyone know if there is an update yet for Kopete that solves this? None of the Yahoo IPs I have tried are working anymore.

---

### Post by jesterthejedi on 2009-06-23
Its broken now.

---

### Post by Sentience on 2009-06-23
Yesterday it was fixed but today its broken again and changing the IP does not help anymore.

I just reinstalled Pidgen and it said some files could not be uploaded. I have pidgen again after some other instructions that were supposed to update it ended up deleting it, but yahoo is still not working, even though I just downloaded it.

---

### Post by ppyo on 2009-06-25
> **Sentience said:**
> Yesterday it was fixed but today its broken again and changing the IP does not help anymore.

I just reinstalled Pidgen and it said some files could not be uploaded. I have pidgen again after some other instructions that were supposed to update it ended up deleting it, but yahoo is still not working, even though I just downloaded it.

Check this post, it has the answer that works:

[http://ubuntuforums.org/showpost.php?p=7480983&postcount=21](http://ubuntuforums.org/showpost.php?p=7480983&postcount=21)

Yahoo messed it up AGAIN! :mad:

---

### Post by undoIT on 2009-06-25
Yes, this server has been working well for me over the past couple days:

cn.scs.msg.yahoo.com

---

### Post by kxmas on 2009-06-29
FYI, Kopete has been patched to use the new logon scheme 

[https://bugs.kde.org/show_bug.cgi?id=197104]("https://bugs.kde.org/show_bug.cgi?id=197104")

---

### Post by eugen_nicoara on 2009-06-30
Try that: [http://www.kabatology.com/06/22/pidgin-2-5-7-for-ubuntu-fixes-yahoo-login-issues/]("http://www.kabatology.com/06/22/pidgin-2-5-7-for-ubuntu-fixes-yahoo-login-issues/")

---

