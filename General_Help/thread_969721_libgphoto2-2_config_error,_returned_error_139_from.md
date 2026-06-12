---
title: "libgphoto2-2 config error, returned error 139 from segfault."
date: 2008-11-03
forum: General Help
---

### Post by personjerry on 2008-11-03
Okay so I was upgrading from Hardy Heron to Intrepid Ibex yesterday (a while back, now, considering the longevity of this thread), and it basically told me that libgphoto2-2 config had errors. Then, other programs' config went wrong as well. I reconfigured it again, see below. Please help me to solve this.

Alright it's been a while, a whole lotta bumps.
The following is a list of pages where there are posts of interest: [1]("http://ubuntuforums.org/showthread.php?t=969721"), [2]("http://ubuntuforums.org/showthread.php?t=969721&page=2"), [4]("http://ubuntuforums.org/showthread.php?t=969721&page=4"), [5]("http://ubuntuforums.org/showthread.php?t=969721&page=5"), [7]("http://ubuntuforums.org/showthread.php?t=969721&page=7"), [8]("http://ubuntuforums.org/showthread.php?t=969721&page=8").

The errors happen whenever reconfiguring happens, dpkg --configure -a, etc. all has the same results.

Updated errors:
(still based off libgphoto2-2)

```
Setting up libgphoto2-2 (2.4.2-0ubuntu3) ...
Segmentation fault
dpkg: error processing libgphoto2-2 (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of f-spot:
 f-spot depends on libgphoto2-2 (>= 2.4.0); however:
  Package libgphoto2-2 is not configured yet.
dpkg: error processing f-spot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsane:
 libsane depends on libgphoto2-2 (>= 2.4.0); however:
  Package libgphoto2-2 is not configured yet.
dpkg: error processing libsane (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs-backends:
 gvfs-backends depends on libgphoto2-2 (>= 2.4.0); however:
  Package libgphoto2-2 is not configured yet.
dpkg: error processing gvfs-backends (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kamera:
 kamera depends on libgphoto2-2 (>= 2.4.0); however:
  Package libgphoto2-2 is not configured yet.
dpkg: error processing kamera (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine:
 wine depends on libgphoto2-2 (>= 2.4.0); however:
  Package libgphoto2-2 is not configured yet.
dpkg: error processing wine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on gvfs-backends; however:
  Package gvfs-backends is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gthumb:
 gthumb depends on libgphoto2-2 (>= 2.4.0); however:
  Package libgphoto2-2 is not configured yet.
dpkg: error processing gthumb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on libsane (>= 1.0.11-3); however:
  Package libsane is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xsane:
 xsane depends on libsane (>= 1.0.11-3); however:
  Package libsane is not configured yet.
dpkg: error processing xsane (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on nautilus (>= 2.10); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hpijs:
 hpijs depends on hplip (= 2.8.7-0ubuntu6); however:
  Package hplip is not configured yet.
dpkg: error processing hpijs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-cd-burner:
 nautilus-cd-burner depends on nautilus; however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-cd-burner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-core:
 gnome-core depends on nautilus (>= 2.20.0); however:
  Package nautilus is not configured yet.
dpkg: error processing gnome-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-desktop-environment:
 gnome-desktop-environment depends on gnome-core (= 1:2.22.2~4ubuntu2); however:
  Package gnome-core is not configured yet.
 gnome-desktop-environment depends on nautilus-cd-burner (>= 2.20.0); however:
  Package nautilus-cd-burner is not configured yet.
dpkg: error processing gnome-desktop-environment (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-office:
 gnome-office depends on gnome-core (= 1:2.22.2~4ubuntu2); however:
  Package gnome-core is not configured yet.
 gnome-office depends on xsane; however:
  Package xsane is not configured yet.
dpkg: error processing gnome-office (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hpijs-ppds:
 hpijs-ppds depends on hpijs (>= 2.8.7-0ubuntu6); however:
  Package hpijs is not configured yet.
dpkg: error processing hpijs-ppds (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome:
 gnome depends on gnome-desktop-environment (= 1:2.22.2~4ubuntu2); however:
  Package gnome-desktop-environment is not configured yet.
dpkg: error processing gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-accessibility:
 gnome-accessibility depends on gnome-core (= 1:2.22.2~4ubuntu2); however:
  Package gnome-core is not configured yet.
dpkg: error processing gnome-accessibility (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip-gui:
 hplip-gui depends on hplip; however:
  Package hplip is not configured yet.
dpkg: error processing hplip-gui (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of foomatic-db-hpijs:
 foomatic-db-hpijs depends on hpijs (>> 2); however:
  Package hpijs is not configured yet.
dpkg: error processing foomatic-db-hpijs (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libgphoto2-2
 f-spot
 libsane
 gvfs-backends
 kamera
 wine
 nautilus
 ubuntu-desktop
 gthumb
 hplip
 xsane
 nautilus-share
 hpijs
 nautilus-cd-burner
 gnome-core
 gnome-desktop-environment
 gnome-office
 hpijs-ppds
 gnome
 gnome-accessibility
 hplip-gui
 foomatic-db-hpijs
jerry@CPE0018c0754434-CM00195eda24f6:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
22 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up libgphoto2-2 (2.4.2-0ubuntu3) ...
Segmentation fault
dpkg: error processing libgphoto2-2 (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of libsane:
 libsane depends on libgphoto2-2 (>= 2.4.0); however:
  Package libgphoto2-2 is not configured yet.
dpkg: error processing libsane (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on libsane (>= 1.0.11-3); however:
  Package libsane is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine:
 wine depends on libgphoto2-2 (>= 2.4.0); however:
  Package libgphoto2-2 is not configured yet.
dpkg: error processing wine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of f-spot:
 f-spot depends on libgphoto2-2 (>= 2.4.0); however:
  Package libgphoto2-2 is not configured yet.
dpkg: error processing f-spot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems preNo apport report written because the error message indicates its a followup error from a previous failure.
                                                       No apport report written because the error message indicates its a followup error from a previous failure.
 No apport report written because MaxReports is reached already
                                                               No apport report written because MaxReports is reached already
                                             No apport report written because MaxReports is reached already
                           No apport report written because MaxReports is reached already
         No apport report written because MaxReports is reached already
                                                                       No apport report written because MaxReports is reached already
                                                     No apport report written because MaxReports is reached already
                                   No apport report written because MaxReports is reached already
                 No apport report written because MaxReports is reached already
                                                                               No apport report written because MaxReports is reached already
                                                             No apport report written because MaxReports is reached already
                                           No apport report written because MaxReports is reached already
                         vent configuration of hpijs:
 hpijs depends on hplip (= 2.8.7-0ubuntu6); however:
  Package hplip is not configured yet.
dpkg: error processing hpijs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of foomatic-db-hpijs:
 foomatic-db-hpijs depends on hpijs (>> 2); however:
  Package hpijs is not configured yet.
dpkg: error processing foomatic-db-hpijs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs-backends:
 gvfs-backends depends on libgphoto2-2 (>= 2.4.0); however:
  Package libgphoto2-2 is not configured yet.
dpkg: error processing gvfs-backends (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on gvfs-backends; however:
  Package gvfs-backends is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-core:
 gnome-core depends on nautilus (>= 2.20.0); however:
  Package nautilus is not configured yet.
dpkg: error processing gnome-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-cd-burner:
 nautilus-cd-burner depends on nautilus; however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-cd-burner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-desktop-environment:
 gnome-desktop-environment depends on gnome-core (= 1:2.22.2~4ubuntu2); however:
  Package gnome-core is not configured yet.
 gnome-desktop-environment depends on nautilus-cd-burner (>= 2.20.0); however:
  Package nautilus-cd-burner is not configured yet.
dpkg: error processing gnome-desktop-environment (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome:
 gnome depends on gnome-desktop-environment (= 1:2.22.2~4ubuntu2); however:
  Package gnome-desktop-environment is not configured yet.
dpkg: error processing gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-accessibility:
 gnome-accessibility depends on gnome-core (= 1:2.22.2~4ubuntu2); however:
  Package gnome-core is not configured yet.
dpkg: error processing gnome-accessibility (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xsane:
 xsane depends on libsane (>= 1.0.11-3); however:
  Package libsane is not configured yet.
dpkg: error processing xsane (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-office:
 gnome-office depends on gnome-core (= 1:2.22.2~4ubuntu2); however:
  Package gnome-core is not configured yet.
 gnome-office depends on xsane; however:
  Package xsane is not configured yet.
dpkg: error processing gnome-office (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gthumb:
 gthumb depends on libgphoto2-2 (>= 2.4.0); however:
  Package libgphoto2-2 is not configured yet.
dpkg: error processing gthumb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hpijs-ppds:
 hpijs-ppds depends on hpijs (>= 2.8.7-0ubuntu6); however:
  Package hpijs is not configured yet.
dpkg: error processing hpijs-ppds (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip-gui:
 hplip-gui depends on hplip; however:
  Package hplip is not configured yet.
dpkg: error processing hplip-gui (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on nautilus (>= 2.10); however:
  Package nautilus is not configured yet.
dpkg: error proceNo apport report written because MaxReports is reached already
                                                                               No apport report written because MaxReports is reached already
                                                             No apport report written because MaxReports is reached already
                                           No apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already
       No apport report written because MaxReports is reached already
                                                                     No apport report written because MaxReports is reached already
                                                   ssing nautilus-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
 ubuntu-desktop depends on nautilus-cd-burner; however:
  Package nautilus-cd-burner is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kamera:
 kamera depends on libgphoto2-2 (>= 2.4.0); however:
  Package libgphoto2-2 is not configured yet.
dpkg: error processing kamera (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libgphoto2-2
 libsane
 hplip
 wine
 f-spot
 hpijs
 foomatic-db-hpijs
 gvfs-backends
 nautilus
 gnome-core
 nautilus-cd-burner
 gnome-desktop-environment
 gnome
 gnome-accessibility
 xsane
 gnome-office
 gthumb
 hpijs-ppds
 hplip-gui
 nautilus-share
 ubuntu-desktop
 kamera
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by personjerry on 2008-11-04
Bump
Ump
Mp
P

---

### Post by Maurizio Benedetti on 2008-11-05
Same problem for me guys.

---

### Post by personjerry on 2008-11-05
Bump
Ump
Mp
P

---

### Post by personjerry on 2008-11-06
Bump
Ump
Mp
P

---

### Post by personjerry on 2008-11-07
Bump
Ump
Mp
P

---

### Post by personjerry on 2008-11-08
Bump
Ump
Mp
P

---

### Post by personjerry on 2008-11-09
Bump
Ump
Mp
P

---

### Post by personjerry on 2008-11-10
bump yet again!

---

### Post by fatdragon on 2008-11-11
Same problem here after upgrading from Hardy to Intrepid...

---

### Post by fatdragon on 2008-11-11
Here are the errors when I reinstall libgphoto2-2:

E: libgphoto2-2: subprocess post-installation script returned error exit status 139
E: libsane: dependency problems - leaving unconfigured
E: hplip: dependency problems - leaving unconfigured
E: f-spot: dependency problems - leaving unconfigured
E: hpijs: dependency problems - leaving unconfigured
E: foomatic-db-hpijs: dependency problems - leaving unconfigured
E: gthumb: dependency problems - leaving unconfigured
E: gvfs-backends: dependency problems - leaving unconfigured
E: nautilus: dependency problems - leaving unconfigured
E: nautilus-cd-burner: dependency problems - leaving unconfigured
E: nautilus-share: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured
E: xsane: dependency problems - leaving unconfigured

---

### Post by personjerry on 2008-11-11
yes, so i'm bumping again!

---

### Post by personjerry on 2008-11-11
btw, since those configurations depend on the libgphoto2-2, the actual error would be just the one in the title.

---

### Post by personjerry on 2008-11-12
rebump

---

### Post by personjerry on 2008-11-13
bump agggggggggain

---

### Post by personjerry on 2008-11-14
Another bump

---

### Post by personjerry on 2008-11-15
B-b-b-bump

---

### Post by personjerry on 2008-11-16
another bump

---

### Post by personjerry on 2008-11-17
yet another bump

---

### Post by personjerry on 2008-11-18
buuuuuuump

---

### Post by personjerry on 2008-11-19
Bump

---

### Post by personjerry on 2008-11-24
Bump

---

### Post by personjerry on 2008-11-26
_bump_

---

### Post by personjerry on 2008-11-27
BumP

---

### Post by personjerry on 2008-11-28
Bump

---

### Post by personjerry on 2008-11-29
someone please help...

---

### Post by personjerry on 2008-11-30
Yet another bump

---

### Post by personjerry on 2008-12-01
yet another yet another bump

---

### Post by personjerry on 2008-12-02
yet another bump

---

### Post by personjerry on 2008-12-03
bumpage

---

### Post by personjerry on 2008-12-04
bump

---

### Post by personjerry on 2008-12-05
another bump

---

### Post by personjerry on 2008-12-06
yet another bump

---

### Post by personjerry on 2008-12-07
yet another another bump

---

### Post by personjerry on 2008-12-08
yet another yet another bump

---

### Post by personjerry on 2008-12-09
bum p

---

### Post by personjerry on 2008-12-10
b ump

---

### Post by personjerry on 2008-12-11
bu mp

---

### Post by personjerry on 2008-12-12
bump

---

### Post by ton145 on 2008-12-16
Someone posted this:
[http://ubuntuforums.org/showthread.php?p=2429580#post2429580](http://ubuntuforums.org/showthread.php?p=2429580#post2429580)

> OK, it is obvious that taskjuggler is the problem and all of the above help was fruitless.

Open a console and type in the following:

Code:

sudo gedit /var/lib/dpkg/status


Search through the file for any reference to taskjuggler and CAREFULLY delete all of that entry.

Save the file

Code:

sudo apt-get update

Your problem should now be solved, as Synaptic can no longer see this errant package and as disk space is taken up, it will be over-written.

Regards,
Roger 

I have same problems, still no luck until today.

---

### Post by personjerry on 2008-12-21
I tried those instructions, to no avail.

---

### Post by personjerry on 2008-12-22
bump

---

### Post by personjerry on 2008-12-23
bump

---

### Post by personjerry on 2008-12-24
bump

---

### Post by personjerry on 2008-12-25
bump

---

### Post by mc4man on 2008-12-25
wow, almost 2 months
You may be better off saving what you want externally and doing a fresh install, what do you use for a file manager?

I would look in 2 area's, hplip. hplip-data, and in foomatic (foomatic-db, foomatic-filters.) What does synaptic show about these? (version numbers if any are installed.



Edit:
Might as well post your sources

```
cat /etc/apt/sources.list
```

---

### Post by personjerry on 2008-12-26
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

```

