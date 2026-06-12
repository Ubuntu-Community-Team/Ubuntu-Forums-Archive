---
title: "synaptic warning....."
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by beamendslrs on 2009-05-06
Hi All,
I've just run synaptic to check for updates and I get this:

"Warning

You are about to install software that can't be authenticated! Doing this could allow a malicious individual to damage or take control of you system."

There's a bit more.

The list of changes includes practically everything, but starts with gs-esp-x which I don't recognise.

Two questions really - is this a real threat, and if so how do stop it trying to update the offending software?

Cheers
Richard

---

### Post by zvacet on 2009-05-06
Are you using just official Ubuntu repos or you added somrthing else and idf you do what exactly?Thereis no reason to be afraid if you are using just official Ubuntu repos.

---

### Post by pmlxuser on 2009-05-06
sometimes all the warning serves is to notify you that the software is not 
1. officially supported.
2. has stopped being officially supported

but some times depending on the source can really be a serious threat.

the best way to stop the message is to only install software from officially supported  repositories. However you might find this not the best option as some of the best programs are not found in the official repositories.

the best solution is to use you intellect and judgement as to which software you can install rather than let the synaptic manager lead you..

---

### Post by beamendslrs on 2009-05-07
Ok, can anyone tell me if any of these are suspect - I really cannot remember if I have changed etc/apt/souces.list - I don't think so!


deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
## deb [http://ubuntu.roomandspace.com/](http://ubuntu.roomandspace.com/) feisty main

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe


Cheers
Richard

---

### Post by Partyboi2 on 2009-05-07
Gusty has reached its end of life so the problem you are having could be due to the gutsy repos being moved.
I would suggest upgrading to a later release of Ubuntu, otherwise comment out your current repos and add
```
deb http://old-releases.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-backports main/debian-installer
deb-src http://old-releases.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
```


Edit: Corrected spelling mistakes

---

### Post by HyRax on 2009-05-07
Gutsy should still be supported for at least another 6 months (total 18 months), but yeah I agree - upgrade to something more recent!

---

### Post by beamendslrs on 2009-05-07
> **HyRax said:**
> Gutsy should still be supported for at least another 6 months (total 18 months), but yeah I agree - upgrade to something more recent!

Can you say what the latest version is that installs without problems - I ask as I run my business on the machine and an upgrade failure would be really serious. Last time I lost access to the Windows partition (not the end of the world admittedly) and I don't have the skills to put it right if it all goes wrong - re-installation is not an option as I have files and dbases all over and can't be 100% certain they are all backed up because I don't know where everything goes!

Cheers
Richard

---

### Post by awclemen on 2009-05-07
> **Partyboi2 said:**
> Gusty has reached its end of life so the problem you are having could be due to the gutsy repos being moved.
I would suggest upgrading to a later release of Ubuntu, otherwise comment out your current repos and add
```
deb http://old-releases.ubuntu.com/ubuntu/ gusty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gusty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gusty-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gusty-backports main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gusty-backports main/debian-installer
deb-src http://old-releases.ubuntu.com/ubuntu/ gusty-backports main restricted universe multiverse
```

Thanks for the tip, however when I run this I still get 404 errors.

