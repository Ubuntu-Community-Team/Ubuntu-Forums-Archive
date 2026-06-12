---
title: "PXE LiveCD Boot w/o NFS"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by Cardnyl on 2009-05-15
I currently have a working PXE server (Windows machine running TFTPD32) that serves up netboot images of ubuntu desktop. I am trying to see if it would be possible to take this a step further and have a few of my workstations run the LiveCD via PXE. We currently do not have the option of switching our DHCP or DNS servers to Linux nor do I have the option at this time to install an NFS server onto the windows machine running the PXE server. Damn near every guide I have read says to copy the files on the cd to a drive, mount the files as a loop device, serve the files up via NFS, and then add the following to the PXE default file. (Bear in mind the following is an example from a guide I read, I am actually doing this using Jaunty)

```
**pxelinux.cfg/default**

LABEL live-hardy-i386
        kernel hardy-i386/vmlinuz
        append boot=casper netboot=nfs nfsroot=192.168.2.200:/srv/tftpboot/hardy-i386/mnt initrd=hardy-i386/initrd.gz --

```The problem I am having right now is that during the syslinux/casper (not sure which) init scripts it gets to a point where I receive the following screen output repeatedly:
```

EXT3-fs: mounted filesystem with ordered data mode.
kjournald startng. Commit interval 5 seconds.
```After which I am dropped to a BusyBox shell. Upon cat'ing the casper.log file I see the following messages:

```
/init: line1: cannot open /dev/scd0: No medium found
```I had a feeling I would be seeing something like this. It's looking for files off of the cd and not finding them because the files are instead on the network. 

Are there any configuration changes I can make to TFTPD32 or to the default file listed above (maybe some other boot=<OPTION> that I don't know about) that will allow the boot process to continue by pulling all of the files from a folder underneath the PXE root folder on the hard drive without the need for mounting the files copied from the cd as a loop device and then accessing them via NFS?

---

### Post by Cardnyl on 2009-05-19
I guess no one has tried this then. Any ideas how I can perform the mount and nfs portions of this set of instructions if the network itself is entirely windows based?

[https://wiki.ubuntu.com/LiveCDNetboot](https://wiki.ubuntu.com/LiveCDNetboot)

---

