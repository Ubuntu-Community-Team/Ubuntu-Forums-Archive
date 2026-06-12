---
title: "GRUB not working, not installed ?"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by Hagar55 on 2009-09-10
I had Jaunty in dual boot with XP (on different drive then the XP install).
I decided to try karmic , so I restored the MBR with the Xp installatino diskt.Now I wanted to install Karmic with ext 4 so I booted the live CD, choose manual install and deleted the ext3 partitions.
Then made new partitions, one, with mount point \ as root, one swap file (no mount point and one with \home.

The rest of the install went without errors but I don't get GRUB so I just boot straight into XP.

Did I forget something in the install or doesn't GRUB get installed if you choose the manual install ?

Can I fix it or should I reinstall an other way ?

---

### Post by phillw on 2009-09-10
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Go down to the section on re-installing grub after windows.

Phill.

---

### Post by bumanie on 2009-09-10
Can you post the output of > sudo fdisk -l from a live cd and also state whether you are using grub-legacy or whether tried to upgrade to grub 2.

---

### Post by Hagar55 on 2009-09-10
Sorry in the meantime I reinstalled Karmic again, only this time I clicked in the advanced menu of the installer.

There I told him to install grub in the windows partition...this wasn't a good idea, now I only got the word GRUB at startup and nothing else.
Wich isn't good since I need the windows installation for other things. So I booted into the XP disk and tried FIXMBR, diden't work, booted into it again and tried FIXBOOT.

Now the windows installation works again, is there a way to salvage the linux install or should I try again and change something ?

Is the problem that the linux installation is on a totally different drive then windows ?

I read somewhere when you manually partition you have to enable BOOT in the root partition, but I cannot see where I can do that.

---

### Post by bumanie on 2009-09-10
May be you have an odd BIOS??? Usually grub will setup perfectly to dual boot - it doesn't matter to grub whether it is on the first, second or third hard drive or whether it is in a logical partition, unlike windows it can boot from any partition and yes to successfully dual boot, grub is written to the MBR and gives the user the choice to boot to windows or linux. If windows is chosen, grub hands over to the windows bootloader files to boot windows. I once had a computer that would only boot into ubuntu (dual boot with windows) via supergrub disk - I figured it was a BIOS issue with a computer of about 6 years ago. I have dual booted multiple computers, but that one would not 'play the game' at all. You could try super grub disk and see if it helps - it's a live cd with a simple menu that can help with many bootloader issues. Get it [here]("http://www.supergrubdisk.org/index.php?pid=5"). But as you are using karmic, which uses grub 2 (which is technically only up to version 1.97 beta), I am not sure whether super grub disk supports it or not.
Other than being able to give you this background, I am not sure I can be of any more help. As grub 2 is new, there is not a heap of information about it around as yet. You can look [here ]("http://members.iinet.net/~herman546/p20.html")for some links that may help explain about grub 2. As karmic is still in testing/development, you may be better off installing jaunty (ubuntu 9.04) - it still uses grub-legacy and is a stable release. Best of luck.

---

### Post by Hagar55 on 2009-09-10
Ok, thanks for the help already given, just a few more questions.
I'll probably wipe the ext4 partitions and do it all over again.

But just to be sure
these are the partitions I'll make :
one primary, mount point \ (this should become root)please tell me if there are more parameters I should check
one swap file, no mount point
one primary \home this should become my home partition

now then there are several other mount points available
should they be used ?
for instance
\boot
\root
should I assing a mount pount to the windows XP install ?

thanks for any assistence given.....

---

### Post by bumanie on 2009-09-10
The way I setup my computers is to choose manual at the partitioning stage and do much as you have suggested. I have / of about 5-10gb /home as large as I want and a 1-2 /swap.
There is no need to set a mount point for xp during installation - if you are successful in getting grub to work as it should in a dual boot configuration with windows, grub will give you the option of booting into ubuntu or windows. If you want to access xp and have it automount when ubuntu is booted, you can install ntfs-config, which will add a mount point to /etc/fstab for the xp partition. As said, other than on one computer I owned, this has always worked without fail. I presently am running two triple boot computers - one uses grub-legacy and the other is using grub 2, so if things still don't work, I don't think I can suggest any thing more that will be of help. One thing to keep in mind is that it is far easier to get grub to work if windows is on the first partition of the first hard drive, without that, /boot/grub/menu.lst needs modifying to trick windows into thinking it is on the first hard drive. Again, good luck.

---

### Post by Hagar55 on 2009-09-10
So I started up the live-CD and started over, however karmic asked me if I wanted to dual boot with itself and not windows......
Everything went well, then I noticed that windows was on the second hard-drive to boot.

I changed that in "Advanced" and installed Karmic afresh....

Rebooted and although it does GRUB2 a long time to get there it shows Karmic to start up.....windows however is nowhere to be seen...

So at least GRUB is showing itself and Karmic is booting, now I only have to get win XP in the GRUB menu !

The installer is great in almost everything but this part is lousy !

---

### Post by Hagar55 on 2009-09-13
As it stood, windows XP wasn't anywhere to be seen in the new GRUB.
Many people on the net have said it worked faster then the original GRUB, but that certainly wasn't the case on my computer.

I searched for menu.lst to try and modify GRUB so it would add my XP system, but somehow in boot\GRUB the file was nowhere to be found.

And since my XP installation isn't something that I can go without I had no choice but to get out the XP disc again and after FIXMBR and FIXBOOT my XP as back and Karmic is dead once again.

I hope things are going to get better in the final release, otherwise I'll have a hard time installing it again on my desktop and I don't know if I'll be able to upgrade my laptop..

---

### Post by Tteddo on 2009-09-14
Hi! I just fixed mine, Karmic didn't put an entry for Windows in the menu. I found in someone's bug report that they ran:
> sudo os-prober
sudo update-grub2
in a terminal that it fixed it.
Worked for me!

---

### Post by Hagar55 on 2009-09-15
Well since I fixed the MBR with XP (really need it for some things) I can't use that anymore.

By the way the karmic install is still on the disk, can I use the install program to keep the home partition I made and just replace the OS files to try again ?

---

### Post by Tteddo on 2009-09-15
Sure! Just don't format it when you install. That will put grub back on it, then you can do what I mentioned earlier to get the dual boot working. I have never done the automated partitioner, I do manual, and just tell it to mount the EXT partition at / and that's it.

---

