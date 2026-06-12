---
title: "Selecting Software sources results in errors"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by Predatorian on 2009-05-29
i was trying to select software sources to hopefully find more programs, and i was using the ubuntu software sources program. i selected software updates, and i selected the important, recommended, pre-released, and unsupported updates. and then i reloaded my sources file, and now all i get is this error:

```
Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release  Unable to find expected entry  restriced/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/dists/jaunty-updates/Release  Unable to find expected entry  restriced/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/dists/jaunty/Release  Unable to find expected entry  restriced/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/dists/jaunty-security/Release  Unable to find expected entry  restriced/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/dists/jaunty-backports/Release  Unable to find expected entry  restriced/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/dists/jaunty-proposed/Release  Unable to find expected entry  restriced/binary-amd64/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
```


is there some fix i can do?

---

### Post by Partyboi2 on 2009-05-29
Hi, can you open a terminal and post your sources.list
```
cat /etc/apt/sources.list
```

---

### Post by Predatorian on 2009-05-29
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

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
# deb http://de.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner


## Virtualbox
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free

## Remastersys
deb http://www.remastersys.klikit-linux.com/repository remastersys/

## DRBL 
deb http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/ jaunty restriced main universe restricted multiverse
deb-src http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/ jaunty universe main multiverse restriced restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ jaunty-security restriced main universe restricted multiverse
deb-src http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/ jaunty-security restriced main universe restricted multiverse #Added by software-properties
deb http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/ jaunty-updates universe main multiverse restriced restricted
deb-src http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/ jaunty-updates universe main multiverse restriced restricted
deb http://free.nchc.org.tw/drbl-core drbl stable
```

---

### Post by Partyboi2 on 2009-05-29
Open up your sources.list and remove the word ```
restriced
```from your sources.list
```
gksu gedit /etc/apt/sources.list
```then remove restriced as shown in red below.
```
deb [http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/](http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/) jaunty [COLOR=Red]restriced[/COLOR] main universe restricted multiverse
deb-src [http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/](http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/) jaunty universe main multiverse [COLOR=Red]restriced[/COLOR] restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security [COLOR=Red]restriced[/COLOR] main universe restricted multiverse
deb-src [http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/](http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/) jaunty-security [COLOR=Red]restriced[/COLOR] main universe restricted multiverse #Added by software-properties
deb [http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/](http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/) jaunty-updates universe main multiverse [COLOR=Red]restriced[/COLOR] restricted
deb-src [http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/](http://ftp.uni-bayreuth.de/linux/ubuntu/ubuntu/) jaunty-updates universe main multiverse [COLOR=Red]restriced[/COLOR] restricted
deb [http://free.nchc.org.tw/drbl-core](http://free.nchc.org.tw/drbl-core) drbl stable
```
then save the changes and close gedit, afterwards in the terminal type
```
sudo apt-get update
```

---

### Post by Predatorian on 2009-05-29
thank you. it worked. is there a reason it would have done that in teh first place?

---

### Post by Partyboi2 on 2009-05-29
I am not sure what caused it. Happy to have helped. :)

---

### Post by kiwi-pete on 2009-05-31
Hi all, sorry for jumping in here but im getting the folowing error.

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-proposed/Release](http://security.ubuntu.com/ubuntu/dists/jaunty-proposed/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


But try as I might, I cannot find a cure.
This has come about since I updated from Ibex to jaunty.

---

### Post by Partyboi2 on 2009-05-31
> **kiwi-pete said:**
> Hi all, sorry for jumping in here but im getting the folowing error.

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-proposed/Release](http://security.ubuntu.com/ubuntu/dists/jaunty-proposed/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


But try as I might, I cannot find a cure.
This has come about since I updated from Ibex to jaunty. If you don't need to use the proposed repo you can open up Software Sources and under the "Updates" tab untick the box next to jaunty proposed.

---

