---
title: "Feisty Fawn repository gone already?  Upgrade path?"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by hardmath on 2008-12-07
Oops, I waited to upgrade my mother-in-law's Feisty Fawn installation, and now when I try to upgrade from 7.04 to 7.10 (Gutsy Gibbon), it stops with an error about not being able to connect to the various Feisty repositories.

I realize that Feisty end-of-life'd in October (month before last), but the installation has been checking for updates, apparently successfully, until today.

Anyone have a suggestion on an upgrade workaround?


regards, hardmath

---

### Post by taurus on 2008-12-07
Maybe the repos for Feisty are closed.

[http://ubuntuforums.org/showthread.php?t=947232](http://ubuntuforums.org/showthread.php?t=947232)

---

### Post by joeslugg on 2008-12-08
I'm also looking for an upgrade path from Feisty to Gutsy.

It seems the upgrade tools won't progress unless the Feisty repo indexes
are available.  Is there some way to work around that and have the tools
(or command line) do the upgrade to Gutsy?

Regards and Thanks,

---

### Post by mk1w86 on 2008-12-08
Open /etc/apt/sources.list (you will need root privileges) and replace all instances of feisty with gutsy.

Then run

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

---

### Post by jeggerleg on 2008-12-08
> **mk1w86 said:**
> Open /etc/apt/sources.list (you will need root privileges) and replace all instances of feisty with gutsy.

Then run

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```


Same problem here but permission denied when I try to open the list. That  presumably means I don't have root privileges - who the hell does then? :p

---

### Post by mk1w86 on 2008-12-08
> Same problem here but permission denied when I try to open the list. That presumably means I don't have root privileges - who the hell does then?  

Use sudo in front of the command to give you temporary root privileges.

e.g.

```
sudo gedit /etc/apt/sources.list
```

---

### Post by igeterrors on 2008-12-10
> **mk1w86 said:**
> Open /etc/apt/sources.list (you will need root privileges) and replace all instances of feisty with gutsy.

Then run

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

Has this worked for anyone? I keep getting the following:

```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.40 80]
```

---

### Post by Sef on 2008-12-10
The best way to upgrade is a clean install.  However, you can try using a [cd to upgrade]("https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion"), but it is not recommended.

---

### Post by nobar on 2008-12-10
They have an archive of the feisty repository at an alternative location.

Here's a description of how to do the upgrade: [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by hardmath on 2008-12-13
Using a combination of the Gutsy Upgrade guide that nobar pointed to and the suggestions on this thread by mk1w86 (about directly editing /etc/apt/sources.list), I was able to make some progress toward an upgrade.

However the machine in question has about 3.7Gbytes of hard disk space, and only 590Mbytes free.  The Upgrade Manager is telling me that over 700Mbytes are needed to do a 'partial upgrade' (some 540 packages need updates).

I don't know if there is a safe workaround here.  The bulk of disk space seems to be taken up in folders /usr/lib and /usr/share.


regards, hardmath

---

### Post by pekka.lehtikoski on 2009-02-11
We have been using feisty fawn under vmware to cross compile and develop our apps for an embedded platforms. It will take long time before we will get all development tools properly tested under newer versions of Ubuntu or other linux distribution, and taken to use by developers. Moved repositories really cause us some harm. (otherwise I have been very happy).

It is normal that distributions have specific life time, and I like that Ubuntu clearly states the support life time. But I see no reason why to have legacy version users need to reconfigure repositories. 

Best regards,
Pekka Lehtikoski

---

### Post by avtolle on 2009-02-11
You do realize that the packages are still available, but not from the repositories that were formerly maintained? And, that there will not be any other updates to said packages? You need to edit your /etc/apt/sources.list file to include the following:
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse

---

### Post by avtolle on 2009-02-11
I would also suggest that the "normal" Feisty repositories be commented out in the /etc/apt/sources.list, as I understand you will not be upgrading, but rather looking for the packages. HTH.

---

### Post by snowpine on 2009-02-11
> **pekka.lehtikoski said:**
> We have been using feisty fawn under vmware to cross compile and develop our apps for an embedded platforms. It will take long time before we will get all development tools properly tested under newer versions of Ubuntu or other linux distribution, and taken to use by developers. Moved repositories really cause us some harm. (otherwise I have been very happy).

It is normal that distributions have specific life time, and I like that Ubuntu clearly states the support life time. But I see no reason why to have legacy version users need to reconfigure repositories.

Best regards,
Pekka Lehtikoski

Hi Pekka, I recommend an LTS (long term support) release, which is supported 3 years, in your situation. 8.04 Hardy Heron is the current LTS, supported through April 2011.

---

### Post by pekka.lehtikoski on 2009-02-11
Thank's Avtolle for help
I tried that before I wrote. Placed the new repository locations "/etc/apt/sources.list". I got errors on "Translation-en_US" (all of them?) and some FTP timeouts errors on larger files (this is network problem at my end). I just tried it again, with about same errors, but the gftp got loaded this time. Can I just ignore errors with "Translation-en_US"?

Still I think that it would be much better to let legacy version repositories exists at original locations. Even it is not hard for me to email sources.list file to other developers and for them to copy it in, it seems sort of unnecessary.

Best regards,
Pekka Lehtikoski

---

### Post by pekka.lehtikoski on 2009-02-11
> **snowpine said:**
> Hi Pekka, I recommend an LTS (long term support) release, which is supported 3 years, in your situation. 8.04 Hardy Heron is the current LTS, supported through April 2011.

Thank you for recommendation. We will do this when it is time to set up the next vmware image for our embedded development team. This is probably during this spring. 

Best regards,
Pekka Lehtikoski

ps. I regret saying things stronger in first post than was needed. Part of it was that yesterday I was showing to my colleague how easy it is to add new features to Ubuntu, and since before it always worked, got surprised by "unable to fetch files". I edited my previous post, to take off unnecessary edge. I am impressed how quickly avtolle and snowpine helped me.

---

### Post by flapphead on 2009-03-14
I know this is a little late, but I need to add my 2 cents here.  

I just dropped in looking for a solution to fix my broken sources.list.  I've fixed it without too much trouble, but what about less experienced users?  The distro requires semi-advanced intervention to function normally after the repositories require.  

Why can't we just leave the repositories where they are and avoid this crap?

2nd of all, I was going to upgrade from a CD-ROM, but the mythical /cdrom/cdromupgrade script does not exist.  That's weak, considering these instructions are plastered all over ubuntu.com.

[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD)

---

### Post by JoBurgMerlin on 2009-05-19
I'm trying to upgrade my instance of Ubuntu 7.10 having not used this Linux laptop for a while, and as with all things Linux it's a near impossible mission to have something work 'right first time'. I get "Could not download all repository indexes" and have been trawling for solutions most of the day.
Every single thing that needs doing in  Linux one has to become a rocket scientist to make it work. :mad:
So I'm simply going to download 9.04 overnight, wipe and re-install.
Hopefully THAT works.
If not well then back to Bill.

---

### Post by snowpine on 2009-05-19
> **JoBurgMerlin said:**
> I'm trying to upgrade my instance of Ubuntu 7.10 having not used this Linux laptop for a while, and as with all things Linux it's a near impossible mission to have something work 'right first time'. I get "Could not download all repository indexes" and have been trawling for solutions most of the day.
Every single thing that needs doing in  Linux one has to become a rocket scientist to make it work. :mad:
So I'm simply going to download 9.04 overnight, wipe and re-install.
Hopefully THAT works.
If not well then back to Bill.

7.10 is no longer supported; installing 9.04 is a good solution. (Just be sure to upgrade to something else before oct. 2010 when 9.04 reaches the end of the line.)

---

### Post by dannyboy79 on 2009-06-11
is there any way to upgrade from fesity to something higher at this point in the game? my sources.list has all the correct repos which are deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) feisty main restricted and all the rest of them

please help

---

