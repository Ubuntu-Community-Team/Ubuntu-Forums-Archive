---
title: "dual boot vista and ubuntu from same hd"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by bd41 on 2008-12-28
alright so heres the situation.

I had vista home premium installed earlier today. now i downloaded ubuntu, and installed it to my EXTERNAL 1TB harddrive. (im writing this from ubuntu running on my external) So far ubuntu is really cool, but i would like to dual boot vista and ubuntu from the SAME hard disk.

 i do not mind losing my current vista info as all my important media is saved on my 1tb external hd.

So, how do i uninstall ubuntu from my 1tb external hd (without losing the media thats on my external) , and installing ubuntu on my C drive so i can dual boot vista and ubuntu?

For the record,my machine is gateway gt5414e.

---

### Post by bd41 on 2008-12-28
hmm or should i just be safe and get another small internal sata hd and just throw ubuntu on that so i dont mess with my other drive?

---

### Post by cariboo on 2008-12-28
The preferred method, is to use Vista's disk management software to resize your Vista patition, then install Ubuntu on the free space you created.

I have Vista installed, but I don't use it enough to be familiar with some of the administration functions. When I installed Vista, I had in mind that I was going to install a Linux distribution, so I only partitioned half of the hard drive for Vista and left the rest of the drive blank. When it became time to install Ubuntu, I used the manual partiton option to set up the partitons I wanted on the blank half of the drive.

Jim

---

### Post by bd41 on 2008-12-28
nothing will let me partition the drive vista is on (c) .. ive been using vista for a good time now so i dont think i can partition it without messing up the files on it

---

### Post by tommcd on 2008-12-28
> **bd41 said:**
> nothing will let me partition the drive vista is on (c) .. ive been using vista for a good time now so i dont think i can partition it without messing up the files on it

Vista comes with it's own hard disk partitioning tool. See this:
[http://articles.techrepublic.com.com/5100-10878_11-6170510.html](http://articles.techrepublic.com.com/5100-10878_11-6170510.html)
Use Vista's partitioning utility to create some free space for Ubuntu. Then install Ubuntu onto the newly created free space.

For removing Ubuntu from the external drive, once you have Ubuntu installed to the internal drive you can install **gparted** to partition and format the external drive any way you want. Or you could just get the gparted live CD or **Parted Magic** live CD and use one of them to partition the drive. 

If you created a separate /home partition when you installed Ubuntu to the external drive then just save that partition and your data will be safe. If you did not create a separate /home then you will have to back up your data on the external drive before removing Ubuntu.

---

### Post by bd41 on 2008-12-28
Thank you TOM, one problem, it will only let me partition 5-7 Gigs.. is that enough for ubuntu?

---

### Post by tommcd on 2008-12-28
> **bd41 said:**
> Thank you TOM, one problem, it will only let me partition 5-7 Gigs.. is that enough for ubuntu?

Yes that would be enough for Ubuntu. For 5-7 GB I would create just a root partition with a 512mb swap.

It seems that Vista's partitioning utility leaves much to be desired. See the section titled **Understanding the size discrepancy** in the link I gave in my last post.

Do you have a backup partition or a recovery partition on that Gateway computer? Boot up the Ubuntu live CD and open a terminal (applications > accessories > terminal) and post the output of:
```
sudo fdisk -l
```
This will list the partitions on your computer.

You could gain some free space by deleting any backup or recovery partitions you may have. The only other option would be to try a Gparted or Parted Magic live CD. I have no idea how well they may work with Vista though. A quick search indicates that people have used Gparted on Vista:
[http://gparted-forum.surf4.info/viewtopic.php?id=431](http://gparted-forum.surf4.info/viewtopic.php?id=431)
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)
This may be risky though. Use Gparted at your own risk.

Be sure to defragment Windows before partitioning in any case.

---

### Post by Nico-dk on 2008-12-28
[A real nice first time dual booters guide](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

