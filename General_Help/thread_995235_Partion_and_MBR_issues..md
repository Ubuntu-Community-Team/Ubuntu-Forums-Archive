---
title: "Partion and MBR issues."
date: 2008-11-27
forum: General Help
---

### Post by denn0069 on 2008-11-27
Hi,
When first installing Ubuntu Hardy Heron a while ago I split my drive into 2 partitions of equal size. One was left empty and the 1st partition I installed Ubuntu on.
Now after installing windows xp on the blank partition I've run into the following issue.
At first I ran windows fixboot, which replaces the boot.ini file with a fresh one, and then ran fixmbr. Which of course clears the MBR and puts microsofts loader in. That worked fine.
Then using SuperGrubDisk I "fixed" the MBR and installed grub into it.
Now just using grub I can get into the linux partition(hd0,0) perfectly fine. However when I select Windows from the list I receive a message stating "NTLDR Missing. Rebooting.".
However if I boot from the SuperGrubDisk and use its option for booting windows it works fine.
Here's the kicker both my menu.lst and the SuperGrubDisk run the exact same grub commands:
```
rootnoverify(hd0,1)
chainloader +1
boot
```
But only the GrubLoaderDisk works.

Which confuses me because its not like GRUB is on a separate disk and cant find window loader its on the same disk.

Any help is appreciated.

---

### Post by meierfra. on 2008-11-27
This probably will not work, but you might give it a try. Boot into Ubuntu from  the Super Grub CD.  Open a terminal and replace the Ubuntu stage files by  the Super Grub stage  files:

```
cd /boot/grub
sudo mkdir Backup
sudo mv *stage* Backup/
sudo cp /media/cdrom0/boot/grub/*stage* .
```
(don't miss the "period" at the end of the last line)

Then reinstall grub:

```
sudo grub 
```
and at the grub prompt
```

root (hd0,0)
setup (hd0)
quit
```

Then try to boot into Windows.

---

### Post by denn0069 on 2008-11-27
I followed your steps and it did help get grub to come up now without having to hit escape.
However it did not fix my NTLDR issue.
But it did point out to me the actual issue.
In my menu.lst I have the following lines at the end:
```
title Windows Xp
rootnoverify (hd0,1)
chainloader +1
boot
```
However, upon selecting Windows XP from the list it only runs chainloader +1 and boot.

It's probably something retardly obvious but I'll have to figure out why it's skipping that line.

---

### Post by meierfra. on 2008-11-27
> upon selecting Windows XP from the list it only runs chainloader +1 and boot.

I am pretty sure that grub also is running "rootnoverify (hd0,1)", otherwise you would get a different error message. You probably have to put Windows in control of the MBR and add Ubuntu to  the Windows Bootloader. But lets first have a look at your partitions and menu.lst: Post the output of  

```
sudo fdisk -lu
cat /boot/grub/menu.lst
```

---

### Post by TeXtonyx on 2008-11-27
That is an odd thing that Windows won't boot from grub's menu.lst
but Windows will boot from SGD with the same booting entry. I used 
the SGD to fix a Linux entry for menu.lst once, but the method does
not work for Windows?! Too subtle, as in a wink is as good as a nod.

---

