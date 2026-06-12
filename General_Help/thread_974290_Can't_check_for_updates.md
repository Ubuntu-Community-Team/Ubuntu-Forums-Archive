---
title: "Can't check for updates"
date: 2008-11-07
forum: General Help
---

### Post by rasmus91 on 2008-11-07
Hey

I just tried to update, haven't been able to do that for eleven days now. the message i get is:

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

"Method gave invalid 400 URI Failure message"


I'm pretty annoyed about this, do you have any idea of what to do about this?

Thanks in advance

---

### Post by Yellow Pasque on 2008-11-07
Please post output of 
```
cat /etc/apt/sources.list
```

---

### Post by cdtech on 2008-11-07
Have you tried to change the "Download from" in the "Software sources"?

---

### Post by rasmus91 on 2008-11-09
```
rasmus@rasmus-DellE6400:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

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
# deb http://dk.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb http://packages.dfreer.org gutsy main
deb mirror://www.getdeb.net/playdeb-mirror/hardy/// hardy/

```

this is the output.

Yeah, did change it from denmark to main server. no difference

---

### Post by rasmus91 on 2008-11-09
Just tried cutting of the updates for playdeb hardy and intrepid. Now i get this error message > Failed to fetch [http://packages.dfreer.org/dists/gutsy/main/binary-amd64/Packages.gz](http://packages.dfreer.org/dists/gutsy/main/binary-amd64/Packages.gz)  302 Found
Some index files failed to download, they have been ignored, or old ones used instead.

What the heck should i do? My system was last updated 13 days ago!

---

### Post by cdtech on 2008-11-09
I've tried to hit all of the sources you have listed and they all connect except for this one:
deb mirror://www.getdeb.net/playdeb-mirror/hardy/// hardy/

I would comment this line and see what you get. Other than that they all work fine...

Hope this helps......

---

### Post by rasmus91 on 2008-11-09
> I've tried to hit all of the sources you have listed and they all connect except for this one:
deb mirror://www.getdeb.net/playdeb-mirror/hardy/// hardy/

I would comment this line and see what you get. Other than that they all work fine...

Hope this helps...... 

Sorry, i don't understand what you mean. can you explain this in anorther way?

---

### Post by rasmus91 on 2008-11-10
Do i have to make a reinstall? Well if i don't get any more help i think thats what i'm gonna do... What ever... it doesn't take a long time

---

### Post by bryncoles on 2008-11-10
just wondering, are you using hardy or intrepid...? i ask because one of your sources is for hardy. might be an issue if you're using intrepid...

and 'comment out' means add a hash symbol (#) to the start of the line, as this'll tell ubuntu to ignore that line. net result is that you wont check that repo, which should resolve your error message. 

you could also try updating that repo to intrepid (assuming you're using intrepid)

---

### Post by kostkon on 2008-11-10
> **rasmus91 said:**
> Do i have to make a reinstall? Well if i don't get any more help i think thats what i'm gonna do... What ever... it doesn't take a long time
Instead of playing with configuration files as some more advanced users are advising you to do (wrongly, in my opinion), you can easily access (and modify, add, remove, etc) your third party repositories in *System -> Administration -> Software Sources* in the *Third-Party* tab.

---

### Post by dburnett77 on 2008-11-10
I was curious about the 400 URI error, and it seems the playdeb.net server causes apt to crash when it has an issue.

Here's the launchpad URL:

[https://bugs.launchpad.net/playdeb/+bug/278635](https://bugs.launchpad.net/playdeb/+bug/278635)

---

### Post by rasmus91 on 2008-11-11
I am using intrepid, but the only lines i've added are those for playdeb 

sure, I'll try that

---

### Post by jmate24 on 2008-11-11
i think that the servers are closed due to the removal of feisty and it's repository from their servers.

---

### Post by rasmus91 on 2008-11-13
Disabled them all, now i can update

---

