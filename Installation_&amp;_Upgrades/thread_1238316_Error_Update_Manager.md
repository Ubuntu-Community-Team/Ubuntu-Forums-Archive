---
title: "Error Update Manager"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by Thoork on 2009-08-12
Whenever I try to run the update manager, it downloads up to 61 out of the 64 packages and then it gives me this error:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Could not connect to packages.freecontrib.org:80 (34.52.53.34). - connect (113 No route to host)

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2)  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release)  

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources)  Unable to connect to packages.freecontrib.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.


I've tried changing the server with no luck. Here's my sources.list:

    ## Add comments (##) in front of any line to remove it from being checked.
    ## Use the following sources.list at your own risk.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

    ## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

    ## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

    ## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

    ## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free



Thanks!

Guillem.

---

### Post by Soul-Sing on 2009-08-12
Dapper and Dapper sources are at ELO.
The source.list contains Dapper and Jaunty sources, did you try a version upgrade?

---

### Post by zvacet on 2009-08-12
I looked at [Medibuntu]("http://www.medibuntu.org/") site and there is no  repos for Dapper.You can try other way to see if it work.

```
gksudo gedit /etc/apt/sources.list
```

and remove 
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

you can also remove 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main

because you don´t want to have mixed repos.After saving and closing file in terminal 

