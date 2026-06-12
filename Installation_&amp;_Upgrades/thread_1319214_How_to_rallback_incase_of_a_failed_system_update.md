---
title: "How to rallback incase of a failed system update"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by emigrant on 2009-11-08
hi all,
is there a way i can create a restore point or something like that, so that, since im going to update my system (which at the moment dosent have any issues), i want to make sure that i don't get any problems after the update.


incase if the upgrade fails, is there a way to rollback?
or is it safe to stay without updating

thank you very much.

---

### Post by donato roque on 2009-11-08
> **emigrant said:**
> hi all,
is there a way i can create a restore point or something like that, so that, since im going to update my system (which at the moment dosent have any issues), i want to make sure that i don't get any problems after the update.


incase if the upgrade fails, is there a way to rollback?
or is it safe to stay without updating

thank you very much.

I see that you're using 9.04 jaunty.  All regular ubuntu releases are supported for 18 months.  The LTS releases are supported for 3 years (desktop) and 5 years (servers).  9.04 jaunty's support will end on October 2010.  Canonical will send you security UPDATES until then.  

If you are the kind of user who does not have to use the latest version of programs and you do not have any issues with 9.04, I see no reason why you cannot continue using 9.04.  

Most people's reason for delaying an UPGRADE is they want to give the developers more time to fix bugs.  That way when they use the version all the bugs are reported, known and hopefully fixed already. 

A rollback after an UPGRADE is not possible.  It isn't like a windows patch i'm afraid.  The parallel here is if you have win7 it isn't like you can roll back to xp or vista.  If you want to go from win7 to xp you'll have to wipe the hard drive and start installing xp.

A restore point is usable if you're just configuring the behavior of a system.  The nature of an UPGRADE is beyond simple configuring.

---

### Post by emigrant on 2009-11-08
im referring to a system UPDATE not an UPGRADE (from jaunty to karmic)

---

### Post by donato roque on 2009-11-10
What sort of failure after the update?  Updates are released to solve / fix bugs.  If you want you can review the items before you commit.  Other than that you have to put some trust in the ubuntu teams who prepared the updates.

---

### Post by Mighty_Joe on 2009-11-10
> **emigrant said:**
> incase if the upgrade fails, is there a way to rollback?


No.  If you plan to do an upgrade, you'd better make sure that 9.10 works on your hardware.  Download the Live CD and use it.  Better yet, install 9.10 to a flash drive or spare hard drive.
I got burned with a failed upgrade to 7.10 that left me with a broken system.  From now on, I'm doing fresh installs to a new partition so I have the old version on its own partition to fall back on.
Oh, and if you don't have a backup of all your data, now's the time to do it.  And have a backup of the backup, preferably off-site.

---

### Post by emigrant on 2009-11-10
thanks for the suggestion Mighty_Joe

---

