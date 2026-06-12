---
title: "Harddrive Questions"
date: 2008-06-20
forum: Hardware
---

### Post by TheMixtureMedia on 2008-06-20
Hi there question I have xubuntu 8.04 and running the main drive off ide and want to add a 2nd drive off sata hard drive with a pci sata card. My question is when I install the hard drive should xubuntu find it right away and let me use it or how hard is it going to be to get it xubuntu to find the drive and get it to work.

Thanks+

---

### Post by logos34 on 2008-06-20
xubuntu should detect the drive fine (although the pci sata host card may complicate things), but to automount the partitions you'll have to add it to fstab.  After you hook it up reboot and go into the bios--check that it's being detected properly.  Then boot into linux and run

sudo fdisk -l

it should show up.

If the is the sata blank, you can use Gparted to create partitions and format them.  

Add partitions to fstab and configure:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Add: you might want to use UUIDs instead of '/dev/sdxy' format.  Find them and substitute them so they look like the others:

sudo blkid 

or

ls -l /dev/disk/by-uuid

---

