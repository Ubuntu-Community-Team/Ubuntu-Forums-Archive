---
title: "error in package manager"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by jacobsn on 2009-01-02
When i start package manager i get following Error

"Opening the cache  (E: Type  '"deb' is not known on line 56 in source list /etc/apt/sources.list , E: The list of sources could not be read.)"

What can i do to solve this problem.

p.s give me pleace some details i'm not the best to Ubuntu yeat ;)

---

### Post by wmoore on 2009-01-02
> **jacobsn said:**
> When i start package manager i get following Error

"Opening the cache  (E: Type  '"deb' is not known on line 56 in source list /etc/apt/sources.list , E: The list of sources could not be read.)"

What can i do to solve this problem.

p.s give me pleace some details i'm not the best to Ubuntu yeat ;)[Google search]("http://www.google.com.au/search?q=E%3A+Type+%27%22deb%27+is+not+known&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a") See the first result.

---

### Post by Partyboi2 on 2009-01-02
> **jacobsn said:**
> When i start package manager i get following Error

"Opening the cache  (E: Type  '"deb' is not known on line 56 in source list /etc/apt/sources.list , E: The list of sources could not be read.)"

What can i do to solve this problem.

p.s give me pleace some details i'm not the best to Ubuntu yeat ;)
Can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
cat /etc/apt/sources.list 
```

---

### Post by jacobsn on 2009-01-02
I have tryid following now

To open the file for editing in Ubuntu, run
 gksudo gedit /etc/apt/sources.list
Then delete the last line of the file, save and close. Then go to System->Administration->Software Sources and make sure the boxes are checked that you want. Close that, and run
 sudo apt-get update
 sudo apt-get upgrade

But then this happen when i write  " sudo apt-get update " in the terminal:

"  E: The type '"deb' is not known in line 56  in etc/apt/sources.list"

---

### Post by jacobsn on 2009-01-02
> **Partyboi2 said:**
> Can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
cat /etc/apt/sources.list 
```

then i get this message:

```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://dk.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://dk.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://dk.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy universe
deb http://dk.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://dk.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://dk.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://dk.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://dk.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
“deb http://www.getautomatix.com/apt dapper main”

```

---

### Post by wmoore on 2009-01-02
Edit the file and remove this line:
```
“deb http://www.getautomatix.com/apt dapper main”
```

---

### Post by jacobsn on 2009-01-02
> **wmoore said:**
> Edit the file and remove this line:
```
“deb http://www.getautomatix.com/apt dapper main”
```

okay.. now it works.

the guide just said one line.. and now i have deleted to lines.

---

### Post by wmoore on 2009-01-02
> **jacobsn said:**
> okay.. now it works.

the guide just said one line.. and now i have deleted to lines.I'm guessing that package manager didn't like the quotes around that line.

---

