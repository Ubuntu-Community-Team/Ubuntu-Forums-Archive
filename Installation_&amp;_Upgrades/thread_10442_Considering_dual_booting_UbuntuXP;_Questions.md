---
title: "Considering dual booting Ubuntu/XP; Questions"
date: 2005-01-07
forum: Installation &amp; Upgrades
---

### Post by Traxis on 2005-01-07
Hi, I'm new here, and also new to Linux. I have fooled around some with Redhat on my old PC, but that is the extent of my experience with Linux. My friend introduced me to Ubuntu, and I thought I would give it a try. My goal is to eventually ween myself away from Windows.

Anyway, I want to dual boot XP and Ubuntu, but I have a few questions before I start. I have heard that some people have had some significant trouble doing this, and I want to avoid most of these problems by collecting the required knowledge beforehand.

1- I currently have a 40 GB HDD, with WinXP (NTFS) occupying the only partition, which spans the entire disk. I plan on creating a 10GB partition for Ubuntu, along with a 512 MB swap. All I will have to do is create a primary ext3 partition and the swap after resizing the existing partition, and I should be able to install just fine, correct?

2- When going to create the Linux ext3 partition, Partition Magic says "This partition crosses the 1024 cylinder boundary and may not be bootable.". Is this anything to worry about?

3- I know of the issues about editing /boot/grub/menu.lst and setting my HDD to LBA in the BIOS, but are there any other common issues and errors I should be aware of before I come crawling back here asking more questions?

4- Should I create a seperate partition for files that both operating systems will use, (such as MP3s)? If so, what type of partition should I create it as?

Thanks for any advice you can give me.

---

### Post by JD2 on 2005-01-07
1)resize your windows partition

2)boot ubuntu into default installation

3)you will be presented with a choice to either wipe out your hd and install linux on it or meddle with the free space that was created from the resize operation

4)choose to hand configure the partitions

5)make either two new partition from the free space ie. root "/" and "swap" or one "/" and put swap into it by creating a logical partition. I created two partitions since I have one harddisk. You only have 4 partition for 4 disks so to save partitions for future disks one would create a primary partition then an extended partition ie. the container partition to hold all the logical partitions. 

6)install ubuntu and it will put grub bootloader into your MBR boot record. Since you have winxp you could have winxp bootloader invoke grub that will then boot you into linux or windows. This way you don't put grub into MBR and can easily go back to "only windows" installation again if you get tired of linux. I have win98 and I had to reformat after reverting back to windows. Taking grub out of my MBR messed up my file allocation tables and who knows what else. So the process of going back is not without terrors :)

7)offer sacrifical cow to the linux gods and pray hard that all your hardware will get detected. 

8)ubuntu gnome is a fun desktop but also easy to break so be careful. Read docs and don't experiment with the gnome panels launching scripts and what not since that might screw up your ubuntu desktop and then must reinstall the os. Ie. don't follow my example :)

I have 128megs of system ram so I created 512meg swap space. If you don't create the swap space during install like I did once before I was too anxious and plainly forgot about it then you can do it afterwards and it's a bit of a messy proposition but quite possible. There are command line tools in the ubuntu distro cd that allow you to do it. You create the swap then activate it. Check out the resource manager graph page tab in the ubuntu desktop to see if you swap space is working. You shouldn't see zeros there. I had like oh 50megs swap space used but it varies. It never went above 128megs but for very memory intensive programs it might. 512megs seems to be enough though for normal desktop user unless they're devs since I read that compiling gcc or some other large programs takes lots of memory. 

After you get ubuntu installed, google for gnome themes. There is an official gnome theme website and check out Glossy_P and some desktop backgrounds because in my view the default ubuntu theme makes me wanna barf. What were those guys thinking? I know brown for africa but come on!

---

### Post by fng on 2005-01-07
1. yep
2. euh, don't think so as long as you put grub/lilo into the MBR.
3. 
4. If both Operating Systems need to write to the partition, i would go for a FAT32.  If only Ubuntu needs to read the partition, NTFS is fine too and in this last case, you dont need an extra partition..

---

### Post by makaveli on 2005-02-02
yeah i want to do the same thing with my computer except i want to tell ntldr to go to grub on my external hardrive how would i do this. also how would i stop grub from automatically being installed into my mbr during the installation of ubuntu?

---

