---
title: "Win7 wont boot after delete ubuntu"
date: 2014-04-09
forum: Hardware
---

### Post by animeredskin on 2014-04-09
Hey guys I'm in total panic mode right. Last night I installed a program to delete partitions. I deleted all the patitions on the backup harddrive (ubuntu was installed on it) I had Ubuntu on the backup and i had Fadora. So I deleted all partitions on backup hardrive so that should get rid of ubuntu and Fadora right? SO today when i start up my computer it has a black screen and says " error: no such device: 399d5061-3cd6-45b8-8b5a-fae702e83031.
Entering rescue mode...
grub rescue>  _ 
How do I get back to Windows 7 whats going on!? I cant get to windows 7 it just keeps on loading up to the black screen! I deleted all the partitions on backup so why cant i boot up windows 7 i deleted ubuntu and fadora not windows 7 why wont it boot! Please help!

*_**[COLOR=#ff0000]Every single secound that goes by... I crinkle up wondering if I Dun Goofed Help .-.[/COLOR]**_*

---

### Post by oldfred on 2014-04-09
If it was a default type install, grub was loader to sda. But if Ubuntu was on sdb, you really should have kept grub on sdb and changed BIOS to boot from sdb.

You can just use your Windows repair CD or Flash drive to run fixMBR command. Which you should have, but have to make yourself or pay for it, if not.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Or you can use your Ubuntu live installer DVD or flash drive to install a Windows work alike boot loader that will boot Windows.

      
 How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

   Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub

      
 Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader to boot partition with boot flag (Windows).

Or just use Boot-Repair which you can install into your Ubuntu installer, or download as a full repair ISO as its own flash drive.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

