---
title: "Specific website not detecting Java plugin"
date: 2008-10-04
forum: General Help
---

### Post by josefski on 2008-10-04
I was wondering if someone could help me solve a mystery:

I have Java installed with Firefox 3 and the Java website verifies that it is there and works, it's just a version behind. (When I upgraded versions, all hell broke loose, so I had to revert) There is one website that chronically does not detect that the plugin is there. It's the same site that doesn't work with firefox and java on My XP box. But this same portal does work on the computers running firefox at the I work in. 

This is the offending url:[http://esis4.nwpartnership.org:7777/forms/frmservlet?config=esis](http://esis4.nwpartnership.org:7777/forms/frmservlet?config=esis)

If you access it and it works, you'll see logon prompt for eSIS, the bane of many a teacher's (including mine) existence. But for me, it says I don't have the plugin installed, but about:plugins indicates that it is indeed installed and java.com assures me that it is working.

Any clues?

---

### Post by Crafty Kisses on 2008-10-04
What are the results of this command?
```
java -version
```

---

### Post by josefski on 2008-10-05
I get this:

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

But I realize that this is one update old. I think there could be something else going on with this specific website, because it's the only one that gives me trouble. It isn't that it says the version is too old, it simply refuses to acknowledge it is there. It did the same exact thing when I upgraded to Java 1.6.0_07, except that version caused havoc with websites that had previously worked, so I downgraded. 

I really doubt that it has anything to do with the version.

Thanks a lot for replying!

---

### Post by xreaper on 2008-10-05
hey, I tried the link on my web browser (same as yours) and it turns out that there weren't any plugins to be able to be installed for my pc either. if it helps, you might want to try updating java to the latest version. shouldn't be a problem to find in the repositories, just search "jre 6".

---

### Post by ellgor on 2008-10-05
Hi,

I have Gutsy with ONLY j2re-1.4 installed (mainly for poker sites) I tried the link you gave and had no problem accessing the site, from past experience it seems that this j2re-1.4 is like the swiss army knife of plugins, hope this of help to you.

Regards, Ellgor.

---

### Post by josefski on 2008-10-05
Where did you find j2re 1.4?

---

### Post by wphampton on 2008-10-14
Hi josefski,

We use eSIS at our work as well and when I try to access the application from my Ubuntu 8.04 Hardy workstation I receive the same errors as you do.  I believe what is happening is not that you need to update you JRE version, but rather you have a version much newer than the "approved" version.

If you look at the source code of the page that you gave us the link for, you'll see multiple mentions of eSIS needing JRE Plugin 1.4.2_06 ("_06" means builds 06 in Java world...).  So the browser is actually being told not to load up any other Java plugin except that one specific version...ridiculous.  Sadly, that's many, many versions ago.  

I know of two fixes I've actually used in the past successfully, although I am out searching again today because I've lost my notes and code for accomplishing this and am looking to recreate this solution.

Solution #1: Actually download and install the Java 1.4.2 JRE and plugin from the Java archive ([http://java.sun.com/products/archive/](http://java.sun.com/products/archive/)) and create a symbolic link in the browser plugin directory to the newly installed version.  I was working on this today though and having trouble nailing down the proper plugin directory.  Actually the JRE 1.4.2_06 I was downloading from Java.com was not running properly.  But I honestly have had this working in the past year or two.  If I remember correctly I actually had two different Java Plugins installed in Firefox.

Solution #2...hack: In Firefox you can use the Greasemonkey extension/addon to literally modify the eSIS HTML code before the browser renders it to make it think that instead of needing the 1.4.2_06, it actually needs the version you have.  Even though it's not "approved" to run eSIS, I had no problems in the past, although that was with JRE 1.5.xx, but I'd imagine 1.6.xx would probably also be fine.  Again, I've lost that script somewhere but am looking to recreate one of these solutions so that I don't have to remote into a WindowsXP box to get to eSIS.

Hope this helps...it's really just acknowledging your problem I know, but maybe it gets you on the right track until I can put together the pieces again...

Cheers!

Wes

---

### Post by josefski on 2008-10-23
Thanks for the info! I know that the guy in our building wrote an executable script that goes on the xp desktop and that is the only way firefox is able to access fecis from in xp. I'm guessing this script must have that language written into it. Installing the older java turned into an all day disaster of commenting out code in binaries and eventually messing my computer up so badly that I had to reinstall my op system. I'll see if I can hack the open the script our guy wrote and if I find the magic code, I'll post it here.

Cheers, 

Josef

---

### Post by jamesstansell on 2008-10-25
This page seems to start up ok, using sun java 6u10 on hardy.

[http://esis.mesd.k12.or.us/](http://esis.mesd.k12.or.us/)

(click on the login button)

I think the administrator must have made a minor change that lets the applet load.

---

### Post by josefski on 2008-10-26
That's what I had found as well. Unfortunately, my school district is for some reason unable to access eSIS through that portal. Different contract or something I guess. On a note totally unrelated to this post: If you are working in a district considering using eSIS, *please* have them interview the end users, teachers, from districts that have it. It's pure garbage.

Enough diatribe. 

I downloaded greasemonkey, but I don't yet feel comfortable writing code, just modifying existing code.

Is there a free html source code viewer out there that works well? I'd like to see the website code myself so that I would even know what I need to modify. 

Adding to this mystery: Opera and Konquerer connect to the aforementioned site with no problem. Trouble is, they both seem a little challenged when it comes to detecting proxy settings, so I still can't use ol' linuxtop at work(cus, you know, proxy servers are kind of common thing these days). 

Still, overall this linux stuff has been a lot of fun,

Thanks again for all your help!

---

### Post by jamesstansell on 2008-10-26
Firefox 3 is the free html source code viewer that I use the most.  Choose View -> Page Source to see the source.  When you do that you'll see that both pages are nearly identical

Who is the webmaster for esis4.nwpartnership.org?  Perhaps he would change (fix!) the html if he knew there was a problem.

-james.

---

### Post by josefski on 2008-10-27
> **jamesstansell said:**
> Firefox 3 is the free html source code viewer that I use the most.  Choose View -> Page Source to see the source.  When you do that you'll see that both pages are nearly identical

Who is the webmaster for esis4.nwpartnership.org?  Perhaps he would change (fix!) the html if he knew there was a problem.

-james.

You would think. That's why all who use eSIS often refer to it as Fecis, or eSUCKS, precisely because they don't respond to obvious problems like this one. I'm slowly introducing the idea of having just one open source writing lab (conveniently located in my classroom) made up of old hardware. It's really, really hard to sell free software to school boards. Our techies have tried again and again. 

Honestly, I don't see how an open source SIS could be any worse than this garbage. 

I love venting on the internet. 

Thanks for all your help guys.

---

### Post by josefski on 2009-02-05
Okay, with the magnanimous help of the brilliant system administrator at my school, I have a pseudo solution to this. So the problem, as earlier noted, is that the stupid Oracle program is looking for the wrong version of Java. The first thing my admin tried was changing line 13 in pluginreg.dat to application/x-java-applet;jpi-version=1.4.2_06:java::$ But if you do this, first you have to modify the right file, which is under home/<username>/.mozilla/firefox/<random profile folder>/pluginreg.dat 

This next part is the reason why it isn't a real fix, you then have to chmod 400 pluginreg.dat which removes write permission for firefox because otherwise firefox (version 3) mysteriously changes it back. You can imagine this may cause a problem the next time you update firefox or try to install another plugin. 

But, after all this, I finally have eSIS working on two ubuntu linux computers. Hooray!

---

