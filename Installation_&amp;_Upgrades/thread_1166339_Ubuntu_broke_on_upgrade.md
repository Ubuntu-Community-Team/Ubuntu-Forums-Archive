---
title: "Ubuntu broke on upgrade"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by Rhino2 on 2009-05-21
Ubuntu keeps crashing in my VM.  I have no problems with XP.  I was told in a forum to upgrade to latest version of ubuntu.

When I try to upgrade (by System->Admin->Update Manager) it gives an error about Linux kernel package missing or corrupt.  I try partial upgrade and removing it like it suggests, but still errors out.  It then says I need to fix it by an apt-get install -f, I run that and it also gives an error:

> 
rabiit@rabiit-desktop:~$ uname -a
Linux rabiit-desktop 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 G          NU/Linux
rabiit@rabiit-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package linux-image-2.6.27-11-generic needs to be reinstalled, but I can'          t find an archive for it.
rabiit@rabiit-desktop:~$



I'm not impressed. I run XP using the same VM software and it doesn't crash and windows update works fine.

VM is Virtual Box 2.2.  Sun's site says that it does support Linux... 

How do I get Ubuntu upgrade it's self properly since it's obviously in a completely broken state?  If I have to do a full reinstall, then I'm going to go with windows since this is turning out to be such a pain.  How do I manually re-install this linux-image-2.6.27-11-generic ?

---

### Post by taurus on 2009-05-21
Just post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by Rhino2 on 2009-05-21
I haven't touched this file, it's what came with it.


# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

---

### Post by taurus on 2009-05-21
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Rhino2 on 2009-05-21
It is now saying my software index is broke (when I go to package manager).
The message is:

"Software Index is Broke".

... please run 'apt-get install -f' (which I did, see above).

When I goto package Manager it says:


"The package linux-generic..xxxx needs to be re installed but I can't find an archive for it

E: Internal Error opening cache.  Please Report"

---

### Post by Rhino2 on 2009-05-21
> **taurus said:**
> ```
sudo apt-get update
sudo apt-get dist-upgrade
```

First command works fine.  The second gives this error:



"The package linux-generic..xxxx needs to be re installed but I can't find an archive for it"

---

### Post by Rhino2 on 2009-05-21
I talked to my friend over the phone.  He says I need to do a full reinstall of Linux.  He says that it's best to do a full reinstall with every new version of Ubuntu.  Last time it took over 4 hours to install and told him I'm not doing that again.  

Can I just do a "Linux update" and just download the newest 'everything'?  Just force an install the newest packages?  If it can't find this linux-generic.xxxx how do I force it to just download a new copy of it and install that copy instead?  If the file is corrupt, why doesn't it just re-download a good copy?  I don't understand.

In window, I once downloaded a bad version of firefox.  My internet connection dropped and it got corrupted. It won't run, so I deleted it and re-downloaded again and that version wasn't corrupt and installed fine.  Why I can't I just "download" a new version of this linux-generic?

---

### Post by taurus on 2009-05-21
Bet that kernel version is only available for Intrepid but your /etc/apt/sources.list is pointing to Jaunty.  Therefore, the system can't find that version in the repos anymore.  What if you edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and change all the word **jaunty** back to **intrepid** in there.  Save it and run

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Rhino2 on 2009-05-21
ok, I did that and ran it and it gave me some errors.

I ran it again and seems to be doing something, but now getting a bunch of "incompatible binary revision" and lots of "segment fault" messages and weird squiggly messages.

Then the VM crashed with a kernel panic message.

hrm, brb, going to reboot it.

---

### Post by Rhino2 on 2009-05-21
wow, it's taking a really long time to boot.  It says it's checking /dev/sda 

at the rate it's going, this is going to take awhile.  I need to do some errands, I'll be back in a bit.

---

### Post by Rhino2 on 2009-05-21
ok, it finally finished with it's little disk check.

it's back at the same thing: "the package linux-image.xxx needs to be reinstalled but I can't find an archive for it."

this is getting tiresome.

---

### Post by Rhino2 on 2009-05-21
It's all complaining that my "software index is broke".

wtf, seriously.  piece of junk.  I NEVER touched my software index.  I've used this for firefox and that is it.  Why is this so buggy?  Everyone says it's better then XP, but that is a load of crap.  Both my host and other VM are XP and never had any problems like this what so ever.  Windows update works and I have never had to reinstall them.  Neither of them crash, but all those problems happen under Linux.

But, I'll play along.  How do I rebuild my "software index" ?  Why doesn't it automatically fix it?  The guy in xchat said that I never had to touch the command line in Ubuntu because the desktop "just works".   I guess that isn't the case now because apparently it has troubles running a web browser without exploding and corrupting it's self.

---

### Post by taurus on 2009-05-21
You did something to your machine because it changed from intrepid to jaunty in /etc/apt/sources.list.  But if you think windows is better, then stick with it.

---

### Post by Rhino2 on 2009-05-21
> **taurus said:**
> You did something to your machine because it changed from intrepid to jaunty in /etc/apt/sources.list.  But if you think windows is better, then stick with it.

Indeed, I did change that and also did try and run the update manager.  Both of them were suggested from this forum; which I would assume (or at least hope) was correct and informed advice.

But I guess it is A) it's broke and not ready for the normal desktop user and B) the advice Ubuntu forums was incorrect and C) their final suggestion is "go back to windows".

If that is your final answer, then I'll print that for my review.

---

### Post by taurus on 2009-05-21
Running Ubuntu as a guest OS (in VM environment) is not the same as running Ubuntu on it own partition.  Therefore, the normal way of doing things in Ubuntu might not apply in your case.

---

### Post by Rhino2 on 2009-05-21
Sun says they official support, not only linux, but Ubutnu in their VM.

Secondly, this document from Ubutnu suggests that it is in fact supported:

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

If it's not supported, then I will take that into consideration, but really think there should be a disclaimer on that document (and others).

---

### Post by taurus on 2009-05-21
Of course it is supported!  But the problem is that you try to upgrade from one release to another release (who knows what exactly did you do or how did you do that) and somehow caused a problem.  Did you have any problem at all when you ran Intrepid on your machine as a guest OS (before you modified your /etc/apt/sources.list to Jaunty)?

---

### Post by Rhino2 on 2009-05-21
> **taurus said:**
>  But the problem is that you try to upgrade from one release to another release (who knows what exactly did you do or how did you do that)

I did an install and have been using fire fox.  It has been crashing.  Some times every 10 minutes, so times every 2 or 3 days.  Other then the install and using firefox, I haven't been changing anything with the system.

They said I should upgrade to newest version of both Virtual Box (which I did and worked fined) and Newest version of Ubuntu to fix the problem with it crashing.

See my first post, I went to 'Update Manager' (like they suggested) and at top it said "New version is available, x.x.x'.  I clicked 'Update' (like they suggested).  It grinned the disk for awhile and appeared to be working then threw that error (see my first post.  "linux-generic is corrupt, etc").

I didn't do anything other then click 'update' on the Update Manager.

If that is not supported or not suppose to do that, then why did they program it in?

>  and somehow caused a problem.  Did you have any problem at all when you ran Intrepid on your machine as a guest OS (before you modified your /etc/apt/sources.list to Jaunty)?

Yea, the reason they told me to try 'Intrepid' is because Jaunty wasn't updating the Linux-generic correctly.  It was crashing and failing to update before I even tried Intrepid.  I only tried it because of their suggestions.

There are two problems:  

1) It' crashing.  This was happening before I updated any packages.

2) It can't update linux-generic, saying package is corrupt.  I was trying to upgrade (like they suggested) to fix the crashing.

---

