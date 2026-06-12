---
title: "Can't update 9.10"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by bchamberlain on 2009-10-14
When running update manager for 9.10, it claims I need to do a partial upgrade.  I click continue and it eventually spits out an error after gathering ~170 of the required files for download.  It claims that some of the files could not be found.  It gives me a 404 file not found on each of the remaining 20 or so files.  Are they just not ready yet?  Or is something wrong?  Do I need to change/enable certain repositories?  Thanks for any help!

---

### Post by mac9416 on 2009-10-14
Could you please post the output where you get the 404s? While you're at it, please post your /etc/apt/sources.list. 
Thanks.

---

### Post by dagarshali on 2009-10-14
guys,
I just upgraded and when it restarted..i get a screen with a couple lines blinking and with login:

i can't type anything properly either..

so I restarted the laptop in recovery mode and i was able to login and see my files. I have forgotten to back up some important data..is there any way that i can connect a externl drive and copy the data to that..

and help to fix the problem or not restarting...

Regards,
Vishwa

---

### Post by Nebutron on 2009-10-14
> **dagarshali said:**
> guys,
 I have forgotten to back up some important data..is there any way that i can connect a externl drive and copy the data to that..

and help to fix the problem or not restarting...

Regards,
Vishwa

Yes,  If you have a live CD, you can boot from the CD and should be able to access your files on the HD and save to a USB flash drive or other media.

---

### Post by dagarshali on 2009-10-14
i found online that there is bug report concerning nvidia driver...and mine has nividia driver..

[https://bugs.launchpad.net/ubuntu/+bug/450318](https://bugs.launchpad.net/ubuntu/+bug/450318)

the report says to replace xrog.conf with xorg.conf.failsafe..

the problem is i dont see xrog.conf.failsafe file in /etc/X11/

all i see is xorg.conf.backup, xorg.conf.di...
xorg.conf.original

what do i do..

---

### Post by Nebutron on 2009-10-15
> **dagarshali said:**
> i found online that there is bug report concerning nvidia driver...and mine has nividia driver..

[https://bugs.launchpad.net/ubuntu/+bug/450318](https://bugs.launchpad.net/ubuntu/+bug/450318)

the report says to replace xrog.conf with xorg.conf.failsafe..

the problem is i dont see xrog.conf.failsafe file in /etc/X11/

all i see is xorg.conf.backup, xorg.conf.di...
xorg.conf.original

what do i do..

If you can still boot into recovery mode, it may be worth trying the "xfix" option.  You will have to scroll down in the red window to find it.  Not sure if it will work, but worth a try.

---

### Post by bchamberlain on 2009-10-16
> **mac9416 said:**
> Could you please post the output where you get the 404s? While you're at it, please post your /etc/apt/sources.list. 
Thanks.

Here are the 404's.

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.31-11.38_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.31-11.38_i386.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.19.91.20091001-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.19.91.20091001-0ubuntu2_i386.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/ntfs-3g/libntfs-3g54_2009.4.4-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ntfs-3g/libntfs-3g54_2009.4.4-1ubuntu2_i386.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/klibc/klibc-utils_1.5.15-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/klibc/klibc-utils_1.5.15-1ubuntu1_i386.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/klibc/libklibc_1.5.15-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/klibc/libklibc_1.5.15-1ubuntu1_i386.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/ntfs-3g/ntfs-3g_2009.4.4-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ntfs-3g/ntfs-3g_2009.4.4-1ubuntu2_i386.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_9.10.8_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_9.10.8_all.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgail-common_2.18.1-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgail-common_2.18.1-1_i386.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgail18_2.18.1-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgail18_2.18.1-1_i386.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-common_2.18.1-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-common_2.18.1-1_all.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk2-engines-pixbuf_2.18.1-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk2-engines-pixbuf_2.18.1-1_i386.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.18.1-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.18.1-1_i386.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/gnome-control-center_2.28.0-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/gnome-control-center_2.28.0-0ubuntu3_i386.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/capplets-data_2.28.0-0ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/capplets-data_2.28.0-0ubuntu3_all.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/libgnome-window-settings1_2.28.0-0ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/libgnome-window-settings1_2.28.0-0ubuntu3_i386.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/devicekit-disks/devicekit-disks_007-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/devicekit-disks/devicekit-disks_007-1_i386.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/f-spot/f-spot_0.6.1.3-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/f-spot/f-spot_0.6.1.3-1ubuntu1_i386.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-disk-utility/libgdu-gtk0_2.28.0-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-disk-utility/libgdu-gtk0_2.28.0-1_i386.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-disk-utility/libgdu0_2.28.0-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-disk-utility/libgdu0_2.28.0-1_i386.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-disk-utility/gnome-disk-utility_2.28.0-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-disk-utility/gnome-disk-utility_2.28.0-1_i386.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-bin_2.18.1-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-bin_2.18.1-1_all.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.20_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.20_all.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon-gtk_0.10+bzr242-0ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon-gtk_0.10+bzr242-0ubuntu3_all.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/aptdaemon_0.10+bzr242-0ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/aptdaemon_0.10+bzr242-0ubuntu3_all.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon_0.10+bzr242-0ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon_0.10+bzr242-0ubuntu3_all.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_0.4.4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_0.4.4_all.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.97~beta3-1ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.97~beta3-1ubuntu7_i386.deb) 404  Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.97~beta3-1ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.97~beta3-1ubuntu7_i386.deb) 404  Not Found [IP: 91.189.88.30 80]

