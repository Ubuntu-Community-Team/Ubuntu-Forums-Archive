---
title: "Latest Firefox Update Leads to Frequent Flash Related Crashes"
date: 2008-11-20
forum: General Help
---

### Post by jocose on 2008-11-20
**Firefox & Flash 10 were working perfectly, *until*...**

(Ubuntu 8.04.1) I updated Firefox to 3.0.4 from the repos. Now, it's constant crash after crash.

*How does it crash?* All it takes is visiting a site with Flash content, and the browser exits quickly and completely. I have the option to restore when I restart Firefox, but often the restored page(s) with flash content crash the browser again and again, leaving me no time to view the page with the flash content.

I thought with Flash 10 this problem would be over. This problem plagued me every time I updated Firefox in the past with Flash 9, but I'm thinking this may be an issue with Firefox and how it's updated, maybe, IMO, even within the repos and how it's handled somehow in the upgrade process since this is when it starts with the problems. I can't put my finger on it, I've read all of the related threads, tried all of the solutions, nothing works. I have no high hopes, or hopes at all of anyone knowing how to resolve this, since searching the forums here and the web have offered no sure result to fix it on my system.

I've had to switch to manually installing Seamonkey and using Flash 10 to view sites with Flash, where it doesn't crash with Flash content like Firefox does now since I've updated. As stupid as it may sound, I'm starting to consider never updating Firefox when it works originally with Flash 10 on a fresh install, no matter how many security updates are touted, as the updates **always** seem to lead to Flash crashes with any webpage featuring flash content.

With no solution in sight, I don't know what to do, other than disabling Flash completely in Firefox, which isn't a good option for the many users I manage who prefer Firefox. I know about Flash Block, but this is no solution for the newbie users I manage who are frustrated by plugins like Flash Block, No Script, and other plugins I use. I would love to hear from others experiencing this problem. If anyone has magically resolved this somehow by way of some miracle, detailed steps to fix this would be appreciated. Are there any open and active Launchpad related links for this problem? Let's work together on this if it's a problem experienced by many users.

Edit: I should mention this issue seems similar to the problems/errors mentioned in this thread:
[http://ubuntuforums.org/showthread.php?t=984315](http://ubuntuforums.org/showthread.php?t=984315)

---

### Post by SoCalChris on 2008-11-20
I've been having similar problems. I assumed that it was from upgrading to the beta 64 bit Flash 10 plugin, but now that you mention it, I also updated Firefox immediately before this started happening. It happens mainly when viewing fairly long flash videos.

---

### Post by The Pinny Parlour on 2008-11-20
I get random flash related crashes too.  It's starting to really bug me as it locks me system and I have to press the reset button on the box.  I don't know how to fix.  if it continues, I'll have to look for an alternative OS.  I have used Ubuntu for a couple of years now, but this issue really a problem.

---

### Post by HappyHenry on 2008-11-20
Flash is the problem and not Ubuntu. Flash is a restricted/proprietary software that purposfully is designed to work within a certain OS. Ubuntu is an Open Source OS that is not considerd by the software companies that stand to make a profit by designing proprietary/restricted software. Ubuntu and other Open Sorce OS's can design there own software but that will also require acceptance by the public to use it OR react to the demands of adapting there OS to work within the demands of copy-write to develop a way to make the proprietary software work.
Many times generous people have come to the rescue of Open Source, to design such that, Ubuntu works so well in so many ways. It's all done by folks and shared with others with only the hope that it will be useful. 
I will search for their solutions and post when i find it. I'm sure someone will come to the rescue. Please be a little patient in this kind of situation we can only react, since the software company does not take free into consideration. If we want consideration we will have to depend on each other. Trust, hope, love, it can be done.

---

### Post by futta on 2008-11-22
same problem here; ubuntu 8.04 with FF 3.0.3 (using Flash 9.0 r124) worked great, 3.0.4 crashes very regularly.

concerning Flash being "purposfully is designed to work within a certain OS"; that's not entirely correct; there's a small team working on the linux-native version since 2006. you can check out their blog on [http://blogs.adobe.com/penguin.swf/](http://blogs.adobe.com/penguin.swf/)

---

### Post by MatthewPlanchard on 2008-11-22
I just wanted to validate this issue on this system.

After updating to Firefox 3.04 with Adobe Flash Player 10 installed, all Flash dependent web content has become inaccessible.

Thank you for the suggestion of using Seamonkey.  I will be trying that now.

Blessings!

---

### Post by boxrec on 2008-11-23
Just to add that after upgrading I also get random flash related crashes.

Edit ... using Seamonkey solved the problem :-)

---

### Post by airencracken on 2008-11-24
I'm having the same issue and it seems to affect the beta of 3.1 as well as Seamonkey 1.12 and Opera 9.27. Has anyone filed a bug report?

---

### Post by jocose on 2008-11-24
*Thanks for the many replies in this thread, it's good to read confirmations of this problem from others.* I'm not sure whether or not this particular bug has been reported or not. Someone should take the time to properly report this.

I've experienced Firefox crashes even on pages *without* Flash, so I'm curious as to whether or not this is entirely a Flash issue, or whether it's an issue with Firefox alone, following an update. Given the problems with Flash and Firefox in the past, and how quickly Firefox after the update goes down with Flash content, though, I feel it must be Flash related.

What could happen following an update to bring about this behavior? Do we have someone here who is interested in filing a bug report at Launchpad (LP), posting the LP link here and a group of individuals who can confirm this on the appropriate LP bug entry page so this receives some serious attention?

**Now, about Seamonkey:**

With Firefox upgrades and this problem in the past, I had tried installing Seamonkey from the repos and experienced the same problem with crashes, while a manual download of Seamonkey from Mozilla's site and manual install of Seamonkey worked fine, with no crashes.

Stability issues aside, I would suggest **not** using Seamonkey from the repos if it's an older version. The current version as of this posting, which I am running, is Seamonkey 1.1.13. I strongly recommend a manual download/install of Seamonkey, due to the critical security issues fixed in the current version. 

**Let's go back to Firefox for a moment:**

Has anyone tried (backing up important files, first) purging Firefox installed from the repos, then manually downloading Firefox from Mozilla's site and installing it and testing it for a day or two with the hopes of reproducing the behavior noted following the FF upgrade from the repos? If, like Seamonkey manually downloaded/installed, FF from Mozilla's site does not exhibit this behavior, this would be interesting to know, thank you all.

---

### Post by firemanbill on 2009-03-09
Having the same problems.  Flash now crashing mozilla, opera, and seamonkey.  Have purged adobe, tried the open source ones, ended up purging them and reloading adobe.  Updated it and pages with flash media, suddenly cause a browser shut down.  Am getting fed up with the issue.  Only hope someone will come up with a fix for it.


Running Dell Inspiron 1526.

---

