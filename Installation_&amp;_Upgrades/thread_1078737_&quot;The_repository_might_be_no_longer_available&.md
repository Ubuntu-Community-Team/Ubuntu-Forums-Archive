---
title: "&quot;The repository might be no longer available&quot;"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by javaChick on 2009-02-23
I cannot install absolutely anything! I think that sources.list file is making problems, since everytime I try to install something it says :

```
 The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences. 
```

And this is sources.list file :

```

 See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted

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
# deb http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

```

This is the only Linux distro I have, and what should I do? :(

---

### Post by Pumalite on 2009-02-23
Feisty is no longer supported. There is an 'old repo' somewhere. I'll try to find it.

---

### Post by howefield on 2009-02-23
Try the post by kostkon in this thread.

[http://ubuntuforums.org/showthread.php?p=6319924#post6319924](http://ubuntuforums.org/showthread.php?p=6319924#post6319924)

---

### Post by ptn107 on 2009-02-23
In your sources.list file replace every instance of [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) with [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)

---

### Post by javaChick on 2009-02-24
Finally! Thank u all! :))

---

### Post by Pinejoker on 2009-02-24
hey what you did to fix your ubuntu 7.04 i mean to update it??? give me the source list?

---

### Post by ptn107 on 2009-02-24
The sources.list would look kinda like this:
```
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
```

---

### Post by Pinejoker on 2009-02-24
this is the code? what im going to do with that? just copy  and paste? do i need to remove the all files inside of the sources list and paste that?

---

### Post by javaChick on 2009-02-24
it works for me :)

---

### Post by Pinejoker on 2009-02-24
okay if works to you.. can you help me so it will work on me also?/ how???

---

### Post by avtolle on 2009-02-24
Edit your file by deleting everything in it, then cut and paste the contents from post #7 into /etc/apt/sources.list. Then, after saving it, open a terminal and```
sudo aptitude update
sudo aptitude safe-upgrade
sudo aptitude dist-upgrade
```one at a time. The first command will update your repositories; the second, which you should run after the first command runs, will likely give you a lot of updates to download; the third command, which should be run after the updates generated by the second command and downloaded and installed, will pick up any kernel, etc., updates that didn't download the first time. The third command might not generate anything new, as the second command will generally get everything (but not always), so don't worry if nothing downloads after that one is issued. Hopefully, once all that is done, and you exit the terminal, you will be offered the opportunity to upgrade to 7.10.

---

### Post by Pinejoker on 2009-02-24
and then? just copy this file 

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse

---

### Post by avtolle on 2009-02-24
Do that first; copy that into your /etc/apt/sources.list; either comment everything else out or delete everything else from the file, so that those lines are the only ones active in the file (either not commented out or deleted). Then run the commands I posted, one at a time as stated.

---

### Post by Pinejoker on 2009-02-24
and then on the second code what will im going to do with it?

---

### Post by avtolle on 2009-02-24
Once you have copied the lines into your file, and you have otherwise edited it as you wish, save it and close out of the editor. Then, run```
sudo aptitude update
```which will refresh your repositories. If no errors, then run ```
sudo aptitude safe-upgrade
```which will download and install updates to your base 7.04 system. Then, to check if there is anything else remaining after step 2 completes (may take a while) do```
sudo aptitude dist-upgrade
```to catch any kernel updates, etc., that the second step might not have downloaded and installed. 

Once all that has completed, you could then go to System>Administration>Update Manager and see if the offer to upgrade to a new release (in this case 7.10) appears at the top of the box; if it does, click on the button that says, IIRC, Upgrade Now, and if everything goes right, you will end up with 7.10 on your system.

---

### Post by Pinejoker on 2009-02-24
im done in the first step.. and here is the only error i had Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main/debian-installer Packages
  404 Not Found [IP: 91.189.88.45 80]

---

### Post by avtolle on 2009-02-24
> **Pinejoker said:**
> im done in the first step.. and here is the only error i had Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main/debian-installer Packages
  404 Not Found [IP: 91.189.88.45 80]
OK, go into your /etc/apt/sources.list file and find the line complained of and comment it out. I'd look for one that has feisty backports at the end. Then run```
sudo aptitude update
```again to see if you caught it, and if no errors, continue to ```
sudo aptitude safe-upgrade
```

---

### Post by hubertofliege on 2009-08-06
I just started getting this message.  Before I attempt what has been suggested, I'd like to know what is going on, and what I'm doing.  I don't even know what the repository is, and I'm not sure if this stuff applies to me since I'm running Jaunty.

What does this error mean?

---

### Post by Partyboi2 on 2009-08-06
> **hubertofliege said:**
> I just started getting this message.  Before I attempt what has been suggested, I'd like to know what is going on, and what I'm doing.  I don't even know what the repository is, and I'm not sure if this stuff applies to me since I'm running Jaunty.

What does this error mean?
If you are using Jaunty you will not need to add the 'old release' repos that are mentioned in this thread, as Jaunty is  a current release. I would suggest opening a new thread with the information of the error you are getting. :)

---

