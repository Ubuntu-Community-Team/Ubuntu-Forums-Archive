---
title: "Re-Partitioning"
date: 2005-12-21
forum: Installation &amp; Upgrades
---

### Post by faceoftheearth on 2005-12-21
I have read through the current "Uninstalling Ubuntu" thread, and it really doesn't help, so perhaps someone can help me. Currently I have XP and Ubuntu dual booting on a 60Gb hard drive. XP is on a 33,126.2MB NTFS partition, Ubuntu is on a 19,187MB EXT3 partition. There are two Linux swap partitions. Actually that's how it used to be, I just went into partition magic 8 and deleted the Linux partitions. I haven't restarted the computer because I'm afraid with Grub gone I'll never boot again. Right now Partition Magic shows the following partitions

Dellutility-FAT-47MB
Local Disk(C:)-NTFS-33,126.2MB
*-Extended-20,214.6MB
*-Unallocated-20,214.6MB
Local Disk(*.)-CP/M concurrent DOS, CTOS
(*)-Unallocated-7.8MB

The first unallocated space is where Linux was. My first thought was to boot from the XP disk and type fix MBR so that XP boots automatically. However, I'm afraid that I've dove into the deep end here. Can anyone give me solid advice on what to do with what I have?  

Thanks

---

### Post by SomethingTohide on 2005-12-21
Oh dear god lmao, I've tried that. GRUB will give an error on restart saying can't find something or something like that. Use a boot disk or something and do fdisk /mbr, and you should be fine

---

### Post by GregMartyn on 2005-12-21
fixboot and fixmbr on the windows cd are all you need. You'll be fine.

---

### Post by faceoftheearth on 2005-12-21
Well, I dove in again. I think I'm ok, I didn't do fixboot, but I ran FIXMBR and it's ok so far. Should I go back and do fixboot as well?

---

