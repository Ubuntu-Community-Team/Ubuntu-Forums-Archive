---
title: "new install fresh ubuntu 7.04 why i cant update it?"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by Pinejoker on 2009-02-24
I need someone to help me to update my ubuntu 7.04. 

here's my error.

[IMG]http://img3.imageshack.us/img3/7960/screenshotj.png[/IMG]

---

### Post by MasterNetra on 2009-02-24
Just backup everything and do a fresh install of Hardy 8.04 or 8.10, I don't think 7.04 is supported anymore, could be wrong...but still thats what it looks like. :/

---

### Post by Pinejoker on 2009-02-24
i don't get, but i dont have fresh hardy 8.04 only i had is ubuntu 7.04.

---

### Post by avtolle on 2009-02-24
As has already been posted (IIRC) on the other thread you have opened about this problem, 7.04 reached its end of life and thus no longer supported in October, 2008; the repos were taken down and the packages moved to another site. If you will look in your other thread, you will find where I posted a link to how to upgrade from Feisty to Gutsy, which involves editing your /etc/apt/sources.list file to reflect the old packages site for Ubuntu. Apparently, you did not do this from the above error message. 

Is there something you don't understand about editing the above file? If so, post here, and someone can help you (although I'm puzzled why you don't d/l and do a fresh installation of either 8.04 or 8.10).

---

### Post by avtolle on 2009-02-24
> **Fully updating 7.04**

 Before upgrading to Ubuntu 7.10, you should make sure Ubuntu 7.04 is fully up to date. Ubuntu 7.04 does not have ongoing support and has now been removed from the normal archives and mirrors, but its packages are still available if you add these lines to your /etc/apt/sources.list file: 
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverseThe above is how you enable the old-release packages for 7.04. From reading a plethora of other threads on this Forum, you may need to comment out the existing repos and only have these as active in the /etc/apt/sources.list file.

EDIT: Once you have enabled these sites, then you should be able to upgrade 7.04 to as current a state as is possible using the Feisty packages. To go further, you will need to upgrade to a newer release.

---

