---
title: "[SOLVED] cannot install GIMP"
date: 2008-08-04
forum: General Help
---

### Post by bimaljr on 2008-08-04
Hello,
I have Kubuntu 8.04 on my system

I have done this command from Konsole :
> sudo apt-get install gimp

and I got these massages :
> bimal@brcreation:~$ sudo apt-get install gimp
[sudo] password for bimal:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gimp: Depends: libgimp2.0 (>= 2.4.6) but it is not going to be installed
        Depends: libgimp2.0 (< 2.4.6-z) but it is not going to be installed
        Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is to be installed
E: Broken packages


Please help me on installing GIMP... Thank you

---

### Post by tuxxy on 2008-08-04
GIMP should come with the default install on Ubuntu I thought, check you havnt got it already and if not search for it synaptic and install the dependant files

EDIT: Your command with an * on the end should install the dependant files too

```
sudo apt-get install gimp*
```

---

### Post by bimaljr on 2008-08-04
Thanks for fast reply... but I am using Kubuntu, so there is no default GIMP installed
anyway.. still not solved :
> bimal@brcreation:~$ sudo apt-get install gimp*
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting gimp-cbmplugs for regex 'gimp*'
Note, selecting gimp-gap for regex 'gimp*'
Note, selecting gimp-libcurl for regex 'gimp*'
Note, selecting gimp-texturize for regex 'gimp*'
Note, selecting gimp-print for regex 'gimp*'
Note, selecting gimp-normalmap for regex 'gimp*'
Note, selecting gimp2.0-quiteinsane for regex 'gimp*'
Note, selecting gimp-wget for regex 'gimp*'
Note, selecting flegita-gimp for regex 'gimp*'
Note, selecting gimp-help-de for regex 'gimp*'
Note, selecting gimp-help-en for regex 'gimp*'
Note, selecting gimp-help-es for regex 'gimp*'
Note, selecting gimp-help-fr for regex 'gimp*'
Note, selecting libggimisc2 for regex 'gimp*'
Note, selecting gimp-help-it for regex 'gimp*'
Note, selecting gimp-help-ko for regex 'gimp*'
Note, selecting gimp-help-nl for regex 'gimp*'
Note, selecting gimp-help-no for regex 'gimp*'
Note, selecting gimp-help-ru for regex 'gimp*'
Note, selecting gimp-help-sv for regex 'gimp*'
Note, selecting gimp-help for regex 'gimp*'
Note, selecting gimp-svg for regex 'gimp*'
Note, selecting grokking-the-gimp for regex 'gimp*'
Note, selecting gimp-gnomevfs for regex 'gimp*'
Note, selecting gimp1.2-quiteinsane for regex 'gimp*'
Note, selecting cupsys-driver-gimpprint-data for regex 'gimp*'
Note, selecting gimp1.3 for regex 'gimp*'
Note, selecting gimp-data-extras for regex 'gimp*'
Note, selecting gimp-dimage-color for regex 'gimp*'
Note, selecting gimp-help-common for regex 'gimp*'
Note, selecting mrwtoppm-gimp for regex 'gimp*'
Note, selecting cupsys-driver-gimpprint for regex 'gimp*'
Note, selecting gimp-helpbrowser for regex 'gimp*'
Note, selecting gimp-refocus for regex 'gimp*'
Note, selecting libggimisc2-dev for regex 'gimp*'
Note, selecting gtkam-gimp for regex 'gimp*'
Note, selecting gimp-resynthesizer for regex 'gimp*'
Note, selecting gimageview for regex 'gimp*'
Note, selecting gimp-dcraw for regex 'gimp*'
Note, selecting gimp-perl for regex 'gimp*'
Note, selecting libgimp-perl instead of gimp-perl
Note, selecting gimp1.2-perl for regex 'gimp*'
Note, selecting gimp-gutenprint for regex 'gimp*'
Note, selecting gimp for regex 'gimp*'
Note, selecting gimp-plugin-registry for regex 'gimp*'
Note, selecting libgimp2.0 for regex 'gimp*'
Note, selecting slugimage for regex 'gimp*'
Note, selecting gimp1.3-cbmplugs for regex 'gimp*'
Note, selecting extremetuxracer-gimp-dev for regex 'gimp*'
Note, selecting ijsgimpprint for regex 'gimp*'
Note, selecting gimp-data for regex 'gimp*'
Note, selecting gimp-ufraw for regex 'gimp*'
Note, selecting foomatic-db-gimp-print for regex 'gimp*'
Note, selecting libgimp-perl for regex 'gimp*'
Note, selecting libgimp2.0-dev for regex 'gimp*'
Note, selecting gimp1.2-cbmplugs for regex 'gimp*'
Note, selecting planetpenguin-racer-gimp-dev for regex 'gimp*'
Note, selecting libgimp2.0-doc for regex 'gimp*'
Note, selecting gimp-dbg for regex 'gimp*'
Note, selecting gimp-python for regex 'gimp*'
Note, selecting gimmie for regex 'gimp*'
Note, selecting gimmix for regex 'gimp*'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gimp: Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is to be installed
  gimp-gnomevfs: Conflicts: gimp-libcurl but 2.4.6-1ubuntu1~hardy1 is to be installed
  gimp-libcurl: Conflicts: gimp-gnomevfs but 2.4.6-1ubuntu1~hardy1 is to be installed
  gimp-normalmap: Conflicts: gimp-plugin-registry but 0.5.1-4 is to be installed
  gimp-python: Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is to be installed
  gimp-ufraw: Conflicts: gimp-dcraw but 1.29-0ubuntu3 is to be installed
  libgimp2.0: Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is to be installed
