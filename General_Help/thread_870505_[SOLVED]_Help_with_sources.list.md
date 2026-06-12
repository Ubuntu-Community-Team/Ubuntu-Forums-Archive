---
title: "[SOLVED] Help with sources.list"
date: 2008-07-25
forum: General Help
---

### Post by macmichael01 on 2008-07-25
Hello I have to ask this newbish question b/c I honestly don't know the answer. Whenever I reinstall a version of unbutu I always have some issue with sources.list. I don't seem to have all of my deb sources and I am not sure why. when I try to install something as simple as python or postgres, ubuntu can't find everything it needs. Below is what my sources.list file currently looks like. If there are some additional sources that I need to add, how do I do them and why aren't they commented out for me to enable like they were in the previous versions?

```
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy mai$

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

Any ideas? thanks in advance for this newbish question!

---

### Post by Oldsoldier2003 on 2008-07-25
replace mirror.anl.gov with the mirror you want to use.
```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Alpha i386 (20080306.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
deb http://mirror.anl.gov/pub/ubuntu/ hardy main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.anl.gov/pub/ubuntu/ hardy-updates main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mirror.anl.gov/pub/ubuntu/ hardy universe
deb-src http://mirror.anl.gov/pub/ubuntu/ hardy universe
deb http://mirror.anl.gov/pub/ubuntu/ hardy-updates universe
deb-src http://mirror.anl.gov/pub/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.anl.gov/pub/ubuntu/ hardy multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ hardy multiverse
deb http://mirror.anl.gov/pub/ubuntu/ hardy-updates multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ hardy-updates multiverse

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
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://mirror.anl.gov/pub/ubuntu/ hardy-security main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ hardy-security main restricted
deb http://mirror.anl.gov/pub/ubuntu/ hardy-security universe
deb-src http://mirror.anl.gov/pub/ubuntu/ hardy-security universe
deb http://mirror.anl.gov/pub/ubuntu/ hardy-security multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ hardy-security multiverse
```

*Moved thread to General Help*

---

### Post by macmichael01 on 2008-07-25
Thank alot seems to have done the trick. Do you know why some of these were not in my sources file by default for me to enable? I couldn't even download mysql.

---

### Post by sandb on 2008-07-25
.

---

### Post by drs305 on 2008-07-25
macmichael01,

as you copy the above, you might want to keep your old, commented reference to the hardy cd. it's the first entry. since your's is different than the one in the post above, if you ever uncomment the cd it would probably not find the correct cd version. i think it makes a difference... hopefully not that you should ever need the cd again.

---

### Post by macmichael01 on 2008-07-25
Thanks. but the question still stands why by default did my sources.list file look like this:

```

#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy mai$

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

Why, when I reinstalled ubuntu, it did NOT put the commented out repos that I could enable in there? I couldn't install anything with out these. I am just courious as to why it did not place the commented out repos in there by default. Could it have been a simple glitch? Is there a command to tell ubuntu to put these in there my default other than CP'ing someone else's sources.list?

---

### Post by macmichael01 on 2008-07-25
Hello This thread IS NOT [SOLVED]. My orginal question was not answered can someone help or will I have to repost the question?

---

### Post by drs305 on 2008-07-26
I can't offer any insight into why your sources.list did not contain the extra information. I can tell you that when I have done either full installs or upgrades the comments have always been included, the main repositories have been enabled, and I have had to re-enable the extra repositories such as 'hardy-proposed' and 'backports' when I eventually wanted something from them.

There are times I've run commands to inspect the sources.list to view it without the comments. It almost appears that the command was run on your sources.list and then the file was copied and saved that way. The command I'm referencing is:
```
cat /etc/apt/sources.list | grep -v '#'
```

By the way, since I mentioned the commented cdrom line at the top of the sources.list, the next time you edit it you might want to change the last word from "mai$' to 'main'.

Also, I believe you can go back to the 'Thread Tools' and remove the SOLVED status should you wish to do so.

---

### Post by macmichael01 on 2008-07-26
Thanks alot for your help.

---

