---
title: "partition not showing"
date: 2013-08-06
forum: Hardware
---

### Post by sgriesel on 2013-08-06
Hi guys,

I was using PhotoRec to recover some data, after restart Ubuntu would not boot up again with error message 'error no such partition grub rescue'.'

After doing some research I found the Linux partition was unmounted. 

When booting with cd, click on "Try Ubuntu", once in the GUI go to  terminal and type 'sudo fdisk -l' it shows the following. But not  showing the Linux partition? Any idea how I can get this back?

/dev/sda1           1             638      5124703  b   W95 FAT32
/dev/sda3           4526          4635     497980   82  Linux swap

---