```
sudo wget http://www.medibuntu.org/sources.list.d/dapper.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

and after that 

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

If that does´t work (even if it does) you can think about upgrade to Hardy ( next LTS release).[Here]("https://help.ubuntu.com/community/HardyUpgrades") are instructions how to do it.

---

### Post by Thoork on 2009-08-14
[zvacet]("http://ubuntuforums.org/member.php?u=79320"), thanks, that worked perfectly.

---

### Post by alfu on 2009-09-10
I get a "Not all updates can be installed" error that won't go away.  I tried to minimize the checking frequency with "sudo gconf-editor" as suggested by the [Lifehacker website]("http://lifehacker.com/5295449/disable-ubuntus-annoying-update-manager-popup"), but Update Manager  seems to be a zombie Eveready Bunny that won't respond to its configuration file defaults.

Philosophically, the kind of 'push' technology represented by Update Manager is why I am trying to leave the M$ OS in the first place.  **Is there a way to just rip Update Manager out?**  Wouldn't we all be just as happy running Synaptic occasionally, and isn't the philosophy of Linux to avoid the gazillion different ways to do things in Windoze?  

I would prefer to update when I have a felt need to do so, not just because some bot wants to screw around with the interlocking dependencies already running in the computer.

---

### Post by Naturally-Simple on 2009-12-08
Hi. Reading through various posts when people say they are absolute beginners, they sure seem a lot more knowledgeable than I am about Ubuntu and how to receive the help and instructions the pros give. So let me be very very clear that I know next to NOTHING about ubuntu. I downloaded and am currently learning to use 9.10. But I'm learning. Slowly. I have no idea what Hardy or Debian or any of these other things mean. I think it's called Karmic what I have, but that's just the code name for 9.10, right?

Anyway, my apologies for the long intro. Here's my issue I need help with: My problem is the same as the initial poster. I get error messages that "failed to fetch" and "time out". I get what that means, but I don't get why it's doing this now, after working fine two weeks ago.

After some searching, I found what you were referring to as "sources.list" and mine doesn't look much like Thoork's. Here it is:

#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

If you're wondering about these unsupported things, I suppose that might be from me using Skype and VLC or whatever other non-open-source software (I think it's just those two, though, unless you count some sort of Java thing I installed--JDK or something?).

I really hope some of you can help me out. I'm not sure about following the instructions listed already because I don't know what my system is or how to find out these things to give you more system info in case you need it.

---

### Post by cybercookie72 on 2009-12-09
Greetings...

I was getting the same type of error...and when update manager was open it had a msg towards the top saying
 something about not being updated in 35 days.  After some google-fu I found two things that worked for me 
(the second being the one I am going to stick with)

----------------------------
This first thing is for 9.10 ONLY (found in this forum...sry I can't find the post again to give props)::

gksudo gedit /etc/apt/sources.list

REMEMBER TO BACK UP FIRST!!!
and delete the old entries
and replace with the following::


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main universe multiverse restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main universe multiverse restricted

# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main universe multiverse restricted

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main universe multiverse restricted


-----------------------------------

The second was a webpage that not only got rid of the errors but
 also put in some entries that updated things like pidgin and VLC

[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

once you fill out the form you will be given a sources.list 
and some commands to run to get the keys for the extras on the list....


both those worked for me...hope it helps you guys

good luck

---

### Post by Naturally-Simple on 2009-12-09
Okay, so I think I'll go for the second option, since you said the second is better, but why mention the first if you don't think it's as good as option 2? Just wondering, especially if you mentioned that you used both? :confused:

Anyway... I'm right now looking at the site for the link you posted, and I have no idea what I'm supposed to check off on all of these lists. The best I can figure is that I should just check off each of the first two repositories (what are those anyway?) in the "Ubuntu Updates" section, which are: "Security Sources Repository" and "Updates Sources Repository"

I'll see if this works. But maybe I should do as you did and try pasting in that text/code. Why should I backup, though? Can it potentially mess stuff up?

Personally, I'm not too concerned about messing things up on this computer. It's an old laptop I got for free and just trying to get used to using Ubuntu. I installed 9.10 a month ago and don't have any personal files on it, so if things go wonky to the point of complete system failure, I'll just wipe it all and re-install.

Thanks so much for your help! :p

---

### Post by Naturally-Simple on 2009-12-09
Ah, I should've checked out that site a little more thoroughly before posting that last post. So that site basically just generates the code or whatever I need to paste into my source.list file. But I don't understand it, so I'm just going to bite the bullet here and copy and paste what you wrote in your post and see what that does. I found a way to back it up, but whether I can fix things if it gets messed up, that may be another thing... I'll let this thread know if it works, or, in the case that things go terribly terribly wrong, I'll be asking for more help!

---

### Post by Naturally-Simple on 2009-12-09
OK. I changed the sources.list file by copying and pasting what you typed. Then I ran the sudo apt-get update thing, like the ubuntu site said I should. Then I tried Update Manager again, but still same problem.

So I checked off a bunch of the items listed on that second option you gave, the website which gives a new sources.list to copy and paste (I figured that if I already have the repository, it won't do any harm, and I think I was right).

Nothing has changed, though, with Update Manager. I still get this error message after waiting for the files to download (sorry for how long it is): 
> W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg/x11-common_7.4+3ubuntu10_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg/x11-common_7.4+3ubuntu10_all.deb)
  Could not connect to 10.0.1.4:8080 (10.0.1.4), connection timed out

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-16-generic_2.6.31-16.53_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-16-generic_2.6.31-16.53_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2009s-0ubuntu0.9.10_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2009s-0ubuntu0.9.10_all.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2009s-0ubuntu0.9.10_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2009s-0ubuntu0.9.10_all.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/u/ureadahead/sreadahead_0.90.3-2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/u/ureadahead/sreadahead_0.90.3-2_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/u/ureadahead/ureadahead_0.90.3-2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/u/ureadahead/ureadahead_0.90.3-2_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-50_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-50_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg50_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg50_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc50_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc50_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc50_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc50_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns50_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns50_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns53_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns53_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres50_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres50_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/d/devicekit-disks/devicekit-disks_007-2ubuntu4_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/d/devicekit-disks/devicekit-disks_007-2ubuntu4_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.0.42.34ubuntu0.9.10.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.0.42.34ubuntu0.9.10.1_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.28.1-0ubuntu2.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.28.1-0ubuntu2.1_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-screensaver/gnome-screensaver_2.28.0-0ubuntu3.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-screensaver/gnome-screensaver_2.28.0-0ubuntu3.1_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.28.1-0ubuntu3_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.28.1-0ubuntu3_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.31.16.29_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.31.16.29_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.31.16.29_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.31.16.29_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-16_2.6.31-16.53_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-16_2.6.31-16.53_all.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-16-generic_2.6.31-16.53_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-16-generic_2.6.31-16.53_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.31.16.29_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.31.16.29_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.31-16.53_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.31-16.53_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.28.1-0ubuntu3_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.28.1-0ubuntu3_all.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.28.1-0ubuntu3_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.28.1-0ubuntu3_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/n/ntp/ntpdate_4.2.4p6+dfsg-1ubuntu5.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/n/ntp/ntpdate_4.2.4p6+dfsg-1ubuntu5.1_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.4+3ubuntu10_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.4+3ubuntu10_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-input-all_7.4+3ubuntu10_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-input-all_7.4+3ubuntu10_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg_7.4+3ubuntu10_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg_7.4+3ubuntu10_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xorg_7.4+3ubuntu10_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xorg_7.4+3ubuntu10_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.97~beta4-1ubuntu4.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.97~beta4-1ubuntu4.1_i386.deb)
  Unable to connect to 10.0.1.4 8080:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.97~beta4-1ubuntu4.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.97~beta4-1ubuntu4.1_i386.deb)
  Unable to connect to 10.0.1.4 8080:


And these are apparently important security updates I need. Can't say I feel like I'm missing them. I also have to agree with an earlier post equating this update manager fiasco to Windows with regular reminders to update and install things I don't understand or want to be bothered with if my operating system appears to be doing just fine as is.

Anyway, any other help based on this time-out error after trying to change my sources.list file?

---

### Post by Naturally-Simple on 2009-12-17
Just to update for anyone who cares: I switched my sources.list file to what it was originally, then did some reading (can't remember where on the Ubuntu forum or documents) which led me to look at System - Preferences - Network Proxy, and changed it from manual to "Direct Internet Connection" instead. Seemed to do the trick! The update file downloads lag sometimes, but it never times out, and eventually gets the job done (may just be the wireless card).

So it's all good for that issue for me for now.

---

