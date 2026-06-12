---
title: "Partman does not see sda disk"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by nsche on 2009-01-28
I have an old Dell Inspiron 3500 laptop with a Celeron, 192 mb ram and a 10gb disk.  The cd is toast (apparently I threw it out cause I cannot even find it) but it will talk on the net using win 98 with an ethernet card I have.  Using win 98 I have transfered vmlinuz and initrd.gz to the disk and can boot using linld097.  I transfered a copy of the alternative iso over and want to do an install from that.

The problem comes with partman.  It does not give me the chance to partition sda.  It does not even come up on its list.  If I attach an external usb disk that disk is detected and it offers to partition it but not sda.  Looking in syslog nothing looks strange.  The disk and its partitions are detected.  sda1 is mounted on /hd-media and is usable (though ro).

Why does partman not detect it?  What can I do to work around this?  Any ideas?

Thanks
Norm

---

### Post by lha on 2009-02-03
I've seen this problem occur with faulty partition tables. Please, post the output of 'sudo fdisk -lu /dev/sda'. It'll tell you if your partitions are overlapping.

---

### Post by nsche on 2009-02-04
```
sudo fdisk -lu /dev/sda
Disk /dev/sda: 10.0 GB, 10056130560 bytes
240 heads, 63 sectors/track, 1299 cylinders, total 19640880 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     8195039     4097488+   b  W95 FAT32
/dev/sda2         8195040     8966159      385560   82  Linux swap / Solaris
/dev/sda3         8966160    19640879     5337360   83  Linux
```
As you can see the partions are ok.  I finally got the system up but I never figured out what caused the non-recognition of the partitions in question.  I ended up doing an install to an empty partition on an external USB (1.0, slow) disk I had around.  I then did a format on sda2 and mkswap on sda3 and copied the root partition over (with rsync) and edited boot/grub/menu.lst and did a grub-install and finally got it running.  It works fine now!

Thanks for the reply and if you have any ideas on what the problem was I would be intellectually interested.

Thanks
Norm

---