```

ldbalancer@PROD-LOAD-BALANCER:/etc/apt$ sudo apt-get update
Ign http://old-releases.ubuntu.com gusty Release.gpg
Ign http://old-releases.ubuntu.com gusty/main Translation-en_US
Ign http://old-releases.ubuntu.com gusty/restricted Translation-en_US
Ign http://old-releases.ubuntu.com gusty/universe Translation-en_US
Ign http://old-releases.ubuntu.com gusty/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com gusty-updates Release.gpg
Ign http://old-releases.ubuntu.com gusty-updates/main Translation-en_US
Ign http://old-releases.ubuntu.com gusty-updates/restricted Translation-en_US
Ign http://old-releases.ubuntu.com gusty-updates/universe Translation-en_US
Ign http://old-releases.ubuntu.com gusty-updates/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com gusty-security Release.gpg
Ign http://old-releases.ubuntu.com gusty-security/main Translation-en_US
Ign http://old-releases.ubuntu.com gusty-security/restricted Translation-en_US
Ign http://old-releases.ubuntu.com gusty-security/universe Translation-en_US
Ign http://old-releases.ubuntu.com gusty-security/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com gusty-backports Release.gpg
Ign http://old-releases.ubuntu.com gusty-backports/main Translation-en_US
Ign http://old-releases.ubuntu.com gusty-backports/restricted Translation-en_US
Ign http://old-releases.ubuntu.com gusty-backports/universe Translation-en_US
Ign http://old-releases.ubuntu.com gusty-backports/multiverse Translation-en_US
Ign http://old-releases.ubuntu.com gusty-backports/main/debian-installer Translation-en_US
Ign http://old-releases.ubuntu.com gusty Release
Ign http://old-releases.ubuntu.com gusty-updates Release
Ign http://old-releases.ubuntu.com gusty-security Release
Ign http://old-releases.ubuntu.com gusty-backports Release
Ign http://old-releases.ubuntu.com gusty/main Packages
Ign http://old-releases.ubuntu.com gusty/restricted Packages
Ign http://old-releases.ubuntu.com gusty/universe Packages
Ign http://old-releases.ubuntu.com gusty/multiverse Packages
Ign http://old-releases.ubuntu.com gusty-updates/main Packages
Ign http://old-releases.ubuntu.com gusty-updates/restricted Packages
Ign http://old-releases.ubuntu.com gusty-updates/universe Packages
Ign http://old-releases.ubuntu.com gusty-updates/multiverse Packages
Ign http://old-releases.ubuntu.com gusty-security/main Packages
Ign http://old-releases.ubuntu.com gusty-security/restricted Packages
Ign http://old-releases.ubuntu.com gusty-security/universe Packages
Ign http://old-releases.ubuntu.com gusty-security/multiverse Packages
Ign http://old-releases.ubuntu.com gusty-backports/main Packages
Ign http://old-releases.ubuntu.com gusty-backports/restricted Packages
Ign http://old-releases.ubuntu.com gusty-backports/universe Packages
Ign http://old-releases.ubuntu.com gusty-backports/multiverse Packages
Ign http://old-releases.ubuntu.com gusty-backports/main/debian-installer Packages
Ign http://old-releases.ubuntu.com gusty-backports/main Sources
Ign http://old-releases.ubuntu.com gusty-backports/restricted Sources
Ign http://old-releases.ubuntu.com gusty-backports/universe Sources
Ign http://old-releases.ubuntu.com gusty-backports/multiverse Sources
Err http://old-releases.ubuntu.com gusty/main Packages
  404 Not Found
Err http://old-releases.ubuntu.com gusty/restricted Packages
  404 Not Found
Err http://old-releases.ubuntu.com gusty/universe Packages
  404 Not Found
Err http://old-releases.ubuntu.com gusty/multiverse Packages
  404 Not Found
Err http://old-releases.ubuntu.com gusty-updates/main Packages
  404 Not Found
Err http://old-releases.ubuntu.com gusty-updates/restricted Packages
  404 Not Found
Err http://old-releases.ubuntu.com gusty-updates/universe Packages
  404 Not Found
Err http://old-releases.ubuntu.com gusty-updates/multiverse Packages
  404 Not Found
Err http://old-releases.ubuntu.com gusty-security/main Packages
  404 Not Found
Err http://old-releases.ubuntu.com gusty-security/restricted Packages
  404 Not Found
Err http://old-releases.ubuntu.com gusty-security/universe Packages
  404 Not Found
Err http://old-releases.ubuntu.com gusty-security/multiverse Packages
  404 Not Found
Err http://old-releases.ubuntu.com gusty-backports/main Packages
  404 Not Found
Err http://old-releases.ubuntu.com gusty-backports/restricted Packages
  404 Not Found
Err http://old-releases.ubuntu.com gusty-backports/universe Packages
  404 Not Found
Err http://old-releases.ubuntu.com gusty-backports/multiverse Packages
  404 Not Found
Err http://old-releases.ubuntu.com gusty-backports/main/debian-installer Packages
  404 Not Found
Err http://old-releases.ubuntu.com gusty-backports/main Sources
  404 Not Found
Err http://old-releases.ubuntu.com gusty-backports/restricted Sources
  404 Not Found
Err http://old-releases.ubuntu.com gusty-backports/universe Sources
  404 Not Found
Err http://old-releases.ubuntu.com gusty-backports/multiverse Sources
  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty-updates/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty-updates/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty-updates/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty-updates/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty-security/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty-backports/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty-backports/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty-backports/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty-backports/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty-backports/main/debian-installer/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty-backports/main/source/Sources.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty-backports/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty-backports/universe/source/Sources.gz  404 Not Found
Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/gusty-backports/multiverse/source/Sources.gz  404 Not Found
Reading package lists... Done

```

So, I was leaning toward upgrading anyway but it leaves a question in my mind - do I need to make sure all is updated first BEFORE I upgrade, or should I able to upgrade to 8.04 without having to worry about the updates?

Also, I notice that there were some warning about attempting to upgrade with the 2.6.22-15 kernel and it was recommend that one should boot into the 2.6.22-14 kernel before upgrading.  However, the machine is remote (i.e. 120 miles away), so I'm not sure I can boot into a different kernel (is there a way to do that remotely?). I'm on the 2.6.22-16 kernel - has anyone had any problems upgrading from the 2.6.22-16 kernel?

Thanks in advance for all the help,

