---
title: "Creating a partitioning within free space"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by alh2354@comcast.net on 2009-08-06
[COLOR=black][FONT=Arial Narrow]I am running Ubuntu 9.04 on a separate hard disk, where there is over 200 GB of free space, some of  which I want to format as NTFS. [/FONT][/COLOR][COLOR=black][FONT=Arial Narrow]GParted (System > Administration > Partition Editor[/FONT][/COLOR][COLOR=black][FONT=Arial Narrow] won’t let me unmount the free space partition so I can work with it. It says to manually unmount it, but I don’t see how to do that. I tried booting to a GParted live DVD-it didn’t even see the hard drive on which Ubuntu is installed. It only saw a separate hard drive on which Windows is installed. I also tried using a terminal window from within Ubuntu and also using a Knoppix live DVD, but it says that I don’t have permission to access the linux partition. Is there some way to get around this ?[/FONT][/COLOR]

---

### Post by om26er on 2009-08-06
run ubuntu jaunty live cd and then sudo fdisk -l paste it herre

---

### Post by alh2354@comcast.net on 2009-08-06
Thanks-I'll try that.

---

