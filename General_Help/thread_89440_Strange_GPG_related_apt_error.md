---
title: "Strange GPG related apt error"
date: 2005-11-12
forum: General Help
---

### Post by trentonjray on 2005-11-12
When doing an apt-get update today, I recieved the following error.. not sure if I need to get a new signature, and if so.. not sure how to go about doing that. Does anyone know what may be causing this? Thanks in advance!

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by Wandering Wombat on 2005-11-12
Is this badsig problem going to be addressed there are so many threads that i have searched and can't find a bloody answer!!!!! I have tried so many ways its getting really ridiculous ](*,)

---

### Post by Samuel on 2005-11-12
when i got this problem i made a backup of my sources.list deleted the sources.list file then changed the name of the backup to sources.list and it fixed it.

got the tip from the forums, dunno why it worked but it did :confused:

---

### Post by Wandering Wombat on 2005-11-12
There doesn't seem to be one fix for all and there seems to be very few posts by mods in any of these badsig threads, what is going on!!!

---

### Post by aysiu on 2005-11-12
What's your /etc/apt/sources.list look like? I just did a *sudo apt-get update* five minutes ago and it was fine (I used the instructions in the first link of my sig).

---

### Post by Wandering Wombat on 2005-11-12
Ok you know what, finally fixed it after trying so many things including your procedure in your sig nothing had worked, so I thought well I will just manually delete whats in the sources.list then ran sudo apt-get update obviously I didn't get any updates cos the file was empty eg. totally. Then I tried your procedure and now it works, maybe previously it just kept reverting to my back up. This has been very weird.  Thanx for your reply I thought as I had an empty sources.list its worth one last try, thanks for replying. Cheers.

---

### Post by aysiu on 2005-11-13
[QUOTE=Wandering Wombat]There doesn't seem to be one fix for all and there seems to be very few posts by mods in any of these badsig threads, what is going on!!![/QUOTE] Mods aren't Ubuntu superheroes. We're moderators. We moderate the boards. We aren't all technical experts (especially me), and we don't work for Canonical, and we aren't Ubuntu developers. We're just other users, just like you. Whether or not we post in threads has nothing to do with them getting solved.

---

### Post by Wandering Wombat on 2005-11-13
Touche' though the mods do obviously read most threads and have an idea of whats going on, not all of us users are superheroes either believe it or not, I appreciate what you guys do. The badsig threads keep coming up though ;) 
Cheers and have a good day! There are many and confusing procedures to fix the badsig problems, some work for some others don't. Maybe your sig could be stickied, just a thought. Once again I thank you for your reply as previously stated.

---

### Post by aysiu on 2005-11-13
> **Wandering Wombat]The badsig threads keep coming up though  said:**
>  I know. It's annoying, but such is the case when repositories go down.

[quote] 
There are many and confusing procedures to fix the badsig problems, some work for some others don't. Maybe your sig could be stickied, just a thought. I don't believe in mods stickying their own threads. Just keep spreading the word.

---

### Post by emperor on 2005-11-13
[quote=trentonjray]When doing an apt-get update today, I recieved the following error.. not sure if I need to get a new signature, and if so.. not sure how to go about doing that. Does anyone know what may be causing this? Thanks in advance!

W: GPG error: [http://archive.ubuntu.com]("http://archive.ubuntu.com") breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>[/quote]

The error seems to be just in the ".us.archive..." repos. Removing the ".us" solves the problem for me!

---

### Post by trentonjray on 2005-11-13
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe  
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe  
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse

Here is my sources file prior to trying aysiu's fix.. I dont see any .us or anything odd about it. Tried aysiu's fix and it had no results whatsoever. Same error :(

So my current sources.list is the first link in his sig, but going ahead and pasting it in here to make it easier on everyone.

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

---

### Post by neohunt on 2005-11-14
Hi

This is waht I did: first, I deleted the "cl." from all the archive.ubuntu.com repositories. Then I did a sudo apt-get update and everything worked fine. After that I put "cl." in the repositories where they were before, and none GPG error ocurred :D 

I'll post here if a have new errors.

---

### Post by Trajan on 2005-11-15
This still does not work for me at all... i keep on getting the same errors. No matter what i do it still gives me the same error
```

Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:4 http://security.ubuntu.com breezy-security Release [19.6kB]
Get:5 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Ign http://archive.ubuntu.com breezy Release
Hit http://archive.ubuntu.com breezy-updates Release
Hit http://archive.ubuntu.com breezy-backports Release
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Fetched 20.0kB in 1s (16.6kB/s)
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

```
Is there any other way to address this error ?

---

