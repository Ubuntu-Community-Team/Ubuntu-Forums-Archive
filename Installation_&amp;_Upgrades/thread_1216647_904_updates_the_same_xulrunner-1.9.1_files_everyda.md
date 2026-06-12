---
title: "904 updates the same xulrunner-1.9.1 files everyday"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by forestwalkerjoe on 2009-07-18
I did online update from 8:10 to 904 as a wubi In April.. and there were small issues.. but i have since been able to solve Nearly all.. except this recent issue. 
In the past 2 weeks.. i get a Daily required Update manager request. Saying there are updates. Some times they are newer updates which is ok.. be each and every day it includes this two files. EVERY SINGLE day. 

```
xulrunner-1.9.1 and xulrunner-1.9.1-gnome-support
``` I am not amazingly technical.. and i have tried to search for this issue.. but found nothing related to MY issue. i can find things about Firefox after this files update NOT working.. or other little bitties like that.. but nothing where it succeeds? or so it seems.. but comes back every single day? nothing on that at all. 
Can Some one please? help me find out what the Heck the system is doing to cause it to See it every day as needing to be updated but yet.. succeed in its "UPDATE" and then Needed it again.. tomorrow? 

Thanks 
FWJ

---

### Post by lovinglinux on 2009-07-18
It's the [Groundhog Day](http://www.imdb.com/title/tt0107048/) effect. :)

Now seriously, I have no idea what's causing this. The xulrunner-1.9.1 package is shipped with Firefox 3.5 (Shiretoko), but I'm running a compiled build, which apparently does not require it.

I will install Shiretoko and check if I get the same updates.

Have you included some PPA repositories, like *ubuntu-mozilla-daily*, *ubuntu-mozilla-security*? I'm not sure, but maybe they are updating xulrunner-1.9.1 daily ;)

---

### Post by forestwalkerjoe on 2009-07-19
well.. a guy was helping me in here to install the 3.5 , was that you? and we found that there were multiple tries on my part to install.. which all failed.. you/he had me uninstall some stuff and try again and then it worked. 
I dont think its the sheriko version.. or whatever its called.. but.. I do know that this issue didn't start before that install.. but after. Is there a PPA or what ever that is.. in here? its likely.. i tried a few different attempts to get an update or try to install.. so its likely there is some  hanger on. BUT i have not the first clue how to recognize which is which and what to remove and how. 

I'll be truly waiting for your data. Do you have any sort of Terminal code you want me to try , so i can show you some sort of internal details? 

thanks for helping agian. 

FWJ

---

### Post by forestwalkerjoe on 2009-07-20
yesterday, as has been true for a little while.. there was a selection of updates.. including this xulrunner.. today there was another set of updates.. but for the first time in two weeks.. NO Xulrunner update. 
i have checked it.. ran update manager on its own.. the whole bit.. but.. some how.. it seems maybe its not doing the repeat. 

I hope you will answer though.. it might return.. and i would like to find a way to make sure there is nothing wrong in my system. 

FWJ

---

### Post by lovinglinux on 2009-07-21
> **forestwalkerjoe said:**
> well.. a guy was helping me in here to install the 3.5 , was that you? and we found that there were multiple tries on my part to install.. which all failed.. you/he had me uninstall some stuff and try again and then it worked. 

I guess so.

> **forestwalkerjoe said:**
> 

Run the command below to open your software sources list then paste the contents of the file her:

```
gedit /etc/apt/sources.list
```


[QUOTE=forestwalkerjoe;7648226]yesterday, as has been true for a little while.. there was a selection of updates.. including this xulrunner.. today there was another set of updates.. but for the first time in two weeks.. NO Xulrunner update. 
i have checked it.. ran update manager on its own.. the whole bit.. but.. some how.. it seems maybe its not doing the repeat. 

I hope you will answer though.. it might return.. and i would like to find a way to make sure there is nothing wrong in my system. 

FWJ

It seems that you might have enabled an extra repository for Firefox, so xulrunner is being update regularly. I don't think you have a problem, but once you post the results of the command above we will be able to find out.

---

### Post by forestwalkerjoe on 2009-07-21
and today it came back again. there have also been some great Grey out Freezes.. some thing is wrong. 

here is the OUPUT you requested. its long. sorry. 

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
# PulseAudio Fixes - http://ubuntuforums.org/showthread.php?t=789578
# deb http://ppa.launchpad.net/psyke83/ubuntu jaunty main # disabled on upgrade to jaunty
# deb-src http://ppa.launchpad.net/psyke83/ubuntu jaunty main # disabled on upgrade to jaunty
deb http://packages.medibuntu.org/ jaunty free non-free # disabled on upgrade to jaunty
# deb-src http://packages.medibuntu.org/ jaunty free non-free # disabled on upgrade to jaunty
deb http://security.ubuntu.com/ubuntu/ jaunty-security restricted main multiverse universe
# deb http://packages.medibuntu.org/ jaunty free non-free # disabled on upgrade to jaunty
# deb http://wine.budgetdedicated.com/apt jaunty main # disabled on upgrade to jaunty
# deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu jaunty main # disabled on upgrade to jaunty
# deb http://ppa.launchpad.net/c-korn/ubuntu jaunty main # disabled on upgrade to jaunty
# deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu jaunty main # disabled on upgrade to jaunty
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main

deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
# deb http://us.archive.ubuntu.com/ubuntu edgy universe
# deb http://wine.budgetdedicated.com/apt edgy main
```

---

### Post by eternalsword on 2009-07-21
```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
```

there's your culprit.

---

### Post by lovinglinux on 2009-07-23
> **eternalsword said:**
> ```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
```

there's your culprit.

Yep. As I suspected, there is nothing wrong with the OP system, they are just updates from ubuntu-mozilla-daily.

You can disable it. Go to "System >> Administration >> Software Sources >> Thisrd-party Software" and disable the option deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main

---

### Post by forestwalkerjoe on 2009-07-24
ok.. i don't understand.. This Jaunty Main PPA thing.. it's not supposed to be there? now that i have turned it off.. will i be missing important updates? or was this just a repeat that should not have been there? 

FWJ

---

### Post by lovinglinux on 2009-07-24
> **forestwalkerjoe said:**
> ok.. i don't understand.. This Jaunty Main PPA thing.. it's not supposed to be there? now that i have turned it off.. will i be missing important updates? or was this just a repeat that should not have been there? 

FWJ

It's not a repeat, it's an extra repository. The "main" part of the address is referring to the main repository of *ubuntu-mozilla-daily* not the main repository for Ubuntu.

For example, the source updates only wine, with packages from wine.budgetdedicated.com:

```
deb http:/**/wine.budgetdedicated.com**/apt jaunty **main**
```

In the other hand, the source below updates only mozilla applications, with packages from ppa.launchpad.net/ubuntu-mozilla-daily.

```
deb [http://**ppa.launchpad.net/ubuntu-mozilla-daily](http://**ppa.launchpad.net/ubuntu-mozilla-daily)**/ppa/ubuntu jaunty **main**
```

As you can see, they are completely different repositories, that updates different applications.

---

### Post by forestwalkerjoe on 2009-07-25
So it will not cause me to miss some thing important now that i have taken that one out? 
well, i am sure its not surprise to you that today, one day later, i have not received any sort of update for this RUNNER thing. 
I'll post back in a couple days if its still holding strong. 


FWJ

---

### Post by lovinglinux on 2009-07-25
> **forestwalkerjoe said:**
> So it will not cause me to miss some thing important now that i have taken that one out? 

If you delete only the *ubuntu-mozilla-daily*, then no. You won't miss anything.

---

### Post by dbd on 2009-07-27
I've had the same problem, have made the fix suggested, and now xulrunner doesn't want to update anymore.

But I'm worried that I've got a daily version of xulrunner still installed, which may well be buggy compared to the last stable release. How do I downgrade to the last stable release?

Thanks

---

### Post by lovinglinux on 2009-07-27
> **dbd said:**
> I've had the same problem, have made the fix suggested, and now xulrunner doesn't want to update anymore.

But I'm worried that I've got a daily version of xulrunner still installed, which may well be buggy compared to the last stable release. How do I downgrade to the last stable release?

Thanks

```
sudo apt-get remove firefox-3.5
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install firefox-3.5
```

---

### Post by dbd on 2009-07-27
Thanks, that seems to have done it.

---

### Post by forestwalkerjoe on 2009-08-06
yeah.. so, i am finally able to get back with you.. the removal of that DAILY update thing.. did the trick.. i have a had some other types of updates now.. and once in a while one of those is the XULRUNNER.. but they seem valid and not glitchy. 
I have run into another type of problem.. however. 
Since i put the version 3.5 of Firefox in my system.. i have noticed that some times when i click in a web page.. the screen will turn Grey.. seem to freeze for about 15 to 20 seconds.. and then finally let loose again. I do like the version 3.5 quite a bit.. with that one serious glitch. If any one else has had similar experience.. please let me know what you have done as a solve?
FWJ

---

### Post by lovinglinux on 2009-08-06
> **forestwalkerjoe said:**
> yeah.. so, i am finally able to get back with you.. the removal of that DAILY update thing.. did the trick.. i have a had some other types of updates now.. and once in a while one of those is the XULRUNNER.. but they seem valid and not glitchy. 
I have run into another type of problem.. however. 
Since i put the version 3.5 of Firefox in my system.. i have noticed that some times when i click in a web page.. the screen will turn Grey.. seem to freeze for about 15 to 20 seconds.. and then finally let loose again. I do like the version 3.5 quite a bit.. with that one serious glitch. If any one else has had similar experience.. please let me know what you have done as a solve?
FWJ

See **Solution** [*[COLOR="Red"]**FOT010**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT010).

---

### Post by forestwalkerjoe on 2010-04-02
I am very Tired.. laid off for a long time.. for those of you who knew me.. i was obsessive
I am trying to find my own forum page.. i cant not focus long enough to even find the Forums itself. please send me links to Seerson @ gmail com I am now recently connected Via a very slim WIFI connection. it works but its giving me a hard time on the barest minumum for the Updates i have NOT gotten.. i can not seem to figure out how to change any thing.. as i have not been using this system for much of any thing.. i believe i must have shut off the AUTO download of Updates and a bunch of other FUN things.. 
Please help me out.. it is taken me hours to even FIND the pages here.. and now i just cant find where i am supposed to be.. I MAY need a bunch more help.. thanks FANS 

Forestwalkerjoe

---