E: Broken packages
bimal@brcreation:~ 

---

### Post by tuxxy on 2008-08-04
Use synaptic to install GIMP

---

### Post by LowSky on 2008-08-04
I assume Kubuntu has Add/Remove just like Ubuntu. Make sure that Show says All Availible Apllications. and install Gimp from there.
[IMG]http://www.psychocats.net/ubuntu/images/installingsoftware06.png[/IMG]

---

### Post by Titan8990 on 2008-08-04
Try the following before running apt-get install gimp again:


sudo apt-get update

sudo apt-get dist-upgade

note: above command might install new kernels if they are available.

---

### Post by bimaljr on 2008-08-04
I have also tried this but no luck..
here I am attaching screenshot for this
The error is :
> There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.

---

### Post by mb_webguy on 2008-08-04
Try this:
```
sudo apt-get update
sudo apt-get autoremove --purge
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install gimp
```
And post the output of these commands.

---

### Post by Bachstelze on 2008-08-04
A simple

```
sudo apt-get update
sudo apt-get install gimp
```

should be enough... Also, please apste the contents of your sources.list.

---

### Post by bimaljr on 2008-08-05
Thank you all, but still no success :(

> **HymnToLife said:**
> A simple

```
sudo apt-get update
sudo apt-get install gimp
```

should be enough... Also, please apste the contents of your sources.list.

here is the output for **HymnToLife** :
> 
sudo apt-get update
[sudo] password for bimal:
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_IN
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_IN
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_IN
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_IN
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_IN
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Fetched 1B in 3s (0B/s)
Reading package lists... Done


bimal@brcreation:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gimp: Depends: libgimp2.0 (>= 2.4.6) but it is not going to be installed
        Depends: libgimp2.0 (< 2.4.6-z) but it is not going to be installed
        Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is to be installed
E: Broken packages


My **sources.list** file :
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

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
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main
# deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free



For **mb_webguy** here are all command output :

> bimal@brcreation:~$ sudo apt-get autoremove --purge
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bimal@brcreation:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bimal@brcreation:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bimal@brcreation:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gimp: Depends: libgimp2.0 (>= 2.4.6) but it is not going to be installed
        Depends: libgimp2.0 (< 2.4.6-z) but it is not going to be installed
        Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is to be installed
E: Broken packages
bimal@brcreation:~$              

---

### Post by bimaljr on 2008-08-06
Hi,
No one ?

ok.. sorry guys the problem is solved... Thanks you to all of you for support. Without you, I don't know that the prob with the sources.list .

* My problem was that the **Unsupported updates** is selected in **Manage Repositories**. I don't know how this happen, maybe any application done this. I don't know.

_**I want to share how to do this :**_

_*How to :*_
**(1)** Just start *Adept Manager* and go to **Manage Repositories** in **Adept** menu. Now, go to **Updates** tab.

**(2)** under *Kubuntu upadtes* select this two **Important Security Updates** and **Recommended updates**.

**(3)** Don't select **Recommended updates** and **Unsupported updates**

**(4)** OK.. done. Close this box and Adept will automatically Fetch Updates, if not then click on **Fetch Updates** in Adept Manger.

---

### Post by thomasconor on 2008-08-14
THanks a lot man you saved my time. 

This works with synaptic tooo...

Tom

---

