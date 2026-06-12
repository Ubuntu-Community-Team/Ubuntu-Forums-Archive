---
title: "sudo apt-get update fail"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by cptnfool on 2009-05-19
Hi
so i seem to be having a problem with my updates, both graphical, and using sudo apt-get update.  the problem that i found in the archive here [http://ubuntuforums.org/showthread.php?t=551530](http://ubuntuforums.org/showthread.php?t=551530) is the exact same as what i seem to be getting now, except on the beginning of page two where he says he cannot run aptitude in a terminal.  it will run for me, i see the program running... however, i have no clue what i should do to fix my problem from within aptitude... could someone point me in the right direction? ill poke around until i see a reply.  thanks in advance!

---

### Post by taurus on 2009-05-19
Can you post the whole outputs of these two commands, running one at a time from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by cptnfool on 2009-05-19
acutally, my errors are a little bit different from what he had.  i believe its just the jaunty title that is different, but here they are

cptnfool@moblieamish:~$ sudo apt-get update
~*****~ /*lots of fetching stuff*/
Fetched 815B in 1s (618B/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mirror.csclub.uwaterloo.ca_ubuntu_dists_jaunty_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
cptnfool@mobileamish:~$

cptnfool@mobileamish:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mirror.csclub.uwaterloo.ca_ubuntu_dists_jaunty_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
cptnfool@mobileamish:~$

---

### Post by taurus on 2009-05-19
1.  Go into System -> Administration -> Software Sources and switch to another server.  Then close it and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

or

2.  Post your /etc/apt/sources.list and the output of this command.

```
lsb_release -a
cat /etc/apt/sources.list
```

---

### Post by cptnfool on 2009-05-19
You wanted sources.lst c/p here? if not ill edit it out again for clenliness.... 

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) jaunty main restricted
deb-src [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) jaunty-updates main restricted
deb-src [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) jaunty universe
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) jaunty multiverse
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) jaunty-updates multiverse

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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) jaunty-security main restricted
deb-src [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) jaunty-security restricted main multiverse universe #Added by software-properties
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) jaunty-security universe
deb [http://mirror.csclub.uwaterloo.ca/ubuntu/](http://mirror.csclub.uwaterloo.ca/ubuntu/) jaunty-security multiverse
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free # disabled on upgrade to jaunty

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free # disabled on upgrade to jaunty
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) jaunty main # disabled on upgrade to jaunty
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) jaunty main # disabled on upgrade to jaunty
# deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) stable contrib
# deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) jaunty main # disabled on upgrade to jaunty
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) jaunty main # disabled on upgrade to jaunty
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) jaunty main # disabled on upgrade to jaunty


deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main # disabled on upgrade to jaunty
# deb [http://www.fbriere.net/debian/dists/stable](http://www.fbriere.net/debian/dists/stable) misc/


note that i purposely re-enabled some of those sources... some of them a bad idea perhaps?
and the output of lsb_release -a
~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty

ps, me == forum noob, how do i put code braces around my stuffs?

---

### Post by taurus on 2009-05-19
You, somehow, have an entry for hardy, second to last, deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main # disabled on upgrade to jaunty.  Therefore, you either need to replace the word hardy to jauntry in there or place a # in front of the line to comment it out.

```

#deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main # disabled on upgrade to jaunty
```
Now, do those things in Step 1 in my previous message, switching to another server.

p.s.  To edit /etc/apt/sources.list, run

```
gksudo gedit /etc/apt/sourcces.list
```

---

### Post by cptnfool on 2009-05-19
when i changed sources, it went through the pagkace download process, checking for updates for a few seconds, then it came up with this error again...
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

when i closed the error, it exited the sources program.

changed hardy to jaunty. 
(why gksudo gedit?  sudo gedit seems to work fine, but im just curious :))




cptnfool@mobileamish:~$ sudo apt-get clean 
       < ---- gave no output, just a new line waiting for more input.
cptnfool@mobileamish:~$ sudo apt-get update

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/jaunty/main/binary-amd64/Packages](http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/jaunty/main/binary-amd64/Packages)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

cptnfool@mobileamish:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
corey@mobileamish:~$

---

### Post by cptnfool on 2009-05-19
i gotta run for a few hours, thanks for the help insofar.
ill try what you post when i get back later tonight.

---

### Post by taurus on 2009-05-19
You need to add PPA's keys to your machine before you can use the ppa.launchpad.net repos.

[https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA](https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA)

Sudo is for a terminal while gksu/gksudo is more for a GUI apps.

---

### Post by cptnfool on 2009-05-19
yes, i know that those ppa are not properly working, they have not been for some time.  still, i tried to reactivate them, but i was not succesful, as this required me to use the source manager, which also gives me an error.... maybe time to re-install?

---

### Post by taurus on 2009-05-19
All you have to do is to edit your /etc/apt/sources.list and put a # in front of all the repos that have ppa.launchpad.net in there.  That's how you comment out your repos.  Then, save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by cptnfool on 2009-05-20
after i have commented out all ppa.launchpad.net entries in my sources.lst, i still get errors when i run apt-get update

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_jaunty_non-free_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

---