Here's /etc/apt/sources.list

#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Beta i386 (20090929.2)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

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

Hope that helps!

---

### Post by EriQ_10 on 2009-10-29
I am having the same problem.:( I have tried changing the download server, But it makes no difference.

---

### Post by EveryNameUsedAlready on 2009-10-30
I had the same problem as did a guru friend. His suggestion worked for me:
 
Open a terminal. Update you apt-cache with this command:
apt-get update
 
Try to upgrade again.

---

### Post by grandtoubab on 2009-10-30
partial upgrade is a bad choice,
[http://ubuntuforums.org/showthread.php?t=1286309](http://ubuntuforums.org/showthread.php?t=1286309)

for the other problem are you sure you still have your Internet connection working?

---

### Post by IHaveNoLinuxSkills on 2009-11-14
Hey guys,
I am having same problem. plus i cant download from synaptic and software center all because of a similar problem.
Need help fast. im desperate. lol
Dunno if the below will help.

 W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/main/b/boost1.38/libboost-system1.38.0_1.38.0-6ubuntu6_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/main/b/boost1.38/libboost-system1.38.0_1.38.0-6ubuntu6_i386.deb)
  Could not connect to nz.archive.ubuntu.com:80 (202.7.6.10), connection timed out


W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/main/b/boost1.38/libboost-filesystem1.38.0_1.38.0-6ubuntu6_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/main/b/boost1.38/libboost-filesystem1.38.0_1.38.0-6ubuntu6_i386.deb)
  Unable to connect to nz.archive.ubuntu.com http:


W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/main/b/boost1.38/libboost-regex1.38.0_1.38.0-6ubuntu6_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/main/b/boost1.38/libboost-regex1.38.0_1.38.0-6ubuntu6_i386.deb)
  Unable to connect to nz.archive.ubuntu.com http:


W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/main/b/boost1.38/libboost-signals1.38.0_1.38.0-6ubuntu6_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/main/b/boost1.38/libboost-signals1.38.0_1.38.0-6ubuntu6_i386.deb)
  Unable to connect to nz.archive.ubuntu.com http:


W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/libt/libtorrent-rasterbar/libtorrent-rasterbar5_0.14.6-1_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/libt/libtorrent-rasterbar/libtorrent-rasterbar5_0.14.6-1_i386.deb)
  Unable to connect to nz.archive.ubuntu.com http:

---

### Post by soluckytouselinux on 2009-11-23
Hi everyone. I have a problem updating karmic. any help? I see updates in my update manager, but they are shaded out. I also installed satanic ubuntu before my upgrade. Thank-you

---

### Post by VvWolverinevV on 2010-02-04
> **EveryNameUsedAlready said:**
> I had the same problem as did a guru friend. His suggestion worked for me:
 
Open a terminal. Update you apt-cache with this command:
apt-get update
 
Try to upgrade again.

This worked for me too :)

---

### Post by eugenevdm on 2010-04-28
> **EveryNameUsedAlready said:**
> apt-get update

I confirmed the above command worked for me when I got loads of these:

> Err [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/main base-files 5.0.0ubuntu18
  404  Not Found [IP: 91.189.88.30 80]
Err [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/main libc6-i386 2.11.1-0ubuntu6
  404  Not Found [IP: 91.189.88.30 80]
Err [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/main libc-dev-bin 2.11.1-0ubuntu6
  404  Not Found [IP: 91.189.88.30 80]
Err [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/main libc6-dev 2.11.1-0ubuntu6
  404  Not Found [IP: 91.189.88.30 80]
Err [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) lucid/main libc-bin 2.11.1-0ubuntu6
  404  Not Found [IP: 91.189.88.30 80]

---

