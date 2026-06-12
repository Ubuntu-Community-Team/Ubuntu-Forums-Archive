---
title: "ubuntu 9.10 dual boot vista"
date: 2009-10-31
forum: Hardware
---

### Post by petitlou60 on 2009-10-31
Hello everybody

i have two ntfs partitions windows vista and data , and a 10Gb unallocated space

i install ubuntu in this freespace , just before install i choose advanced and set grub install in /dev/sda5  (because if mbr is altered my DVD is not detected by vista)

install is successfull

after rebooting in vista i check partition sceme, ubuntu has built an extended partition with two logicals in it ,one for linux and one for swap

i attempt with easybcd to customize vista boot loader to see linux , operation seems successfull , but at boot time boot failed
I am not surprised because linux is in a logical partition and may be bootloader vista is unable to start systelm in logical partition

If anaybody have an idea ???

best regards

---

### Post by sujoydc on 2009-11-23
I have faced similar problem with Ubuntu 8 with Vista as well. 
But dual boot with XP runs perfect. I guess there is a problem with Ubuntu and Vista in dual boot. 
Experts please comment, I am also looking for answers.

---

### Post by v00lo on 2010-01-26
Did you manually assign the swap space? It's a good way to control your partitions while install takes place. If not, while installing, ubuntu could "steal" some of the space previously assigned to vista, which makes it impossible to boot. It actually happened to my friend using vista/linux, but that was way before I started using it myself, so I can't remember any details. And keep in mind to install Ubuntu on ext, or FAT partition only, from what I'm aware NTFS is just for the windows...
I could be wrong, just giving some info I recall, so double check everything I've posted, although I hope I could be of any help.

---

