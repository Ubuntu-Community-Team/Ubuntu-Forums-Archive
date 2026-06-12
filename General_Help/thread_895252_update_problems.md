---
title: "update problems"
date: 2008-08-20
forum: General Help
---

### Post by xGutsAndGloryx on 2008-08-20
i tried running a update on my system. It says, " Not All Updates Can Be Installed." Run a partial upgrade to install as many as possible. I run a partial upgrade. It gives me a error saying, "Error authenticating some packages. " It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.



what does the mean and how do i fix it?

---

### Post by mb_webguy on 2008-08-20
Try changing your server.  I've the authentication problem before, and it was fixed when I changed servers.

---

### Post by p_quarles on 2008-08-20
Have you added any third-party repositories/software sources since installing? It's possible that you added a source without signing its key, which will make packages from that source show up as "unauthenticated." This means that the software has no way of determining if the packages are legitimate, but doesn't mean there's anything wrong with them.

---

### Post by xGutsAndGloryx on 2008-08-20
> **p_quarles said:**
> Have you added any third-party repositories/software sources since installing? It's possible that you added a source without signing its key, which will make packages from that source show up as "unauthenticated." This means that the software has no way of determining if the packages are legitimate, but doesn't mean there's anything wrong with them.



its possible i might added third party repositories/software sources. how do i find and remove them. i can't remember the exact third-party repositories/software source

---

### Post by p_quarles on 2008-08-20
Post the results of these two commands:
```
cat /etc/apt/sources.list
```
and
```
ls /etc/apt/sources.list.d
```
Then we'll be able to tell you what you added.

---

### Post by xGutsAndGloryx on 2008-08-20
> **p_quarles said:**
> Post the results of these two commands:
```
cat /etc/apt/sources.list
```
and
```
ls /etc/apt/sources.list.d
```
Then we'll be able to tell you what you added.

cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main #Firefox
deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) hardy main #Screenlets
deb [http://ppa.launchpad.net/googlegadgets/ubuntu](http://ppa.launchpad.net/googlegadgets/ubuntu) hardy main #Google gadgets
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

#ULTAMATIX REPOS START

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted

deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
#ULTAMATIX REPOS END




medibuntu.list       playonlinux.list       winehq.list
medibuntu.list.save  playonlinux.list.save  winehq.list.save

---

### Post by p_quarles on 2008-08-20
The launchpad repositories are most likely the culprit here. The Ultamatix stuff could also be to be blame, and looks particularly unnecessary since you have Medibuntu.

If you trust those sources, you can leave them, but you'll have to confirm that error whenever you update software.

---

### Post by xGutsAndGloryx on 2008-08-20
> **p_quarles said:**
> The launchpad repositories are most likely the culprit here. The Ultamatix stuff could also be to be blame, and looks particularly unnecessary since you have Medibuntu.

If you trust those sources, you can leave them, but you'll have to confirm that error whenever you update software.




how do i remove it. i am still pretty new to linux. do i just go to software sources?

---

### Post by p_quarles on 2008-08-20
> **xGutsAndGloryx said:**
> how do i remove it. i am still pretty new to linux. do i just go to software sources?
That should work. If not, run:
```
gksu gedit /etc/apt/sources.list
```
Delete the lines you don't want, and save the file.

---

### Post by xGutsAndGloryx on 2008-08-20
> **p_quarles said:**
> That should work. If not, run:
```
gksu gedit /etc/apt/sources.list
```
Delete the lines you don't want, and save the file.




i tried removing those and its still not working? do you have any other advice?

---

### Post by p_quarles on 2008-08-20
You need to run 
```
sudo apt-get update
```
before the source list cache changes.

---

### Post by prshah on 2008-08-20
> **xGutsAndGloryx said:**
> i tried running a update on my system. It says, " Not All Updates Can Be Installed." 

 It gives me a error saying, "Error authenticating some packages. " It was 


The second error is probably because some packages download has failed; I dont think you need to make any changes to your apt sources.lst;

The first error may also occur if your repo information is not updated; first, run ```
sudo apt-get update && sudo apt-get update
``` to bring both package information as well as installed packages in line with current versions.

---

### Post by p_quarles on 2008-08-20
> **prshah said:**
>  I dont think you need to make any changes to your apt sources.lst;
Did Launchpad change recently to use GPG keys for PPAs? Unless it did, that repo is definitely causing the unauthenticated packages error.

---

### Post by mb_webguy on 2008-08-20
Have you tried changing your repository server?  As I said, I had this problem about a week ago, and changing servers fixed it.

Go to System->Administration->Software Sources, click the "Download from:" drop-down list, and select "Other".  Click the "Select Best Server" button, let it run the tests, then click the "Choose Server" button. then click "Close" and then "Reload" to update your sources.

If that doesn't fix your problem, I'll eat my hat.  Of course, it's a tiny hat I made from a slice of cheese...

---

### Post by xGutsAndGloryx on 2008-08-20
> **p_quarles said:**
> Did Launchpad change recently to use GPG keys for PPAs? Unless it did, that repo is definitely causing the unauthenticated packages error.

i tried the advice in the last two posted. its still not working. is there anyway i can rest the software source to the default ?

---

### Post by mb_webguy on 2008-08-20
To reset your sources to the default, rename /etc/apt/sources.list.d to /etc/apt/sources.list.d.backup, copy /etc/apt/sources.list to /etc/apt/sources.list.backup, and paste the following in /etc/apt/sources.list:
```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security multiverse

```

That's assuming you're using Hardy, of course...

---

### Post by xGutsAndGloryx on 2008-08-20
> **mb_webguy said:**
> To reset your sources to the default, rename /etc/apt/sources.list.d to /etc/apt/sources.list.d.backup, copy /etc/apt/sources.list to /etc/apt/sources.list.backup, and paste the following in /etc/apt/sources.list:
```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security multiverse

```

That's assuming you're using Hardy, of course...




how do i go about rename it? is there commands to enter into the terminal?

---

### Post by mb_webguy on 2008-08-20
```
sudo mv /etc/apt/sources.list.d /etc/apt/sources.list.d.backup
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksu gedit /etc/apt/sources.list
```

The last will open the sources file in the text editor.  Select all of what I posted above and copy, then select all of the file in the text editor and paste, to replace the entire file with what I posted.  Then save and update your sources.

---

### Post by crazyness003 on 2008-08-20
You can either enter
```
gksu gedit /etc/apt/sources.list
```and save as...
or
```
sudo mv /etc/apt/sources.list to /etc/apt/sources.list.backup
```and the same for sources.list.d (whatever that is)

EDIT: aahh, you beat me.
Anyway, theres also a GUI way to do it, but you need some Nautilus scripts to do it.
check out [This Place]("http://www.gnome-look.org/content/show.php/Open+As+Root(Working)?content=76932"). That particular link send you to a good Script. But you have to be VERY CAREFUL when utilizing these scripts. It makes it easier to screw up your system, so be careful. More are on that site. and use only what you need.

---

### Post by xGutsAndGloryx on 2008-08-20
> **mb_webguy said:**
> ```
sudo mv /etc/apt/sources.list.d /etc/apt/sources.list.d.backup
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksu gedit /etc/apt/sources.list
```

The last will open the sources file in the text editor.  Select all of what I posted above and copy, then select all of the file in the text editor and paste, to replace the entire file with what I posted.  Then save and update your sources.

thanks i think that fixed it. its not detecting any updates now but no error

---

### Post by crazyness003 on 2008-08-20
dont forget to mark [SOLVED]!
then :guitar: out with success!

---

