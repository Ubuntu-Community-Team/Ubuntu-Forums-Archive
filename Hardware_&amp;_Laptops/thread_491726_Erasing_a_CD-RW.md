---
title: "Erasing a CD-RW"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by Hexydes on 2007-07-03
Any thoughts as to why I cannot erase a CD-RW in Ubuntu Feisty? I have thus tried with Nero 3 and k3B. Both fail the erasing stage at 5-20%. When I pop the disc back in, it appears to be unchanged (nothing erased).

My burner is a BENQ DW1620 CDRW/DVDRW drive. It is an IDE/PATA device, listed as (according to Nero) being located on IDE:0. I've made the following observations:

1. If I burn a CD-R, it seems to work without any trouble.

2. If I burn a blank CD-RW, it seems to work without any trouble.

3. If I burn an image to a CD-RW with data on it, it fails (normal behavior since the disc is not empty).

4. If I attempt to blank a CD-RW with data on it, the process fails as described above.

Reading any disc (CD or DVD) has never given me any trouble.

Thoughts? Thanks!

---

### Post by tgalati4 on 2007-07-04
On Dapper, I use a slow speed (say 4X) with K3b to erase my CD-RW disks.    I do get some rejects, but usually only a few after erasing a stack of disks.

Post the output of K3b's info page when you click on Disk Info.  It will give you some information about the media.

---

### Post by kerry_s on 2007-07-04
ubuntu auto mounts cd's, you need to unmount it first.

right click the icon and unmount
or
sudo umount /dev/hdc
or
sudo umount /dev/sdc
or
sudo umount /media/cdrom0
might do it

(look in your fstab to see what it's called)

---

### Post by Hexydes on 2007-07-04
> **kerry_s said:**
> ubuntu auto mounts cd's, you need to unmount it first.

right click the icon and unmount
or
sudo umount /dev/hdc
or
sudo umount /dev/sdc
or
sudo umount /media/cdrom0
might do it

(look in your fstab to see what it's called)

No dice, it just kicked it out after 20% of erasing...

---

### Post by kerry_s on 2007-07-04
next step, check if it's a permission thing. launch your writer app as root.
example: alt+f2 type> gksu k3b
then try and wipe the cdrw.

---

