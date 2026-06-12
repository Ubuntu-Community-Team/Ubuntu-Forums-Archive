---
title: "Upgrade to 9.04 from 8.10 = no go, wierd error"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by YWELLC on 2009-10-29
I have been trying to update my 8.10 system to 9.04.  I tried the net-install via update-manager and got a strange error.  I then d/led and tried mounting the alternate cd.  I get the same error every time 2 mins in.  I have searched for it but not been able to find it anywhere.  The update manager calculates the changes and then I get this:

"Please insert the 'Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)' into the drive '/cdrom/'

Consequently, I have a 7.10 install disk here and have loaded in a futile attempt to appease the update manager.  No go, it is somehow unmounted (as in disappears from my desktop (don't know how to check fstab) and then the install fails.  Any help would be greatly appreciated.

Again, this is awfully strange, as I am running 8.10 64bit, not 7.10

---

### Post by running_rabbit07 on 2009-10-29
> **YWELLC said:**
> I have been trying to update my 8.10 system to 9.04.  I tried the net-install via update-manager and got a strange error.  I then d/led and tried mounting the alternate cd.  I get the same error every time 2 mins in.  I have searched for it but not been able to find it anywhere.  The update manager calculates the changes and then I get this:

"Please insert the 'Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)' into the drive '/cdrom/'

Consequently, I have a 7.10 install disk here and have loaded in a futile attempt to appease the update manager.  No go, it is somehow unmounted (as in disappears from my desktop (don't know how to check fstab) and then the install fails.  Any help would be greatly appreciated.

Again, this is awfully strange, as I am running 8.10 64bit, not 7.10
Use your alternate installer disk and do a clean install without formatting the /home partition.

---

### Post by YWELLC on 2009-10-29
I have a fairly complicated partition scheme that made sense a while ago when I performed it.  I also have some 3rd party apps, like Tor and Virtualbox with an XP install that I would prefer not to mess up.  Can I burn the .iso to disk and perform a clean install w/o screwing the poach on everything else? From GParted:

/dev/sda1 ntfs 7.81 MiB ---> defunct dual boot XP install
/dev/sda ext3 / 35.87 GiB
/dev/sda3 ext3 /home 172.85 GiB
/dev/sda4 extended 24.10 GiB
   /dev/sda5 ext3 /usr
   /dev/sda5 linux-swap 8.95 Gib

---

### Post by running_rabbit07 on 2009-10-29
I honestly don't know. I have never messed with that scheme to know what is where. If your system is up and running still, I'd say leave it alone until you can get a good answer.

---

### Post by running_rabbit07 on 2009-10-29
I think it screwed up your sources list, and that is why you are having these problems.

---

### Post by YWELLC on 2009-10-29
I appreciate the advice and agree and will wait.  On the last upgrade the woman lost something like 10% of here photos to some disk errors.  I still hear about it often before I go to bed (that was a year ago)...

---

### Post by running_rabbit07 on 2009-10-29
> **YWELLC said:**
> I appreciate the advice and agree and will wait.  On the last upgrade the woman lost something like 10% of here photos to some disk errors.  I still hear about it often before I go to bed (that was a year ago)...

You may want to back that stuff up if you can.

---

### Post by YWELLC on 2009-10-29
Here it is:

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb http://mirrors.kernel.org/ubuntu intrepid main universe

## experimental tor sites
##deb http://mirror.noreply.org/pub/tor hardy main
##deb-src http://mirror.noreply.org/pub/tor hardy main
##deb http://mirror.noreply.org/pub/tor experimental-0.2.0.x-hardy main
##deb-src http://mirror.noreply.org/pub/tor experimental-0.2.0.x-hardy main
## end expiremental tor sites
## non-experiemental tor
deb http://mirror.noreply.org/pub/tor intrepid main
deb-src http://mirror.noreply.org/pub/tor intrepid main
##

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse


deb http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
```

Good answer, and I'm gonna go ahead and blank out that first one and try it again!

---

### Post by YWELLC on 2009-10-29
LOL, looks like bingo on that one.  I failed to back up the photos, so if they get clobbered, I'm blaming it on you and sending her your way!

Thank you for the advice, it was spot on (and I'm kinda a moron for not looking sources.list before).

I will change this to "solved" when I restart my computer and can still get on the internet! :-)

---

### Post by joewski on 2009-10-29
> **YWELLC said:**
> Here it is:

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb http://mirrors.kernel.org/ubuntu intrepid main universe

## experimental tor sites
##deb http://mirror.noreply.org/pub/tor hardy main
##deb-src http://mirror.noreply.org/pub/tor hardy main
##deb http://mirror.noreply.org/pub/tor experimental-0.2.0.x-hardy main
##deb-src http://mirror.noreply.org/pub/tor experimental-0.2.0.x-hardy main
## end expiremental tor sites
## non-experiemental tor
deb http://mirror.noreply.org/pub/tor intrepid main
deb-src http://mirror.noreply.org/pub/tor intrepid main
##

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse


deb http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
```

Good answer, and I'm gonna go ahead and blank out that first one and try it again!

If there is any chance, you have to edit these file and fix it up.
My basic method is to rename everything to Karmic ie intrepid become karmic, jaunty becomes karmic. 
When you update you will get errors. using something like sudo aptitude update.
To fix those errors you need to comment out or delete those lines in this file. Make a note on a piece of paper so you can go back to the web site to fix those entries to the correct place for karmic.

When you edited the file. Run update-manager again and continue to upgrade. Eventually all the packages you have will be upgraded.

Be warned the lastest version of virtualbox (the .10) crashes VM's so stick with the .08 version. You may need to downgrade this like I did.

Hope that is of some help. So far I have done two in place upgrades to 9.10 from 9.04 using a third party repository, which just made the whole thing complicated.

---

### Post by running_rabbit07 on 2009-10-29
> **joewski said:**
> If there is any chance, you have to edit these file and fix it up.
My basic method is to rename everything to Karmic ie intrepid become karmic, jaunty becomes karmic. 
When you update you will get errors. using something like sudo aptitude update.
To fix those errors you need to comment out or delete those lines in this file. Make a note on a piece of paper so you can go back to the web site to fix those entries to the correct place for karmic.

When you edited the file. Run update-manager again and continue to upgrade. Eventually all the packages you have will be upgraded.

Be warned the lastest version of virtualbox (the .10) crashes VM's so stick with the .08 version. You may need to downgrade this like I did.

Hope that is of some help. So far I have done two in place upgrades to 9.10 from 9.04 using a third party repository, which just made the whole thing complicated.

I didn't realize they upgrade vbox again. That must be very new. I haven't ran it in two days.

---

### Post by JBAlaska on 2009-10-29
I know in your OP, you said you wanted to upgrade to 9.04 but I think now that 9.10 final is out you should go that route.

Since you have separate /home and /usr partitions, you should not loose any personal files on a upgrade (I say should cause ..well you know..).

Your software sources are all over the map,with CD-ROM sources pointing to 7.10 and 8.04, and repositories pointing every which way.

I think if you fix this, you should be ok for a net-install, If you do a iso install this should be overwritten for you.

Good luck and for gosh sake back up the womans files first LOL.

---

