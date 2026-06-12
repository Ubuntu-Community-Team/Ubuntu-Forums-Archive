---
title: "Problem with Dropbox Installation"
date: 2008-09-15
forum: General Help
---

### Post by asdir on 2008-09-15
I just installed the newest Dropbox version after downloading it from their website, using gdeb. It seemed to install fine. I checked for the listed dependencies (note: "glib" should be "libglib" in their manual).

I logged out and in again. 

However, there is only the little open blue box sitting in the tray doing nothing. There is no new folder in my home-directory and when I try to enter "nautilus-dropbox" or "dropboxd" in the terminal, the system does not know the commands.

When the blue box is right-clicked it states "connecting to dropbox" in greyed out letters. However, nothing happens.

There is not daemon runnning either (checked via ps -A).

Does anyone have a clue what the problem is here?

Thanks for any advice.

---

### Post by asdir on 2008-09-15
Thanks, no help needed. I followed some steps here:
[http://forums.getdropbox.com/topic.php?id=1200&replies=77](http://forums.getdropbox.com/topic.php?id=1200&replies=77)

---

### Post by DJ_Peng on 2008-09-17
Thanks, asdir! I followed your link and was able to get Dropbox working on my comp. I owe you a beer.

---

### Post by asdir on 2008-09-23
No Problem. I just wanted to make up for spamming the forums although I could have found the solution myself. :-D
But be careful with your gratitude: I might show up in Boston one day. ;-)

---

### Post by csmth on 2009-01-20
I have removing .dropbox and .dropbox-dist, reinstalling the deb and no luck. But I found a workaround for this problem.

At "Almost Text-based Install":
[http://wiki.getdropbox.com/TipsAndTricks/AlmostText-BasedLinuxInstall](http://wiki.getdropbox.com/TipsAndTricks/AlmostText-BasedLinuxInstall)

I follow the steps and can use the Pthyon script to start the dropbox. I realized that correct (workable) for my x86_64 .dropbox-dist should be "dropbox-lnx.x86_64-0.6.416.tar.gz". I have tried 0.6.427 and 0.6.432 and they are no good.

---

### Post by Robangutan on 2011-07-10
> **csmth said:**
> I have removing .dropbox and .dropbox-dist, reinstalling the deb and no luck. But I found a workaround for this problem.

At "Almost Text-based Install":
[http://wiki.getdropbox.com/TipsAndTricks/AlmostText-BasedLinuxInstall](http://wiki.getdropbox.com/TipsAndTricks/AlmostText-BasedLinuxInstall)

I follow the steps and can use the Pthyon script to start the dropbox. I realized that correct (workable) for my x86_64 .dropbox-dist should be "dropbox-lnx.x86_64-0.6.416.tar.gz". I have tried 0.6.427 and 0.6.432 and they are no good.


With reference to this I had a similar problem. Can I ask do you have a ntfs partition as your home directory. Though I'm not 100% sure I think this was the result of my issues with the install. The ownerships seem to be very locked down on any ntfs drive despite efforts to edit this using both fstab and other methods. What I found worked as  a terrible hack was once the .dropbox-dist file was created by the installer I moved it to a part of my system that was not ntfs based (/usr though probably not recommended I have never got to grips with the standards) and run the ./dropboxd from there. It all seemed to work fine for me though this may just be idiots luck.~

Anybody fancy pointing out a good quick way of unlocking ntfs drive permissions?

---

