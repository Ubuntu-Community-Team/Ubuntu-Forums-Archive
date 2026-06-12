---
title: "Install Order - Ubuntu, XP and 7"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by goodvikings on 2009-09-21
Hey everyone
 
I'm about to set up a new computer triple booted with Ubuntu 9.04 (or 9.10 depending on when I get around to it...) winXP and win7. I had some issues previously when installing XP on a laptop that came with Vista, relating to the fact that XP needed to be installed first.
 
Is there a order of installation I need to use, and at what point would I install grub?
 
Thanks in advance
 
Damian

---

### Post by pastalavista on 2009-09-21
I don't believe it matters which Windows is installed first because the Windows boot loader recognizes other Windows installations. But be sure to install Ubuntu last because Windows won't recognize a Linux filesystem and you would have to reinstall grub to get them all to work.

---

### Post by dentharg on 2009-09-21
Win XP, then Win 7, then Ubuntu.
Windows 7 should detect Win XP and Ubuntu will detect both.

---

### Post by goodvikings on 2009-09-21
Cheers guys. XP, 7 then ubuntu it is.

---

### Post by mk4umha on 2009-11-20
Did that work out for you?

My install order was Win7, XP, then Ubuntu. Grub sees XP as Win7 in the menu. I guess I'll have to reinstall AGAIN jsut to get it to work since I need WinXP and Win7 to work.

---

### Post by dentharg on 2009-11-20
hmm.. What happen if you boot into Win7? Doesn't it show anything to start Win XP?

What entries does `update-grub` show?

---

### Post by mk4umha on 2009-11-20
Well, it has the ubuntu, memtest and win7 options. If i pick win7, it goes into XP. I went ahead and nuked the xp and win7 partitions. i'm reinstalling xp first, then win7, then going to boot into the Live CD and rerun grub2 to see if it finds both all 3.

---

### Post by oldfred on 2009-11-20
Win7 combines its boot loader with XP, so only one windows boots and then you choose from that. You cannot then directly boot from grub to both windows.

One workaround I saw but have not seen anyone confirm was to turn off the boot flag on the first windows install. The second install will not see the first and installs standalone. You then cannot boot both windows from windows but can from grub.

Both windows have to be in primary partitions. Some installs of win7 after XP will install to a logical partition and will work only because the boot is really from the XP install in the primary partition.

Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

---

### Post by mk4umha on 2009-11-20
What's the quick/easy way removing the boot flag on the partition?

---

### Post by oldfred on 2009-11-20
I only know gparted, but I bet the command line partition tools can do it also, but I have not had a need nor checked.

---

### Post by mk4umha on 2009-11-20
Ok, thanks, i'm going to try that method now. I know if you install XP then win7 then ubuntu it will work. as you said, win7 and xp do not show up in grub menu. I would like win7 and xp to show up on the Grub menu so i'll see if turning the boot flag off will work.

---

### Post by Perturbed Penguin on 2009-11-20
I believe if you want both Windows partitions to show up on GRUB you have to manually add them because GRUB only automatically adds the Windows 'vista boot loader' which then contains all of your Windows partitions... or at least it ought to I thought. I forget how exactly to manually add your partitions - and it will be slightly different now than when I did it because Ubuntu 9.10 uses GRUB2 which is slightly different. Look around though for how to manually add each individual partition to GRUB's list. On a side note I am not certain why the vista loader isn't recognizing both of your Windows partitions I am pretty sure I have gotten it to work with XP/Vista in the past... perhaps Win7 has a slightly different version of the 'vista boot loader'?

---

### Post by linux-hack on 2009-11-20
> **dentharg said:**
> Win XP, then Win 7, then Ubuntu.
Windows 7 should detect Win XP and Ubuntu will detect both.

this way grub will take over

---

### Post by wilee-nilee on 2009-11-20
> **Perturbed Penguin said:**
> I believe if you want both Windows partitions to show up on GRUB you have to manually add them because GRUB only automatically adds the Windows 'vista boot loader' which then contains all of your Windows partitions... or at least it ought to I thought. I forget how exactly to manually add your partitions - and it will be slightly different now than when I did it because Ubuntu 9.10 uses GRUB2 which is slightly different. Look around though for how to manually add each individual partition to GRUB's list. On a side note I am not certain why the vista loader isn't recognizing both of your Windows partitions I am pretty sure I have gotten it to work with XP/Vista in the past... perhaps Win7 has a slightly different version of the 'vista boot loader'?

You install XP then W7 then Linux when you choose the vista boot it takes you to the Windows bootloader where you have the choice of XP or W7.

---

### Post by underquark on 2009-11-20
Out of interest (i.e. nosiness) , why is XP needed?  If it's a minor player in your setup then you could install Win7 and then ubuntu and run XP in a virtual machine (in either of the main OS's).  I once quad-booted with Windows something, Windows something else, Linux (Dapper Drake, I think) and BeOS installed just because I could rather than because I needed to.  Heck of a messy hard disk partitioning.

---

### Post by mk4umha on 2009-11-20
I was hoping to pick the OS's all inside grub without layering 2 boot menus.

---

### Post by wilee-nilee on 2009-11-20
> **underquark said:**
> Out of interest (i.e. nosiness) , why is XP needed?  If it's a minor player in your setup then you could install Win7 and then ubuntu and run XP in a virtual machine (in either of the main OS's).  I once quad-booted with Windows something, Windows something else, Linux (Dapper Drake, I think) and BeOS installed just because I could rather than because I needed to.  Heck of a messy hard disk partitioning.

