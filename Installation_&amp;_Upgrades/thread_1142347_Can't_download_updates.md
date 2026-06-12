---
title: "Can't download updates"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by nashikens on 2009-04-29
I'd like to upgrade to 9.04, but read I should first install all updates for 8.10.  I tired, but repeated get "failed to fetch" when using the update manager.  In terminal I used "sudo apt-get update" and was returned:
sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty Release.gpg
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty Release
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty-updates Release
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty/main Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty/main Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty/universe Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty/universe Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) jaunty-updates/multiverse Sources
Reading package lists... Done


I'm not really sure why they all say jaunty-updates when I still am running intrepid, unless it just works like that. Thought it might be my internet connection so wanted to try with a VPN, but I can't configure a VPN, it's not installed.  I can't install one because the Add/Remove programs menu can't update either.  I'm new to the whole Ubuntu scene. Any thoughts?

---

### Post by Partyboi2 on 2009-04-29
Hi, according to that output there is nothing wrong, except that it looks like you are running Jaunty not intrepid. You can check what version you are using by typing in a terminal
```
lsb_release -d
```

---

### Post by nashikens on 2009-04-29
"Ubuntu 8.10"
In the update manager it tells me there's a new dist available too (9.04)

---

### Post by Partyboi2 on 2009-04-29
Can you open a terminal and post the output to
```
cat /etc/apt/sources.list
```
and
```
 uname -r
```

---

### Post by nashikens on 2009-04-29
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
hodges@dell:~$ uname -r
2.6.27-11-generic

---

### Post by nashikens on 2009-04-29
(double post, my apologies)

---

### Post by Partyboi2 on 2009-04-29
I have no idea how you got jaunty repos. What I suggest doing is backup your current sources.list and replace it with a Intrepid source.list
In a terminal backup the current one with
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.jaunty
```then open your sources.list
```
gksu gedit /etc/apt/sources.list
``` once open delete the contents and copy and paste the Intrepid sources.list repos from [[COLOR=Blue]here[/COLOR]]("http://repogen.simplylinux.ch/") then save the changes and close gedit. Then 
```
sudo apt-get update
```

---

### Post by nashikens on 2009-04-29
Well... maybe I did that right:

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Sources
Reading package lists... Done

---

### Post by Partyboi2 on 2009-04-29
Ok go ahead and try updating your machine with
```
sudo apt-get upgrade
```

---

### Post by nashikens on 2009-04-29
That's what the previous post is.  And I think it worked, because before I had something like 700 items to update.  then after, it downloaded and finished the update in about 5 minutes, there were only a few.  I'm trying the 9.04 alternative upgrade now.  So as long as it can download the pieces from the internet I'm set. 

Thanks a lot, seems like that was the problem.  It's very bizarre too, I just installed 8.10 from a cd, clean, yesterday or the day before on that machine. Not sure how the jaunty stuff got there.

---

### Post by nashikens on 2009-04-29
(double post, really don't understand why that's happening)

---

