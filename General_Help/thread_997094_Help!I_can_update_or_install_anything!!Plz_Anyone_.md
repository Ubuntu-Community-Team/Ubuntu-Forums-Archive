---
title: "Help!I can update or install anything!!Plz Anyone have The Solution??????"
date: 2008-11-29
forum: General Help
---

### Post by DizzyEwok on 2008-11-29
Hi this is my second post, i have been using ubuntu for about 6 months.
Currently i am using Hardy.
My problem is that when I try to update ubuntu or install any program through terminal these errors appear:
Installing Through Terminal:

Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

And for the updating:

An error occured, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.
The error message was: 'Error opening the cache (E:Problem parsing dependency depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.)' THis usually means that your installed packages may have unmet dependencies


I have tried everything I know(not much)!And have tried everything that it lists in the error message.

Anyone have a solution????????
Thanks

---

### Post by oldos2er on 2008-11-29
Check System, Administration, Software Sources to make sure all your repositories are enabled.

---

### Post by DizzyEwok on 2008-11-29
> **oldos2er said:**
> Check System, Administration, Software Sources to make sure all your repositories are enabled.

I tried that and it didnt work.
Thx anyway though

---

### Post by oldos2er on 2008-11-29
Hmmm. You could try making a backup copy of this file: /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, then delete it (the original, not the copy!), then run the command "sudo aptitude update && sudo aptitude safe-upgrade".

---

### Post by TheLions on 2008-11-29
the easiest way is to go in recovery mode and pick fix repositories!
5 minute work!

---

### Post by DizzyEwok on 2008-12-05
> **TheLions said:**
> the easiest way is to go in recovery mode and pick fix repositories!
5 minute work!
I went into recovery mode and it gave me 3 options I tried all of them and nothing has happened...I think I may have to edit the file in some way??

---

### Post by plucky on 2008-12-05
Open a terminal and ```
cat /etc/apt/sources.list
``` and post the output to the forum between [noparse]```

```[/noparse] tags.

> /var/lib/apt/lists/repoubuntusoftware.info_dists_[color=red]harty[/color]_all_binary-i386_Packages,

There is something wrong with one of your repos.

Good Luck

---

### Post by mkvnmtr on 2008-12-05
Ok I haven't had this problem but I have an idea. If you go to your package manager and click on custom filters and then on broken you should get a list of all packages that are broken. Broken packages are packages that don't have all their dependences . If you remove these packages would not that fix your problem? Then if you want them back the will be installed with everything they need.   OHHHHHH I said I had never had this problem. AI think I had it in 6.06 and this is the way I fixed it. My problem now is I am kind of old and forget stuff.

---

### Post by DizzyEwok on 2008-12-06
> **plucky said:**
> Open a terminal and ```
cat /etc/apt/sources.list
``` and post the output to the forum between [noparse]```

```[/noparse] tags.



There is something wrong with one of your repos.

Good Luck
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe


deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

#ULTAMATIX REPOS START

deb http://repoubuntusoftware.info harty all

deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse main universe restricted

deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse main universe restricted

deb http://repoubuntusoftware.info harty all

deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-security multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ hardy-security multiverse

deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-security universe

deb http://gb.archive.ubuntu.com/ubuntu/ hardy-security universe

deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-security main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ hardy-security main restricted

deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.canonical.com/ubuntu hardy partner
#ULTAMATIX REPOS END

```

---

### Post by DizzyEwok on 2008-12-06
> **mkvnmtr said:**
> Ok I haven't had this problem but I have an idea. If you go to your package manager and click on custom filters and then on broken you should get a list of all packages that are broken. Broken packages are packages that don't have all their dependences . If you remove these packages would not that fix your problem? Then if you want them back the will be installed with everything they need.   OHHHHHH I said I had never had this problem. AI think I had it in 6.06 and this is the way I fixed it. My problem now is I am kind of old and forget stuff.
Thanks for teh suggestion but it won't let me open Synaptic.
Sorry

---

### Post by plucky on 2008-12-06
Can you not see what is wrong with your sources.list?

Compare it with mine.


```
# 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse

```


I recommend you use my Hardy sources.list and do not use ULTAMIX to update your repos.


Good Luck

---

### Post by DizzyEwok on 2008-12-07
> **plucky said:**
> Can you not see what is wrong with your sources.list?

Compare it with mine.


```
# 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse

```


I recommend you use my Hardy sources.list and do not use ULTAMIX to update your repos.


Good Luck

Thankyou so much it is totally fixed now!!!!!

---

