---
title: "[SOLVED] Best way to upgrade ???"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by jfl on 2009-01-04
Hi,

I have Hardy and XP installed on a Lenovo R61 laptop.
I have the */home* on a separate partition.
It took me some time to have everything work "my way".

For some reason the upgrade bug bit me, I want to upgrade to 8.10.
Why ? ........... because it is there !!!!

**Question**:  What is the best route to upgrade with minimal chances of loosing my present configuration ???
**Alternate CD  or  Network upgrade (DSL).**
Why ?

Thanks !!!

---

### Post by logos34 on 2009-01-05
I prefer a clean install straight from the alternate cd--eliminates potential download problems and is faster.  
> 
[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)

Clean Install Upgrade (not recommended)

If your /home directory is contained on a separate hard-disk partition you should be able to upgrade by performing a clean install of the current release of Ubuntu and 'adopting' the old /home directory.

Back-up any important data before following this procedure as data loss is possible, and very well may be likely.

1. Obtain an installation CD for the release of Ubuntu you wish to install, and boot from it.
   
2. Start the installation process. When you reach the Prepare disk space stage of installation, choose the Manual option and press Forward.

3. Identify your current '/' (root) partition. Select '/' as the mount point and ensure that Format is ticked. You will lose all data on this partition and the new version of Ubuntu will be installed there instead.

4. Identify your swap partition and set its mount point as 'swap'.

[COLOR="Red"]5. Identify your /home partition. Set its mount point as '/home' and make sure that Format is** not** ticked.[/COLOR]

6. Continue installation as normal until you reach the Who are you? stage, enter a username and password which exactly match your current username and password.
   
7. Complete the installation as normal. 

Once the installation has completed, you should be able to log in to Ubuntu and your /home partition with all of your documents and settings should be intact.

---

### Post by jrusso2 on 2009-01-05
I did the network install worked fine.  Only thing I do first is rem out any non standard repos.

---

### Post by binbash on 2009-01-05
I prefer alternate cd

---

### Post by jfl on 2009-01-05
Thanks !!!

Well, 3 options and 3 different suggestions  :)

Clean install is my last choice; I'd rather take a chance of not having to hunt for, download, install and tweak all the apps I am using ...
Getting the Garmin GPS to connect was no fun.

I had good luck with the network upgrade last time - Gutsy to Hardy - so I'll give it a shot.
What is your thinking for unchecking the "non standard repos" ?

I'll let you know how it goes, if I can :D

jfl

---

### Post by jfl on 2009-01-05
SUCCESS !!!  :D :D :D

The network upgrade worked beyond my wildest dreams !!!
I updated my system just before starting the upgrade.
It took the best part of 2 hours; when it rebooted, I thought I was still in Hardy, everything was the same except the background image; all my little apps worked as before.
Kudos to the Ubuntu team, it has come a long way ... had a few nightmares in 2006-2007 doing upgrades.

I am so glad I didn't do a "clean install"; I'd be spending a couple of days, at best, trying to remember where I got what...

This year starts well !

---

