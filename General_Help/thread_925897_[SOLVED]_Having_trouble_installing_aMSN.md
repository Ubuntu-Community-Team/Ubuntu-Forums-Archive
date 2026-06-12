---
title: "[SOLVED] Having trouble installing aMSN"
date: 2008-09-21
forum: General Help
---

### Post by ziggy25 on 2008-09-21
When i try to log on as root using the terminal the password is accepted. If i get that login window that asks for the root password (to update packages or to do any administrative task), the password is rejected. Is something wrong with my installation?

---

### Post by damis648 on 2008-09-21
Are you using sudo or su? Sudo uses YOUR password, and so does that gksudo window that pops up when updating packages. Su will use specifically root's password.

---

### Post by aysiu on 2008-09-21
Ubuntu does not let you log in graphically as a root user by default, and the forums have a policy that does not allow for tutorials on how to enable a graphical root login.

Why don't you tell us why you think you need to log in as root, and then we'll tell you the proper way to accomplish that task?

In the meantime, you may find this helpful:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by ziggy25 on 2008-09-21
Well im not really sure whether i need to log on as root. 

I am new to Ubuntu and was trying to find out how i can install new software.  To do this i clicked on applications>>add/remove and did a search on aMsn. The program i was looking for was shown in the list but when i click on the application i get that login prompt to enter the password. 

If Ubuntu does not allow root login graphically, how do i then install the software? Can i install the software via the command prompt?

---

### Post by aysiu on 2008-09-21
You should be able to install aMSN from Add/Remove. Let me double-check.

In the meantime, read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by aysiu on 2008-09-21
Okay. This is how you install aMSN with Add/Remove.

Go to Applications > Add/Remove

Make sure you show All Available Applications

Then search for *amsn*

Check the box next to aMSN

When prompted to enable extra repositories, go ahead and do so

Wait for the available software information to refresh

Apply changes

It should now be in your Applications > Internet menu

---

### Post by outsider_gutsy on 2008-09-21
Use Synaptic Package manager. (System > Administration > Synaptic Package Manager) Check [https://help.ubuntu.com/community/SynapticHowto]("https://help.ubuntu.com/community/SynapticHowto") for details.

Once you have updated the list of packages ( a piece of software ) you can search for amsn and say "Apply". Synaptic will download and install it for you.

And yes, once you are used to Synaptic, installing any software will be a piece of cake. Go ahead. Give it a try

---

### Post by ziggy25 on 2008-09-21
Thanks guys for helping with this. 

I followed your instructions and tried it via the add/remove menu. It did download but when it tried to install it produced this error. 

> Cannot install 'amsn'

This application conflicts with other installed software. To install 'amsn' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

I tried to switch to synaptic but got the following error when i tried to "mark for Installatoin" the amsn entry in synaptic, i got this error. 

> 
Could not mark all packages for installation or upgrade. 
amsn:
 Depends: tcl8.4  but it is not installable
 Depends: tk8.4  but it is not installable
 Depends: tcltls but it is not going to be installed


---

### Post by aysiu on 2008-09-21
Did you edit your /etc/apt/sources.list file manually? Conflicting software or dependency errors usually come from conflicting software repository sources.

Can you paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
cat /etc/apt/sources.list
```

---

### Post by ziggy25 on 2008-09-21
> **aysiu said:**
> Did you edit your /etc/apt/sources.list file manually? Conflicting software or dependency errors usually come from conflicting software repository sources.

Can you paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
cat /etc/apt/sources.list
```

Hi here is the output 

```

ziggy@ziggy-ub:~/Downloads$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
ziggy@ziggy-ub:~/Downloads$ 



```

---

### Post by aysiu on 2008-09-21
It looks as if you were having some internet connection issues when Ubuntu got installed and tried to verify the software repository sources.

Am I right that in thinking you are using Ubuntu 7.10 (codenamed *Gutsy Gibbon*)?

If so, paste these commands into the terminal: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.broken
gksudo gedit /etc/apt/sources.list
``` This last command should open a blank text file. In the blank text file, paste in ```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted


deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

``` Save and exit the file. Then paste in the terminal ```
sudo apt-get update
sudo apt-get install --reinstall amsn
``` Add/Remove should work after this.

---

### Post by ziggy25 on 2008-09-21
That worked perfectly. Im starting to like this Ubuntu mania. 

Thanks again for your help. It is now installed and im getting automatic updates as well which i wsnt getting before :)

---

