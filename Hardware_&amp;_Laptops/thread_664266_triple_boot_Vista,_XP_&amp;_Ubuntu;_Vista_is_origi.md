---
title: "triple boot Vista, XP &amp; Ubuntu; Vista is original OS"
date: 2008-01-11
forum: Hardware &amp; Laptops
---

### Post by ctoaun on 2008-01-11
Good evening,
I have three questions preceded by two statements for clarity&#8217;s sake

It seems that most instructions for dual booting Ubuntu with Vista operate under the assumption that XP was the original OS and Vista/Ubuntu was just a user desired upgrade. This also applies to instructions for triple booting Vista, XP & Ubuntu.

Although I can make Ubuntu work on my other laptop, which was sold with XP SP2 as its operating system, If I install XP SP2, Xandros or Ubuntu, I cannot make drivers (video, sound modem) work  work on this Toshiba laptop, which was sold with Vista installed on it. The laptop is a Satellite A215-4697. 

Toshiba&#8217;s website does not supply XP drivers for this Vista product, which seems to mean that Linux cannot work on this laptop. I am limited to using the Toshiba supplied Operating CD, which basically limits me to Installing vista and then using a third party&#8217;s disk resizing software to reduce the unnecessarily oversized Vista installation. See caution below.

My three questions are:
1)	How will  Ubuntu recognize and use Vista drivers since Xandros did not?
2)	If Ubuntu will not recognize and use Vista drivers, are there XP drivers that will run vista hardware?
3)	Does anyone know of a triple boot or at least a dual boot scheme that might work?

Any help would be greatly appreciated. I hate Vista


Caution for those of you thinking of trying Vista. 

Be advised that it will stick some system files in the middle of the disk. This means that although a fresh install of Vista should take 10-30 gig of space. However, Vista will put say 15gig at the beginning of disk and say 1-10 gig in the middle of the disk. This means that a 10 gig vista install actually consumes about 50 to 70% of any disk on which it&#8217;s install, making it necessary to use third party disk resizing software. I hate Vista.

---

### Post by Sef on 2008-01-11
For resizing Vista, use the partitioner that comes with it.

---

### Post by woodcarver on 2008-01-11
My first question would be: Why do you want to triple-boot Vista AND XP?????
I would eliminate Vista and simply dual-boot XP and Umbuntu. Then search for drivers that will work in XP first, then work on the drivers for Umbuntu.

Vista is a bad "space-hog"!! Plus it is always connected to Microsoft, and there is no way to break the connection.

Just my opinion.

---

### Post by Mze on 2008-01-11
Quick search on the forum brings up this [thread]("http://ubuntuforums.org/showthread.php?t=220452")

---

### Post by anoopjohn on 2008-01-11
You can try this instructions for installing Ubuntu on a system that already has vista preinstalled. 
[http://www.zyxware.com/articles/2007/12/27/windows/installing-ubuntu-laptops-single-ntfs-partition-windows-xp-or-vista](http://www.zyxware.com/articles/2007/12/27/windows/installing-ubuntu-laptops-single-ntfs-partition-windows-xp-or-vista)
The only change that you have to take care in your specific case is to create one more additional partition for your xp installation. But the basic process is the same - resize vista partition, create new empty partitions for ubuntu and xp, install ubuntu and xp on the new partitions.
Cheers
Anoop

---

### Post by ctoaun on 2008-01-11
> **Sef said:**
> For resizing Vista, use the partitioner that comes with it.

Thanks Sef, but for the following succeeding reason, I do not think that I should follow your advice on this. 

Vista’s partition program is garbage. I know this because I’ve deleted accounts and defragmented the disk. Afterwards, I’ve run the Vista defragmentation program from the command prompt with the output set to analyze in verbose mode. The result is that 32 gig was scattered across 103 gig of a 160 gig. This means that if I only use the Vista Partitioning program, which is garbage, I can only play with Ubuntu and XP in the remaining 54 or so gigs of space. It’s no wonder that Microsoft removed the GUI from Vista’s disk defragmentation program; they do not want people to see what I see what I saw.

---

### Post by anoopjohn on 2008-01-11
Then perhaps you can try my method listed above :)
Anoop

---

### Post by ctoaun on 2008-01-11
> **woodcarver said:**
> My first question would be: Why do you want to triple-boot Vista AND XP?????
I would eliminate Vista and simply dual-boot XP and Umbuntu. Then search for drivers that will work in XP first, then work on the drivers for Umbuntu.

Vista is a bad "space-hog"!! Plus it is always connected to Microsoft, and there is no way to break the connection.

Just my opinion.

The reason for wanting to triple boot is as I stated. There are no XP drivers for this computer. It was purchased with Vista installed. If XP or Ubuntu is installed, none of the LAN, Ethernet, modem, sound or video drivers will work. Therefore, I wanted vista installed on a very small partition. Hopefully, someone knows of way to make them work for XP. IF so, then I can have games on XP and everything else on Ubuntu. 

Also, as I said before, all dual boot schemes hinge upon a computer that was originally sold with a XP operating system or a pre Windows XP OS installed. these schemes therefore do not work for a computer that was sold (new OEM) with Vista installed on it.

---

### Post by ctoaun on 2008-01-11
**To Mze and Virtuoso, thanks but...**
The problem with this is that my Vista DVD give me two choices: restore the disk to factory specs or repair an existing install. Also, I know of no Xp drivers for Vista, which means Ubuntu will most likely not run Vista drivers either. In other words, either run Vistas or nothing, and since Vista is a lot of nothing, I'd like to use XP for games and Ubuntu for all else. I see a lot of potential in it.

---

### Post by ctoaun on 2008-01-11
> **Mze said:**
> Quick search on the forum brings up this [thread]("http://ubuntuforums.org/showthread.php?t=220452")

The problem with this is that my Vista DVD give me two choices: restore the disk to factory specs or repair an existing install. Also, I know of no Xp drivers for Vista, which means Ubuntu will most likely not run Vista drivers either. In other words, either run Vistas or nothing, and since Vista is a lot of nothing, I'd like to use XP for games and Ubuntu for all else. I see a lot of potential in it.

---

### Post by ctoaun on 2008-01-11
> **anoopjohn said:**
> Then perhaps you can try my method listed above :)
Anoop

thanks, 

I think what I'll do is see if I can get live CD to boot and then go online via dial-up or broadband WIFI, which are my only options right now. My fear is that Ubuntu will not have the Vista drivers for the modems,  and thus, I'd be right back where I started.

I guess I'll let you know before Monday

---

### Post by Mze on 2008-01-13
Follow this [thread]("http://www.notebookforums.com/showthread.php?postid=2719828") to see if you can get the drivers in XP fixed after install.

---

### Post by ctoaun on 2008-01-13
> **Mze said:**
> Follow this [thread]("http://www.notebookforums.com/showthread.php?postid=2719828") to see if you can get the drivers in XP fixed after install.

Thanks a lot! :)

I've looked at the site, and it has potential. I think I'll bookmark it.

To be honest though, I may not need to do this. I spent the weekend trying to get wifi to work. I take wifi for granted!  No laptop is complete without it. A significant number of people would not buy a laptop without wireless.

I must say that I am very disappointed that this OS is not better equipped to deal with WFI, and I even more disappointed with its dialup woes, considering that it's now 2008.

This OS is shooting itself in the foot in terms of winning windows converts.

However, I do really appreciate your help, so again thanks

---

