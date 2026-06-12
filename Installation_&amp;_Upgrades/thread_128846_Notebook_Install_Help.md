---
title: "Notebook Install Help"
date: 2006-02-12
forum: Installation &amp; Upgrades
---

### Post by SVFUSiON on 2006-02-12
I have install ubuntu on my desktop and i enjoy it so much I don't want to be away from it :p I want to install it on my notebook but I am not sure what the partiton sizes need to me, This is going to be a dual boot with Windows XP Home SP2, It is a 40 GB Hard drive, I want to give nix 10GB, but I am not sure what the swap and all of that needs to be. I have not had real good luck with the Ubuntu partiton manager in the installer so that is why i come here to make sure I don't lose anything this time :P . Also, will Ubuntu install a boot loader and deteat my xp install automaticly or do I need to set that up manually?
Thanks!
svfusion
(tux is my pet)

---

### Post by nurdin on 2006-02-12
[QUOTE=SVFUSiON]I have install ubuntu on my desktop and i enjoy it so much I don't want to be away from it :p I want to install it on my notebook but I am not sure what the partiton sizes need to me, This is going to be a dual boot with Windows XP Home SP2, It is a 40 GB Hard drive, I want to give nix 10GB, but I am not sure what the swap and all of that needs to be. I have not had real good luck with the Ubuntu partiton manager in the installer so that is why i come here to make sure I don't lose anything this time :P . Also, will Ubuntu install a boot loader and deteat my xp install automaticly or do I need to set that up manually?
Thanks!
svfusion
(tux is my pet)[/QUOTE]

I've got Ubuntu on my laptop, I recommend 3 partitions: root, swap and /home my root partition is 10 gigs but only 2.3 gigs are used so you're better of going for 2.5-4 gigs to have a little room left over.  The rule (or guideline rather) for swap is to have 2*RAM so if you have 512 mb ram, use 1 gig. As for home make that as big as you want to use.

So here is what I would do in your situation:
20 gig winxp
4 gig root
1 gig (assuming you have 512 mb ram) swap
15 gig home

When installing ubuntu you are going to want to manually partition your harddrive and resize the winxp drive, (thats what I do, I believe there is a regular option to resize but I haven't used that) and then make those new partitions. Also ubuntu installs grub boot loader which detects windows xp so you don't have to worry about that. 

GOOD LUCK

---

### Post by SVFUSiON on 2006-02-14
When I got to the partion part it wanted to use 25GB of my HD, I only have 13.00 GB free, so if I did that my windows partition would be gone. It would not let me change the size manually, when I put in something like 10.00GB, it said "Partiton too small" Any ideas, thanks for your help and support. :)

---

### Post by SVFUSiON on 2006-02-14
anyone ?

---

### Post by wint on 2006-02-15
You must divide your HDD manualy in installation proccess...
Then Ubuntu-setup Will ask you how to divide disk, you must select some like "manual"... Next you'll see dialog box there you can choose partitions of your HDD...
From free space avable on you HDD you need to create first swap partition (1 Gb) root partition with mount-point '/' and if you want your own partition '/home'
Like My_Documents in XP...

---

### Post by jcaceres on 2006-02-15
What i did ..on a 60GB HDD :-k 
on xp with "partition magic" shrinks the windows partition to 15GB. I create a partition FAT32 of 25GB, and let 20GB free.
After that, i install ubuntu on 20GB partition. 2GB of swap.:p  
The partition FAT32 allows you share files between linux and windows. You could create a document o copy an mp3 file, and change o erase them on both plataforms.:rolleyes: 

with FAT32 you loose some advantages of ntfs of XP, but who cares :twisted:  !!! . 
I mount the fat32 partition only to my user..
That's it....

---

