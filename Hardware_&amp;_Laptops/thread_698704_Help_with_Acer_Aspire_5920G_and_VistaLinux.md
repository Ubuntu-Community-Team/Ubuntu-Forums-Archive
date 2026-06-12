---
title: "Help with Acer Aspire 5920G and Vista/Linux"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by jhetfield17 on 2008-02-16
Hi I recently bought an Acer Aspire 5920G and I've been switching over distros cause of some probs but the thing is that since acer doesn't give a recovery cd with the laptop,laptops have one or two secret recovery partitions which isn't bothersome as an idea,but they both are primary partitions and since the vista partition is also a primary we have a total of 3 primary partitions.So whenever I try to manually make a swap and a root partition,it only lets me make one primary and the other is of some other kind but its neither logical or primary its something else.
So I'm wondering would it be ok to just delete the two secret recovery partitions since I have already made a copy of the recovery cd and then make the swap and the root partitions both primary?Or do I have to format everything and make a new windows partition and the linux ones?You probably have guessed that I want to avoid format and you're right.can I avoid it????

---

### Post by overdrank on 2008-02-16
> **jhetfield17 said:**
> Hi I recently bought an Acer Aspire 5920G and I've been switching over distros cause of some probs but the thing is that since acer doesn't give a recovery cd with the laptop,laptops have one or two secret recovery partitions which isn't bothersome as an idea,but they both are primary partitions and since the vista partition is also a primary we have a total of 3 primary partitions.So whenever I try to manually make a swap and a root partition,it only lets me make one primary and the other is of some other kind but its neither logical or primary its something else.
So I'm wondering would it be ok to just delete the two secret recovery partitions since I have already made a copy of the recovery cd and then make the swap and the root partitions both primary?Or do I have to format everything and make a new windows partition and the linux ones?You probably have guessed that I want to avoid format and you're right.can I avoid it????

HI and I would suggest resizing vista from within vista and then you can use the extra space to create a extended partition and this will allow you to create your swap and root and even a home if you like. :)
Edit a good link on partitions
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by jhetfield17 on 2008-02-17
Yes but that still doesn't answer my question.I'm asking about what to do with the two secret recovery partitions from vista that take up primary partition slots.I don't want to resize vista I have plenty of free space but I can't use it for some reason.And then there are the two secret partitions that also aren't being used nor do they have a meaning to be cause I have burnt a recovery dvd.How to erase them is my question.Is  it ok to erase them with the partition managers of either a distro or a windows installation????Or do I have to erase everything and format the whole disk and then make the partitions that I want???

PS:I'm looking for an answer that doesn't include formatting the disk if possible.If not,(swearing)I don't have a choice.

---

### Post by AJB2K3 on 2008-02-17
As vista is pointless on laptops (needs more power then the alptop can give and you cant do anything with a native install) I just deleted all partitions and started from scratch

---

### Post by jhetfield17 on 2008-02-17
Look to end this vagueness I vouln't be more supportive of your doing AJB2k3 but the thing is that I don't want to mess with the windows on the laptop cause Acer found it really fun not to publish XP drivers for my lappy model so I can't do much about it.But I just want to get rid of the two secret partitions so that I can make my Linux partitions primary and finaly use all the rest to make a big NTFS Spare parition usable by both Linux and Windows.How can I do this without formatting the drive???Can't I just delete them and use all the space???Or is it gonna make a prob????

---

### Post by spegru on 2008-02-23
I hope I can assist this thread by being more useful - although I dont have a complete answer yet.

I too have an Acer Aspire 5920G, bought recently from PC World in the UK

It's quite amazing the amount of Crapware that come preinstalled (including the 60day trial/honeypot trap of Office 2007 that's designed to get people to create docx format documents that they later wont be able to open without paying P$FT 400 quid!!!)

Anyway. It doesn't come with any Discs at all so you _must_ use the Acer backup utility if you want to be able to recover vista from any problems when installing Linux (which you obviously should do!)


jhetfield17 is correct that there are hidden partitions on the disk. I suspect that these have been put in specifically to make it difficult to install Linux, because you cannot create enough new primary partitions.

I've now had two goes at installing Linux in a dual boot config with vista, without success. I can get Linux working but then vista does not boot and I have to use the recovery discs and start everything again from scratch

I have found that deleting the hidden partitions using gparted still allows vista to boot, but if I move the vista partitions to make more continuous space on the disk for linux, vista then fails to boot (continuous starting to boot, and then restart every few seconds)

So far I have not tried leaving the partitions where they are, but I will do that next after my latest recovery!

hope this helps a bit

spegru

---

### Post by spegru on 2008-02-23
Hmm my vista recovery has been a problem. 
I got 'Type Mismatch' error from vista and it just stopped
So I wiped all partitions but got the same error again

Then I tried formatting the whole disk as ntfs - and it then worked OK in vista 
(I didnt try Linux yet)

But here's the thing. There is now only one partition!
Also I can't create another Backup disk (which is annoying as I was hoping to make one without all the crapware and with Openoffice Firefox etc etc)

I think I saw in another thread that the Acerbackup uses a FAT32 partition, not NTFS (which is also what I saw when I started this process) so my next ploy is to resize vista and install linux, making sure I also create a FAT32 Partition.

I hope everyone appreciates the running commentary!

spegru

---

### Post by spegru on 2008-02-23
I've now reinstalled vista (using the recovery discs I made when I first got the machine) **and** installed PC Linux OS for the first time! 

(I stuck with PCLOS because I prefer KDE and because the wireless worked without me doing anything - this is the wrong forum really I guess but I expect the same process will apply for Ubuntu)
 
I first created a NTFS partition and a FAT32 partition (about half the disk each) first using gparted, and so avoided the 'Type Mismatch' error from the Vista recovery disc and and so got a contiguous partition for Linux to use **and** got it to boot in vista

After the vista recovery install there were only two partitions rather than the original 4: The Vista NTFS one and the FAT32 one

Then I resized the partitions so that NTFS was about one third, FAT32 was about 1 third and the final third was empty. This worked much better than resizing the original Acer Partition setup because it didn't need to move the vista data since that was now at the beginning of the disc rather than half way up as it was before (it just needed to move the empty end of the partition to make room for the empty FAT32 and the empty space for Linux at the end of the disc). I'm not sure I needed 3 partitions really but at least this way I will be able to look at the exact same files in the FAT32 partition with either Linux or Windose - a bit  like having a internal USB drive

However the Acer recovery utility has now disappeared so I cannot create a new set of recovery discs. However I think that's deliberate M$FT crapness becuase I have another Laptop that I put Kubuntu onto, and the vista would only allow one backup - ever (it actually said that!)

Anyway I seem to now have a dual booting Acer Aspire 5920. It's been a huge task of trial and error, taking at least 3 full days - but I got there in the end!

I guess/ hope that's it now. The only other things that might be worth experimenting with different partition sizes for the three sections

Bye now

spegru


**DISCLAIMER:** DO NOT FIDDLE WITH PARTITIONING UNLESS YOU KNOW WHAT YOU ARE DOING AND MAKE SURE to MAKE YOUR VISTA BACKUP DISCS (using the Acer utility)  IF YOU EVER WANT TO SEE IT AGAIN


spegru:guitar:

---

