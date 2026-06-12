---
title: "[SOLVED] Repository Failure"
date: 2008-09-17
forum: General Help
---

### Post by bravo351 on 2008-09-17
Downloads and installs no longer available in my Hardy.  Receiving error in reads of lines 40, 42, and 47 in /etc/apt/sources.list that preclude the use of Synaptic, apt-get's, and any further updates.

I am a noob to Linux (even worse, a Windows rat), and would appreciate any input on this problem.  Thank you for your time, in advance!

---

### Post by kostkon on 2008-09-17
> **bravo351 said:**
> Downloads and installs no longer available in my Hardy.  Receiving error in reads of lines 40, 42, and 47 in /etc/apt/sources.list that preclude the use of Synaptic, apt-get's, and any further updates.

I am a noob to Linux (even worse, a Windows rat), and would appreciate any input on this problem.  Thank you for your time, in advance!
Could you please paste here the output of your *sources.list* file? To do it, open a terminal (i.e. *Applications -> Accessories -> Terminal*) and give:
```
gedit /etc/apt/sources.list
```

---

### Post by drs305 on 2008-09-17
No problem. Just run the following command and post the results here:

```
cat /etc/apt/sources.list
```

We'll be able to figure it out.

---

### Post by drs305 on 2008-09-17
Make a backup of the file and open for editing. The "+40" will open gedit with the cursor on line 40, where your first problem is:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
gksu gedit +40 /etc/apt/sources.list

```

If you don't see the problems with the lines you mentioned above, post the results. Once things are corrected, hit "Reload" in synaptic or software sources or run the following in terminal:

```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by bravo351 on 2008-09-17
eb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse #Added by software-properties
e
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe main multiverse restricted #Added by software-properties


This is output of /etc/apt/sources.list.  I cannot make heads or tails of it.

---

### Post by drs305 on 2008-09-17
It was probably a cut/paste error on line 1, but here's what to look at:

line 1:  **eb**  should be **deb**
line 42:  remove the **e** on the line by itself.

If the "#Added by software-properties" spills over to another line, make sure it is all one joined line that is wrapped and not a separate line with **properties** as a new line entry.

In fact, just remove the entries **# Added by software properties** entirely.

Those are the errors I see right off the bat. Make those changes, then run the last commands from my previous post. If you get more errors, let us know what they say.

PS. If you don't want to have to insert the CD-ROM each time you do an update, you can just place a comment symbol # in front of the first line ( but change it to "deb" anyway ).

---

### Post by bravo351 on 2008-09-17
drs305, you are a GOLDEN GOD!!!!!

It was just the "e" error in line 42; what I don't get is why popups spoke of an "e" error in lines 40 and 47(?)  Whatever though, problem is solved.  Thank you all for the insight, and I'm happy to be here!!!:popcorn::popcorn::popcorn::popcorn::popcorn:

---

