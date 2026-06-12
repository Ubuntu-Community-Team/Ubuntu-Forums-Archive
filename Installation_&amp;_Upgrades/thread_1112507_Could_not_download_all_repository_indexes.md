---
title: "Could not download all repository indexes"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by bikepunk on 2009-03-31
hi

here is my first post to this forum, until now, I got only answers over here and I didn't even need to create an acount.  but now, I don't find the solution of my problem.

so, as the title says : "Could not download all repository indexes"
I know this is a quite common proble, I found already a few posts about it on this forum, but not MY solution.

this is the title of the error message I get when I try to change my repository or when I try to use Synaptic...
it's fulled with that :
> 
"The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

and then > [http://ubuntu.supp.name/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu.supp.name/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz:](http://ubuntu.supp.name/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz:) 404 Not Found


I guess that my problem is from my /etc/apt/sources.list file (although I didn't edit it)

here it is :
 See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade
to
# newer versions of the distribution.

deb [http://ubuntu.supp.name/ubuntu/](http://ubuntu.supp.name/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.supp.name/ubuntu/](http://ubuntu.supp.name/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the
Ubuntu
## team, and may not be under a free licence. Please satisfy yourself
as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu
security
## team.
deb [http://ubuntu.supp.name/ubuntu/](http://ubuntu.supp.name/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the
Ubuntu
## team, and may not be under a free licence. Please satisfy yourself
as to
## your rights to use the software. Also, please note that software in
#
See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


thank you in advance for help

---

### Post by drs305 on 2009-03-31
Your sources.list is trashed, in addition to containing references to feisty, which is no longer supported. If you really want feisty repos, let me know and I can provide more information.

Here is a link to a sources.list generator made by hyper_ch:
[http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/")

Run it, then replace the contents of /etc/apt/sources.list with what you get from running his script.

To replace the contents, back it up, then open sources.list for editing, remove the contents and paste the results of the script. Then save the file and run the final command to update your repositories:
```

sudo cp /etc/apt/source.list /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list
*after saving the result*
sudo apt-get update

```

If you have any problems with it just come back and ask and we can help.

**[COLOR="Red"]Welcome to the ubuntu forums.[/COLOR]**

*Added:* If you have general questions about repositories, here is the ubuntu wiki:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by bikepunk on 2009-03-31
tanks a lot, It works !!!

I have no idea about what is "feisty"... could you explain me or give a link ?
and I tried to use again the "software sources" tool and I got the same problem again... Is it such a bad idea to use the tools from xubuntu ?

---

### Post by kpatz on 2009-03-31
"Feisty Fawn" is Ubuntu 7.04 (I think, search to be sure).  You're running 8.04 "Hardy Heron" (or so you said in your profile).  So you should be pointing to the Hardy repositories, not the Feisty ones.

Now, if you're really running Feisty, you need to upgrade as it's no longer supported...

---

### Post by drs305 on 2009-03-31
Feisty was an older version of ubuntu. Each normal release is supported for 18 months; long term releases such as hardy are supported for 3 years. At the end of that time, no further updates are made and the repositories are eventually taken down.

Here is the release schedule: 
[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

Usually someone has a version for a long time and fails to update to a more recent version. They find out when the repositories no longer work. In your case, some of your links referenced feisty.

There are places to find the old repositories for users who really want to stick with a very old version, but these versions aren't updated or officially supported by ubuntu.  If you look at the stickies, there is a warning that Gutsy is reaching it's EOL - end of life. This reminds users that they need to consider upgrading.

I just reread your post. If you are still having problems, post the contents of your sources.list and confirm the version you are using.
```

cat /etc/apt/sources.list

```

---

### Post by bikepunk on 2009-03-31
I just installed linux for the first time in my life, using a CDR from a friend (I guess the CDR is old) is written xubuntu 8.04 so I guessed it was hardy (but I didn't check... :rolleyes: let's got for it !!)

---

### Post by drs305 on 2009-04-01
Here is the sources.list straight from the xubuntu livecd. The server is for the US. You can change it to another US server, another country's server, or choose the best server at the moment you check by opening synaptic or software sources (System, Administration, Synaptic or Software Sources. Settings, Repositories, then Download From, Other and select something if you don't want the US server.

Note the listings almost all refer to Ubuntu rather than Xubuntu. That's because they are very similar in many ways, and once you have one installed it is very easy to swith over to see how the other one looks. Also note that the CD-ROM entry is not active (that's what the # symbol does at the start of the line). If you try to enable it via the Settings menu, it may or may not work. It has to be the same date/version as your CD to work. It's best to leave it the way it is, otherwise every time you want to do any update it would ask you to insert the CD.

To change your sources.list, backup the file, open it and delete everything, and past this in. Save the file and then run the last line in the box to update your repository list. When you open the file, you will see a warning about editing the file. This is a system file but you won't hurt it as long as you follow these instructions.
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
gksudo mousepad /etc/apt/sources.list
[COLOR="Blue"]*Replace the entire contents with the entry quoted below. Then save the file and run:*[/COLOR]
sudo apt-get update   # Refresh the repository listings
sudo apt-get upgrade  # You will have a lot of updates!

```
> 
#deb cdrom:[Xubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


Good luck.

---

### Post by kpatz on 2009-04-01
Type **cat /etc/lsb-release** in a terminal to find out what version of Ubuntu you *really* have.

I bet it's Feisty.  Maybe your friend burned the wrong ISO when he made the CD for you...

---

### Post by bikepunk on 2009-04-01
no, actually, I've got hardy

> 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.2"
\

anyway, now, I got a lot of problem, the system is really not stable and for example, firefox close itself without reason...

actually, I'm working on an old computer (Pentium 3, 500Mhz...)
and I don't need such a user friendly OS, so, I'll try to install an other system, but thank you for help anyway ;)

---

