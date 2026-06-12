---
title: "How to upgrade from 7.10 to 9.04?"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by kenwong on 2009-07-19
How can i upgrade from 7.10 (Xubuntu) to 9.04?  What is the best way?  Burn an image CD?

My hard disk has free space of about 1.2GB only.

Thanks.

---

### Post by mikewhatever on 2009-07-19
You can't install Ubuntu on 1.2 GB, and you can't upgrade directly from 7.10 to 9.04. Given the circumstances, I think the best option is to backup your files and reinstall.

---

### Post by vegetarianshrimp on 2009-07-19
Hmm...you can either go through the upgrade a million times, try to install 9.04 on a separate partition and then have your computer crash because you have no memory left, or you can back up your home partition on a USB drive and completely reinstall with a LiveCD.

---

### Post by raymondh on 2009-07-19
Mikewhatever has a point about the size/space.  Lowest I've had Ubuntu is at 8GB.  Right now, my root is already at 4.3GB because of all the apps I installed.

As for upgrades ... you'll have to go sequentially and ensure that each version is updated prior to upgrading to the next.  That does take time.  But, your choice.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Back up your files before proceeding.  try the liveCD of your preferred version to see if it does "fit" your system specs' and your needs.

Good luck.

---

### Post by vegetarianshrimp on 2009-07-19
> **raymondhenson said:**
>  try the liveCD of your preferred version to see if it does "fit" your system specs' and your needs.

Just keep in mind that the LiveCD is slower than a real install.

---

### Post by philcamlin on 2009-07-19
format and reinstall is the best 

upgrading isnt a good idea 

ive dont it and it creates more issues then formatting and reinstalling :popcorn:

---

### Post by raymondh on 2009-07-19
Also, now is the time when a separate /home partition shows its' advantage.  

I say this because if you do plan to resize and give Ubuntu more space, and re-install, consider having a separate /home (for future upgrading/reinstall actions).

Good luck.

---

### Post by Rapture1781 on 2009-07-20
Hi.... "I'm new"... where is the bar for introduce myself?
-----------------------------

 I think you can upgrade... 

Go to ```
/etc/apt/sources.list
``` and then change Gutsy in Jaunty, then:
```
sudo apt-get update
sudo apt-get dist-upgrade
```You could find some problems with packets dependencies....
Good luck!!! :D

---

### Post by presence1960 on 2009-07-20
you can upgrade but the time spent upgrading from 7.10 > 8.04 > 8.10 > 9.04 in itself is a reason not to do it.

But don't take my word for what I am about to say, peruse back through our forum and you will see that the upgrade process to 9.04 has caused many who have tried it major problems.

I would do a clean install of 9.04.

---

### Post by kenwong on 2009-07-23
Thank you all for your help and advice.

It sounds that a clean installation with a Live CD is the best way.  Will try it.  Hope the newest version will not work too slowly on my old machine. :D

---

### Post by Sef on 2009-07-23
>  Hope the newest version will not work too slowly on my old machine

How much ram do you have?  If you have less than 512 mb of it, then check out [xubuntu]("http://xubuntu.org").  If it made for machines without a lot of ram.  Or you could install more ram.

---

### Post by raymondh on 2009-07-23
> **kenwong said:**
> Hope the newest version will not work too slowly on my old machine. :D

Kenwong,

As SEF posted ... do check the [release notes]("http://www.xubuntu.org/get") for Xubuntu vis-a-vis your system specs.  That or you can always opt for a lighter windows manager (i.e. openbox, etc).  Or you can try a lightweight derivative of Ubuntu (i.e. [crunchbanglinux]("http://crunchbanglinux.org/") which uses openbox)

Have fun.  Back up your files.

---

### Post by kenwong on 2009-07-24
Thanks Sef and Raymond.

I got 228MB Ram on my ThinkPad 600E ([http://www.thinkwiki.org/wiki/Category:600E](http://www.thinkwiki.org/wiki/Category:600E)).

Will CrunchBang Linux run faster than Xubuntu on my machine?

Thanks.

---

### Post by raymondh on 2009-07-24
> **kenwong said:**
> Thanks Sef and Raymond.

I got 228MB Ram on my ThinkPad 600E ([http://www.thinkwiki.org/wiki/Category:600E](http://www.thinkwiki.org/wiki/Category:600E)).

Will CrunchBang Linux run faster than Xubuntu on my machine?

Thanks.

I find crunchbang "snappier" than Xubuntu nowadays. With our modest specs, responsive is a better descriptive than fast ;)

Try it.  If you don't like it, a new OS is both FREE and a CD-burn away :)

Have fun and happy ubuntu-ing.

---

### Post by kenwong on 2009-09-05
> **raymondhenson said:**
> I find crunchbang "snappier" than Xubuntu nowadays. With our modest specs, responsive is a better descriptive than fast ;)

Try it.  If you don't like it, a new OS is both FREE and a CD-burn away :)

Have fun and happy ubuntu-ing.

Thanks Raymond.

Have tried and used Crunchbang Linux for a few weeks.  It is light-weighted and responsive and is therefore really a good OS for old machines like mine.  

Thanks again for your advice.

---

### Post by raymondh on 2009-09-06
> **kenwong said:**
> Thanks Raymond.

Have tried and used Crunchbang Linux for a few weeks.  It is light-weighted and responsive and is therefore really a good OS for old machines like mine.  

Thanks again for your advice.

You're welcome and happy ubuntu-ing :)

---