### Post by Pinejoker on 2009-02-24
i found a link.. and i follow this can you check if this is correct. [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

---

### Post by MasterNetra on 2009-02-24
> **Pinejoker said:**
> i don't get, but i dont have fresh hardy 8.04 only i had is ubuntu 7.04.

You can get it free from Ubuntu.com, Just download and burn it. or you can order a cd or request a free one. (If you can download and burn it. then do it, if not buy the CD or DVD if you can, it don't cost much and it will reach you quickly via mail...of course if you can't do either then you can request a free CD but that can take up to 9 weeks to get to you.

---

### Post by avtolle on 2009-02-24
> **Pinejoker said:**
> i found a link.. and i follow this can you check if this is correct. [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)
No, that link won't help you.

EDIT: Again, look at [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by Pinejoker on 2009-02-24
well.. i dont have cd burn.. is there other way to update my ubuntu 7.04 by replacing the files inside of my source list?

---

### Post by avtolle on 2009-02-24
> **Pinejoker said:**
> well.. i dont have cd burn.. is there other way to update my ubuntu 7.04 by replacing the files inside of my source list?
I've read other threads where **some** posters have had success with that (understanding your question to be whether you could upgrade by changing each occurrence of feisty to gutsy), and **some** others have had major problems. If you decide to try it, after editing your */etc/apt/sources.list* to reflect gutsy rather than feisty, then (as I recall) from terminal do```
sudo aptitude update
sudo aptitude dist-upgrade
```**but** you do this at your own risk.

---

### Post by Pinejoker on 2009-02-24
but i cant fully update my ubuntu 7.04 because i have errors while doing the updating.

---

### Post by avtolle on 2009-02-24
Take a look at [http://ubuntuforums.org/showthread.php?t=1078737](http://ubuntuforums.org/showthread.php?t=1078737) and do what is suggested in post 3.

EDIT: My mistake, should be post #4.

---

### Post by Pinejoker on 2009-02-24
so what is exactly do i need to do to update it? i mean in the changing of the old files? on source list? can you make me one? so i can update mine?

---

### Post by avtolle on 2009-02-24
> **Pinejoker said:**
> so what is exactly do i need to do to update it? i mean in the changing of the old files? on source list? can you make me one? so i can update mine?deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
should be changed to read
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted

You would do this for each repository url that you have in your /etc/apt/sources.list file. Use either ```
gksudo gedit /etc/apt/sources.list
``` or```
sudo nano /etc/apt/sources.list
```or other editor of your choice with which to make these changes.

In other words, change "http://archive.ubuntu.com/ubuntu/" to read "http://old-releases.ubuntu.com/ubuntu/" throughout your *sources.list* file. Or, copy the lines I posted earlier and paste them into your /etc/apt/sources.list file and comment out (by placing a # before the line) all lines other than those copied and pasted, using your text editor of choice.

---

### Post by Pinejoker on 2009-02-24
i just  going to copy it and paste it there? do i need to remove all the file inside of my source list?


is this correct??

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse


# deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
# deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted
# should be changed to read
# deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted
# deb-src http://old-releases.ubuntu.com/ubuntu/ feisty main restricted

```

---

### Post by Pinejoker on 2009-02-24
my spec. also [IMG]http://img213.imageshack.us/img213/8664/screenshot.png[/IMG]

---

### Post by avtolle on 2009-02-24
No, you should comment out the earlier lines and uncomment these lines that you added at the bottom of your file so that these show as
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse 			 		
without the comments.

---

### Post by Pinejoker on 2009-02-24
can you edit my source code? sorry to bother im just new.. so i just copy and paste it...

---

### Post by Pinejoker on 2009-02-24
```
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse 

``` 

is this right and then save?

---

### Post by Pinejoker on 2009-02-24
here is the new one that i make.. look if this correct.



```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted
# deb-src http://old-releases.ubuntu.com/ubuntu/  feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted
# deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://old-releases.ubuntu.com/ubuntu/ feisty universe
# deb-src http://old-releases.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://old-releases.ubuntu.com/ubuntu/ feisty multiverse
# deb-src http://old-releases.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```

---

### Post by avtolle on 2009-02-24
Sorry, had to do some work. Yes, that's correct (same effect as the help you got on the other thread). Good luck.

---

### Post by Pinejoker on 2009-02-24
```
family@family-desktop:~$ sudo do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting '/tmp/tmp-1yX90/gutsy.tar.gz'
authenticate '/tmp/tmp-1yX90/gutsy.tar.gz' against '/tmp/tmp-1yX90/gutsy.tar.gz.gpg' 

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Ignored http://us.archive.ubuntu.com feisty-backports Release.gpg
Failed http://us.archive.ubuntu.com feisty-backports Release.gpg
Done http://old-releases.ubuntu.com feisty-updates Release.gpg
Done http://old-releases.ubuntu.com feisty Release.gpg
Done http://old-releases.ubuntu.com feisty-backports Release.gpg
Ignored http://us.archive.ubuntu.com feisty-backports Release
Failed http://us.archive.ubuntu.com feisty-backports Release
Done http://old-releases.ubuntu.com feisty-security Release.gpg
Done http://old-releases.ubuntu.com feisty-proposed Release.gpg
Hit http://old-releases.ubuntu.com feisty-updates Release
Done http://old-releases.ubuntu.com feisty-updates Release
Ignored http://us.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Failed http://us.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com feisty Release
Hit http://old-releases.ubuntu.com feisty-backports Release
Hit http://old-releases.ubuntu.com feisty-security Release
Done http://old-releases.ubuntu.com feisty Release
Done http://old-releases.ubuntu.com feisty-backports Release
Done http://old-releases.ubuntu.com feisty-security Release
Failed http://us.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com feisty-proposed Release
Done http://old-releases.ubuntu.com feisty-proposed Release
Hit http://old-releases.ubuntu.com feisty-updates/main Packages
Hit http://old-releases.ubuntu.com feisty-updates/restricted Packages
Hit http://old-releases.ubuntu.com feisty-updates/main Sources
Hit http://old-releases.ubuntu.com feisty-updates/restricted Sources
Hit http://old-releases.ubuntu.com feisty-updates/main Packages
Hit http://old-releases.ubuntu.com feisty-updates/restricted Packages
Hit http://old-releases.ubuntu.com feisty-updates/universe Packages
Hit http://old-releases.ubuntu.com feisty-updates/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-updates/main Sources
Hit http://old-releases.ubuntu.com feisty-updates/restricted Sources
Hit http://old-releases.ubuntu.com feisty-updates/universe Sources
Hit http://old-releases.ubuntu.com feisty-updates/multiverse Sources
Hit http://old-releases.ubuntu.com feisty/universe Packages
Hit http://old-releases.ubuntu.com feisty/universe Sources
Hit http://old-releases.ubuntu.com feisty/multiverse Packages
Hit http://old-releases.ubuntu.com feisty/multiverse Sources
Hit http://old-releases.ubuntu.com feisty-backports/main Packages
Hit http://old-releases.ubuntu.com feisty-backports/restricted Packages
Hit http://old-releases.ubuntu.com feisty-backports/universe Packages
Hit http://old-releases.ubuntu.com feisty-backports/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-backports/main Sources
Hit http://old-releases.ubuntu.com feisty-backports/restricted Sources
Hit http://old-releases.ubuntu.com feisty-backports/universe Sources
Hit http://old-releases.ubuntu.com feisty-backports/multiverse Sources
Hit http://old-releases.ubuntu.com feisty-security/main Packages
Hit http://old-releases.ubuntu.com feisty-security/restricted Packages
Hit http://old-releases.ubuntu.com feisty-security/main Sources
Hit http://old-releases.ubuntu.com feisty-security/restricted Sources
Hit http://old-releases.ubuntu.com feisty-security/universe Packages
Hit http://old-releases.ubuntu.com feisty-security/universe Sources
Hit http://old-releases.ubuntu.com feisty-security/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-security/multiverse Sources
Hit http://old-releases.ubuntu.com feisty-proposed/main Packages
Hit http://old-releases.ubuntu.com feisty-proposed/restricted Packages
Hit http://old-releases.ubuntu.com feisty-proposed/universe Packages
Hit http://old-releases.ubuntu.com feisty-proposed/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-proposed/main Sources
Hit http://old-releases.ubuntu.com feisty-proposed/restricted Sources
Hit http://old-releases.ubuntu.com feisty-proposed/universe Sources
Hit http://old-releases.ubuntu.com feisty-proposed/multiverse Sources
Done downloading            
Ignored http://us.archive.ubuntu.com feisty-backports Release.gpg
Failed http://us.archive.ubuntu.com feisty-backports Release.gpg
Done http://old-releases.ubuntu.com feisty-updates Release.gpg
Done http://old-releases.ubuntu.com feisty Release.gpg
Done http://old-releases.ubuntu.com feisty-backports Release.gpg
Ignored http://us.archive.ubuntu.com feisty-backports Release
Failed http://us.archive.ubuntu.com feisty-backports Release
Done http://old-releases.ubuntu.com feisty-security Release.gpg
Done http://old-releases.ubuntu.com feisty-proposed Release.gpg
Hit http://old-releases.ubuntu.com feisty-updates Release
Done http://old-releases.ubuntu.com feisty-updates Release
Ignored http://us.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Failed http://us.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com feisty Release
Hit http://old-releases.ubuntu.com feisty-backports Release
Hit http://old-releases.ubuntu.com feisty-security Release
Done http://old-releases.ubuntu.com feisty Release
Done http://old-releases.ubuntu.com feisty-backports Release
Done http://old-releases.ubuntu.com feisty-security Release
Failed http://us.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com feisty-proposed Release
Done http://old-releases.ubuntu.com feisty-proposed Release
Hit http://old-releases.ubuntu.com feisty-updates/main Packages
Hit http://old-releases.ubuntu.com feisty-updates/restricted Packages
Hit http://old-releases.ubuntu.com feisty-updates/main Sources
Hit http://old-releases.ubuntu.com feisty-updates/restricted Sources
Hit http://old-releases.ubuntu.com feisty-updates/main Packages
Hit http://old-releases.ubuntu.com feisty-updates/restricted Packages
Hit http://old-releases.ubuntu.com feisty-updates/universe Packages
Hit http://old-releases.ubuntu.com feisty-updates/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-updates/main Sources
Hit http://old-releases.ubuntu.com feisty-updates/restricted Sources
Hit http://old-releases.ubuntu.com feisty-updates/universe Sources
Hit http://old-releases.ubuntu.com feisty-updates/multiverse Sources
Hit http://old-releases.ubuntu.com feisty/universe Packages
Hit http://old-releases.ubuntu.com feisty/universe Sources
Hit http://old-releases.ubuntu.com feisty/multiverse Packages
Hit http://old-releases.ubuntu.com feisty/multiverse Sources
Hit http://old-releases.ubuntu.com feisty-backports/main Packages
Hit http://old-releases.ubuntu.com feisty-backports/restricted Packages
Hit http://old-releases.ubuntu.com feisty-backports/universe Packages
Hit http://old-releases.ubuntu.com feisty-backports/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-backports/main Sources
Hit http://old-releases.ubuntu.com feisty-backports/restricted Sources
Hit http://old-releases.ubuntu.com feisty-backports/universe Sources
Hit http://old-releases.ubuntu.com feisty-backports/multiverse Sources
Hit http://old-releases.ubuntu.com feisty-security/main Packages
Hit http://old-releases.ubuntu.com feisty-security/restricted Packages
Hit http://old-releases.ubuntu.com feisty-security/main Sources
Hit http://old-releases.ubuntu.com feisty-security/restricted Sources
Hit http://old-releases.ubuntu.com feisty-security/universe Packages
Hit http://old-releases.ubuntu.com feisty-security/universe Sources
Hit http://old-releases.ubuntu.com feisty-security/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-security/multiverse Sources
Hit http://old-releases.ubuntu.com feisty-proposed/main Packages
Hit http://old-releases.ubuntu.com feisty-proposed/restricted Packages
Hit http://old-releases.ubuntu.com feisty-proposed/universe Packages
Hit http://old-releases.ubuntu.com feisty-proposed/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-proposed/main Sources
Hit http://old-releases.ubuntu.com feisty-proposed/restricted Sources
Hit http://old-releases.ubuntu.com feisty-proposed/universe Sources
Hit http://old-releases.ubuntu.com feisty-proposed/multiverse Sources
Done downloading            
Ignored http://us.archive.ubuntu.com feisty-backports Release.gpg
Failed http://us.archive.ubuntu.com feisty-backports Release.gpg
Done http://old-releases.ubuntu.com feisty-updates Release.gpg
Done http://old-releases.ubuntu.com feisty Release.gpg
Done http://old-releases.ubuntu.com feisty-backports Release.gpg
Ignored http://us.archive.ubuntu.com feisty-backports Release
Failed http://us.archive.ubuntu.com feisty-backports Release
Done http://old-releases.ubuntu.com feisty-security Release.gpg
Done http://old-releases.ubuntu.com feisty-proposed Release.gpg
Hit http://old-releases.ubuntu.com feisty-updates Release
Done http://old-releases.ubuntu.com feisty-updates Release
Ignored http://us.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Failed http://us.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com feisty Release
Hit http://old-releases.ubuntu.com feisty-backports Release
Hit http://old-releases.ubuntu.com feisty-security Release
Done http://old-releases.ubuntu.com feisty Release
Done http://old-releases.ubuntu.com feisty-backports Release
Done http://old-releases.ubuntu.com feisty-security Release
Failed http://us.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com feisty-proposed Release
Done http://old-releases.ubuntu.com feisty-proposed Release
Hit http://old-releases.ubuntu.com feisty-updates/main Packages
Hit http://old-releases.ubuntu.com feisty-updates/restricted Packages
Hit http://old-releases.ubuntu.com feisty-updates/main Sources
Hit http://old-releases.ubuntu.com feisty-updates/restricted Sources
Hit http://old-releases.ubuntu.com feisty-updates/main Packages
Hit http://old-releases.ubuntu.com feisty-updates/restricted Packages
Hit http://old-releases.ubuntu.com feisty-updates/universe Packages
Hit http://old-releases.ubuntu.com feisty-updates/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-updates/main Sources
Hit http://old-releases.ubuntu.com feisty-updates/restricted Sources
Hit http://old-releases.ubuntu.com feisty-updates/universe Sources
Hit http://old-releases.ubuntu.com feisty-updates/multiverse Sources
Hit http://old-releases.ubuntu.com feisty/universe Packages
Hit http://old-releases.ubuntu.com feisty/universe Sources
Hit http://old-releases.ubuntu.com feisty/multiverse Packages
Hit http://old-releases.ubuntu.com feisty/multiverse Sources
Hit http://old-releases.ubuntu.com feisty-backports/main Packages
Hit http://old-releases.ubuntu.com feisty-backports/restricted Packages
Hit http://old-releases.ubuntu.com feisty-backports/universe Packages
Hit http://old-releases.ubuntu.com feisty-backports/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-backports/main Sources
Hit http://old-releases.ubuntu.com feisty-backports/restricted Sources
Hit http://old-releases.ubuntu.com feisty-backports/universe Sources
Hit http://old-releases.ubuntu.com feisty-backports/multiverse Sources
Hit http://old-releases.ubuntu.com feisty-security/main Packages
Hit http://old-releases.ubuntu.com feisty-security/restricted Packages
Hit http://old-releases.ubuntu.com feisty-security/main Sources
Hit http://old-releases.ubuntu.com feisty-security/restricted Sources
Hit http://old-releases.ubuntu.com feisty-security/universe Packages
Hit http://old-releases.ubuntu.com feisty-security/universe Sources
Hit http://old-releases.ubuntu.com feisty-security/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-security/multiverse Sources
Hit http://old-releases.ubuntu.com feisty-proposed/main Packages
Hit http://old-releases.ubuntu.com feisty-proposed/restricted Packages
Hit http://old-releases.ubuntu.com feisty-proposed/universe Packages
Hit http://old-releases.ubuntu.com feisty-proposed/multiverse Packages
Hit http://old-releases.ubuntu.com feisty-proposed/main Sources
Hit http://old-releases.ubuntu.com feisty-proposed/restricted Sources
Hit http://old-releases.ubuntu.com feisty-proposed/universe Sources
Hit http://old-releases.ubuntu.com feisty-proposed/multiverse Sources
Done downloading            
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

Getting upgrade prerequisites failed
The system was unable to get the prerequisites for the upgrade. The upgrade will abort now and restore the original system state.

Please report this as a bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

Restoring original system state

Aborting
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

```


what about this?

---

### Post by avtolle on 2009-02-24
The reason it failed is that you hadn't totally updated your 7.04 release before issuing it. See my post to the other thread where you are posting for my thoughts on the commands to run.

---

### Post by Pinejoker on 2009-02-24
which one?

---

### Post by avtolle on 2009-02-24
This one.
> Edit your file by deleting everything in it, then cut and paste the contents from post #7 into /etc/apt/sources.list. Then, after saving it, open a terminal and 	Code:
 	sudo aptitude update
sudo aptitude safe-upgrade
sudo aptitude dist-upgrade 
one at a time. The first command will update your repositories; the second, which you should run after the first command runs, will likely give you a lot of updates to download; the third command, which should be run after the updates generated by the second command and downloaded and installed, will pick up any kernel, etc., updates that didn't download the first time. The third command might not generate anything new, as the second command will generally get everything (but not always), so don't worry if nothing downloads after that one is issued. Hopefully, once all that is done, and you exit the terminal, you will be offered the opportunity to upgrade to 7.10.
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=6793809") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=6793809")

---

### Post by Pinejoker on 2009-02-24
how to do it? sudo aptitude safe-upgrade kernel like this???

---

### Post by avtolle on 2009-02-24
```
sudo aptitude safe-upgrade
```only.

---

### Post by Pinejoker on 2009-02-24
anyway.. i just started to reinstalled my ubuntu 7.04 because i feel that i really mess up now here... if im done here... what is the thing that i need to do to update my ubuntu 7.04 to 7.10??

---

### Post by avtolle on 2009-02-24
After reinstalling, the first thing you have to do is to edit the /etc/apt/sources.list file to add the old-release stuff to it as we have been working on most of the afternoon (my time). See the prior posts in this thread and the other one to which you have been posting to assure yourself that this has been done. Once that is done, and the old URLs have either been removed by deletion or by commenting them out, then proceed to do```
sudo aptitude update
```to make sure there aren't any of the old repository addresses still active. Then, totally update your 7.04 install by```
sudo aptitude safe-upgrade
```. If you get a message about packages being held back do```
sudo aptitude dist-upgrade
```to get those. Once your system is totally updated, get out of the terminal, make sure no other package managers are open, then go to System>Administration>Update Manager and see if there is a box at the top announcing that a new release (7.10 in your case) is available. If so, click on the Upgrade now button to begin the upgrade to 7.10.

While reading the ugrade notes, for a server network installation, it was suggested that the user just comment out the old repository lines and not delete them, such that during the initial part of the upgrade process one might access another terminal and uncomment them so the upgrader could find them to upgrade them to Gutsy. I don't think, but do not know, this is needed for a desktop upgrade. BTW, you never indicated, to my recollection, whether you are doing a desktop or server upgrade. If a server upgrade, there is an additional step that must be taken as outlined in the linked help piece I posted quite a while ago; if you are just on a desktop, then you don't need to worry about this.

---

### Post by Pinejoker on 2009-02-24
Oh thanks for information so much.. sorry to bother you again.. i'm still working on this.. since yesterday morning up to day..

from javachick:

well, I've just deleted everything and added this to sources.list

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse

I have only that in file... [email]nattydread.yu@gmail.com[/email] my msn/email, ask me if it isn't working... when u paste that, u can either do sudo apt-get update in terminal, or manually go on System-Administration-Update Manager-Check Updates-Install ( I had to install 225 updates)

what about this?

---

### Post by avtolle on 2009-02-24
Yes, just as the email said. Good luck; I've got to go and won't be back until tomorrow.

---

### Post by Pinejoker on 2009-02-24
thanks alot =)

---

### Post by Pinejoker on 2009-02-24
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main/debian-installer Packages
  404 Not Found [IP: 91.189.88.31 80]
error 1 during sudo aptitude update


sudo aptitude safe-upgrade

family@family-desktop:~$ sudo aptitude safe-upgrade
Unknown command "safe-upgrade"
aptitude 0.4.4
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...
  Actions (if none is specified, aptitude will enter interactive mode):

 install      - Install/upgrade packages
 remove       - Remove packages
 purge        - Remove packages and their configuration files
 hold         - Place packages on hold
 unhold       - Cancel a hold command for a package
 markauto     - Mark packages as having been automatically installed
 unmarkauto   - Mark packages as having been manually installed
 forbid-version - Forbid aptitude from upgrading to a specific package version.
 update       - Download lists of new/upgradable packages
 upgrade      - Perform a safe upgrade
 dist-upgrade - Perform an upgrade, possibly installing and removing packages
 forget-new   - Forget what packages are "new"
 search       - Search for a package by name and/or expression
 show         - Display detailed information about a package
 clean        - Erase downloaded package files
 autoclean    - Erase old downloaded package files
 changelog    - View a package's changelog
 download     - Download the .deb file for a package
 reinstall    - Download and (possibly) reinstall a currently installed package

  Options:
 -h             This help text
 -s             Simulate actions, but do not actually perform them.
 -d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions
 -y             Assume that the answer to simple yes/no questions is 'yes'
 -F format      Specify a format for displaying search results; see the manual
 -O order       Specify how search results should be sorted; see the manual
 -w width       Specify the display width for formatting search results
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z                 Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times)
 -t [release]   Set the release from which packages should be installed
 -q             In command-line mode, suppress the incremental progress indicators.
 -o key=val     Directly set the configuration option named 'key'
 --with(out)-recommends Specify whether or not to treat recommends as
                strong dependencies
 -S fname: Read the aptitude extended status info from fname.
 -u      : Download new package lists on startup.
 -i      : Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.

---

### Post by avtolle on 2009-02-25
Good morning; instead of```
sudo aptitude safe-upgrade
```do```
sudo aptitude upgrade
```
I forgot you were using 7.04. Later versions of aptitude have deprecated the upgrade command in favor of safe-upgrade. I'll be here "off and on" today. Good luck.

---

### Post by Pinejoker on 2009-02-25
> **avtolle said:**
> Good morning; instead of```
sudo aptitude safe-upgrade
```do```
sudo aptitude upgrade
```
I forgot you were using 7.04. Later versions of aptitude have deprecated the upgrade command in favor of safe-upgrade. I'll be here "off and on" today. Good luck.

so after this.. i can update my ubuntu 7.04 to 7.10???


[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.40 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/debian-installer/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/debian-installer/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.40 80]

---

