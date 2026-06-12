---
title: "Help!! my Download/ Update manger is broken"
date: 2008-10-20
forum: General Help
---

### Post by itachikid on 2008-10-20
Hi in the past few weeks iv had a problem with my download manger and i can t see to get it working so i can't update or download and install manually and no one seems to have the same problem as me so here the error message so please if you can help thanks (i'm not sure why but this displays happy faces i don't know why) ((also it seems The smile face  replaces :  D no space there need them to not show face))


A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'W:Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy_multiverse_binary-i386_Packages), W:Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hardy-updates_multiverse_binary-i386_Packages), W:Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_multiverse_binary-i386_Packages), W:Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_universe_binary-i386_Packages), W:Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_hardy_free_binary-i386_Packages), W:Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_hardy_non-free_binary-i386_Packages), E:Problem parsing dependency Depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.}

---

### Post by scragar on 2008-10-20
could you do me a favour and attach the file that appears on your desktop called sources.list after you run this command, thanks.
```
cp /etc/apt/sources.list ~/Desktop/sources.list
```

---

### Post by itachikid on 2008-10-20
Here i ran the command and this is what came up (used abi word to look at it and paste)


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

#ULTAMATIX REPOS START

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe

deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
#ULTAMATIX REPOS END

---

### Post by alohadiaz on 2008-10-20
I have got the same error on both my UE 1.9 computers

E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by scragar on 2008-10-20
> ```

#ULTAMATIX REPOS START

deb http://repoubuntusoftware.info harty all

deb-src http://us.archive.ubuntu.com/ubuntu hardy-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu hardy-updates multiverse

deb-src http://us.archive.ubuntu.com/ubuntu hardy multiverse

deb http://us.archive.ubuntu.com/ubuntu hardy multiverse

deb http://repoubuntusoftware.info harty all

deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

deb http://security.ubuntu.com/ubuntu hardy-security multiverse

deb-src http://security.ubuntu.com/ubuntu hardy-security universe

deb http://security.ubuntu.com/ubuntu hardy-security universe

deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.canonical.com/ubuntu hardy partner
#ULTAMATIX REPOS END
```
what's ultamatix? and I'm sure the problem is it's excessive use of the word harty, instead of hardy.

Anyway, I've downloaded your list, and I'm going to try it in place of my own, testing 1 line at a time till I find the error, shouldn't take long, I'll reply when I've found it.


@ alohadiaz : if you could upload the file like I said in my first file I'll do the same for you when I'm done, see if I can find the error and post a correction for you.

---

### Post by scragar on 2008-10-20
OK, I ran it for myself and couldn't get the same errors as you, I've got a fix for one of the errors, but I couldn't experience the parse error you encountered(this is why I requested it as an attachment, just copy and pasted like that makes it very hard to copy the code without missing something), remove the extra copy of the line:
```
deb http://repoubuntusoftware.info harty all
```it appears twice in the section of code I quoted.

---

### Post by itachikid on 2008-10-21
i looked at the list and replaced the repeat witrh this 
deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy all
and then the other with this 

deb-src [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy all

this allowed me to download again im not sure if im still going to get some errors but so far its a step forward

---

