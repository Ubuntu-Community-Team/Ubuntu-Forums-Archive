---
title: "Update Manager not running daily since upgrade to Intrepid"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by davidkahn on 2008-12-06
If I run it manually it works perfectly.  However, before the upgrade (Note: previously upgraded from Feisty to Gutsy to Hardy without a problem), every morning it checked for updates and silently downloaded them.  The "Update" tab of the "Software Sources" control panel is set up correctly (identically to another server that is correctly checking for updates).

uname -a
Linux CERTIBY-DEV1 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

---

### Post by frankleeee on 2008-12-06
> **davidkahn said:**
> If I run it manually it works perfectly.  However, before the upgrade (Note: previously upgraded from Feisty to Gutsy to Hardy without a problem), every morning it checked for updates and silently downloaded them.  The "Update" tab of the "Software Sources" control panel is set up correctly (identically to another server that is correctly checking for updates).

uname -a
Linux CERTIBY-DEV1 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

I assume that you have check daily in software sources. I guess you answer that in your post.

---

### Post by ethos_dacapo on 2008-12-22
Did you ever figure out the problem? I'm having the same thing happening to me. Even after i manually run the update manager it still says last updated 4 days ago. This didn't start until i upgraded from 8.04 to 8.10.I'm about to backup my home folder and do a clean install.

---

### Post by Snypez on 2008-12-23
I am having the same problem on my box after upgrading from 8.04 to 8.10. Update manager works fine if I initiate it manually but it will not automatically update package information so that update notifier can alert me. To ethos_dacapo if your system is checking for updates and just not correctly displaying when the package information was last updated check your repos. I have read that if your repos are incorrect it will cause this error and it is common after updates.

---

### Post by ethos_dacapo on 2008-12-23
> **Snypez said:**
> I am having the same problem on my box after upgrading from 8.04 to 8.10. Update manager works fine if I initiate it manually but it will not automatically update package information so that update notifier can alert me. To ethos_dacapo if your system is checking for updates and just not correctly displaying when the package information was last updated check your repos. I have read that if your repos are incorrect it will cause this error and it is common after updates.

Wow thanks for that tid bit of info. I did have a launchpad repository for pidgin that i updated from hardy to intrepid and it was giving me an error saying it couldn't be found. I just unchecked it for now and now my update manager at least shows it was updated today. I suspect its still not gonna check on its own though because i only edited the repositories 5 days ago and updated everything from hardy to intrepid. I really don't want to miss any important security updates and especially a realtime kernel update since i'm using ubuntustudio. It hasn't done too bad so far but i am getting a few xruns. Anyways hopefully this thread will come to life with a way to fix the problem we're having with daily updates.

---

### Post by hatten on 2008-12-23
doesn't work for me either, 2 days ago since last check for updates, and that time i checked myself (of what i can recall)

---

### Post by Snypez on 2008-12-23
FYI: Thanks button looks like a little medal in bottom right. Glad I could help with your issue. Now if only we could figure out why update manager is not automatically updating package info we would be in good shape.

---

### Post by ethos_dacapo on 2008-12-23
[http://ubuntuforums.org/showthread.php?t=1004403]("http://ubuntuforums.org/showthread.php?t=1004403")
from the above link:
> I have the same problem, and found that /etc/cron.daily/apt did not have execute-permission. I believe that this script is responsible for update-manager checking the sources.

So i suggest checking if the you have the execute-permission set, and if not, set it (sudo chmod a+x /etc/cron.daily/apt)

Is this the answer we're looking for? I'm not so quick to change file permissions until i know whether or not its safe. It isn't set to execute as a program on my system though. This looks like the answer but can anyone confirm before i change it?

---

### Post by Snypez on 2008-12-23
I ain't scrred. I did a "sudo chmod 755 /etc/cron.daily/apt". We will see if that fixes it.

---

### Post by Snypez on 2008-12-24
No luck with the file permissions. The problem persists still on my box :(
EDIT:
Or I didn't wait long enough before I posted. It appears this did indeed fix the issue. Do a ls -l /etc/cron.daily/ and you will see that all files in this dir have 755 permissions except the apt script. Chmoding it to 755 does indeed allow the update manager to automatically check for updates.

---

### Post by ethos_dacapo on 2008-12-24
So its back to the drawing board i guess.

---

### Post by Snypez on 2008-12-24
:) Success!! for all following this thread sudo chmod 755 /etc/cron.daily/apt is the solution!:guitar:

---

### Post by hatten on 2008-12-25
did it, hope it works

My gnome power doesn't seem to start at startup, rendering my inhibit applet useless until i start it manually, is there a similar solution to that?

---

### Post by ethos_dacapo on 2008-12-25
worked for me

---

### Post by sleepyjon on 2008-12-25
> **Snypez said:**
> No luck with the file permissions. The problem persists still on my box :(
EDIT:
Or I didn't wait long enough before I posted. It appears this did indeed fix the issue. Do a ls -l /etc/cron.daily/ and you will see that all files in this dir have 755 permissions except the apt script. Chmoding it to 755 does indeed allow the update manager to automatically check for updates.

I'm pretty sure you want 744. 755 lets anyone execute it, 744 only lets root execute.

---

### Post by Snypez on 2008-12-29
@sleepyjon Thats what I thought as well until
> **Snypez said:**
>  Do a ls -l /etc/cron.daily/ and you will see that all files in this dir have 755 permissions except the apt script. Chmoding it to 755 does indeed allow the update manager to automatically check for updates.

---

### Post by sleepyjon on 2008-12-30
I sit corrected.

---

### Post by HerbCSO on 2009-10-05
At the risk of beating a dead horse - I ran into the same issue in Jaunty. Same fix described here worked there as well. This was a system that was upgraded from Hardy to Jaunty.

Does anybody know how the permissions get messed up in the first place? Is there a problem with the upgrade process that still persists here?

---

### Post by steveg944 on 2009-10-06
Herb, Thanks for beating that dead horse. I have had the same problem since upgrading to Jaunty. I searched for a solution once before but did not see it until you bumped this thread from the dead.

I do not know how the permissions were changed.

---

### Post by michaelshiloh on 2009-11-08
And to further (re) beat that poor dead horse yet again, I experienced exactly the same problem (lacking execute permission on apt) after the upgrade to Karmic.

Not sure it makes a difference, but I had upgraded prior to the official release using update-manager -d.

---

### Post by Donalb on 2009-11-08
And I'm also joining this ongoing party, after a fresh Karmic Install (not upgrade) from Intrepid (skipping Jaunty).

Thanks for the fix, (though I'm just plugging it in now)!

regards.

---

### Post by zooounds on 2010-03-22
I have the same issue with Karmic but the fix does not work.

---

### Post by zooounds on 2010-03-22
[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945)

---

