---
title: "Ubuntu 8.10 and removing Windows partitions"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by cattlerepairman on 2009-04-07
I am a newbie to Ubuntu and I did search. However, I am still unsure on how exactly to accomplish what I want:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc5fcbd5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   306054314   153027126    7  HPFS/NTFS
/dev/sda2       306054315   597537674   145741680    5  Extended
/dev/sda3       597537675   625137344    13799835    7  HPFS/NTFS
/dev/sda5       306055168   314660636     4302734+   7  HPFS/NTFS
/dev/sda6       314665218   585970874   135652828+  83  Linux
/dev/sda7       585970938   597537674     5783368+  82  Linux swap / Solaris


I want to get rid of the remaining windows partitions, with all the Vista crap that is still on them. I guess that would be sda3 and sda5. I want the whole HDD to be Ubuntu.

How, exactly, do I do this? I would much appreciate a step-by-step....

---

### Post by 67GTA on 2009-04-07
First, open Menu>System>Administration>Partition Editor and make sure the extended partition is not wrapped around your ubuntu partition or swap partition. If not, then boot up your live cd, open the partition editor, and just drag your ubuntu partition all the way over to the edge so it covers everything except swap. This will expand it to cover the whole hard drive and erase the vista partitions. The fdisk command does not show the partitions in the order as they are in on your hard drive, but the numbers will be the same. You want to be left with only sda6 and sda7.

---

### Post by cattlerepairman on 2009-04-07
> **67GTA said:**
> First, open Menu>System>Administration>Partition Editor and make sure the extended partition is not wrapped around your ubuntu partition or swap partition. If not, then boot up your live cd, open the partition editor, and just drag your ubuntu partition all the way over to the edge so it covers everything except swap. This will expand it to cover the whole hard drive and erase the vista partitions. The fdisk command does not show the partitions in the order as they are in on your hard drive, but the numbers will be the same. You want to be left with only sda6 and sda7.

Ok, here is the screenshot of what the partitions look like: I do not want to be a pain, but I want to be sure I understand correctly before messing with the partitions. 

When you say "drag your ubuntu partition all the way" you are referring to sda6? I simply extend sda6 to cover all, except sda7? This will not kill the GRUBloader?
Should I delete any partitions first, such as sda3 (the last partition)?

---

### Post by 67GTA on 2009-04-07
That is what I was afraid of. Your linux partitions are inside the extended partition. If you delete the extended, whatever is inside will go with it. You might benefit from a complete reinstall. That way you can create a separate /home partition and never lose your settings when upgrading or installing a newer version. If you want to try and save what you have (may not work), then my advice would be:

1. Get gparted live cd
2. Boot gparted live cd
3. Delete sda1 (hit apply to execute)
4. Then try to move sda2 (extended partition) to the empty space where sda1 was
5. If that is successful, delete sad2
6. Delete sda3 and sad5
7. Resize/move sda6 and sda7 to your liking  

I strongly suggest you look at creating a separate /home partition. This link will show you how to do it if you are able to save your existing partitions: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If you do a clean install, just choose manual, and create two partitions plus swap. Then tell the installer to mount one as root(/) and one as home(/home). This way you can do a clean install with a live cd anytime in the future, choose manual, and tell the installer to mount your home partition as /home but not to format it. This will let you preserve your personal settings/info. You will still have to install any apps you had again, but thier settings will stay intact in /home.

---

### Post by cattlerepairman on 2009-04-07
67GTA, thanks for this explanation. I think I am better off with a re-install. I know that something went wrong when I installed ubuntu on this machine, as far as partitions go.

---

