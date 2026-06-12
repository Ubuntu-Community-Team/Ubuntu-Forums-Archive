---
title: "Error with update and installation of .deb!"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by hambos22 on 2009-06-30
Hi to all! I have ubuntu 8.04. After searching i managed to install Amarok 1.4 (cause i hate Amarok 2). After this job done i decided to install deb package of Adobe flash player.
Then it gives me this error
> Software index is broken
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
And if i go to update my system it gives me
> Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Opening /etc/apt/sources.list.d/amarok.list - ifstream::ifstream (13 Permission denied), E:The list of sources could not be read.'My sources.list is
> deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse
deb [http://ubuntu.intergenia.de/ubuntu/](http://ubuntu.intergenia.de/ubuntu/) hardy main restricted
deb-src [http://ubuntu.intergenia.de/ubuntu/](http://ubuntu.intergenia.de/ubuntu/) hardy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.intergenia.de/ubuntu/](http://ubuntu.intergenia.de/ubuntu/) hardy-updates main restricted
deb-src [http://ubuntu.intergenia.de/ubuntu/](http://ubuntu.intergenia.de/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu.intergenia.de/ubuntu/](http://ubuntu.intergenia.de/ubuntu/) hardy universe
deb-src [http://ubuntu.intergenia.de/ubuntu/](http://ubuntu.intergenia.de/ubuntu/) hardy universe
deb [http://ubuntu.intergenia.de/ubuntu/](http://ubuntu.intergenia.de/ubuntu/) hardy-updates universe
deb-src [http://ubuntu.intergenia.de/ubuntu/](http://ubuntu.intergenia.de/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.intergenia.de/ubuntu/](http://ubuntu.intergenia.de/ubuntu/) hardy multiverse
deb-src [http://ubuntu.intergenia.de/ubuntu/](http://ubuntu.intergenia.de/ubuntu/) hardy multiverse
deb [http://ubuntu.intergenia.de/ubuntu/](http://ubuntu.intergenia.de/ubuntu/) hardy-updates multiverse
deb-src [http://ubuntu.intergenia.de/ubuntu/](http://ubuntu.intergenia.de/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ubuntu.intergenia.de/ubuntu/](http://ubuntu.intergenia.de/ubuntu/) hardy-security main restricted
deb-src [http://ubuntu.intergenia.de/ubuntu/](http://ubuntu.intergenia.de/ubuntu/) hardy-security main restricted
deb [http://ubuntu.intergenia.de/ubuntu/](http://ubuntu.intergenia.de/ubuntu/) hardy-security universe
deb-src [http://ubuntu.intergenia.de/ubuntu/](http://ubuntu.intergenia.de/ubuntu/) hardy-security universe
deb [http://ubuntu.intergenia.de/ubuntu/](http://ubuntu.intergenia.de/ubuntu/) hardy-security multiverse
deb-src [http://ubuntu.intergenia.de/ubuntu/](http://ubuntu.intergenia.de/ubuntu/) hardy-security multiverse


deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"

## amarok 1.4 what can i do?

Thanx

---

### Post by drs305 on 2009-06-30
> **hambos22 said:**
> 
what can i do?

Thanx

The error probably resides in a file in a sources.list.d subfolder.

Open this file and check for errors. If you don't recognize any, post the results:

```

gksudo gedit /etc/apt/**sources.list.d/amarok.list**

```
> deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121)]/ hardy main restricted

Also, if you are tired of being asked to insert your installation CD whenever you do an update, you can place a comment symbol (#) in front of the first line in your sources.list...

---

### Post by hambos22 on 2009-06-30
it's empty :confused: i opened it and it's all empty.. nothing to see

any  other way?

---

### Post by drs305 on 2009-06-30
> **hambos22 said:**
> it's empty :confused: i opened it and it's all empty.. nothing to see

any  other way?

I don't use amarok so I can't vouch that there even is an amarok respository. That being said:

Make sure you typed or copied the command correctly. You will get an empty file if 1) the file doesn't exist or 2) you mistype the command. Actually, #2 is a variation of #1, since if you mistype it the command will try to open a file as typed. You can also open nautilus as root to see what, if anything, *is* in that folder:
```

gksudo nautilus /etc/apt/sources.list.d

```

You can also check your repository list (Synaptic or Software Sources, Settings > Repositories. Check the ones you have enabled, especially under the Third Party tab. If you find one for amarok, if you untick it you should be able to update the rest of your repository entries.

---

### Post by hambos22 on 2009-06-30
i used the command just like you posted it. Empty..

Then with nautilus i opened amarok.list and it'e empty too.

On Software Sources i have checked

*[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
*[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)
*[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

there isn't amarok there.

---

### Post by drs305 on 2009-06-30
Have you tried going to Synaptic to try to fix the broken packages as suggested in the initial error message? Open Synaptic, and from the lower left section, select Custom Filters > Broken. If any are listed and Synaptic offers to fix them, let it.

Next, try searching your current registered lists in /var/lib/apt/lists and see if there is an old listing for amarok. If there is, delete it.
```

gksudo nautilus /var/lib/apt/lists

```

If still unsuccessful, delete all the *files* in /var/lib/apt/lists but keep the *partial* folder. Remove the *contents* of the *partial* folder as well. At the end, you should have only the *partial* folder in /var/lib/apt/lists and the *partial* folder should be empty.

Run the following and if you still get error messages post them here (and I will let others take over!).
```

sudo apt-get update

```

---

### Post by hambos22 on 2009-06-30
Yes! :guitar: Done! Thank you so much my friend! You ROCK!!

---

