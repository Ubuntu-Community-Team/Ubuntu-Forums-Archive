---
title: "Dual Boot problems - Ubuntu 9.04 and XP"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by en5ads on 2009-08-31
Hi, 
I appear to be stuck. I have two hard discs, my primary which is partitioned into 4, containing XP, a Dell Utility partiton, a partition for storage and a ext2 partition that used to have Suse. I wanted to try Ubuntu so I used the standard installer. It formatted the Suse partition and put Grub in the MBR, but following reboot, all I got was 
" 
Grub loading, please wait.
Error 17
"
 So after some panicing last night I reinstalled a windows MBR and got back into Windows. Once bitten twice shy and so I thought I would use the windows bootloader and grub in the root of the linux partition, copying the boot sector image over. 
I did something like; 
grub
find /boot/grub/stage1
root (hd0,2)
quit
dd if=dev/sda3 of=mnt/Win_XP/linux.bin bs=512 count=1
and edited the boot.ini in Windows. 

But now all I get is GRUB GRUB GRUB when I select the linux partition. I hope someone can help...

I have attached what appears to be useful info from a script referenced in another post. 

Thanks

Anthony

---

### Post by ronparent on 2009-08-31
I don't know where it all went wrong, but, results.txt appears consistent with what you have said. I would try to setup grub again - this will rewrite the MBR with grub but it seems you know haw to recover the windows MBR should it be necessary. 

Booting from the live cd open a terminal and do this routine again:

[B]grub
find /boot/grub/stage1
root (hd0,2)[/B]

Then continue with:

[B]setup (hd0)
exit[/B]

If the results.txt is accurate you should now be able to boot all of your OS's from grub. Have fun.

---

### Post by en5ads on 2009-08-31
Okay, thanks. I'll try ...  It might be a while, the computer is used a fair bit.

Anthony

---

### Post by en5ads on 2009-08-31
Hi, 
Had a bit more time than I thought but it didn't work

I got
"GRUB loading stage 1.5
Grub loading, please wait ..
Error 17
"

I collected another results.txt file before I rebooted. 

Anthony

---

### Post by ronparent on 2009-08-31
You may be getting grub error 17 because of a bios limitation. In effect it limits grubs ability to find the grub files if installed in sectors beyond its reach. This leaves two alternatives. 1)install grub in sectors close enough to the beginning of drive for the grub MBR to find it (2 play around with the hd options in bios to see if another option will enable grub to find the grub files. You can implement the first choice with an existing partition as long as it is not formatted ntfs. I don't think you have the capability to setup a small dedicated grub partition because that would exceed an alowable limit of four primary partitions on your drive.

---

### Post by raymondh on 2009-08-31
> **ronparent said:**
> You may be getting grub error 17 because of a bios limitation. In effect it limits grubs ability to find the grub files if installed in sectors beyond its reach. This leaves two alternatives. 1)install grub in sectors close enough to the beginning of drive for the grub MBR to find it (2 play around with the hd options in bios to see if another option will enable grub to find the grub files. You can implement the first choice with an existing partition as long as it is not formatted ntfs. I don't think you have the capability to setup a small dedicated grub partition because that would exceed an alowable limit of four primary partitions on your drive.

@ Ronparent, you might be thinking about [error 18]("http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors")

Error 17 is when GRUB cannot recognize the filesystem type hence, will not mount/boot into it.

@ en5ads,

-  You are booting into the 1st HD (where you installed ubuntu and GRUB), right?
-  You did choose a linux filesystem?
-  In your BIOS, can you set AUTO DETECT to ON.  For access mode, change settings from CHS to AUTO.  If those do not work, try USER instead of AUTO.
-  Another tip is to run a [filesystem check]("http://members.iinet.net/~herman546/p10.html#Running_a_filesystem_check_with_GParted_") on your Ubuntu install using gparted from the liveCD.

Hope one of those tips work. Here's Herman's take on error 17.

[http://members.iinet.net.au/~herman546/p15.html#GRUB_Loading_stage1.5_Read_Error](http://members.iinet.net.au/~herman546/p15.html#GRUB_Loading_stage1.5_Read_Error).

Good luck.

---

### Post by en5ads on 2009-09-01
- You are booting into the 1st HD (where you installed ubuntu and GRUB), right?
>> Yes, I don't have a bootable second harddrive
-  You did choose a linux filesystem?
>> Yes, sda3 has ext2 (you can see this in my attached files)
- In your BIOS, can you set AUTO DETECT to ON. For access mode, change settings from CHS to AUTO. If those do not work, try USER instead of AUTO.
>> I have a fairly old Dell 4550 and this doesn't have many options. I had already tried turning off the second harddrive and this didn't make any difference. I basically can choose auto or off for each harddrive, so I think I have exhausted all the options. 
-  Another tip is to run a [filesystem check]("http://members.iinet.net/%7Eherman546/p10.html#Running_a_filesystem_check_with_GParted_") on your Ubuntu install using gparted from the liveCD.
>> Done and no errors detected. Didn't make any difference. 

I think my most likely chance of success is either to reformat perhaps with a different filesystem type (say ext3) or move the partition closer to the front of the disc. However, if anyone has any other suggestions that take a little less time, I'm happy to listen. 

One other thing I'm going to try is a manual boot following the advice in Herman's webpage. It might give me a few pointers. 

Anthony

---

### Post by en5ads on 2009-09-01
Fixed it!
I tried a grub boot disc and it couldn't see hd0,3 and hd0,4; returned unknown filesystem, with drive biosdisk. I checked my bios and there was an update (from A03 to A08 ). Once I installed that my original method of booting from the windows boot menu worked fine. So I guess some problem addressing drives above a certain size. 

Thanks everyone. 

Anthony

---

### Post by ronparent on 2009-09-01
Considering what I saw in your results.txt, that seems to be most likely cause. In any event it's great news your'e back in business.

---

