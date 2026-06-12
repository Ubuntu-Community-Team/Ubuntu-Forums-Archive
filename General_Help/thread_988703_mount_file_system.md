---
title: "mount file system ?"
date: 2008-11-20
forum: General Help
---

### Post by windowsfree on 2008-11-20
I installed UBUNTU 8.10 with wubi on my windows partition.  How can I mount the windows partition at startup?  Wine searches the C:\ Drive, but I am unsure if and how I can mount it so it shows up as a file system.

---

### Post by jpkotta on 2008-11-20
Wine's C: is not the same as the C: of your Windows partition (unless you set it up that way).  Wine's C: is usually ~/.wine/drive_c/, i.e. just a regular directory in your $HOME.  

For Windows's C:, read this: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by prshah on 2008-11-20
> **windowsfree said:**
> I installed UBUNTU 8.10 with wubi on my windows partition.  How can I mount the windows partition at startup?  Wine searches the C:\ Drive, but I am unsure if and how I can mount it so it shows up as a file system.

a. Wine's C: and your Windows C: are totally separate. You can set them up to be the same, but not in your (this particular) case.

b. Installing the Wubi disks to the partition containing your Windows installation means that you cannot mount your Windows partition in Wubi-Ubuntu. The "host drive" partition cannot be mounted in wubi-ubuntu.

---

