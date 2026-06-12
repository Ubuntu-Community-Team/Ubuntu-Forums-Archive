---
title: "hard disk problem (ext2_check_page...)"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by popperoga on 2007-06-26
Hello Folks,
first of all, I want to say thank you to those who can help me.

I have an ext3 partition that has been recovered after a disk problem. I took an image of this partition ([FONT="Courier New"]dd if=/dev/hda5 of=/media/backup/caska-hda2.iso[/FONT]) after the recovery, so I am sure the data are still present on it.
Partition Magic reported these errors while analysing this partition:
# 1212 and
#1201 (inode 0 has an illegal block 0).

Using a live Ubuntu CD I can see the partition on my disk, and apparently it has the right size and space used.
These are the errors I get when mounting this partition:
[FONT="Courier New"]root@ubuntu:~# mount -t ext2 /dev/hda5 /mnt/recover/ -o ro
root@ubuntu:~# cd /mnt/recover/
root@ubuntu:/mnt/recover# ls
ls: reading directory .: Input/output error
root@ubuntu:/mnt/recover# dmesg | tail 
[17181105.632000] EXT2-fs warning (device hda5): ext2_fill_super: mounting ext3 filesystem as ext2
[17181112.512000] EXT2-fs error (device hda5): ext2_check_page: bad entry in directory #2: rec_len is smaller than minimal - offset=0, inode=0, rec_len=0, name_len=0
[17181112.512000] EXT2-fs error (device hda5): ext2_readdir: bad page in #2
root@ubuntu:/mnt/recover# cd
root@ubuntu:~# umount /mnt/recover/
root@ubuntu:~# mount -t ext3 /dev/hda5 /mnt/recover/ -o ro
mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:~# dmesg | tail  
[17181230.124000] JBD: no valid journal superblock found
[17181230.124000] EXT3-fs: error loading journal.[/FONT]

I understand the filesystem contains errors and something wrong happens when it is mounted.
Furthermore, I have opened the partition's image with the freeware "DiskInternals Linux Recovery", after copying it on a windows based computer. The program correctly mount the image and scan it founding thousands of directories and files, but at the end it displays only the files that has been deleted!! In fact this program aims to do so, but I need to recover all the valid data that the image still contains. At least, I am quite sure my data can be read in some way. This is a tricky problem, isn't it?

The big question is: how can I access to my data?

Thank you for any usefull suggestion I will receive.
Otello

---

