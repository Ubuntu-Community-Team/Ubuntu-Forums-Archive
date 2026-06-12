---
title: "hardy heron - update issues"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by prox-e on 2009-02-22
[COLOR="DimGray"]So I avoided doing update after installing my hardy heron again and it seems to have had a real disliking to this. After hitting problems now  trying to install packages I have decide to just  do it[/COLOR]. *[COLOR="Silver"]reason for avoiding: I have a monthly bandwidth limit and I expected to have the newer 8.10 distro disc from a friend by now, but alas it has not arrived yet and I am craving to learn Ubuntu/nix. Since it hasn't arrived yet I thought I may as well just learn as much I can with what I have[/COLOR]* 

[COLOR="DimGray"]That is what happens when I try run my updates and upgrades. I have also tried to run the updates through the GUI, but as expected there was no difference apart from asking if I want a partial install.[/COLOR] *[COLOR="Silver"]Which I did try but that was unsuccessful.[/COLOR]*

> [COLOR="Gray"]root@prox-e-laptop:~# apt-get update
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-backports/main Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-backports/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-backports/universe Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-backports/multiverse Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-backports Release
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-backports/main Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hardy-backports/multiverse Sources
Reading package lists... Done
root@prox-e-laptop:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  apturl brasero gimp gimp-data gimp-gnomevfs gimp-python libgimp2.0 libpurple0 ntfs-3g pidgin pidgin-data
  transmission-common transmission-gtk
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
root@prox-e-laptop:~#[/COLOR]

[COLOR="DimGray"]This is what my source list looks like, at the very bottom you can see i tried to add VLC's URL source but it won't work because it can't get all the files it depends on.[/COLOR]

> [COLOR="Gray"]# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

#prox-e's added URL's
#deb [ftp://ftp.videolan.org/pub/videolan/ubuntu](ftp://ftp.videolan.org/pub/videolan/ubuntu) dapper universe[/COLOR]

[COLOR="DimGray"]One thing I have just noticed pasting all this information, is that it is an Ubuntu 8.04 _Hardy Heron_ - Release i386, and I am running this on my laptop that is a core2duo will be a cause to most of the issues I am having ? [/COLOR]*[COLOR="Silver"]I have made sure the distro I am getting will support my hardware a bit better by getting the 64 bit version of Ubuntu8.10.[/COLOR]*

---

### Post by Pumalite on 2009-02-22
Yuo can run a 32 bit on a Core 2 Duo

---

### Post by steveneddy on 2009-02-22
You can get an update DVD or just DL the files you need elsewhere, like a cyber cafe or library, and update from the DVD.

---

### Post by prox-e on 2009-02-22
> [COLOR="Gray"]You can get an update DVD or just DL the files you need elsewhere, like a cyber cafe or library, and update from the DVD.[/COLOR]

[COLOR="DimGray"]I don't see how putting my distro disc back in will give me updates if it asked me to update after I installed it, or should it fix the problem so I can download it? Or do you mean I must get the next distro being 8.10, that I already have on it's way  and am hoping to get in the next two weeks only ....so I want to get this working for now.

How / where else would I be able to get the updates for this distro? I wouldn't know where to start, could you point me in the direction I can find these please?[/COLOR]

---

### Post by Steve H on 2009-02-22
Have you tried having a look [here]("https://help.ubuntu.com/community/IntrepidUpgrades")?

;)

---

### Post by prox-e on 2009-02-22
ok I tried this and it gives me the same results.

I did notice that the Ubuntu section of the updates is grayed out and won't let me change any settings there. 

Is there a way to active them  ...why would these be grayed out ?

---

### Post by Steve H on 2009-02-22
Greyed out? Can you provide a screenshot?

---

### Post by prox-e on 2009-02-22
[http://i71.photobucket.com/albums/i147/Epsim/Screenshot.png?t=1235311723]("http://i71.photobucket.com/albums/i147/Epsim/Screenshot.png?t=1235311723")

Sorry my laptop internet is really slow for some strange reason

---

### Post by Steve H on 2009-02-22
Try backing up your source.list file and replacing it with the one [here]("http://ubuntuforums.org/showthread.php?t=739119") then try again.

---

### Post by prox-e on 2009-02-22
Thank so much Steve H, it seems to be working now ... you are legend o/. The download process is up and running and the update icon has returned.

If I run into any other complications i'll return to update this thread, but it all seems to be on track now.

Thanks again, I really appreciate the help.

---

### Post by Steve H on 2009-02-22
No problem, glad to help.

;)

---

