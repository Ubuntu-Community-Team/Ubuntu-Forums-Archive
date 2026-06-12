---
title: "[SOLVED] Repositories that you get when you install the first time?"
date: 2008-09-10
forum: General Help
---

### Post by L337_K3y5 on 2008-09-10
When I first installed Ubuntu, my add/remove selection was huge, but recently I've noticed that it has dwindled down to nearly nothing, I can browse through the entire list in under a minute, which most of them make up my installed programs.  What is the apt lines that you have at the beginning, because I may have accidentally deleted some over time whilst I was configuring Ubuntu to my liking.  I have the picture attached of my current apt lines.

---

### Post by cdtech on 2008-09-10
Looks good to me....

---

### Post by fooman on 2008-09-10
looks to me like you have plenty of repos enabled.

when you open the add/remove window...there is a drop down arrow to the right of "show".

make sure that "all available applications" is selected.

---

### Post by Vivaldi Gloria on 2008-09-10
> **L337_K3y5 said:**
>  my add/remove selection 

Have you tried synaptic?

Top panel > System menu > Admin. > Synaptic

---

### Post by L337_K3y5 on 2008-09-10
Well, I was just wondering, because I just received a free Ubuntu CD in the mail today, and I compared the add/remove to mine already installed.  The one on the disk was considerably larger in every section, as I don't even have any education programs now...There used to be a large selection of games too.

---

### Post by kostkon on 2008-09-10
> **L337_K3y5 said:**
> When I first installed Ubuntu, my add/remove selection was huge, but recently I've noticed that it has dwindled down to nearly nothing, I can browse through the entire list in under a minute, which most of them make up my installed programs.  What is the apt lines that you have at the beginning, because I may have accidentally deleted some over time whilst I was configuring Ubuntu to my liking.  I have the picture attached of my current apt lines.
First of all, are you sure you want the *Proposed* repository to be enabled. It is for people who want to test packages that are going to be given as official updates. Thus, this repository is serving testing and unstable packages.

You can enable the *Backports* repository, though.

Now about your problem. It is better that you post here the contents of the sources.list file that the GUI frontent (the *Software Sources* utility) reads. Thus, open a terminal and do
```
gedit /etc/apt/sources.list
```
and post the contents here for us to check if there are any problems with the file.

Your selection in *Software Sources* looks fine, by the way. The only strange thing I can see is that you have the AWN repository many times in your list of 3rd party software.

---

### Post by L337_K3y5 on 2008-09-10
Here is the message I get whenever I put that code in as root, I don't get this as normal user though:  ```
andrew@andrew-laptop:~$ gedit /ect/apt/sources.lst
andrew@andrew-laptop:~$ su
Password: 
root@andrew-laptop:/home/andrew# gedit /ect/apt/sources.lst

(gedit:30479): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
root@andrew-laptop:/home/andrew# 

```

This might be bad...but whenever I try to open up the sources.lst file...it looks empty.  This is probably not a good thing, I don't know how in the world that happened???:confused::confused::confused:

---

### Post by fooman on 2008-09-10
try this:

```
gksudo gedit /etc/apt/sources.lst
```

---

### Post by kostkon on 2008-09-10
> **L337_K3y5 said:**
> Here is the message I get whenever I put that code in as root, I don't get this as normal user though:  ```
andrew@andrew-laptop:~$ gedit /ect/apt/sources.lst
andrew@andrew-laptop:~$ su
Password: 
root@andrew-laptop:/home/andrew# gedit /ect/apt/sources.lst

(gedit:30479): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
root@andrew-laptop:/home/andrew# 

```
This might be bad...but whenever I try to open up the sources.lst file...it looks empty.  This is probably not a good thing, I don't know how in the world that happened???:confused::confused::confused:
First of all, you don't need to have admin priviledges to read the file. And its name is *sources.list* not *sources.lst*! Just do a
```
gedit /etc/apt/sources.list
```
without *sudo*. You just want to read it, not modify it.

---

### Post by L337_K3y5 on 2008-09-10
Well, thats a first, most files I write to, like grub, is .lst, oh well here it is finally:  ```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

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
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb http://packages.medibuntu.org/ hardy free non-free
deb http://apt.wicd.net hardy extras
deb http://ppa.launchpad.net/tualatrix/ubuntu hardy main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu hardy main
deb http://archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe
```

BTW-I removed the proposed part on my box, it seems I clicked that unknowingly today...lol, but I had a little redundance in my apt file, two sets were the same I believe, so I unchecked them, and uncommented the back ports.

---

### Post by kostkon on 2008-09-10
Your list seems fine. Although, go to *Software Sources* and remove the extra PPA repo lines for *AWN*. You only need a pair of them.

Do the above and then open a terminal and do a
*sudo apt-get update*
and check if you get any error messages.

---

### Post by L337_K3y5 on 2008-09-10
No error messages, fixed!

---

### Post by kostkon on 2008-09-10
> **L337_K3y5 said:**
> No error messages, fixed!
You didn't have any problems with your software sources list after all. So the problem must be elsewhere.

Or by saying fixed you mean that now *Add/Remove* and *Synaptic* show all the packages and thus everything is OK?

---

