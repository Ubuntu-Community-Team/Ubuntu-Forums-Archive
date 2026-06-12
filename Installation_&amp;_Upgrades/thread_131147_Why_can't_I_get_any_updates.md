---
title: "Why can't I get any updates?"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by towsonu2003 on 2006-02-15
These are the links to the available updates that I think apply to my system: 
[http://ubuntuforums.org/showthread.php?t=130909](http://ubuntuforums.org/showthread.php?t=130909) (unzip)
[http://ubuntuforums.org/showthread.php?t=130907](http://ubuntuforums.org/showthread.php?t=130907) (unzip, again)
[http://ubuntuforums.org/showthread.php?t=130908](http://ubuntuforums.org/showthread.php?t=130908) (kernel)

For unzip, 
I have 5.52-3.ubuntu2
Update will get me 5.52-3.ubuntu2-2

For linux kernel,
I have 2.6.12-10.26 (386 and 686)
Update will get me 2.6.12-10.28

Here is my sources.list:
> 
$ cat /etc/apt/sources.list
## Major bug fix updates produced after the final release of the
## distribution.
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## This is backwords, comment once done! Used to get libdvdcss2
## deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## This is for OpenOffice 2.0
## deb [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) ./
sudo apt-get update + upgrade gives no error and behaves as if there are no updates available. Synaptic does not show any upgradable packages either. What's going on in here? Am I too sleepy to miss something very simple?

---

### Post by rfruth on 2006-02-15
Why not just use the package manager (Synaptic) too limiting ?

---

### Post by towsonu2003 on 2006-02-15
problem is, both of them say the same thing: no updates available... :???:

---

### Post by bluevoodoo1 on 2006-02-15
I'm wondering the same thing... why can't I get the updates?? I have a similar sources.list too.

---

### Post by linear on 2006-02-15
If it's any comfort, I don't see them either. Perhaps they just haven't made it into the repositories yet? (You could download from the links given in the posts, if you want the updates right away.)

---

### Post by aysiu on 2006-02-15
[QUOTE=towsonu2003]Synaptic does not show any upgradable packages either. What's going on in here? Am I too sleepy to miss something very simple?[/QUOTE] Right now, this is the only repository in your sources.list file: ```
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
``` A # sign in front of a line basically tells Ubuntu, "Ignore the rest of this line. It doesn't exist."

---

### Post by towsonu2003 on 2006-02-15
[quote=aysiu]Right now, this is the only repository in your sources.list file[/quote] lol I'm not that sleepy :)

the file is a little confusing I know... I had to take out the source (deb-src) repos as I'm using dial up (update by itself takes 20 minutes on dial up without source repos). This list was working great so far (two kernel updates etc.)

These are the repos enabled: 
> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


I remember seeing this in someone's signature so I tried it, but didn't help (oh, it was kinda in aysiu's signature)
```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup
sudo touch /etc/apt/sources.list
sudo apt-get update
sudo rm /etc/apt/sources.list
sudo mv /etc/apt/sources.list.backup /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade
```
didn't work -still no updates out there..

---

### Post by aysiu on 2006-02-15
[QUOTE=towsonu2003]lol I'm not that sleepy :)

the file is a little confusing I know... I had to take out the source (deb-src) repos as I'm using dial up (update by itself takes 20 minutes on dial up without source repos). This list was working great so far (two kernel updates etc.)

These are the repos enabled: [/QUOTE] Ah, you're right. I got distracted by all the # signs in there!

Are you expecting a lot of upgrades...?

---

### Post by towsonu2003 on 2006-02-15
Adding more info
This one is having the same problem: [http://ubuntuforums.org/showthread.php?p=739326#post739326](http://ubuntuforums.org/showthread.php?p=739326#post739326)
This one shows why the security announcements was behaving weird (4-5 posts in the last 9 hours): [http://ubuntuforums.org/showthread.php?p=738474#post738474](http://ubuntuforums.org/showthread.php?p=738474#post738474)

I'll wait a day or two than file a bug I guess...

---

### Post by towsonu2003 on 2006-02-15
[QUOTE=aysiu]
Are you expecting a lot of upgrades...?[/QUOTE]
oops, I didn't see the reply -sorry
I am expecting a kernel upgrade (386+686 headers+image and +restricted modules if needed(?) ) and for unzip upgrade. 
Kernel upgrade usually takes 3-4 hours (2 kernel images + 2 kernel headers) w. dial up, so Im expecting a lot of updates ;)

---

### Post by sal on 2006-02-16
i'm also not get these security udates as of this morning right before posting this here. i tryed synaptic, sudo apt-get update then sudo apt-get upgrade, and then i tryed sudo apt-get update and sudo apt-get dist-upgrade still no luck.

im running kubuntu 5.10 with kde 3.5.1

anyone know whats going on with this?

---

