---
title: "[SOLVED] LVM Encryption + update = initramfs"
date: 2008-08-15
forum: General Help
---

### Post by pofigster on 2008-08-15
So, my desktop has a fully encrypted hard drive (except for /boot) that I set up using passphrases and the alternate CD.  It's been working great, but this morning I installed the updates which required a system restart - when I restarted I get:
> BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)
Any idea on what happened and what I can do to fix it?
My understanding is, worst case scenario, plug in another hard drive, install Ubuntu onto it and when I go to mount the encrypted HDD it should prompt me for a password to decrypt the volume.  Is this correct?

---

### Post by pofigster on 2008-08-15
I'm wondering - if I reinstall Ubuntu (I have separate /boot, / and /home partitions) only reformatting /boot and / - would that allow me to decrypt and access my /home partition?

---

### Post by pofigster on 2008-08-17
Well, in my situation booting off of the alternate CD into the "repair" mode allowed me to decrypt, tar and copy my home partition to an external hard drive - time consuming, but no data loss.

---

### Post by mhrnjad on 2008-10-15
> **pofigster said:**
> Well, in my situation booting off of the alternate CD into the "repair" mode allowed me to decrypt, tar and copy my home partition to an external hard drive - time consuming, but no data loss.

Faced with the same issue I used the following commands to bring up my system:

{{{
cryptsetup luksOpen /dev/your-encrypted-partition whatever
lvm vgchange -a y
exit
}}}

Please ignore any error messages, you may need to hit the Enter key a number of times.

Please see also: [https://bugs.edge.launchpad.net/ubuntu/+source/initramfs-tools/+bug/284904](https://bugs.edge.launchpad.net/ubuntu/+source/initramfs-tools/+bug/284904)

---

