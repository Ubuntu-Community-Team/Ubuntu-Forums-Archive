---
title: "Is it possible to downgrade from 9.04 to 8.10?"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by Shinobihokage on 2009-05-13
After upgrading to 9.04, I've decided that I'd like to go back to 8.10. If this is possible, how do I go about going back to 8.10.

---

### Post by Mark Phelps on 2009-05-13
You don't.  You need to reinstall to go backward.

---

### Post by Shinobihokage on 2009-05-13
ok, then can you walk me thru doing that?

---

### Post by kryptikos on 2009-05-13
> **Mark Phelps said:**
> You don't.  You need to reinstall to go backward.

Not true. With Linux pretty much anything is possible. Sometimes it is a bit more tedious, but usually it can be done. Ubuntu docs exist on the official Ubuntu Community Documentation for how to downgrade. 

[https://help.ubuntu.com/community/DowngradeHowto]("https://help.ubuntu.com/community/DowngradeHowto")

**WARNING:[B]**[/B]Just because something is possible does not mean the software or scripts are perfect. You do run the risk of losing data. Best advice is read through the documentation thoroughly before moving forward and backup any critical data to a CD or USB stick.

But that link should help you. Good luck!

---

### Post by Shinobihokage on 2009-05-13
Thanks for the link, I attempted the first script and it did nothing. Attempting the second now. Hopefully it will work

---

### Post by Shinobihokage on 2009-05-13
Ok, I just tried the second script and it also didn't work. Is there a way i can just fully wipe off 9.04?

---

### Post by kryptikos on 2009-05-13
Fastest way if you just want to wipe your current OS version is to load up a Live CD from an older release and just install it. It will have the option to overwrite existing Linux partitions.

---

### Post by Mark Phelps on 2009-05-13
> **kryptikos said:**
> Fastest way if you just want to wipe your current OS version is to load up a Live CD from an older release and just install it. It will have the option to overwrite existing Linux partitions.

While I agree that it is "possible", one look at the scripts clearly indicates that this is NOT something to be attempted by folks new to Ubuntu or Linux -- which is why I generally tell them to do what you have basically just said -- reinstall.

---

### Post by slumbergod on 2009-05-13
I'm curious about your reasons for wanting to rollback to Intrepid. Is there something wrong in Jaunty that you don't like?

---

### Post by kryptikos on 2009-05-14
> **Mark Phelps said:**
> While I agree that it is "possible", one look at the scripts clearly indicates that this is NOT something to be attempted by folks new to Ubuntu or Linux -- which is why I generally tell them to do what you have basically just said -- reinstall.

The philosophy that I tend to apply with folks and Linux is to give them the options to learn and explore the system instead. I'm not one for telling someone they should NOT attempt something just because they may be new. How else will they learn the system other then by doing? The goal is to guide them to the resources and the knowledge...ultimately increasing the community's knowledge as they'll pass along the "hey I've been there and done that and have the t-shirt, let me show you".

---

### Post by albertz on 2009-05-14
Someone wrote in that wiki "DO NOT DO THIS. YOU CANNOT DOWNGRADE PYTHON ACROSS PACKAGES FROM 8.04 (HARDY) TO 7.10 (GUTSY).". What does that mean? I want to downgrade from 9 to 8 (because my WLAN card doesn't work under 9 but I really need it as soon as possible).

If I decide for reinstall, how can I easilly do that (with keeping all installed applications and user settings). Well, user settings is easy, I guess I just have to keep my home-dir. In Gentoo, for the applications, I just have to keep the /etc and /var/lib/portage and with that backuped, I can just reinstall and I will have the exact same system (just newly installed). Is there some similar way on Debian/Ubuntu?

It seems somehow silly to me that it took so less time for an update, just to figure out that the hardware is not working anymore, and then the downgrade is so complicated.

---

### Post by connorh123 on 2009-05-14
What you could do is download 8.10 onto a CD, then grab all of your memory onto a flash drive.
Then insert the disk, and your files. And there you go.

---

### Post by Shinobihokage on 2009-05-15
> **connorh123 said:**
> What you could do is download 8.10 onto a CD, then grab all of your memory onto a flash drive.
Then insert the disk, and your files. And there you go.

I have a 8.10 disk, but everytime i try to boot from it or run it, it infinitly loops extracting and does nothing. And when i restart and go to choose which version to run the only options are 9.04.

---

### Post by connorh123 on 2009-05-15
Have you tried shutting down. Then trying it?

---

### Post by Lajik on 2009-06-02
I upgraded to 9.04 yesterday and today i'm going to reinstall 8.10.  I can not get the sound working in jaunty at all, I've been googleing and going through the forums all night and day and still nothing. :(

---

### Post by Bob_Dole on 2009-06-05
jaunty -really- should have had a downgrade option, what with the the Drop of support and transition to cruddy/barely there support on certain graphics cards... like mine. i -just- installed jaunty, because I forgot my card was no longer supported, seeing as it -is- relatively new.
Now I have to spend more bandwidth and time than I ought need to, to have to to get my card supported.

---

### Post by flang3r on 2010-03-16
> **albertz said:**
> Someone wrote in that wiki "DO NOT DO THIS. YOU CANNOT DOWNGRADE PYTHON ACROSS PACKAGES FROM 8.04 (HARDY) TO 7.10 (GUTSY).". What does that mean? I want to downgrade from 9 to 8 (because my WLAN card doesn't work under 9 but I really need it as soon as possible).

If I decide for reinstall, how can I easilly do that (with keeping all installed applications and user settings). Well, user settings is easy, I guess I just have to keep my home-dir. In Gentoo, for the applications, I just have to keep the /etc and /var/lib/portage and with that backuped, I can just reinstall and I will have the exact same system (just newly installed). Is there some similar way on Debian/Ubuntu?

It seems somehow silly to me that it took so less time for an update, just to figure out that the hardware is not working anymore, and then the downgrade is so complicated.

Hi i am new here.

I think the reason why it is complicated to downgrade rather than upgrade because if you upgrade something, it overrides the files and there for deletes the old files and replaces them with the new upgrade. 

Of course it would be possible to make the system ask if you want to spend some hard disk space to keep the old files or something like that...

I have Ubuntu 9.10 UNR(Ubuntu Netbook Remix) and have to downgrade because of my graphic card(Mobility Radeon x1400). There are no drivers on Ubuntu 9.10 for my card that work, but on 8.10 they work perfectly from ATI. 
Is anyone here that has the same problem ?

---

### Post by sports fan Matt on 2010-03-16
According to [http://www.ubuntugeek.com/ubuntu-version-names-and-end-of-life-details.html](http://www.ubuntugeek.com/ubuntu-version-names-and-end-of-life-details.html), if one wants to downgrade the end of life is approaching for intrepid.  (Not sure if it was covered with an exact date in this post).

---

### Post by flang3r on 2010-03-18
I backed up everything and partitioned  my system again to Ubuntu 8.10 Intrepid. 
Everything works and my graphic driver is great!(Ati Mobility Radeon x1400). 
I use fglrx restricted driver.

Later today I will try to upgrade everything except: **xorg, xorg-server and fglrx.**

I read somewhere that this worked like a charm.

I will post the outcome here.

---

### Post by smuj76 on 2010-03-18
> **slumbergod said:**
> I'm curious about your reasons for wanting to rollback to Intrepid. Is there something wrong in Jaunty that you don't like?

Not sure about 9.04, but I've just gone to 9.10 and am no longer such an ardent Ubuntu fan.
Bearing in mind that I'm not overly "techy", this means that pretty much my whole weekend will be spent working through a roll back.

But it will be worth it. 9.10 is more difficult to navigate, doesn't work with the HTML creators that my Uni relies on for their online submission sites, requires me to run a Win7 OS over the top to get iTunes, can't open docs from links and is painfully slow.It's incapable of more than one resource heavy process, and takes ages to load applications. Big thumbs down from me.

9.10 - can't wait to get rid of you and go back to 8.10.

---

### Post by slakkie on 2010-03-18
> **sox fan Matt said:**
> According to [http://www.ubuntugeek.com/ubuntu-version-names-and-end-of-life-details.html](http://www.ubuntugeek.com/ubuntu-version-names-and-end-of-life-details.html), if one wants to downgrade the end of life is approaching for intrepid.  (Not sure if it was covered with an exact date in this post).

Intrepid is going EOL in April, that is correct. I assume around the same time Lucid hits the shops. Just keep an eye out for the announcement. [https://lists.ubuntu.com/archives/ubuntu-announce/](https://lists.ubuntu.com/archives/ubuntu-announce/)

I've pre-tested the EOL upgrade from Intrepid to Jaunty and documented it: [https://help.ubuntu.com/community/EOLUpgrades/Intrepid](https://help.ubuntu.com/community/EOLUpgrades/Intrepid)

Although I would not advise it, you can install Intrepid. Although in less then a month it will be unsupported.

---

