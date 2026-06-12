---
title: "Firefox 3.5"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by Buschbarber on 2009-08-19
I have downloaded and installed Firefox 3.5. The instructions I followed had me install the program in a folder within my Home directory. As such, I have had instances where Firefox 3 launches instead of 3.5, such as when I click on Mail Notification to check my Gmail account.

How should programs like this be installed so that they become the universal default web browser? I opened Preferred Applications and set the path to the Firefox folder in my Home directory, but that did not necessarily prevent the old Firefox from being launched, at times.

Should the old Firefox have been uninstalled, using Synaptic or through Terminal?

---

### Post by running_rabbit07 on 2009-08-20
I did what [this page]("http://www.psychocats.net/ubuntu/firefox") says to do and it installed perfectly.

---

### Post by cygnus-X1 on 2009-08-20
Bump! 

I'm running 8.04 and would like to move to FF 3.5 ASAP. It doesn't appear to be in the Hardy repository yet. So much for the easy way! And, I cannot find anything in the searches I have been doing either. Do any of the gracious gurus have a 'howto' put together for us humble students of the terminal?  [-o<
  
Many thanks in advance!

---

### Post by running_rabbit07 on 2009-08-20
> **cygnus-X1 said:**
> Bump! 

I'm running 8.04 and would like to move to FF 3.5 ASAP. It doesn't appear to be in the Hardy repository yet. So much for the easy way! And, I cannot find anything in the searches I have been doing either. Do any of the gracious gurus have a 'howto' put together for us humble students of the terminal?  [-o<
  
Many thanks in advance!

Follow the instructions in my post above. I am running Hardy on this system and it works great. You just download the FF3.5 from the FF website to your home folder then copy and paste a one line command into terminal. And yes, it was written by one of those gurus, not me.

---

### Post by cygnus-X1 on 2009-08-20
Hi running_rabbit07. Perfect! Many thanks! I must have been still banging the keys when you posted the answer to the original query, and following your instructions when responding to mine! I like copy/paste! :biggrin: The video was a big help, too! 

It's a real shame that Canonical hasn't made FF 3.5 available to the **LTS** users. I thought LTS stood for Long Term Support, but maybe in this case it doesn't...  :-k

Thanks again!

---

### Post by running_rabbit07 on 2009-08-20
> **cygnus-X1 said:**
> Hi running_rabbit07. Perfect! Many thanks! I must have been still banging the keys when you posted the answer to the original query, and following your instructions when responding to mine! I like copy/paste! :biggrin: The video was a big help, too! 

It's a real shame that Canonical hasn't made FF 3.5 available to the **LTS** users. I thought LTS stood for Long Term Support, but maybe in this case it doesn't...  :-k

Thanks again!

Your Welcome. I had to downgrade to 32-bit for it to work on my system for some reason, though it worked fine with Karmic 64-bit.

---

### Post by Buschbarber on 2009-08-20
> **running_rabbit07 said:**
> I did what [this page]("http://www.psychocats.net/ubuntu/firefox") says to do and it installed perfectly.

This worked for me, as well.

Will it update automatically or do I have to do it manually via the instructions on the web page psychocats?

---

### Post by running_rabbit07 on 2009-08-20
> **Buschbarber said:**
> This worked for me, as well.

Will it update automatically or do I have to do it manually via the instructions on the web page psychocats?

Once you get it installed the way they show it fixes all the icon and link problems, at least it did for me. After stepping down to 32-bit I have installed via the listed method within Virtual Box and Hardy, Intrepid, and Jaunty and it worked fine each time.

---

### Post by Buschbarber on 2009-08-20
> **running_rabbit07 said:**
> Once you get it installed the way they show it fixes all the icon and link problems, at least it did for me. After stepping down to 32-bit I have installed via the listed method within Virtual Box and Hardy, Intrepid, and Jaunty and it worked fine each time.

Thanks!! I am running Ubuntu Ultimate Edition 2.3 64bit. I forgot to see if there was a 64bit version of 3.5.

This is what it says in Help/About

Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.1.2) Gecko/20090729 Firefox/3.5.2

---

### Post by running_rabbit07 on 2009-08-20
> **Buschbarber said:**
> Thanks!! I am running Ubuntu Ultimate Edition 2.3 64bit. I forgot to see if there was a 64bit version of 3.5.

This is what it says in Help/About

Mozilla/5.0 (X11; U; Linux i686 (x86_64); en-US; rv:1.9.1.2) Gecko/20090729 Firefox/3.5.2

I don't think there is a problem with FF working with 64-bit. I honestly think there was just a glitch with my system when trying to install it. I had a lot of people trying to help but they couldn't recreate the problem, though I reinstalled Ubuntu and tried again a few times before I gave up. The I installed VBox and found that the problem didn't occur with 32-bit and I then installed Hardy 32-bit.

---

### Post by meindian523 on 2009-08-20
> **running_rabbit07 said:**
> Your Welcome. I had to downgrade to 32-bit for it to work on my system for some reason, though it worked fine with Karmic 64-bit.
That's coz FF3.5 is the default browser on Karmic and not the default on Hardy.Plus,Hardy users,I dunno,aysiu probably knows more than me,otherwise he wouldn't have written that tutorial,but look for shiretoko in your repos.That's just the codename for FF3.5.That's what you need to install if you want FF3.5 and don't care about the branding and such.

Plus,LTS means Long Term Support,true.But Ubuntu never changes the software in a release even if it changes 'out there',except for a point release,like 8.04.2 or something.I'm not even sure that software might be upgraded to the latest version in a point release.LTS will give you security updates for a "long term",and AFAIK,it doesn't mean that you get the 'latest and greatest' software,because LTS makes sense only for business customers,and they aren't bothered with changes 'out there' from FF3.0 to FF3.5.

---

### Post by running_rabbit07 on 2009-08-20
> **meindian523 said:**
> That's coz FF3.5 is the default browser on Karmic and not the default on Hardy.Plus,Hardy users,I dunno,aysiu probably knows more than me,otherwise he wouldn't have written that tutorial,but look for shiretoko in your repos.That's just the codename for FF3.5.That's what you need to install if you want FF3.5 and don't care about the branding and such.

Plus,LTS means Long Term Support,true.But Ubuntu never changes the software in a release even if it changes 'out there',except for a point release,like 8.04.2 or something.I'm not even sure that software might be upgraded to the latest version in a point release.LTS will give you security updates for a "long term",and AFAIK,it doesn't mean that you get the 'latest and greatest' software,because LTS makes sense only for business customers,and they aren't bothered with changes 'out there' from FF3.0 to FF3.5.

Hardy doesn't offer Shireteko in Synaptic. 

AYSIU was helping me with my problem when I had the 64-bit version. Unfortunately he couldn't recreate the problem to be able to help me with the problem. (I was happy that he tried though.) I also seem to have been the only one that had the 64-bit problem.

I would have to disagree with the LTS not making sense, being that it uses the least amount of CPU and RAM on my system. Hardy is as named, Hardy aka tough. I may still be a rookie, but I am learning fast from trial and error. That's why I install everything on Virtual Box to test it before bothering with my production system.

---

### Post by meindian523 on 2009-08-21
Just because a release is LTS doesn't make it something that uses the least amount of CPU and RAM.Coincidence doesn't imply correlation doesn't imply causation.

---

### Post by Buschbarber on 2009-08-21
I was just informed that Google has released the 64bit version of Chrome.

How does that stack up against Firefox 3.5?

Is there any big performance advantage to a 64bit browser on a 64bit system, which is what I have?

---

### Post by lockaar on 2009-08-21
Hey everyone,

New Ubuntu user here, am enjoying it immensely, but I now have a problem.

I watched the How-To video posted earlier and followed it to a T, copying the code, etc. and now every time I try to launch Firefox I see the "Starting Firefox Browser" in the lower task bar, but Firefox never opens!

I tried a restart, no luck, I also tried to re-install Firefox 3.0 through Synaptic, still no luck.

I'm now at work and away from my Linux box, but I will need suggestions on how to fix this for when I get home later.

8.04 Hardy LTS 64bit.

Any help would be awesome, thanks guys.

---

### Post by lockaar on 2009-08-21
Update: I used the removal command that was also on that previously linked website and that allowed me to regain access to Firefox, but it is version 3.0.13.

Any other ideas as to how I could update to 3.5?

---

### Post by meindian523 on 2009-08-22
lockaar Please create a new thread and link it here.

---

### Post by bcschmerker on 2009-08-28
Thank you for a briefing on the upgrades situation.  I already presume that Mozilla Firefox 3.5 (3.5.2 or 3.5.3 scheduled for 9.10 Karmic) will be available for 8.10 Intrepid and 9.04 Jaunty before 8.04-LTS Hardy on account of Ubuntu testing procedures for LTS releases.  Firefox 3.5 (and 3.6 when eventually released) will need version-specific Ubuntu Modifications extensions, already available for Firefox 3.0.13. :rolleyes:

---

