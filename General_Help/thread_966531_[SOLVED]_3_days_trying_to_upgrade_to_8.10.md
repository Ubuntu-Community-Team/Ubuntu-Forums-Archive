---
title: "[SOLVED] 3 days trying to upgrade to 8.10"
date: 2008-11-01
forum: General Help
---

### Post by karlmp on 2008-11-01
when i open the update manager a message pops up:

[B]Not all updates can be installed
[/B]
Run a partial upgrade, to install as many updates as possible.


This can be caused by:
-A previous upgrade which didn't complete
-Problems with some of the installed software
-Unofficial software packages not provided by Ubuntu
-Normal changes of a pre-release version of Ubuntu

in the update manager says: you can install 743 updates
download size:399.1 MB

---

### Post by Bablefish on 2008-11-01
You might have to do a clean install

---

### Post by karlmp on 2008-11-01
i cannot do it from the CD since my optical drive doesn't work

---

### Post by zeronothing on 2008-11-01
first try to do a clean of the downloads you have previously downloaded.

open up terminal and do the command
sudo apt-get clean

after that try doing this at the commandline.
sudo update-manager -d

this will allow you to see what packages it is trying to download and see at which package it fails.

---

### Post by Cl0ud9 on 2008-11-01
> **karlmp said:**
> i cannot do it from the CD since my optical drive doesn't work

You can upgrade using only the iso file using the alternate cd image.

---

### Post by mdurham on 2008-11-01
> **Cl0ud9 said:**
> You can upgrade using only the iso file using the alternate cd image.

Cl0ud9, can you explain that one a bit more please.

---

### Post by mdurham on 2008-11-01
> Not all updates can be installed
Have you tried using Synaptic to do the updates?

---

### Post by Cl0ud9 on 2008-11-01
> **mdurham said:**
> Cl0ud9, can you explain that one a bit more please.

Look [here]("http://www.ubuntu.com/getubuntu/upgrading") and scroll down to the section called "Upgrading Using the Alternate CD/DVD".

---

### Post by mdurham on 2008-11-01
> **Cl0ud9 said:**
> Look [here]("http://www.ubuntu.com/getubuntu/upgrading") and scroll down to the section called "Upgrading Using the Alternate CD/DVD".

Thanks Cl0ud9

---

### Post by karlmp on 2008-11-02
i haven't tried synaptic

it failed to download the iso

---

### Post by TWO on 2008-11-02
You could also download the .iso and then make a flash drive bootable and install from that since your optical drive isn't working.

That's how I'm doing fresh installs at the moment.

You can use UNetbootin to make the flash drive bootable.

[http://unetbootin.sourceforge.net/#introduction](http://unetbootin.sourceforge.net/#introduction)

---

### Post by akhil.t on 2008-11-02
I am currently on Hardy and am facing a rather strange problem. Neither my Term nor the update manager are allowing me to upgrade to Ibex. I tried all the commands for term, but it shows this:

    sudo aptitude safe-upgrade
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    Reading extended state information
    Initializing package states... Done
    Building tag database... Done
    No packages will be installed, upgraded, or removed.
    0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
    Need to get 0B of archives. After unpacking 0B will be used.
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    Reading extended state information
    Initializing package states... Done
    Building tag database... Done 

The update manager does not show the 'Upgrade Available' button either. Anyone else facing a similar issue?

---

### Post by karlmp on 2008-11-02
actually i installed Ubuntu that way using unetbootin with the net no with the usb flash drive

i have windows xp too, would that be a problem?


all i want to do is this:
edit my partitions both windows xp and Ubuntu to give ubuntu more space and windows less space, then upgrade to intrepid or do a fresh install of intrepid

which way is the best,fastest?

---

### Post by akhil.t on 2008-11-03
> **karlmp said:**
> actually i installed Ubuntu that way using unetbootin with the net no with the usb flash drive

i have windows xp too, would that be a problem?


all i want to do is this:
edit my partitions both windows xp and Ubuntu to give ubuntu more space and windows less space, then upgrade to intrepid or do a fresh install of intrepid

which way is the best,fastest?
I'd suggest a fresh install, it'll take not more than 20-30 mins.

---

### Post by scouser73 on 2008-11-04
I suggest you go; **System, Administration, Software Sources** click the **Updates** tab and the drop-down menu **Release Upgrade** select **Normal Releases**.  This worked for me when I was on Hardy Heron and I wanted to upgrade to Intrepid Ibex.

---

### Post by marcon00 on 2008-11-04
> **karlmp said:**
> i haven't tried synaptic

it failed to download the iso

Use some download manager to download the iso ?  Use the iso and then do as  Cl0ud9
 said :)

---

### Post by karlmp on 2008-11-04
i followed the instructions here:[http://ubuntuforums.org/showthread.php?t=811397](http://ubuntuforums.org/showthread.php?t=811397)

after installing, rebooting and changing the boot priority order in the BIOS i just get a black screen with the cursor blinking in the upper-left corner

---

### Post by karlmp on 2008-11-05
i think is u3, I'm trying to download the removal tool but for some reason it stops when is going at 45% 1.5MB of 3.3MB in both windows and ubuntu

---

### Post by karlmp on 2008-11-06
i searched for "launchpadremoval.exe torrent" in google and now i have a fresh install of intrepid but new problem:[http://ubuntuforums.org/showthread.php?p=6120191#post6120191](http://ubuntuforums.org/showthread.php?p=6120191#post6120191)

**_thank you all_**

---

