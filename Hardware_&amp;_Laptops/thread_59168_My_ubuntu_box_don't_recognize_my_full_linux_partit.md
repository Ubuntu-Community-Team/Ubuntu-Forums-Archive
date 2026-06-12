---
title: "My ubuntu box don't recognize my full linux partition"
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by biquillo on 2005-08-23
Few moths ago I installed kubuntu in a ext3 partition with 5 gb, few days ago I had to reinstall my windows partition due to my sister broke up the entire system, so I made a backup of my ext3 partition. Before to reinstall windows I made new partitions because I need more space for linux, so I created a ext3 with 10 gb and restored my ghost linux image on it.
The problem is Linux thinks that my ext3 partition is still in 5 gb, what can I do?

Thanks!!


PD: Sorry with my english.....

---

### Post by nad on 2005-08-23
Your English is fine. I wish that I could communicate in a another language as well as you do.

What happened is that the image that you made is only 5GB. As the image includes only a 5GB file system, this is all you got.

Use the parted utility ( gparted or qtparted are graphical frontends for parted, you may need to download parted and one of these first) to confirm that your partition is correctly sized and then resize your file system.

---

### Post by biquillo on 2005-08-23
I didn't expect such a fast reply :D thank you very much!!
I installed qtparted, and the partition size is correctly size = 9.25 gb used space =  5.12 gb, but if I do a "df" command my hda7 mounted on / is used at 100%!!

it's very extrange, but I don't like to reinstall.... I have my system very well configured :( :P

---

### Post by nad on 2005-08-23
The df command is giving you the size of the file system, not the partition. You have not yet resized the file system to the maximum size of the partition.

I do not know how to do it in the graphical editor. The command line from within parted is: resize partition_number start_block_number end_block_number .

By the way, you do not wish to do this while the file system is mounted.

---

