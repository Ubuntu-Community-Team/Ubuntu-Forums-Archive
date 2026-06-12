---
title: "Adding label to ext3 and ntfs disks using gparted - How Safe ?"
date: 2008-12-25
forum: Hardware
---

### Post by beyboo on 2008-12-25
I have my desktop computer with 320GB x 2 drives. One formatted as NTFS and one with ext3. Windows / Ubuntu dual  boot  off a  3rd seperate 80GB disk.

Every time I have to mount the 2 disks by clicking on them and that is by design. I have kept it that way.

The problem is that I see both the drives as 320.1GB Media which gets very confusing as I randomly load the drives, so at times they could be mounted as either disk or disk-1 (which is not the problem).

I would like to add a label like "320GB ext" and "320GB NTFS" to identify the mounts. There is an option to label disks in gparted, but it gives a very severe "might loose data" warning which scares me off !!

Has anyone ever tried adding a label on disks using gparted and not loosing data ?

---

### Post by taurus on 2008-12-25
Any reason why you don't want to add two entries in /etc/fstab to have them mount automatically each time you boot Ubuntu?  Then, you can mount them to whatever mount point you want.

---

### Post by beyboo on 2008-12-25
Just keeping them that way - I earlier did that - but kinda dont want to do it again. If there is no label option, I might consider going back to the automount option.

---

