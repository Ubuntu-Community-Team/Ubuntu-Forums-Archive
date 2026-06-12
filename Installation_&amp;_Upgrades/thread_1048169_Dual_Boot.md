---
title: "Dual Boot"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by lotusalive on 2009-01-23
I have reinstalled 8.10 with a Primary Fat32 partition so that I can run a Windows XP Dual Boot, but when I try to install W's from the disk, my PC goes straight to grub, ignoring my request with F10 to boot from the W's disk.  What am I doing wrong?  Thanks in advance for looking at this.

---

### Post by Sef on 2009-01-23
> I have reinstalled 8.10 with a Primary Fat32 partition so that I can run a Windows XP Dual Boot, but when I try to install W's from the disk, my PC goes straight to grub, ignoring my request with F10 to boot from the W's disk. What am I doing wrong? Thanks in advance for looking at this.

1) XP should be installed upon an NTFS partition.   

2) Have you checked your BIOS to make sure it is set to check the CD-Rom/RW before the hard drive?

---

### Post by lotusalive on 2009-01-23
Thank you Sef.  I was planning to change the partition to NTFS once I get to the W's Install disk.  Was told that was possible, is that right?  Thanks.  I'll go check the BIOS and check back.  Thanks alot.:D

Yes, the BIOS was set and is set to boot from DVD drive first, so I'll try it again...

Wouldn't do it on that attempt either.  Any suggestions welcome.

---

### Post by caljohnsmith on 2009-01-23
Can you boot any CD in your CD/DVD drive? Have you tried your Ubuntu Live CD? If that boots OK, then it sounds like the problem would be with your Windows CD, not your drive or BIOS settings.

---

### Post by lotusalive on 2009-01-23
Yep, must be the disk, since I re-installed 8.10 from disk just fine, and 

made my partitions in the correct order: 1:W's,Primary,used gparted to change from 

Fat32 to NTFS(!)  2:swap,swap  3:root,logical,ext3  4:home,logical,ext3   

5:data,logical,ext3  Please let me know if anyone sees anything wrong with this, 

would you??!!  

Thanks caljohnsmith for your input...  


I've changed the Fat 32 into an NTFS partition.

I've downloaded Sun's correct Java app, but not installed it yet.

I've downloaded Sun's VirtualBox and installed it.  Should I try installing W's there instead of Dual Booting?

I just got my dvds to play with VLC with code I got from TheOzzLives on another thread!  Thank you TheOzzLives!

Lots of questions here still, if anyone cares to take a look on how I should install XP...

---