Those are the results of that command. But file manager...? apt-get? nautilus?

Edit:
And what am I looking for in those areas (hplip, etc.)?

---

### Post by mc4man on 2008-12-26
I want you to search out those 4 packages in synaptic package manager, see if any are installed, and post which are if any and the version numbers.

Did you somehow upgrade from gutsy to intrepid or did you go from hardy to intrepid?

Did you have wine installed when you upgraded?

> ....nautilus?

Your orig. post shows nautilus (file manager) not being installed, what happens when you go places -> home folder? 


Is there some overriding reason you don't want to do a fresh, good install?

---

### Post by personjerry on 2008-12-26
Answers to questions:



```
hplip                           installed, v 2.8.7-0ubuntu6
hplip-data                      installed, v 2.8.7-0ubuntu6
foomatic-db                     installed, v 20080918-0ubuntu4
foomatic-db-engine              installed, v 4.0.0~bzr219-0ubuntu1
foomatic-db-gutenprint      NOT installed.
foomatic-db-hpijs               installed, v 20080915-0ubuntu1
foomatic-filters                installed, v 4.0.0~bzr177-0ubuntu1
foomatic-gui                NOT installed.
```

All the installed packages listed above are the latest.



I went from Hardy to Intrepid.



Yes, I had wine.



Nautilus works as it did before. I'm assuming the config error only applies to the latest upgrade of nautilus.



