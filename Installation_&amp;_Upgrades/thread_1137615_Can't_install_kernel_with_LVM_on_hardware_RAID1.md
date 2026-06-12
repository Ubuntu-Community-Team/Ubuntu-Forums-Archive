---
title: "Can't install kernel with LVM on hardware RAID1"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by bryanburke on 2009-04-25
I am trying to install Ubuntu Server 9.04 on my Silicon Mechanics Rackform iServ R200 ([specs]("http://www.siliconmechanics.com/i2671/dual-xeon-server-64-bit.php")). This server has a Super Micro X6DVA-EG motherboard with an onboard RAID0+1 controller ([specs]("http://www.supermicro.com/products/motherboard/Xeon800/E7320/X6DVA-EG.cfm")). I am using a USB drive created with the Ubuntu startup disk creator, and I am experiencing two confusing issues.

**First Issue**
In my BIOS RAID configuration utility, if I name the RAID1 mirror (example "main"), then during Ubuntu's install process, after I choose to activate the serial ATA RAID devices, I get this error:

```

Could not stat device /dev/mapper/asr_main - No such file or directory.

ERROR!!!

```

However, there is a device node in /dev/mapper named "asr_main". Furthermore, if I leave the RAID1 mirror unnamed, the Ubuntu installer successfully stats the device "/dev/mapper/asr_".

Here is the end of my syslog for the error described above:

```

Apr 25 23:03:27 anna-install: Installing dmraid-udeb
Apr 25 23:03:28 anna[9432]: DEBUG: retrieving dmraid-udeb 1.0.0.rc15-6ubuntu2
Apr 25 23:03:28 anna[9432]: DEBUG: retrieving libdmraid1.0.0.rc15-udeb 1.0.0.rc15-6ubuntu2
Apr 25 23:03:28 disk-detect: Serial ATA RAID disk(s) detected.
Apr 25 23:03:32 disk-detect: Enabling dmraid support.
Apr 25 23:03:33 disk-detect: RAID set "asr_main           " was activated
Apr 25 23:03:33 dmraid-activate: ERROR: Cannot retrieve RAID set information for asr_main           
Apr 25 23:03:34 check-missing-firmware: no missing firmware in /tmp/missing-firmware
Apr 25 23:03:34 main-menu[785]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Apr 25 23:03:34 main-menu[785]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored)
Apr 25 23:03:34 main-menu[785]: INFO: Falling back to the package description for console-setup-udeb
Apr 25 23:03:34 main-menu[785]: INFO: Falling back to the package description for console-setup-udeb
Apr 25 23:03:34 main-menu[785]: INFO: Menu item 'partman-base' selected
Apr 25 23:03:34 kernel: [  154.125571] NTFS driver 2.1.29 [Flags: R/O MODULE].
Apr 25 23:03:34 kernel: [  154.171366] JFS: nTxBlock = 8192, nTxLock = 65536
Apr 25 23:03:34 kernel: [  154.215219] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Apr 25 23:03:34 kernel: [  154.216326] SGI XFS Quota Management subsystem
Apr 25 23:03:34 md-devices: mdadm: No arrays found in config file
Apr 25 23:03:34 partman:   No matching physical volumes found
Apr 25 23:03:34 partman:   Reading all physical volumes.  This may take a while...
Apr 25 23:03:46 kernel: [  166.696282] end_request: I/O error, dev fd0, sector 0
Apr 25 23:03:59 kernel: [  178.848280] end_request: I/O error, dev fd0, sector 0

```

**Second Issue**
This is my main issue. After getting past the first issue by using an unnamed RAID1 mirror, I partition my array using guided LVM partitioning. When installing in normal mode, the base system is installed without any errors, even when I choose LVM. However, in expert mode, no matter which LVM layout or kernel image I choose (example "linux-server"), I get this error:

```

Unable to install the selected kernel
An error was returned while trying to install the kernel into the target system.

Kernel package: 'linux-server'.

Check /var/log/syslog or see virtual console 4 for the details.

```

However, if I partition my array using guided partitioning without LVM, the kernel installs just fine!

Again, here's the end of the syslog:

