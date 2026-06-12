---
title: "Hanging / Pausing / Slow system updates"
date: 2008-10-21
forum: General Help
---

### Post by grilledsalad on 2008-10-21
I recently installed Ubuntu 8.04 onto two desktop systems and both are having an issue that I've never come across. They are fresh installs to replace the Kubuntu 6.10 release that was on both of them for a year or so. Those boxes both ran very nicely. The boxes both run okay now, but there is this one problem with system updates. Whether I run them via the command line (apt-get upgrade, apt-get install [whatever package]), or if I use Synaptic, the problem persists. They have short bursts of normal progress, then have extended periods of pausing. They just hang there and don't appear to be doing anything. To quantify this, there is maybe 10-15 seconds of progress during which the downloads happen, and then 5-10 minutes of stalling.

This never happened in Kubuntu 6.10, so I'm wondering if anything is different in the older releases, or in Kubuntu VS regular gnome ubuntu. I haven't changed any hardware on either machine, and my home network is the same.

Other network operations work perfectly fine. Transfers on my LAN are very quick and don't have any pauses, and transfers from the internet are quick. Bittorrent downloads are great, web surfing is fine, FTP transfers are normal, etc. This definitely seems to be isolated to ubuntu updates. I hate to bring it up, but the Windows machine on the network is also looking okay.

Can anyone make some recommendations? Any particular log files to watch? Is there any other info I can provide?

Thank you!



System information (for one of the hosts):
athlon x2 64-bit processor, 2 GB ram, 160 GB ide HD, pci-x nvidia card with restricted driver enabled, basic motherboard, onboard lan/sound/etc

kevin@linuxdesktop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

#inserted the following line for encrypted DVD playback
#deb [http://medibuntu.sos-sts.com/repo/feisty](http://medibuntu.sos-sts.com/repo/feisty) free non-free

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse

kevin@linuxdesktop:~$

---

### Post by eternalnewbee on 2008-10-21
Maybe it's just a problem with the server you are downloading from. Try another server in Main Menu > System > Software Sources and see how it goes.
Here's a screenshot:
[http://ubuntuforums.org/attachment.php?attachmentid=89202&stc=1&d=1224643727](http://ubuntuforums.org/attachment.php?attachmentid=89202&stc=1&d=1224643727)

---

