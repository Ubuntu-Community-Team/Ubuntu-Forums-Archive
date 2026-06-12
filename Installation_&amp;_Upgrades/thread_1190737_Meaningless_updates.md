---
title: "Meaningless updates?"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by FirstTimeMan on 2009-06-18
Hey all.

I always update my pc when the update manager shows me that there are updates available. Recently however, I've been taking a look at the updates before I click install and I was wondering wether or not I really need to install ALL the updates ALL the time.

I saw some updates for printing and it occured to me that I don't even have a printer, and there were quite a few just for printing, and I'm sure there may be a host of other things which I may or may not need, but I would like to know wether or not I should just keep installing all updates, or pick and choose.

Just trying to get a hang on linux here.
Are all updates necessary?


-FTM

---

### Post by metiosarius on 2009-06-18
In general, it's best to keep all of your system up to date, purely for security purposes. The only time I wouldn't 'instantly update' was if I was running a server or a workstation that needed to be tested. 

You mentioned that there were printing updates, even though you weren't using a printer...well, chances are that CUPS (the printing system) is running as a service in the background...if they plug a security hole, and you don't update, there is a small chance that your system could be compromised by an attacker.

In general, it's best to keep things updated, not only for feature enhancements, or bug fixes, but mainly for security reasons.

---

### Post by ajgreeny on 2009-06-18
If you will never have a printer attached, you could always uninstall the cups packages, I suppose then there will be no updates for them, but frankly, I agree with metiosarius, keep everything updated as far as possible.  The other possibility is to go to Software Sources and choose to use only Security Updates, not the Recommended ones as well, which will cat down the number.

---

### Post by FirstTimeMan on 2009-06-18
Alright, metiosarius said that its better to take all updates all the time especially since it may concern security.

But as ajgreeny said, you can have the update manager download only the security updates if you're not interested in the other updates.

At this point in time however, I'm only interested in the security updates.
I don't use a printer with my netbook and if I can have only the security updates download that is just fine.

I did what  you suggested ajgreeny, but for now when I open update manager and it searches for updates, it only shows me those for CUPS printing.

So this leads me to wonder, do you get all updates when you open update manager yourself, or will the changes that I made for my update preferences show the next time update manager runs automatically?


Thanks for your input so far.

-FTM

---

### Post by ajgreeny on 2009-06-20
I have to admit it but I don't really know about that.  I would assume that it will not matter how update manager is started, it will only show the updates for the way you have the system set.

---

### Post by philcamlin on 2009-06-20
id update my system if i got an update

---

