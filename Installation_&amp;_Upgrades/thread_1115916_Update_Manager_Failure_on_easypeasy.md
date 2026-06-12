---
title: "Update Manager Failure on easypeasy"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by gforshay on 2009-04-04
I am having problems performing recommended updates to easypeasy installed on a EeePC.  Is there a way to force the upgrade of good pieces, uninstall the bad pieces and/or back the system to a last known good configuration?

A Brief history:
I have had EasyPeasy running fine, until I decided to try to add MythBuntu client to the machine.  The install did not complete, as I could not connect to the MythTV back-end.  Since my version of MythTV was on 8.04 of Ubuntu, but my EasyPeasy was on 8.1, I thought it might be an issue of compatability...so..I upgraded my backend machine to MythBuntu 8.1, and MythTV 8.1.

While that was happening, I attempted up perform the recommended Ubuntu upgrades to my EasyPeasy.  During the update, it fails with the report, to follow shortly.  My guess, is that the machine is trying to upgrade against some files against the , and I believe that the result is the upgrades cannot resolve the location of the files to be updated.

Report from Update Attempt:
****Begin Report ****
E: /var/cache/apt/archives/sudo_1.6.9p17-1ubuntu2_i386.deb: unable to create updated files list file for package sudo

E: /var/cache/apt/archives/libnss3-1d_3.12.0.3-0ubuntu5_i386.deb: unable to install new info file `/var/lib/dpkg/tmp.ci/postrm' as `/var/lib/dpkg/info/libnss3-1d.postrm'

E: /var/cache/apt/archives/gstreamer0.10-plugins-good_0.10.10.4-1ubuntu1_i386.deb: failed to install updated files list file for package gstreamer0.10-plugins-good

E: /var/cache/apt/archives/libgvfscommon0_1.0.2-0ubuntu1_i386.deb: unable to create updated files list file for package libgvfscommon0

E: /var/cache/apt/archives/gvfs_1.0.2-0ubuntu1_i386.deb: unable to install new info file `/var/lib/dpkg/tmp.ci/md5sums' as `/var/lib/dpkg/info/gvfs.md5sums'

E: /var/cache/apt/archives/libartsc0_1.5.10-0ubuntu1_i386.deb: unable to install new info file `/var/lib/dpkg/tmp.ci/shlibs' as `/var/lib/dpkg/info/libartsc0.shlibs'

E: /var/cache/apt/archives/linux-libc-dev_2.6.27-11.27_i386.deb: unable to install new info file `/var/lib/dpkg/tmp.ci/md5sums' as `/var/lib/dpkg/info/linux-libc-dev.md5sums'

E: /var/cache/apt/archives/libpostproc51_3%3a0.svn20080206-12ubuntu3_i386.deb: unable to create updated files list file for package libpostproc51

E: /var/cache/apt/archives/libqt4-assistant_4.4.3-0ubuntu1.2_i386.deb: unable to install new info file `/var/lib/dpkg/tmp.ci/postinst' as `/var/lib/dpkg/info/libqt4-assistant.postinst'

E: /var/cache/apt/archives/libsndfile1_1.0.17-4_i386.deb: unable to install new info file `/var/lib/dpkg/tmp.ci/md5sums' as `/var/lib/dpkg/info/libsndfile1.md5sums'

E: /var/cache/apt/archives/libthunar-vfs-1-2_0.9.0-10ubuntu1_i386.deb: unable to install new info file `/var/lib/dpkg/tmp.ci/md5sums' as `/var/lib/dpkg/info/libthunar-vfs-1-2.md5sums'

E: /var/cache/apt/archives/xserver-xorg-core_2%3a1.5.2-2ubuntu3_i386.deb: failed to install updated files list file for package xserver-xorg-core
**** End report****

EasyPeasy Configuration:
UBUNTU Release 8.1 intrepid
Kernal Linux 2.6.27-8-eeepc
GNOME 2.24.1

Hardware
Memory 2GB Ram
Processor:0 Intel(R) Atom (TM) CPU N270 @ 1.6Ghz
Processor:1 Intel(R) Atom (TM) CPU N270 @ 1.6Ghz

System Status:
Available Disk space 24.1 GiB

File Systems
/dev/sda1

(btw...don't know why it shows 2 processors...I thought eeePC had only a single processor)...

---

### Post by gforshay on 2009-04-05
I decided to re-do the install and configuration of my easypeasy netbook...so...probably the easiest, thought time consuming way to go.  It would be nice to know where to find how to recover, or to back-out updates?

...anyone?

---

