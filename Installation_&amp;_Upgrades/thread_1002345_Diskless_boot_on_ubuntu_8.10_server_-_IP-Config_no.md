---
title: "Diskless boot on ubuntu 8.10 server - IP-Config: no response after 60 secs -giving up"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by sabareesh on 2008-12-04
I am trying to enable diskless booting on Ubuntu 8.10 server using instructions in the following link.
[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

After performing all of the steps in the link above I found that the NFS and DHCP were working.

 The client starts to boot from the network and things seem to work until I get the following message

"IP-Config: no response after 60 secs - giving up
/init: .: line 1: can't open /tmp/net-eth0.conf
[ 152.740523] Kernel panic - not syncing: Attempted to kill init!"

While it was booting, I could see that IP-Config had succeeded once before for eth0 and the MAC address and IP were printed on screen.

I am pasting almost all the important files below.


Some config files on the server:
File: /tftpboot/pxelinux.cfg/default
LABEL linux
KERNEL vmlinuz-2.6.27-7-server
APPEND root=/dev/nfs initrd=initrd.img-2.6.27-7-server nfsroot=192.168.1.2:/nfsroot ip=dhcp rw


These are some of my config files for the client stored on the server at /nfsroot.


# /nfsroot/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/nfs        /               nfs     defaults        1       1
none            /tmp            tmpfs   defaults        0       0
none            /var/run        tmpfs   defaults        0       0
none            /var/lock       tmpfs   defaults        0       0
none            /var/tmp        tmpfs   defaults        0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

File: /nfsroot/etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp
iface eth0 inet manual

Just some more information;I have a working installation on the hard disk of the client and the client boots up properly from the disk.

The /etc/fstab on the client is as follows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d6c8917c-b6df-4fa7-ac37-4662fc140812 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=29f269cf-366c-47c2-a294-be422e95b5c2 /tmp            ext3    relatime        0       2
# /dev/sda2
UUID=844e4209-d95f-4b80-8b32-32ac3996f246 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


The partitions on the client look like this
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              9614116    676664   8449080   8% /
tmpfs                  8220624         0   8220624   0% /lib/init/rw
varrun                 8220624        64   8220560   1% /var/run
varlock                8220624         0   8220624   0% /var/lock
udev                   8220624      2728   8217896   1% /dev
tmpfs                  8220624         0   8220624   0% /dev/shm
/dev/sda3             53131068    184276  50247872   1% /tmp

---

### Post by obrienmd on 2009-01-08
No help on this?  I'm having the exact same issue.  I've tried with a built in forcedeth nic, as well as an intel 1000mt (well supported in linux).

One thing I noticed is that when I put a 10/100 switch between my computer and the gigE switch rather than connecting directly, it boots up with no problem (not to mention the initial PXE dhcp goes much faster right after the BIOS, like 2-5 seconds instead of 30-40).

This all worked just fine in Hardy (2.6.22 kernel).  Although, the initial PXE dhcp right after the BIOS was still slow.

---

### Post by mmrr on 2009-05-20
Hi, 

I have the same problem here... any suggestions? 

Thank you and best regards
mmrr

---

