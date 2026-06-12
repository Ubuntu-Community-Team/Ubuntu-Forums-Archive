---
title: "problem mounting hd"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by tyoung212 on 2008-03-26
I used partition magic 8 to repartition my hd (fujisu on a dell e1505) into a 65gb and 5gb space. When i restarted my computer, windows xp ran but then did a chkdsk and says the volume is dirty and says it is inserting an index entry into index $0 of file 14608. The problem is that when i go to click on the windows partition (running ubuntu 7.10) it says "cannot mount volume... $longfile indicates unclean shutdown (0, 0) failed to mount '/dev/sda2': operation not supported mount is denied because NTFS is marked to be in use."

could anyone guide me to force mount this, or how to fix windows? Any help is greatly appreciated. I really need to access the windows partition to get my term paper.

Thanks
Thomas

---

### Post by kpkeerthi on 2008-03-26
Just boot into windows and then into ubuntu. See if ubuntu mounts it this time.

To force mount the partition manually

```

sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda2 /media/windows -o force

```

---

### Post by tyoung212 on 2008-03-26
Thanks you so much kpkeerthi. I accessed the windows partition and got my term paper off of it. Once again thanks, i was about to die if i had to do the whole thing over again.

---

