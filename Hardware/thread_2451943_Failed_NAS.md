---
title: "Failed NAS"
date: 2020-10-13
forum: Hardware
---

### Post by bobnutfield on 2020-10-13
Hello Everyone

i have a Seagate 4TB personal cloud NAS that has failed.  According to Seagate support, it is not repairable and the data is not retrievable.  This drive was only 2 years old and it seemed odd to me to fail so quickly.  Made a clunky sound and then just went down.  Seagate support says that they believe sound was metal against metal, scratching the disk rendering the data unretrievable.  

My question is does anyone know of any means to retrieve the data in this situation?  I'm very disturbed about it as Seagate just blew me off and says they no longer manufacture network drives, only local storage .  The were'nt interested at all in helping me recover the data

Any thoughts appreciated.

Regards

Bob

---

### Post by CelticWarrior on 2020-10-13
It's Seagate, no surprise. It happened with several others. 2TB were notorious for their failure rate. A 3TB of mine failed after less than 4 years.

Unfortunately it's true what they said, data is unrecoverable.

---

### Post by bobnutfield on 2020-10-13
Thanks CelticWarrior

I assumed that to be the case.  I'd also heard that about Seagate, but only after I already had the drive.  It's not a major disaster as I have the date backed up but it will me weeks to collect it all again (mainly family photos from years)  Just have to learn and move on.

Bob

---

### Post by MartyBuntu on 2020-10-13
NO hard drive manufacturer is going to warranty or help you do data recovery.
The responsibilty for data backups is all yours. I once bought a WD 1TB "Blue" drive that gave sector errors the very same day I brought it home from the shop.

---

### Post by mastablasta on 2020-10-14
i had similar experience with WD and their support. drive that i kept in dark and safe place suddenly moved to read only and ultimately failed. 3 years old. and these are the only 2 manufacturers of HDD. so we have to learn to live with it and do backups.

external drives are problematic. the one with separate external power usually last longer, but there is no rule. we had a thread where it seem all had sudden drive failure experience. no matter the brand.

Red (nas drives) are slower and last longer. they are also more expensive. i imagine they use more robust and better quality components.

Seagate had major issues a few years ago. they improved with recent baracuda blue drives. no sure baout external ones. i always used WD for external.

WD blue is also problematic. but you should know things change with models and it's good to check yearly online reliability reports from data centres and large server space providers (so real life usage).

---

### Post by MartyBuntu on 2020-10-14
> **mastablasta said:**
> ...and these are the only 2 manufacturers of HDD.

There are more than two.

---

### Post by mastablasta on 2020-10-15
more brands, but not manufacturers. maybe there are 3. HITACHI used to use their own drives, but i am not sure they still do it. The also usually do not have so much cache as others.  most other brands (Samsung...) make drives in WD or Seagate and then just add their brand on it. this is HDD. SSD is a different matter.

---

### Post by scorp123 on 2020-10-16
> **bobnutfield said:**
>  My question is does anyone know of any means to retrieve the data in this situation?

There are specialised companies that are able to (partially) recover data even from defective and partially destroyed harddrives. **But: This can be VERY costly.** 

Your forum profile says you're based in the United Kingdom... so if you search for *"data recovery service UK"* via Google you should get a few links to UK-based companies that are specialised in this. Please check online reviews about them, chat with them, call them, check how much this could cost you in a worst case scenario. You're trusting them with your data and your privacy, and you might end up having to pay them, so you have to make sure you're not dealing with clueless amateurs who may make matters worse.

Depending on how badly the harddrive is damaged or not recovering data from it may be possible but time-consuming and very costly. Unless the data on that harddrive was absolutely unique and cannot be reacquired by any other means it's usually not worth it.

---

### Post by TheFu on 2020-10-16
Met a guy at a security conference who does data recovery on HDDs.  Basically, it is $3000 per drive, plus whatever the replacement drive costs.  He also teaches insurance companies and law enforcement data forensics techniques, chain of custody stuff, and touches on local laws, since in some places, if you aren't a licensed PI, then you can't perform forensic data recovery legally that will work in court.

Backups are much cheaper. Heck, 3 backups are much cheaper.

I've lost data over the decades too. The first time, it took me about 2 months to finally accept the data was gone.  After that happened, I got backup religion. Fortunately, my paycheck had expanded to support this. Initially, I started just with a weekly mirror using rsync. As time progressed my methods became more sophisticated.  

[LIST]
[*]I still use **rsync** for huge files that never change, basically that is media files. ```
ionice rsync -av --stats --progress --exclude "**/.[tT]rash*" --exclude lost+found  --delete /d/D1/ /d/b-D1/
``` That command makes a mirror for 1 userid. It doesn't retain permissions, so it shouldn't be used when files have more than 1 owner or group. /d/D1 is the source. /d/b-D1 is the target. Good enough for media files like music and videos while still being simple. 
[*]I use a versioned backup tool for most things in in users' HOME directories, DBMSes and other file locations that can change daily.
[https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432](https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432) has a simple example to backup a HOME directory with versions.  There are probably 10 well-known and popular tools for this. That example should work with just minor tweaks. The trade-off between being simple enough for near-beginners and complete enough to be useful is difficult. My backup scripts are more complex, but it all comes down to something very much like the rsync command above, just with a tool that handles versioning for us.
[*]I do not backup entire OSes. I get system settings and lists of installed packages. There are lots of details around getting the different information, ensuring it is updated and placed somewhere safe that will also get backed up.  Took me a few times to actually backup all the data that was necessary to restore a system to completely new hardware 500 miles away.  After that was working, I've added refinements to capture more helpful information to be able to solve other system issues that come up from time to time, even though that extra information isn't needed to restore a backup, it is nice to have to solve other issues.  For example, I don't need the partition layout information, but having it can be the difference between overlaying a good copy of the partitioning layout instead of doing a fully restore process that will take 30-45 minutes.  I'd rather have the 2 minute solution. If having 1 extra tiny file, created nightly, can accomplish that goal, sign me up.
[/LIST]

---

### Post by mastablasta on 2020-10-17
> **TheFu said:**
> 
Backups are much cheaper. Heck, 3 backups are much cheaper.


on the other side, recovery sounds like a good business.

we have lower monthly salaries here, so i think it costs slightly less (arround 2000 EUR). still not bad if you can recover it in a week.

---