A virtual is the best idea but you would need at the least 2 gigs ram for it to not be slowed down. W7 runs very well with 2 gigs ram.

---

### Post by mk4umha on 2009-11-20
OK, I got XP, Win7 and Ubuntu to show up on the Grub2 Menu.

First, I had to make Three Primary Paritions, one for XP one for Win7, One for storage so both XP and Win7. The rest of the drive is extended partition. Inside extended partition, I had for swap, "/" "/home" etc.

I install XP on to the first primary partition, after it's finished, boot into the Live CD and remove that parition Boot Flag.

Then i installed Win7, Then Ubuntu. After that Ubuntu picked up all 3 OS's and I can select which one I want to boot to with no issues.

---

### Post by oldfred on 2009-11-20
Glad to hear it worked,:p

---

### Post by Perturbed Penguin on 2009-11-20
Great, glad you got things working and that is good to know that you have to remove that boot-flag! ;)

---

### Post by mk4umha on 2009-11-21
> **underquark said:**
> Out of interest (i.e. nosiness) , why is XP needed?  If it's a minor player in your setup then you could install Win7 and then ubuntu and run XP in a virtual machine (in either of the main OS's).  I once quad-booted with Windows something, Windows something else, Linux (Dapper Drake, I think) and BeOS installed just because I could rather than because I needed to.  Heck of a messy hard disk partitioning.

The software I am trying to run uses Direct3D or something and when i try runing it in VirtualBox winXP, it crashes. If i try to install it under Win7, it bitches about it. So i'd rather just triple boot. :)

---

### Post by xsever on 2009-12-23
> **mk4umha said:**
> 

I install XP on to the first primary partition, after it's finished, boot into the Live CD and remove that parition Boot Flag.


Could you please specify how you removed the partition boot flag ?

Thank you,

---

### Post by oldfred on 2009-12-23
You can use gparted or

    #make a partition active ("makeactive" in grub legacy)
    parttool (hd0,4) boot+

    #remove active flag from a partition
    parttool (hd0,3) boot-

Make sure you only have one boot flag set per hard drive. Windows relies on the flag and cannot see 2 flags. to see partitions and which has flag (*).
sudo fdisk -l    (el - l, not one- 1 or cap eye I)

---

### Post by Parachutee on 2009-12-23
I just installed Ubuntu. I erased the drive and deleted the Windows xp I had on it before. After I install the Ubuntu, I can't get it to boot up from the hard drive. I get a error message that says " loading Grub, error 57081d47-3977-4177-bced-d5e5a397a5a4.. Failed to boot default entries". So can someone help me, oh yeah I am doing the install with a cd.

---

### Post by oldfred on 2009-12-23
Parachutee - since this thread is solved, although the OP did not change the title not many will look at this. You also have a different problem and should post your own new thread with as much info as you can. 

See also this similar thread for suggestions on what to post:
[http://ubuntuforums.org/showthread.php?t=1360385](http://ubuntuforums.org/showthread.php?t=1360385)

---

### Post by ddddddddd on 2010-08-08
Nvm

---

### Post by topet2k12001 on 2010-12-24
Verified working. :) Now I have a multi-boot setup. :)

---

### Post by ottosykora on 2010-12-25
I have XP, w7, w98se, ubuntu, fedora, debian on one drive on an old laptop.

The original installation was XP.

Then I created extra small partition for grub only at the end of the drive.

Used the gparted , in fact parted magic cd, to set the boot flag and hide unhide the partitions during the installation procedures.

Before installing w7, I had to hide the xp and w98se partitions from gparted and set the bootflag to the w7 partition. Installed the w7 then there.
Hide w7, unhide w98, set w98 bootable, install w98.
all linux then in extended logaical partitions, each of them having its grub installed ***in its root partition***

At the end, copied grub(legacy) files from one ubuntu to the grub partition and used supper grub disk to install the MBR part of the grub and let it find the other stages in the separate grub partition.

Then edited the menu.lst in the grub partition (all done with the parted magic CD which contains all needed) .

This way I am not dependent on any of the linuxes installed, I can delete some ofthem and the rest will still work as before.

---

### Post by love_linux1 on 2011-07-24
Which installer should I use? 

Ubuntu-11.04-desktop-i386.iso or Ubuntu-11.04-desktop-amd64? I have a 32-bit intel pc. 

Which one is called natty narwhal?

thank you.

---

### Post by Anraz on 2012-07-11
To summarize I did do what mk4umha said.  And I confirm it to be working.  So I had to look at how it was setup to work and here is how it does it.

Before doing it this way I kept failing and could only boot to windows 7 and ubuntu.  But now I see exactly how it works and I can explain what I am viewing.

The boot flag is set on the windows xp /dev/sda1
win7
storage
are doing nothing but holding OSes.
My extended stats blank; but ext4 usues it as a logical then I have a linux swap partition.
I truly believe I could if I had to... Would if just set the windows xp partition with the flag and then did a gparted-update.  However I was hardheaded all of those failed installs working with BCDEDIT and EasyBCD.  However many thanks to: mk4umha

---

### Post by wildmanne39 on 2012-07-11
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

