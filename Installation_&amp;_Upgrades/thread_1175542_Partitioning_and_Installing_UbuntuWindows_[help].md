---
title: "Partitioning and Installing Ubuntu/Windows [help]"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by rEgonicS on 2009-06-01
Hello :o'
I recently joined the ubuntu community and installed ubuntu within windows. I decided to upgrade so I tried to install ubuntu alongside windows instead of within it. I followed the ubuntu liveCD instructions but during the step where my hard drive (1TB) is partitioned, it ran an error and stopped. (I have two hard drives. 160 Gb and a 1TB, both NTFS during the installation). Afterwards, i booted to windows and learned that my TB HD didnt work anymore ;__;' So i did some more searching and downloaded gparted. I ran that and had my TB partitioned so that 20GB is ext3 and 980 is NTFS. (Took about 12 hours Dx). I'm at school now so i haven't had the chance to install ubuntu with my newly paritioned hardrive yet. I looked at this site [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) to learn more about paritioning in case i did something wrong. Now my questions is....
 

How should i partition my two hard drives? My only goal is to have windows and ubuntu installed. (I'll probably be using more of ubuntu.) Some of the options the site gave me were
[LIST]
[*]Installing both windows and ubuntu on my 160 GB and use the TB for shared data. While making the TB FAT32
[*]Do the same as the above but make the TB ext3 and use FS-Drive if i need to use Windows.
[*]Installing windows and ubuntu on seperate drives.
[*]Have a /home parition? I dont understand how this would work xD'
[/LIST]So what I'm currently thinking of doing is to have my 160GB partitioned to hold both Windows and Ubuntu and have the spare room for /home? and shared data. And have the TB for shared data as well. While making shared data partitions ext3. (or ext4?)
 
And once I decide how to partition my harddrives how would i go about installing ubuntu on the space I partitioned?

---

### Post by raymondh on 2009-06-01
Hello,

Justa post to help you decide.  Ubuntu /root will be OK with about 8-15GB.  I use 20GB for / as I tend to grow my system fat.

Having a separate partition for media & data to be shared by windows and ubuntu is fine.  Remember though that viruses will affect windows based files so be sure that any file you put in there from windows has been virus-checked.

A separate home partition is a great feature to have.  It allows you to tweak, tamper, upgrade the root files whilst keeping your home files and settings intact.

I would ....

Have a windows OS partition
Have a ubuntu root partition
Have a separate ubuntu /home partition
Have a shared file (media/data/pics) in NTSF

Keep in mind the 4 partition limit (whether primary or extended or a combination of both)

Regards,

---

### Post by rEgonicS on 2009-06-01
Thanks for the reply. I read through this tutorial [https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition) and decided on this...
 
160 GB
[Windows (NTFS) 30GB][Shared Data (NTFS) 98GB][extended[Ubuntu (ext3) 20GB][/home 10GB][Swap 2GB]]
 
1 TB
 
[Shared Data (ext3) 1 TB]
 
 
What changes should I make?
What does a root partition do?

---

### Post by raymondh on 2009-06-01
> **rEgonicS said:**
> Thanks for the reply. I read through this tutorial [https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition) and decided on this...
 
160 GB
[Windows (NTFS) 30GB][Shared Data (NTFS) 98GB][Ubuntu (ext3) 20GB][Swap 2GB]
 
1 TB
 
[Shared Data (ext3) 1 TB]
 
 
What changes should I make?

The 160 looks good.  Remember though that you are not separating /home so, when it comes time to upgrade to a newer standard or LTS release, you will also lose your settings, tweaks that you have done along the way...... just telling you what may happen when you upgrade distributions later on.  Again, your choices as I am sure you are researching that too :)
  
The 1TB shared in ext3 ... am not sure (at the moment) if windows can read/write ext3... am sure windows and ubuntu can both read/write NTSF.  You may want to google/research if windows can read/write to and from ext3.

---

### Post by rEgonicS on 2009-06-01
I edited my post as soon as you posted xD' I decided to change 1 partition to an extended and include home. And there's a project called FS Drive which lets me read ext3 from Windows. [http://www.fs-driver.org/faq.html#acc_ext3](http://www.fs-driver.org/faq.html#acc_ext3)  What's the root partition you mentioned earlier?

---

### Post by raymondh on 2009-06-01
> **rEgonicS said:**
>  What's the root partition you mentioned earlier?

Root is where the system files go.  Think of it as the files canonical or the devs gives us to run an ubuntu OS.  Most just refer to it as /

---

