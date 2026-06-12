---
title: "updates"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by bjhome on 2009-04-28
i have attached a screenshot of an error that has come up when running updates. can someone please explain and is this something i need to worry about.

---

### Post by abn91c on 2009-04-28
it is telling you that you have a 3rd party repo no longer available/out of service, if the error continues remove it

---

### Post by bjhome on 2009-04-28
absolute beginner here how do i go about removing it.

---

### Post by bjhome on 2009-04-28
and does this mean im not getting any updates

---

### Post by Partyboi2 on 2009-04-28
> **bjhome said:**
> absolute beginner here how do i go about removing it.
It looks like there is a spelling mistake in your sources.list. can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
cat /etc/apt/sources.list
```

---

### Post by bjhome on 2009-04-29
copy and pasted code then tried the update check again ,still getting the same message. do i need to shut down and restart the computer.

---

### Post by scratman on 2009-04-29
You should have had a list of code appear in the terminal.  Can you open the terminal,Application>Accessories>Terminal and then either press Ctrl+Shift+V or click Edit>Paste.
```
cat /etc/apt/sources.list >> sources.txt
```

Then if you go to Places>Home Folder there should be a new file called sources.txt.  If you open that, copy the contents, and paste them into your reply, we'll have more chance of resolving the problem.

---

### Post by bjhome on 2009-04-29
i'm still getting the error

---

### Post by bjhome on 2009-04-29
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

#ULTAMATIX REPOS START

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted

deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted

# deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

# deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
#ULTAMATIX REPOS END

---

### Post by bjhome on 2009-04-29
Do i need these updates

---

### Post by Partyboi2 on 2009-04-29
Open a terminal (Applications>Accessories>Terminal) and type or paste the following
```
gksu gedit /etc/apt/sources.list
```Once gedit has opened the sources.list file  go down to this line
```
deb [http://repoubuntusoftware.info]("http://repoubuntusoftware.info/") harty all
```and change it to
```
 deb [http://repoubuntusoftware.info]("http://repoubuntusoftware.info/") hardy all
```Then go down to the 2nd entry of
```
 deb [http://repoubuntusoftware.info]("http://repoubuntusoftware.info/") harty all
``` and place a # infront of the line so it will become
```
# deb [http://repoubuntusoftware.info]("http://repoubuntusoftware.info/") harty all
``` You will need to put a # in front of the following lines also as you have duplicate entries. 
```
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

``` Then save the changes and close gedit, then back in the terminal
```
sudo apt-get update
``````
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

#ULTAMATIX REPOS START

deb [http://repoubuntusoftware.info]("http://repoubuntusoftware.info/") har**[COLOR=Red]t[/COLOR]**y all

**[COLOR=Red]#[/COLOR]** deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

**[COLOR=Red]# [/COLOR]**deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

**[COLOR=Red]# [/COLOR]**deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

**[COLOR=Red]#[/COLOR]** deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

**[COLOR=Red]# [/COLOR]**deb [http://repoubuntusoftware.info]("http://repoubuntusoftware.info/") harty all

  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted

  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted

  deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

  deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted

# deb [http://repoubuntusoftware.info]("http://repoubuntusoftware.info/") harty all

# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

# deb [http://repoubuntusoftware.info]("http://repoubuntusoftware.info/") harty all

# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
#ULTAMATIX REPOS END
```

---

### Post by bjhome on 2009-04-29
i have done the above and i am still getting the screenshot i posted at the beginning. does this mean my computer is not up to date and secure.

---

### Post by Partyboi2 on 2009-04-29
can you post the output to
```
sudo apt-get update
```

---

### Post by bjhome on 2009-04-29
bev@bev-laptop:~$ sudo apt-get update
[sudo] password for bev: 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/universe Translation-en_NZ              
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/multiverse Translation-en_NZ            
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates/universe Translation-en_NZ      
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates/multiverse Translation-en_NZ    
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy Release                                 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates Release                         
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/universe Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_NZ       
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy Release.gpg                           
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy/all Translation-en_NZ                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_NZ     
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/universe Sources              
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/multiverse Packages           
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy/multiverse Sources            
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates/universe Packages     
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-updates/multiverse Packages   
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy Release                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_NZ
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_NZ
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                       
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy/all Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Err [http://repoubuntusoftware.info](http://repoubuntusoftware.info) hardy/all Packages
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
W: Failed to fetch [http://repoubuntusoftware.info/dists/hardy/all/binary-i386/Packages.gz](http://repoubuntusoftware.info/dists/hardy/all/binary-i386/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
bev@bev-laptop:~$

---

### Post by bjhome on 2009-04-29
this is what i get

---

### Post by Partyboi2 on 2009-04-29
Open up your sources.list again 
```
gksu gedit /etc/apt/sources.list
```
and comment out the 
```
deb http://repoubuntusoftware.info/ hardy all
``` line
so it becomes
```
# deb http://repoubuntusoftware.info/ hardy all
``` then save the changes and back in the terminal
```
sudo apt-get update
```

---

### Post by bjhome on 2009-04-29
thanks heaps i think i finally have it.

---

