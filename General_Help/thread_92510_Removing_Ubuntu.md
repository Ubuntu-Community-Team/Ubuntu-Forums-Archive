---
title: "Removing Ubuntu"
date: 2005-11-19
forum: General Help
---

### Post by Watcher on 2005-11-19
Ok, this is the problem. I recently insalled an ubuntu on a windows computer so that the machine became a dual-boot system. Now the person who uses the machine whises to get rid of the ubuntu and wants to make it back to a full windows machine. So far no problem I thought, I just format the disk and reinstall windows.

BUT on the windows part is so much information that making a backup of that information (and all the programs installed on it) is very well (or damn nearly) impossible.

So I was wondering if any of you knew how to just erase the linux part of the disk (deleting the linux is easy), and also how to get rid of GRUB (I heard that just erasing linux could get it go a bit (or not very) weird.

Once that is done, the rest will be a piece of cake using PartionMagic, but I am concerned about the GRUB thingie ... all ideas are very very welcome

---

### Post by lzfy on 2005-11-19
Boot from the original XP CD, when the files are loaded hit R. choose the Windows installation you want to restore and after that enter the admin password. now enter FIXMBR and say yes when it asks you if you're sure.

This will remove GRUB and restore the Windows bootloader. I hope this is what you mean.

---

### Post by Watcher on 2005-11-19
I will give that a try (your absolutly sure this will work?? Sorry to ask it agian, just don't want to screw this up, else there will be hell to pay ;) )

Another thing to just could do the trick is resizing the linux partition so that it takes 40gb (or 20) instead of the 80 it takes now, but I heard somewhere that it is impossible to resize them if mounted. So how do I do that then? Do I use PartionMagic, or could a clean reinstall of Ubuntu do the trick for me? (The Ubuntu is on a second HD with only 25Gb used by a windows which could be backedup on the first HD so a complete clean of the second HD is possible).

---

### Post by glib on 2005-11-19
Well you definitely don't want to be re-installing ubuntu just to uninstall it.

You're right that you can't resize a mounted partition, so you have to boot from a cd if you want to resize say your root partion of your ubuntu install.

If I were you, I would delete the linux partitions you have now and make one big new fat32 partition to fill the space. Then boot to the recovery console and fixboot to get the windows bootloader back. Use the other partition to store data, as that's generally a better idea to have your data on a separate partition from your os.

---

### Post by nuopus on 2005-11-19
[quote=glib]Well you definitely don't want to be re-installing ubuntu just to uninstall it.

You're right that you can't resize a mounted partition, so you have to boot from a cd if you want to resize say your root partion of your ubuntu install.

If I were you, I would delete the linux partitions you have now and make one big new fat32 partition to fill the space. Then boot to the recovery console and fixboot to get the windows bootloader back. Use the other partition to store data, as that's generally a better idea to have your data on a separate partition from your os.[/quote]

It is definately possible to resize a Windows partition if it has NTFS and there are a few programs that let you do it. Partition Magic and Acronis partition exptert are 2 of them. Arcronis adds something to the Windows NTFS partition (after first resize) that lets it be resized and only take a few seconds.

In linux we have parted that lets you resize also, and even has a gparted that lets you resize the NTFS partition. This is on the livecd I believe? Or was it the PCLinuxOS liveCD ... im not sure.

At any rate, getting rid of Windows and all programs just because you want to remove Linux is a bad idea ... just resize it. OR get rid of Windows and keep Linux.

---

### Post by yyagol on 2005-11-19
test

---

### Post by sarah_b on 2005-11-19
I  just recently resized a WinXP partition and then added a Linux distro on the same hard drive as WinXP with &#8220;Disk Drake&#8221;, which Mandriva uses as a partitioner tool (one of the best). I ran the Mandriva install CD until I resized the partition and then exited the install at that point. It worked out great, I have never had any problems but there can always can be an exception to this of course.

I believe though that one can not put WinXP on a hard drive that already has an operating system already on it.

---

### Post by Gadren on 2005-11-19
Even though I know very little about partitioning, I would truly recommend that before you do anything, you at least try to back up what you can.  If something goes wrong, it's better to have some of it saved than none of it...besides, I'd bet that most of the stuff are programs that can be reinstalled easily.

---

### Post by Watcher on 2005-11-20
Thanks for all the help, will try that tonight or tomorrow and i'll let you know how it went

---

### Post by thecosas on 2005-11-20
I am also attempting an uninstall of Ubuntu and running into some problems. 

I would like to be able to boot directly to Windows... is there any way to remove the dual boot option? I (foolishly) attempted to simply erase the Linux partitions and then redistribute the freespace. 

I forgot about the dual boot. 

Is there any way to get back to my old configuration (windows only), other than a reinstall?

I have reinstalled ubuntu, thinking there might be a way in which to solve this from the OS.

Edit: I just read above a bit more carefully... sorry for that guys. Again, missing the details haha.

---

### Post by nuopus on 2005-11-21
[quote=thecosas]I am also attempting an uninstall of Ubuntu and running into some problems. 

I would like to be able to boot directly to Windows... is there any way to remove the dual boot option? I (foolishly) attempted to simply erase the Linux partitions and then redistribute the freespace. 

I forgot about the dual boot. 

Is there any way to get back to my old configuration (windows only), other than a reinstall?

I have reinstalled ubuntu, thinking there might be a way in which to solve this from the OS.

Edit: I just read above a bit more carefully... sorry for that guys. Again, missing the details haha.[/quote]

Well there are 2 ways of doing it. Either boot into a DOS disk with fdisk.exe and type fdisk /mbr or boot into a WinXP command line session and type fixmbr.

---

### Post by adam.tropics on 2005-11-21
take it you have windows disk? many newer machines come with just system restore disk, which would be fine as it deals with the mbr issue, however it doesn't resize the remaining space, in which case you'd probably then be best off using the dos boot disk with fdisk, wiping the lot, and doing a fresh install on blank drive.

Btw, I'm sorry to see people leaving us!

---

### Post by nuopus on 2005-11-21
[quote=adam.tropics]take it you have windows disk? many newer machines come with just system restore disk, which would be fine as it deals with the mbr issue, however it doesn't resize the remaining space, in which case you'd probably then be best off using the dos boot disk with fdisk, wiping the lot, and doing a fresh install on blank drive.

Btw, I'm sorry to see people leaving us![/quote]

The Ubuntu 5.10 Live-CD comes with gparted which can resize NTFS pretty good. You dont have to re-install Windows just because you want to make the partition bigger. If you dont want to use gparted, use the command like parted or commercial Partiton Magic or Acronis Partition Expert.

For the sake of clearing the MBR, use the /mbr switch with a DOS fdisk or the fixmbr program in a winxp command prompt boot.

---