--Andy

---

### Post by CBHedricks on 2009-05-07
Personally I have found the LTS (Long Term Support) versions of Linux Distributions to be much more dependable for buisness.  The ones that I use/prefer for business use are Ubuntu 8.04 LTS (notebooks), SLED for Desktop, and CentOS for servers.  Usually the Ubuntu is running with Gnome, SLED is KDE based, and CentOS is also KDE based as they seem to be better with server applications support.

The principal reason behind my choices is driven by the facts behind the 'normal' distribution release schedule.  This normal schedule is more related to bleeding edge and new hardware adoption. On the flip side a LTS version is all about stability, security and regular **updates** rather than regular **upgrades**.

Hope that helps out.

CB

---

### Post by HyRax on 2009-05-07
> **beamendslrs said:**
> Can you say what the latest version is that installs without problems - I ask as I run my business on the machine and an upgrade failure would be really serious. Last time I lost access to the Windows partition (not the end of the world admittedly) and I don't have the skills to put it right if it all goes wrong - re-installation is not an option as I have files and dbases all over and can't be 100% certain they are all backed up because I don't know where everything goes!

Cheers
Richard

That's shambles, mate - if you're running a business you should already be putting backup procedures in place.

If it's a server, then I recommend the LTS releases, the most recent of which is 8.04 Hardy Heron. If it's just a desktop, then I always recommend the most recent general release, which is currently 9.04 Jaunty Jackalope.

All versions work quite reliably - it's ultimately dependent on what you're installing on top of it. Without more knowledge of what your business is comprised of and without the ability to sit in front of your machine to see how everything is laid out, I cannot say whether you should or should not do a reinstallation on top of your existing setup. I'm afraid you'll either have to do some learning yourself or get a local tech out to assist you.

---

### Post by oldos2er on 2009-05-07
"Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gusty-backports/multiverse Sources"

 Try gutsy instead of "gusty."

---

### Post by Partyboi2 on 2009-05-07
> **oldos2er said:**
> "Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gusty-backports/multiverse Sources"

 Try gutsy instead of "gusty."
Thanks oldos2er :)


@awclemen
Sorry about that :)

---

### Post by sgosnell on 2009-05-07
If you're running a business on a computer, and you don't have backups of your backups, then god help you.  You should be doing a daily backup of all your data, and transporting previous backups off-site, at the very least.  It's not a matter of if your computer will crash horribly, it's a matter of when.  It will either crash on its own, get stolen, burn up, or otherwise become unusable.  That's almost guaranteed.  Get some sort of backup media and start doing it right now.  Today.  

Upgrading to 8.04, the latest LTS release, should pose no problems.  8.10 runs fine on almost everything.

---

### Post by beamendslrs on 2009-05-08
> **sgosnell said:**
> If you're running a business on a computer, and you don't have backups of your backups, then god help you.  You should be doing a daily backup of all your data, and transporting previous backups off-site, at the very least.  It's not a matter of if your computer will crash horribly, it's a matter of when.  It will either crash on its own, get stolen, burn up, or otherwise become unusable.  That's almost guaranteed.  Get some sort of backup media and start doing it right now.  Today.  

Upgrading to 8.04, the latest LTS release, should pose no problems.  8.10 runs fine on almost everything.

I'm fully conversant with back-ups etc, I'm also aware that, as a one man operation, it is all too easy to miss something, so relying on back-ups for non-emergencies is near suicidal - an OS update should not be, or create, an emergency.

If I were to pay for support, I might just as well have used Windows and bought an off-the-shelf package - Linux support in these parts, even if it were affordable, is simply not available.

I shall be leaving the system as is - looking through the potential problems others have had with updates, and after last years experience of ending up with a system that would only boot in text mode after a general update, the risk of having no computer for a couple of day outweighs any advantages of updating. Despite having a degree in Computer Science, I no longer have the time, will or interest in becoming a Linux expert, the computer is just a tool the same as those in the workshop these days. I think needing ask which version to use highlights that Linux has some way to go before it becomes universally accepted outside the enthusiast world.

Please don't take this a whinge, I'm simply trying to put across the non-enthusiasts viewpoint. I don't have any of these issues on my Windows laptop, and if I did system restore would allow me to go back to where I was easily, rather than have no machine! We have a new employee starting in June and I'm now thinking a Windows machine would be a safer option for him.  

Cheers
Richard

---

### Post by sgosnell on 2009-05-08
A system update shouldn't be an emergency, but you should have backups anyway, so even if the update did go wrong you should be able to restore everything.  If you prefer Windows, that's up to you, but you should be aware that it is less stable than Linux, and updates are even more problematic.  It's your money, so it's your decision.  But you should know that almost every server in the world runs some version of Linux or another Unix variant, not Windows.  If you absolutely require stability, Windows isn't what you want.

---

