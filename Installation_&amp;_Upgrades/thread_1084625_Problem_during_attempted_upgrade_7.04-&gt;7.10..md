---
title: "Problem during attempted upgrade 7.04-&gt;7.10."
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by DoktorNo on 2009-03-02
Hi there,

I have a laptop with installed vintage Ubuntu 7.04 distro, and I plan to update it first to 7.10 version via alternate CD, and then, step-by-step upgrade it to 8.10 via Internet, because for unknown reason update-manager does not updates to 7.10.

I inserted a CD to drive, started the upgrade script, and I had an error, possibly in update-manager. What I should do? I'm seriously considering manually adding gutsy repositories and 7.10's CD  into sources list...

---

### Post by DoktorNo on 2009-03-02
Bump. Anyone had any ideas, how to solve this?

---

### Post by avtolle on 2009-03-02
See [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades) for some help.

Basically, your problem is that Feisty reached EOL in October, 2008; the repositories were taken down, and the packages moved to the old-releases site.

---

### Post by DoktorNo on 2009-03-02
I just did, what is said there, and I still have the same problem. :(

---

### Post by avtolle on 2009-03-02
You edited your /etc/apt/sources.list file so that the only lines active (not commented out or deleted) are those given in the link, correct? There are several threads on the Forum concerning upgrading from Feisty to Gutsy, and IIRC, the resolution of the issues was that the only active lines left in the file were the ones pointing to the old release site. Once that is done, then to reload the repositories and to fully update your Feisty system, do (in the terminal)```
sudo aptitude update
sudo aptitude upgrade
```and then, as you have the alternate CD for 7.10, load it (do not boot from it) and proceed as advised in the link. 

I don't recall anyone posting that wasn't doing the sequential network upgrade, and it seems to me that once the sources.list changes were made, they were able to go from 7.04 to 7.10 using Update Manager (unless they were on a server install, which requires something a bit different but likely gets the user to the same place, so to speak).

---

### Post by DoktorNo on 2009-03-02
The problem i get is about prerequists. I tried to add a deb line in sources list pointing to old relase repository, but despite this, the error persists, and in sources.list.d the file with source for main/debian-installer, that points to defunct repository is recreated over and over...

Moreover the script from CD is no longer working, after the 7.04 update.

---

### Post by Ex-windows on 2009-03-02
I tried this as well And with no luck

I tried to add these lines using terminal 

I type in "sudo gedit /etc/apt/sources.list
Type in passwaord and added This to the VERY bottom of the "list file" saved and exit terminal


deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse



 afterwards I get this message from update manager
E: Type '+' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
What can I do to correct this? I just want access to the  old repositories so  I can keep Feisty.

---

### Post by avtolle on 2009-03-02
Please post your /etc/apt/sources.list for a look-see. Thanks.

---

### Post by DoktorNo on 2009-03-02
> **avtolle said:**
> Please post your /etc/apt/sources.list for a look-see. Thanks.

Here you are:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

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
# deb http://pl.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://pl.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

#
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu feisty-backports main/debian-installer
deb http://archive.ubuntu.com/ubuntu/ feisty main universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

```

---

### Post by Ex-windows on 2009-03-02
> **avtolle said:**
> Please post your /etc/apt/sources.list for a look-see. Thanks. 
Wow TY 4 The  quk Response

This is the etc/apt/sources,list 

+# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

---

### Post by DoktorNo on 2009-03-02
That's weired. I just run the update, and get those:

```
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-backports/main/debian-installer/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz 404 Not Found

```

---

### Post by Ex-windows on 2009-03-02
> **DoktorNo said:**
> Here you are:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

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
# deb http://pl.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://pl.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

#
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu feisty-backports main/debian-installer
deb http://archive.ubuntu.com/ubuntu/ feisty main universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

```

TY TY TY  :popcorn:  :guitar:
That did the trick. Now I can keep my Fiesty.
BTW whe:re did the TY button disappear to?

---

### Post by Ex-windows on 2009-03-02
> **DoktorNo said:**
> That's weired. I just run the update, and get those:

```
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-backports/main/debian-installer/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz 404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz 404 Not Found

```

Did u get it yet???

---

### Post by DoktorNo on 2009-03-02
No, I'm still stuck.

---

### Post by Ex-windows on 2009-03-02
> **DoktorNo said:**
> No, I'm still stuck.
 You have Feisty already?, and want to get all the updates so as to go to gutsy? 
What I did was
 opend a terminal
I type in "sudo gedit /etc/apt/sources.list
Type in passwaord and added This to the VERY bottom of the "list file" saved and exit terminal


deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse 

Did u try this as well?

---

### Post by DoktorNo on 2009-03-02
Yes, and that doesn't work.

I'm now preparing myself for the last resort: updating the deb lines manually to gutsy, and running sudo apt-get distr-uprgrade.

---

### Post by Ex-windows on 2009-03-02
> **DoktorNo said:**
> Yes, and that doesn't work.

I'm now preparing myself for the last resort: updating the deb lines manually to gutsy, and running sudo apt-get distro-uprgrade.
 I am not very advanced at all this but I did notice that your error message say it "failed to get Gutsy updates.(Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz) 404 Not Found) Did you already get the Fiesty ones? I am not sure about how to proceed with the actual upgrade cuz I just wanted to get the repos so I could keep Feisty. but if you have all the fiesty  stuff it should now let you upgrade from package manager. Sorry if this doesn't help.

---

### Post by DoktorNo on 2009-03-02
Just installed Gutsy, with brute method described before. Works well (so far)

---

### Post by mmistroni on 2009-03-06
Hello,
I have been following this thread as i am trying to upgrade from 7.04 to 7.10
My system  7.04 is up to date
whenever i type 
```

sudo aptitude upgrade

```
i receive following output
```

marco@worldcorp-laptop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

could anyonehlep pls?

thanks and regards
 marco




here's my sources.list
```

## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

##deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
##deb http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
##deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

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
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

```

---

### Post by avtolle on 2009-03-06
I noted today that the link to the Gutsy upgrade notes I posted here (or on another thread for someone having the same problem) has a newly added note to the effect that it is no longer possible to do a network upgrade from 7.04 to 7.10.

@mministroni, when you go to update manager under System>Administration, is there an option given at the top to do an upgrade to 7.10? The command you gave in terminal would only upgrade your 7.04 install to as current status as possible; it does not do an upgrade to a new distribution.

---

### Post by mmistroni on 2009-03-06
hello,
 thanks fo rreply
via synaptic, it says new distro 7.10 is available....
so i tried to go for it but i failed big time,......

---

### Post by avtolle on 2009-03-06
> **mmistroni said:**
> hello,
 thanks fo rreply
via synaptic, it says new distro 7.10 is available....
so i tried to go for it but i failed big time,......
Well, that certainly adds credibility to the newly added note to the upgrade notes page. I think you have two options: one, to download the alternate cd iso for 7.10 and try the upgrade from that, or two, to get a newer release of 8.04 or 8.10 and do a clean install.

EDIT: Make that three options; the third being the "brute force" method used by the OP.

---

### Post by mmistroni on 2009-03-07
hello,
 thanks for reply..
i am thinking of going for fresh upgrade..
however, i have couple of doubts.. i have following application installed

Oracle 11g
Svn
MySql

Plus lot of my software in my home directory

Will the fresh upgrade to 8.04 clear any of the above?

thanks and regards
 marco

---

### Post by mmistroni on 2009-03-11
Hello, 
 caould anyone advice here?
if i update straight to 8.10 via cd, what will happe to my home directory? will it be wiped out?

thanks and regars
 marco

---

