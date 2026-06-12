---
title: "Installation confusion"
date: 2006-01-01
forum: Installation &amp; Upgrades
---

### Post by DoctorLes on 2006-01-01
Hi,

I burned an ISO install disk for Ubuntu 5.1 after downloading the file a couple of days ago.  It boots up nicely to the installation assistant and finds all my hardware and such.  But I get confused when it runs the partition app.

It shows my two physical drives, both 40 Gigs.  They are hooked-up in an unusual relationship, using a toggle switch I mounted on my case cover.  One position has Win '98 on it and the other has Fedora Core 3.  I can boot either Win '98 or FC3 by throwing the toggle switch, so long as it's before hitting the power button. 

OK, now the partitioner seems to identify both of my drives, even though I thought the toggle switch might prevent that--apparently not.  As best I can recall, the toggle switch uses an old jumper with leads attached, salvaged from some dead 486 box years ago.  I believe it shorts the master/slave option, but I may be wrong; haven't been able to find the schematic for the hack that I used.  

Anyway, I'm showing about 109 MB in the primary of one of the HD's, according to the partitioner.  

I want to keep Win '98 on the one, seperate, physical hard drive, so I can still toggle it on during those rare occasions I want to run Win '98 (I would have wiped it, but I'm afraid I have some old apps, or files on it that I don't want to lose, including passwords and activation keys and such). 

But I do want to divide the other hard drive, the one that already has FC3 on it, so I can dual boot either FC3 or Ubuntu. I am not particular otherwise, and am OK with dividing whatever space there is right down the middle.  Of course, I don't want to lose a byte of my data from my FC3 installation either ;)

So, given the options I visualize on the partitioner window, which should I choose to meet my goal?  Would you mind walking through each step?

Thanks very much for your time.

And Happy New Year!

---

### Post by encompass on 2006-01-01
umm, so you ant to resize the win98 partition to fit ubuntu on it?  if so... I think ubuntu does resizing of partitions... when looking at the partitions with the installer, you should see that it is Fat32 or 16 or something like that.  if it is... then you know you have the win98 disk.  Otherwise... you probably will see ext3 or something like that for the linux FC3 install.  If you want, I can try to help you.... but no promises.:???:

---

### Post by az on 2006-01-01
You have a very unique way of dual booting.  The fact that you are surprised that the installer detects both drives is worrysome.  If it is not working exactly like you thought it should, then you may be running the risk of data loss.

Anyway, the ubuntu installation wil partition and detect the other operating systems on your setup.  It will add them to the grub menu and you will be able to pick which os you boot when you power up.  This method is very very safe.  I would recommend using that instead of your current toggle switch.

---

### Post by DoctorLes on 2006-01-02
Hello Again,

Thanks for the info and patience.

I've decided to try to install Ubuntu on my first drive (hda) maxtor 40 GB.  But the partitioner app is still very confusing to me; all the options seem to suggest my Fedora Core 3 will be erased.  This is what I get:

IDE Master (hda) -41 GB Maxtor 

#1 Primary 106.9 MB (funny, downpointing lightening arrow symbol) smiley face, ext3/ media /hda

#2 Primary 39.5GB smiley face symbol, ext3/media /hda

#3 Primary 1/3 GB down arrow, skull symbol, swap

I checked my total HD used space in terminal, on FC3; I'm using about 52% total space.  

What I'd like to do is divide up the remaining space between Ubuntu and FC3, and install Ubuntu into a new partition made from the half of the remaining disk space.  

The menu in the partitioner is ambiguous and implies it will wipe all my files from the #2 Primary partition if I partition it.  

Can someone just tell me what steps to take within the partitioner I should take to reach my goal???

TIA, once again

Les:confused:

---

### Post by az on 2006-01-02
[QUOTE=DoctorLes]
Can someone just tell me what steps to take within the partitioner I should take to reach my goal???

:[/QUOTE]
Well, since the partitioner thinks it is a 109 Gig drive and you say it is a 40 gig drive, I would not continue with the installation.  Probably your unique setup is confusing the ubuntu installer, or the FC installer corrupted the partition table for whatever reason.

You can manually partition the drive by picking that option in the installer menu, selecting your FC partition and entering a smaller size for it.  Once shrunk, you will see FREE SPACE as part of the partition table.  Scroll back up and pick Guided Partitioning and the installer will do the rest of the work in making the partitions you will need for ubuntu.  You will then press yes to make it create them.

But, again, since the installer is not detecting your drives properly, there is a problem, and I would not proceed until I fixed it.

---

### Post by DoctorLes on 2006-01-02
No, the partitioner is seeing 109 Mega Bytes, not Gigs, of the total 40 GB.

But I can't seem to manually enter any other figure anyway

---

### Post by az on 2006-01-03
[QUOTE=DoctorLes]
But I can't seem to manually enter any other figure anyway[/QUOTE]

Which partition?  You cannot enter a smaller number for the second (39 gig) partition?

---

