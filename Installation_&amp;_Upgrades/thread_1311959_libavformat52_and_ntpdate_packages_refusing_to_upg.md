---
title: "libavformat52 and ntpdate packages refusing to upgrade"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by mcpancakes on 2009-11-02
Hi all,

During the Upgrade process from Jaunty to Karmic, the two packages libavformat52 and ntpdate packages try and retry a couple times to upgrade, but always fail to do so. At the end of the install process, an incomplete install is reported and I'm told that something along the lines of 'dpkg -s' will be run to revert changes, and that my system could be unusable. When I attempt to manually install these packages via apt-get:

```
mcpancakes@desktop:~$ sudo apt-get install ntpdate libavformat52
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gcj-4.3-base libstdc++6-4.3-dev libmono-getoptions2.0-cil guile-1.8 python3.0-minimal lilypond-doc libgcj9-0 libgcj-bc x11proto-kb-dev
  x11proto-xinerama-dev libbeecrypt6 g++-4.3 liblog4j1.2-java-gcj libqt4-sql-mysql x11proto-render-dev libqt4-qt3support screen-profiles libass1
  libxdmcp-dev libsysfs-dev libdirectfb-extra python3.0 libdvbpsi4 gcj-4.4-jre-lib libgcj10 xtrans-dev libx264-65 libopal3.6.1 x11proto-core-dev
  libparted1.8-10 gcj-4.4-base libgcj-common x11proto-randr-dev libpoppler4 libgcj9-jar libffado0 x11proto-input-dev libqt4-sql libpthread-stubs0-dev
  libmagickcore1 libpthread-stubs0 update-motd imagemagick-doc libmono-data2.0-cil libpt2.6.1 libvolume-id1 libmagickwand1 libindicate1 libgmyth0
  libcolamd-3.2.0 ladcca2 libvlccore0 qt4-qtconfig libntfs-3g49
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  libavformat52 ntpdate
2 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
7 not fully installed or removed.
Need to get 0B/774kB of archives.
After this operation, 4,096B disk space will be freed.
(Reading database ... 280945 files and directories currently installed.)
Preparing to replace ntpdate 1:4.2.4p4+dfsg-7ubuntu5.1 (using .../ntpdate_1%3a4.2.4p6+dfsg-1ubuntu5_i386.deb) ...
Unpacking replacement ntpdate ...
dpkg (subprocess): unable to execute old post-removal script: Exec format error
dpkg: warning: old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
dpkg: error processing /var/cache/apt/archives/ntpdate_1%3a4.2.4p6+dfsg-1ubuntu5_i386.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/md5sums': Is a directory
Preparing to replace libavformat52 3:0.svn20090303-1ubuntu6 (using .../libavformat52_4%3a0.5+svn20090706-2ubuntu2_i386.deb) ...
Unpacking replacement libavformat52 ...
dpkg (subprocess): unable to execute old post-removal script: Permission denied
dpkg: warning: old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
dpkg: error processing /var/cache/apt/archives/libavformat52_4%3a0.5+svn20090706-2ubuntu2_i386.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/postrm': Is a directory
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/ntpdate_1%3a4.2.4p6+dfsg-1ubuntu5_i386.deb
 /var/cache/apt/archives/libavformat52_4%3a0.5+svn20090706-2ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mcpancakes@desktop:~$ 

```

Also, at the end of the upgrade process, not only those two packages are said to have had a problem upgrading, but these as well:

```

ubuntu-minimal
gstreamer0.10-ffmpeg
vlc-nox
vlc
vlc-plugin-pulse
```

When booting, I see for a split-second 'fsck.ntfs not found'. Also, sound doesn't work, and the my video performance has decreased significantly (visual lag when dragging/minimizing windows, etc.). I don't know which of these things are connected and which are not, so I'm providing you with everything I can.

edit: also, flash in Firefox seems to have broken. When I go to install Gnash from Firefox:

```
Software index is broken:

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```

---

### Post by mcpancakes on 2009-11-04
More information:

/etc/apt/sources.list - as you can see, all the repos are the correct Karmic ones:

```
# added by the release upgrader
deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)]/ karmic main restricted
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
# deb http://apt.wicd.net jaunty extras # disabled on upgrade to jaunty

```

dpkg --configure -a:

```
root@desktop:~# dpkg --configure -a
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on ntpdate; however:
  Package ntpdate is not installed.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-minimal
root@desktop:~# sudo apt-get --reinstall install ubuntu-minimal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gcj-4.3-base libstdc++6-4.3-dev libmono-getoptions2.0-cil libswscale0 guile-1.8 python3.0-minimal lilypond-doc libgcj9-0 libgcj-bc x11proto-kb-dev
  x11proto-xinerama-dev libbeecrypt6 g++-4.3 liblog4j1.2-java-gcj libqt4-sql-mysql x11proto-render-dev libqt4-qt3support libpostproc51 screen-profiles
  libass1 libxdmcp-dev libsysfs-dev libdirectfb-extra python3.0 libdvbpsi4 libdvbpsi5 gcj-4.4-jre-lib libgcj10 xtrans-dev libx264-65 libx264-67
  libopal3.6.1 libvlc2 x11proto-core-dev libparted1.8-10 gcj-4.4-base libgcj-common x11proto-randr-dev libpoppler4 libgcj9-jar libffado0 x11proto-input-dev
  libqt4-sql libpthread-stubs0-dev libmagickcore1 libiso9660-5 libpthread-stubs0 update-motd imagemagick-doc libmono-data2.0-cil libpt2.6.1 libvolume-id1
  libmagickwand1 libindicate1 libgmyth0 vlc-data libtar libcolamd-3.2.0 ladcca2 libvlccore0 libvlccore2 libvcdinfo0 libebml0 libmatroska0 qt4-qtconfig
  libsdl-image1.2 libntfs-3g49
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libavformat52 ntpdate
The following packages will be upgraded:
  libavformat52 ntpdate
2 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 19 not upgraded.
3 not fully installed or removed.
Need to get 0B/774kB of archives.
After this operation, 4,096B disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 280590 files and directories currently installed.)
Preparing to replace ntpdate 1:4.2.4p4+dfsg-7ubuntu5.1 (using .../ntpdate_1%3a4.2.4p6+dfsg-1ubuntu5_i386.deb) ...
Unpacking replacement ntpdate ...
dpkg (subprocess): unable to execute old post-removal script: Exec format error
dpkg: warning: old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
dpkg: error processing /var/cache/apt/archives/ntpdate_1%3a4.2.4p6+dfsg-1ubuntu5_i386.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/md5sums': Is a directory
Preparing to replace libavformat52 3:0.svn20090303-1ubuntu6 (using .../libavformat52_4%3a0.5+svn20090706-2ubuntu2_i386.deb) ...
Unpacking replacement libavformat52 ...
dpkg (subprocess): unable to execute old post-removal script: Permission denied
dpkg: warning: old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
dpkg: error processing /var/cache/apt/archives/libavformat52_4%3a0.5+svn20090706-2ubuntu2_i386.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/postrm': Is a directory
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/ntpdate_1%3a4.2.4p6+dfsg-1ubuntu5_i386.deb
 /var/cache/apt/archives/libavformat52_4%3a0.5+svn20090706-2ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@desktop:~# 
```

---

