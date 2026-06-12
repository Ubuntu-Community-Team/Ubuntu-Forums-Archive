---
title: "Re-installing Ubuntu while keeping /home intact ... with RAID10"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by cyberkost on 2008-12-24
I would appreciate some help with the following issue (I think it's rather common [except for the RAID10 twist], but the closest thing I was able to find was [this]("http://ubuntuforums.org/showthread.php?t=940060")):

I have Ubuntu 8.04 installed on 3 partitions:
/boot (residing on /dev/md0 -- RAID1)
/ (residing on /dev/md1 -- RAID10)
/home (residing on /dev/md2 -- RAID10)
I've replaced the motherboard, the videocard (in fact everything but the 4 HDDs making up the RAID) and I need to re-install Ubuntu (perhaps upgrading to 8.10 while I'm at it) such that the new /home is the /home from the previous installation and so as to minimize messing with the RAID setup (though I'd like to shrink /boot and, potentially / in favor of larger /home if that's easily accomplished without losing /home data .. I'm afraid RAID10 will make it rather complicated or plain impossible though).

Could some kind soul post instructions on what to do and what NOT to do please.

---

### Post by lemming465 on 2008-12-28
I don't think you can resize the RAID partitions, sorry.  Now, if you make a RAID partition into an LVM physical volume instead of putting a filesystem on it directly, then you can resize the LVM logical volumes. 

I'm not sure why you'd need to reinstall ubuntu, unless the existing 8.04 won't boot due to a change in disk controller chips when you swapped the motherboard.  So one option might be just to run an upgrade (sudo update-manager -d).

The ordinary graphic installer from the live desktop CD isn't bright enough to make RAID partitions, but I think it might be bright enough to use them when they already exist.  If you have a live 8.10 CD, boot it, start the installer, when you get to the disk partitioning step choose **manual**, and see if your existing partions are visible.  If so, just select and assign them to their roles.  You probably want to reformat /boot and /, you certainly want to not reformat /home, just to mount it.  Just keep an eye on the mount point, filesystem, and format checkbox as you edit the existing partitions and all will be well.

If the live desktop CD doesn't see your partitions, download and burn one of the *alternate* install CDs.  I believe those use a different text-based non-GUI installer, but that one is definitely bright enough to cope with using existing RAID partitions.  Once the system is installed you should get the usual GUI boot and login.

---

### Post by cyberkost on 2008-12-28
Lemming465, thank you for your response.  I'm definitely going to use the alternate CD, as the regular one is not mdadm/raid-aware.  If I read you correctly, the installer will find old partitions and I'll just need to assign them to their appropriate roles and only format / and /boot (I'd appreciate a confirmation before I take the plunge). Next time I do a clean install I won't skip the LVM step, so that I can fine-tune the space allocation between / and /home as needed without any kinda of reinstall.

---

### Post by lemming465 on 2008-12-31
I finally had time to fire up virtualbox and do some test installs with an alternate CD.  It can definitely do RAID and LVM partitioning.  Unfortunately, as you have noted, the live GUI desktop CD's are not RAID/LVM aware in the disk partitioning step. On the bright side, there is basically no difference in the outcome in terms of installed packages.

Yes, if you stick to your existing partitions, assign them the mount points / use as types you want, and are careful about which ones get formatted, you should be fine.

---