I've got a lot of stuff installed, many compiled myself, and much in emulators like wine, so that's why I don't really want to reinstall... I do have a large flash storage device so I could potentially backup though, but this would take a long time, and this error doesn't seem to be too serious?

---

### Post by mc4man on 2008-12-26
I'm thinking then you actually don't have a problem at all. 
From post 1
> 
Setting up libgphoto2-2 (2.4.2-0ubuntu2

Check in synaptic and see what libgphoto2 is installed (2.4.2-0ubuntu3 is latest

If you want just run this to clean out old archives and otherwise you seem good to go

```
sudo apt-get autoclean
```

---

### Post by personjerry on 2008-12-27
No, the config error still occurs when i try to reconfig the packages.

---

### Post by mc4man on 2008-12-27
Did you ck. and see what version is installed?

---

### Post by personjerry on 2008-12-27
the latest, the one you said.

---

### Post by personjerry on 2008-12-29
bump

---

### Post by personjerry on 2008-12-30
bump

---

### Post by personjerry on 2008-12-31
bump

---

### Post by personjerry on 2009-01-01
bump

---

### Post by personjerry on 2009-01-02
bump

---

### Post by personjerry on 2009-01-03
bump

---

### Post by personjerry on 2009-01-22
yet another bump...

---

### Post by personjerry on 2009-02-08
Bump

---

### Post by personjerry on 2009-02-09
bump

---

### Post by personjerry on 2009-02-10
bump

---

### Post by personjerry on 2009-02-13
bump

---

### Post by Alterax on 2009-02-13
the sheer amount of bumps will make it nearly impossible for the casual observer that is having this issue to find the fix.

That being said, try this:

```
sudo dpkg --configure -a
```

What you're looking at is a ton of packages that didn't get properly configured because one package is holding up the queue.  Fix the one and the others should fall into place.

After that clears out, I'd recommend running a
```
 sudo apt-get dist-upgrade
``` 
just to get the packages current.

Keep me posted.

---

### Post by personjerry on 2009-02-14
i've tried the first command already... same error.



and thus, the second has the same results.

---

### Post by personjerry on 2009-02-15
bump

---

### Post by mc4man on 2009-02-15
If you run this I assume you still see 'error'
```
sudo apt-get --reinstall install libgphoto2-2
```

If you were to search libgphoto2-2 in synaptic, highlight it and in the packages tab, force the  version back to intrepid. (2.4.2-0ubuntu2
then click apply, and exit. Then try to update it. (or don't click exit and it will update right then

---

### Post by personjerry on 2009-02-17
alright I converted libgphoto2-2 and libgphoto2-port0, same errors. After seeing the same errors as previous, I converted them to the latest version again, just in case something else would go wrong, but if there's any other tests for a prev version, I can force them again i guess.

---

### Post by mc4man on 2009-02-17
Here's something similar, went nowhere
[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/301209](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/301209)

Somewhat described as an annoyance rather than having any deleterious effect which also seems similar.

---

### Post by SirThom on 2009-04-26
I'm having these same errors after upgrading to Jaunty.  Nothing seems to fix it so far.
I'm woundering if it has any connexion with Rhythmbox suddenly not working?  That was the problem that I was trying to solve when I found this.

And I already tried most of the suggestions here before finding this thread.

Under Intreped I tweaked a few things to try to get my webcam to work with Skype.  Any connexion there?

---

### Post by personjerry on 2009-04-27
Connections with Jaunty and Intrepid I doubt because I had this even in Hardy. And yes, the "fixes" didn't work for me too. This doesn't really seem like a malignant bug, however.

---

### Post by personjerry on 2009-04-29
bump

---

### Post by spsmysp on 2009-05-04
BUMP
I have the same problem!!

---

### Post by personjerry on 2009-05-08
yet another bump

---

### Post by personjerry on 2009-05-09
bump

---

### Post by vishwajeet.dusane on 2009-05-12
I have the same error

---

### Post by vishwajeet.dusane on 2009-05-13
I was able to fix this problem, please try the same and let me know does it work for you as well


   ```

              sudo apt-get remove libgphoto2-2
              sudo apt-get autoremove
              sudo apt-get install

  
```
   
and please remove those bumps, its annoying for other users as well

---

### Post by personjerry on 2009-05-29
I don't think it's possible to remove posts...

---

