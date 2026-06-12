---
title: "problem with swap device"
date: 2008-10-05
forum: General Help
---

### Post by rkleemann on 2008-10-05
Hi,

I have Ubuntu Server 8.0.4 installed.

I designated multiple partitions for swap (I have 4 drives and designated 1 partition in each drive for swap).

For example, in sda I have in fdisk:

/dev/sda5           60318       60801     3887698+  82  Linux swap / Solaris

However the system won't mount the swap partitions and won't even allow me to format the swap partition:

$ sudo mkswap /dev/sda5
/dev/sda5: Device or resource busy

Why would it be busy? It's not mounted... the "free" command reports 0 swap. Running top also shows 0 swap.

I'm running LVM2, but sda5 is not part of any physical or logical volume. I'm running raid5 underneath the LVM, but none of the raid devices make use of sda5, and sda5 is properly typed as a swap partition.

Anyone have suggestions on how to troubleshoot this?

Thanks
Ricardo

---

### Post by porchrat on 2008-10-05
try reformatting it?

I was running a RAID0 an briefly encountered that problem.  Can't remember the exact steps I took, but I think I used fdisk to reformat and ran a mkswap again and that did the trick.  Note though that the UUID numbers change and I had to modify the /etc/fstab accordingly.

---

### Post by rkleemann on 2008-10-05
> **porchrat said:**
> try reformatting it?

I was running a RAID0 an briefly encountered that problem.  Can't remember the exact steps I took, but I think I used fdisk to reformat and ran a mkswap again and that did the trick.  Note though that the UUID numbers change and I had to modify the /etc/fstab accordingly.

Thanks,

but reformat in what sense? I don't want the other partitions to be affected, and I thought mkswap was already the swap formatting utility.

---

