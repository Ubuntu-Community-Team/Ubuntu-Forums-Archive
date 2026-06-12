---
title: "Upgrade?? &quot;or not&quot;"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by toolmanpaul on 2009-11-05
using 9.04 and ok with it....is 9.10 worth the effert to upgrade....also will clicking on the upgrade button work or create problems.....thanks   ( i like to keep current but not if it creates "buggs".)

---

### Post by dhavalbbhatt on 2009-11-05
> **toolmanpaul said:**
> using 9.04 and ok with it....is 9.10 worth the effert to upgrade....also will clicking on the upgrade button work or create problems.....thanks   ( i like to keep current but not if it creates "buggs".)
I would stay away from the upgrade - however, I will advise you to perform a fresh install. I did a fresh install yesterday evening and it was worth it. Ubuntu 9.10 64 bit seems to rock on my laptop. Just one point, if you do perform a fresh install, use the alternate CD and not the installation CD - there seems to be issues with partition manager on the installation CD. But then again, if you are happy with Jaunty, there is no real need for you to upgrade at all.

---

### Post by ManiacDan on 2009-11-05
I would recommend an upgrade rather than a wipe and reinstall, but I would wait a month or two until all the critical bugs have been patched.

-Dan

---

### Post by qwerty57 on 2009-11-05
I'm regretting upgrading.  It seems slower to boot now & I've lost my sound.

---

### Post by Mighty_Joe on 2009-11-05
For the love of $DIETY, no matter what you choose, try out the Live CD first!  9.10 (really, any upgrade) can break things! 
Personally, I'm not upgrading.  I'm installing to a flash drive and trying it out for a few days to make sure 9.10 doesn't break anything.  Then I'm installing to a new hard drive so I have 9.04 to fall back on if something breaks.

---

### Post by raymondh on 2009-11-05
> **Mighty_Joe said:**
>  no matter what you choose, try out the Live CD first! 

+1000

Try out a live session first.  Then peruse the forums for the next 2-3 weeks and see what fellow members are experiencing ... then go from there.

Also, when you download to burn a CD/USB, torrent. 

Personally, I prefer a fresh install.

---

### Post by togo59 on 2009-11-05
> **raymondhenson said:**
> +1000

Try out a live session first.  Then peruse the forums for the next 2-3 weeks and see what fellow members are experiencing ... then go from there.

Also, when you download to burn a CD/USB, torrent. 

Personally, I prefer a fresh install.
The live CD is a necessary but not sufficient condition -- e.g. you might not be able to test your intended graphics driver until _after_ the upgrade/fresh install (when it's too late).

I fresh-installed 9.10 on my lap-top: I don't see any "must-have" advantages, I see a number of things I don't much like (but I'm not bothered either way) and I cannot use compiz any more, because the 2D/3D effects aren't supported any more. Every time my upgrade manager kicks into life it tells me I'm running on batteries, whether I am or whether I'm not. Weird.

I have kept 9.04 Ubuntu Studio on my home PC as _there is no live CD_ for the 64 bit version. But I'm certain the new version will screw things up so I'll leave well alone :sad:

---

### Post by prshah on 2009-11-05
On my desktop, upgrading was painless and 9.10 worked very well; audio output is far better (I don't understand how a software change can affect this).

On my laptop, I have some problems; essentially it "feels" slightly slower (sluggish), and for some reason, OpenOffice disappeared and had to be reinstalled (Perhaps because I'd used a custom PPA for OOo3 in Jaunty).

I've continuously upgraded both of these from Gutsy onwards (laptop from Hardy). I feel that if I perform a fresh install, setting everything back the way I like it will take too long, and may be incomplete.

Upgrading has always worked without a problem for me.

However, I feel that my performance was slightly better in 9.04 than 9.10, so maybe it might be better for you to hold off the upgrade in the short term.

And, boot improvements notwithstanding, on the laptop (desktop is fine and dandy) Karmic takes over 3 minutes to boot up to a usable desktop. To be fair, Jaunty took long too, but with Karmic forbearance has changed to irritation.

Firefox is the exception though; it opens like lightning (Within 2 seconds) on my desktop, and only about a second or so longer on the laptop).

---

### Post by ^_Pepe_^ on 2009-11-05
> **prshah said:**
> 
...
And, boot improvements notwithstanding, on the laptop (desktop is fine and dandy) Karmic takes over 3 minutes to boot up to a usable desktop. To be fair, Jaunty took long too, but with Karmic forbearance has changed to irritation.
...
.

I have no founded opinion about what is better: Upgrade or reinstall. But...anyway, 9.10 is faster than 9.04. Not difficult at all. 

Fresh installed 9.10 takes only 12 seconds from GRUB to GDM and 4 from GDM to desktop in my E4200 (I know...fast hardware). 

In my server, though, updated from 7.10 one by one...9.10 is faster than 9.04, but not so brilliant as Laptop. Anyway hardware is also not comparable, so that's why I have no clear opinion about that.

If your question is: Update or not? Wait!!! Lot of issues there.

Regards,
^_Pepe_^

---

### Post by Bobhuber on 2009-11-05
I'd wait.There are lots of bugs both in the update and a fresh install.
I've tried both.I'm still using the fresh install to try and work out the problems and will post my efforts after I do some more research  but may still reload the 9.04 backup image if I can't get things worked out.One positive note once they get all of the bugs worked out it should be an awsum release.It has a lot of new features that are worth the change.

---

### Post by recluce on 2009-11-05
The Golden Rules here:

1.) Do you have a pressing need to upgrade? Goto 3.)

2.) Wait a month or so for Karmic to get more stable and the bugs to be eradicated.

3.) Backup everything, make an image backup with a tool that allows restoration of your root-partition into a bootable state (Clonezilla, Acronis, whatever). Use one of the many tutorials to make a snapshot of all installed packages.

4.) Try to upgrade. If everything works, goto 7.)

5.) If upgrading fails, do a clean install and reinstall your packages with the snapshot from 3.) If everything works, goto 7.)

6.) If it still does not work, restore your backups and goto 2.)

7.) Be happy....

Short version: never be an early adopter of a new OS on a production machine!

---

