---
title: "Update in Ubuntu 9.04 gets a 404"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by Fenrisulfr on 2009-05-30
[FONT=Arial]somewhere around 2 weeks ago, the synaptic automatic update (for lack of knowledge of its name) gave me a message saying some stuff was out of date and to start the updater manually, When I let it run through checking for updates, it gives me this error: [/FONT]

"[B]Failed to fetch [http://archive.ubuntulinux.jp/ubuntu-ja/jaunty/Packages](http://archive.ubuntulinux.jp/ubuntu-ja/jaunty/Packages) 404 Not Found Some index files failed to download, they have been ignored, or old ones used instead."

[/B][FONT=Arial]and it has not been able to system updates and the like, though I can go into Add/Remove and do things there just fine

I'm not too savvy about Linux yet, but does the .jp instead of .com (or what ever it may be) have something to do with it?

oh yeah, I tried the link in firefox just to see what would happen and it still gives the 404 error.
[/FONT]

---

### Post by Mark Phelps on 2009-05-30
My guess would be that the ".jp" and "ja" would indicate japanese sources.  My sources are of the form "us.archive.ubuntu.com/ubuntu/"

---

### Post by Fenrisulfr on 2009-05-31
How would I go about changing to a US source that works?

---

### Post by Mark Phelps on 2009-05-31
You could install UbuntuTweak from the link below:

[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

It will allow you to edit your sources.list file. Choose Applications --> Sources Editor.

My sources are listed below (yours may need to be different):
```

 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner
deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main #ubuntu-tweak
deb http://packages.medibuntu.org/ jaunty free non-free #medibuntu
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://ppa.launchpad.net/rvm/ppa/ubuntu jaunty main #SMplayer

```

---

### Post by Old_Grey_Wolf on 2009-05-31
> **Fenrisulfr said:**
> How would I go about changing to a US source that works?

Try going to menu "System > Administration > Synaptic Package Manager". In Synaptic Package Manager select menu "Settings > Repositories". Look for a pulldown menu labeled "Download from". Choose a different server. Selecting "Other..." will give you a list of servers by country.

Hope that helps.

---

### Post by Fenrisulfr on 2009-05-31
Yes, Old_Grey_Wolf, that worked, thank you

too bad though, the new source I chose is significantly slower :/ (I let it attempt to find the quickest connection but there was none)

But my problem is solved, again, thank you

---

### Post by Old_Grey_Wolf on 2009-05-31
The problems with the servers are usually temporary. In a few days you may want to check if there is a faster one available.

And, thanks for letting me know my suggestion was helpful.

---