```

Apr 25 22:27:09 in-target: Setting up wireless-crda (1.7) ...
Apr 25 22:27:11 in-target: Setting up linux-image-2.6.28-11-generic (2.6.28-11.42) ...
Apr 25 22:27:11 in-target: Running depmod.
Apr 25 22:27:11 in-target: update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
Apr 25 22:27:11 in-target: mkinitramfs: missing dm- root /dev/mapper/ubuntu-root /sys entry
Apr 25 22:27:11 in-target: mkinitramfs: workaround is MODULES=most
Apr 25 22:27:11 in-target: mkinitramfs: Error please report the bug
Apr 25 22:27:11 in-target: update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
Apr 25 22:27:11 in-target: Failed to create initrd image.
Apr 25 22:27:11 in-target: dpkg: error processing linux-image-2.6.28-11-generic (--configure):
Apr 25 22:27:11 in-target:  subprocess post-installation script returned error exit status 2
Apr 25 22:27:11 in-target: Setting up binutils-static (2.19.1-0ubuntu3) ...
Apr 25 22:27:11 in-target: Setting up linux-restricted-modules-common (2.6.28-11.15) ...
Apr 25 22:27:11 in-target: update-rc.d: warning: /etc/init.d/linux-restricted-modules-common missing LSB information
Apr 25 22:27:11 in-target: update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
Apr 25 22:27:11 in-target: 
Apr 25 22:27:11 in-target: dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-11-generic:
Apr 25 22:27:11 in-target:  linux-restricted-modules-2.6.28-11-generic depends on linux-image-2.6.28-11-generic; however:
Apr 25 22:27:11 in-target:   Package linux-image-2.6.28-11-generic is not configured yet.
Apr 25 22:27:11 in-target: dpkg: error processing linux-restricted-modules-2.6.28-11-generic (--configure):
Apr 25 22:27:11 in-target:  dependency problems - leaving unconfigured
Apr 25 22:27:11 in-target: Setting up linux-firmware (1.11) ...
Apr 25 22:27:11 in-target: No apport report written because the error message indicates its a followup error from a previous failure.
Apr 25 22:27:11 in-target: dpkg: dependency problems prevent configuration of linux-image-generic:
Apr 25 22:27:11 in-target:  linux-image-generic depends on linux-image-2.6.28-11-generic; however:
Apr 25 22:27:11 in-target:   Package linux-image-2.6.28-11-generic is not configured yet.
Apr 25 22:27:11 in-target: dpkg: error processing linux-image-generic (--configure):
Apr 25 22:27:11 in-target:  dependency problems - leaving unconfigured
Apr 25 22:27:11 in-target: dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
Apr 25 22:27:11 in-target:  linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-11-generic; however:
Apr 25 22:27:11 in-target:   Package linux-restricted-modules-2.6.28-11-generic is not configured yet.
Apr 25 22:27:11 in-target: dpkg: error processing linux-restricted-modules-generic (--configure):
Apr 25 22:27:11 in-target:  dependency problems - leaving unconfigured
Apr 25 22:27:11 in-target: dpkg: dependency problems prevent configuration of linux-generic:
Apr 25 22:27:11 in-target:  linux-generic depends on linux-image-generic (= 2.6.28.11.15); however:
Apr 25 22:27:11 in-target:   Package linux-image-generic is not configured yet.
Apr 25 22:27:11 in-target:  linux-generic depends on linux-restricted-modules-generic (= 2.6.28.11.15); however:
Apr 25 22:27:11 in-target:   Package linux-restricted-modules-generic is not configured yeNo apport report written because the error message indicates its a followup error from a previous failure.
Apr 25 22:27:11 in-target: No apport report written because MaxReports is reached already
Apr 25 22:27:11 in-target: No apport report written because MaxReports is reached already
Apr 25 22:27:11 in-target: t.
Apr 25 22:27:11 in-target: dpkg: error processing linux-generic (--configure):
Apr 25 22:27:11 in-target:  dependency problems - leaving unconfigured
Apr 25 22:27:11 in-target: Errors were encountered while processing:
Apr 25 22:27:11 in-target:  linux-image-2.6.28-11-generic
Apr 25 22:27:11 in-target:  linux-restricted-modules-2.6.28-11-generic
Apr 25 22:27:11 in-target:  linux-image-generic
Apr 25 22:27:11 in-target:  linux-restricted-modules-generic
Apr 25 22:27:11 in-target:  linux-generic
Apr 25 22:27:11 in-target: E: Sub-process /usr/bin/dpkg returned an error code (1)
Apr 25 22:27:11 base-installer: error: exiting on error base-installer/kernel/failed-install

```

From what I can tell, mkinitramfs cannot find the root LVM logical volume, causing a domino effect on the rest of the kernel packages. What boggles my mind the most about this error is that mkinitramfs seems to have no trouble at all finding the root logical volume when using the installer's normal mode (instead of expert mode). Could I be choosing an option in expert mode that would affect this?

Any help with these issues (especially the second one) would be very much appreciated. Thanks in advance!

---

### Post by bryanburke on 2009-04-26
I have submitted bug reports for both of these problems.  If anyone else is experiencing these issues, please confirm that they affect you on Launchpad.

First Issue = [https://bugs.launchpad.net/bugs/367505](https://bugs.launchpad.net/bugs/367505)

Second Issue = [https://bugs.launchpad.net/bugs/367486](https://bugs.launchpad.net/bugs/367486)

---

