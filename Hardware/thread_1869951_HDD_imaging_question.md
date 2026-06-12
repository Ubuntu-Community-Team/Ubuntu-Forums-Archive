---
title: "HDD imaging question"
date: 2011-10-26
forum: Hardware
---

### Post by Super_Dork_42 on 2011-10-26
I have two old hard drives currently in use in my computer. One is an 80GB that I use for Windows, and the other is a 40GB I use for Ubuntu. My Windows drive is about 5GB from full and the performance is getting really slow. Also, since both drives are IDE drives and my motherboard only has one IDE connector, I can't connect either of my IDE optical drives.
My question is, is there a good, free disc imaging software that will allow me to do the following?
I plan on partitioning my new 1TB SATA HDD to have a 85GB partition, then burning an image of my 80GB HDD on there, then expanding the partition to 500GB, then doing the same for my 40GB.
Basically I need a good, free disc imaging software that, preferably, can do all that in Ubuntu. Any ideas?
(Sorry if this is in the wrong place. I tried to figure the most correct place for it.)

---

### Post by kurt18947 on 2011-10-26
It might be worthwhile to check your hard drive manufacturer's site.  Most offer a means to move partitions.  I assume you have SATA ports available. You could plug your new drive into a SATA port and your old drive into your IDE port. You can have two devices on one IDE cable.  I'm assuming you have an IDE CD/DVD drive so you'd have one old hard drive and the boot CD drive on one IDE cable.  Depending on the manufacturer, you might have to burn an .iso file to a CD and boot off that CD.  I use a shareware imaging program where I can select the size of the restored partition.  Clonezilla is a common imaging program but I don't know how clonezilla handles partition sizes -- I don't know if the restored partition has to be the same size as the original or not.

If these options don't work for you and you have spare SATA ports, you could either get an external enclosure for your old hard drives or you could get an IDE-SATA adapter. I got one from monoprice:
[http://www.monoprice.com/products/product.asp?c_id=104&cp_id=10407&cs_id=1040701&p_id=2193&seq=1&format=2](http://www.monoprice.com/products/product.asp?c_id=104&cp_id=10407&cs_id=1040701&p_id=2193&seq=1&format=2)

I have a couple and they do work. The only trick I found was that a western digital IDE drive had to be jumpered as master. In the PC it didn't need any jumpers when the only drive on that cable. Using the SATA adapter it had to be jumpered.

Edit:  I don't know if I ever tried one of these with Linux.  They'd probably work because I don't think they rely on the operating system but I don't know for sure.

---

### Post by Super_Dork_42 on 2011-10-26
Well, I plan on using gparted or parted magic to do the partitioning. I just want a reliable, free disc imaging program that I can use in Ubuntu. I just upgraded to 11.10.

---

### Post by diasf on 2011-10-26
what you need is dd
For instance, assume your old partition running linux is /dev/hda1 and the new one (pre-expand) is /dev/sda1, then

dd if=/dev/hda1 of=/dev/sda1

should do the job. In combination with FTP, that will also work for networks (it's tricky, but works like a charm).

BUT be advised, dd will do whatever you tell him to, so be careful of what you ask :)

---

### Post by Super_Dork_42 on 2011-10-27
> **diasf said:**
> what you need is dd
For instance, assume your old partition running linux is /dev/hda1 and the new one (pre-expand) is /dev/sda1, then

dd if=/dev/hda1 of=/dev/sda1

should do the job. In combination with FTP, that will also work for networks (it's tricky, but works like a charm).

BUT be advised, dd will do whatever you tell him to, so be careful of what you ask :)

Sorry, but I, despite having had Ubuntu on a computer of mine since 5.10, haven't done enough with the command line to know what you're talking about. Will that, and correct me if I'm wrong, create the image AND put it to the new partition of the new hdd? I'm a little confused.

---

### Post by diasf on 2011-10-27
[http://en.wikipedia.org/wiki/Dd_%28Unix%29](http://en.wikipedia.org/wiki/Dd_%28Unix%29)

---

### Post by Super_Dork_42 on 2011-11-20
So is dd basically equal to the windows command of xcopy, but more dangerous if you don't know what you're doing?

---

### Post by oldfred on 2011-11-20
No dd is a byte for byte copy program. Xcopy copied files like cp or rsync.

DD nickname is Data Destroyer as many have mistyped something and it does exactly what you tell it. It really only works from same size to same size drive. Some have had issues expanding partiitons as dd set some internal thing that made the new larger drive think it was the smaller size. Most have been able to use gparted but one or two users had to use drive vendor software to reset drive back to larger size.

I usually suggest small system partitions of 30-50GB for Windows and 10-20GB for Linux when you have a separate /home or separate data partition. With both Windows & Ubuntu you also should have a shared NTFS partition for any data you want to share with Windows.

Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)

---

### Post by Super_Dork_42 on 2011-11-21
> **oldfred said:**
> No dd is a byte for byte copy program. Xcopy copied files like cp or rsync.

DD nickname is Data Destroyer as many have mistyped something and it does exactly what you tell it. It really only works from same size to same size drive. Some have had issues expanding partiitons as dd set some internal thing that made the new larger drive think it was the smaller size. Most have been able to use gparted but one or two users had to use drive vendor software to reset drive back to larger size.

I usually suggest small system partitions of 30-50GB for Windows and 10-20GB for Linux when you have a separate /home or separate data partition. With both Windows & Ubuntu you also should have a shared NTFS partition for any data you want to share with Windows.

Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)

Thanks for that useful information. I had never heard of ddfldd before.

So, just to be clear, what would be the commands for cloning my Ubuntu disk to a partition of basically the same size on my new 1TB hard drive, without messing with my other partition?

---

### Post by oldfred on 2011-11-21
It copies exactly what you tell it to copy. It does not care where you are copying from or to, it just does it.

In fact Windows has info in MBR & PBR boot sectors that you probably want to include, but Windows will still want to call home it it will see its on a new drive. But if you have a partition table on the new drive and copy the entire MBR, you overwrite the partition table.

---

### Post by Super_Dork_42 on 2011-11-21
Thank you for all your help so far. All I need right now are the exact commands to copy my 40GB hard drive (sda0) to a 40GB partition on my 1TB drive. I'm nowhere near the 40GB so I don't need to expand it yet, I'll ask about that when I get there.

---

