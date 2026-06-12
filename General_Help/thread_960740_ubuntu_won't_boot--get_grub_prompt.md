---
title: "ubuntu won't boot--get grub prompt"
date: 2008-10-27
forum: General Help
---

### Post by valikor on 2008-10-27
Hey folks,

I'm a new linux user and yesterday ubuntu stopped booting. I installed it with Wubi, alongside Windows XP. I can no longer access ubuntu, as it leaves me at a grub> prompt. This has never happened before so I don't know how to tell grub to load ubuntu.

Suggestions?

Thanks

David

---

### Post by alienprdkt on 2008-10-27
during boot up try pressing esc see if there is a previous kernel to boot from???

---

### Post by valikor on 2008-10-27
In doing that, I get 8 options

find /ubuntu/disks/boot/grub/menu.lst
find /ubuntu/install/boot/grub/menu.lst
find /menu.lst
find /boot/grub/menu.lst
find /grub/menu.lst

When selected, all of these options simply give me the grub> prompt, except for the first one, which gives me "Error 15--File not Found" and then a grub> prompt.

and: command line, reboot, halt.

:/

David

---

### Post by valikor on 2008-10-27
bump :(

---

### Post by alienprdkt on 2008-10-28
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD)

First of all, we burn a Hardy Heron (Ubuntu 8.04) ISO (on a CD(R , RW) or DVD (+R , +RW)) or make sure that we have one already.

Then, we change, in the BIOS, the boot load sequence and we put the CD/DVD option first.

After that, we boot the Live CD, we choose the first option and in a few minutes we have arrived at the Live CD Desktop.

So, we go :

 Applications --> Accessories --> Terminal 

Then, we have to remember which is our Ubuntu installation partition.

In our example, it is the second one (/dev/sda2), formatted as ext3, in the first HDD of a SATA controller. We suppose that it is the second one, since, in case we have Windows that demand to be in the first partition (/dev/sda1), this one is occupied.

Now, you have to be really careful. You have to enter the right partition, instead of sda2 (unless it is the same) In the terminal :

  cd /
  
 
  sudo -s -H

  mount -t ext3 /dev/sda2 /mnt

  mount -t proc proc /mnt/proc

  mount -t sysfs sys /mnt/sys

  mount -o bind /dev /mnt/dev

  chroot /mnt  /bin/bash

And now, you are actually "running" Ubuntu within the Hard Drive but through Live CD's terminal.

Now we restore GRUB like that:

1) Restoration to MBR

  grub-install /dev/sda

2) Restoration to partition (example: /dev/sda2)

  grub-install /dev/sda2

In the first case (that is the most usual) you have certainly installed GRUB on MBR after you receive, in the terminal, the message that there are no errors.

After you reboot, you have your favorite bootloader restored.

---

### Post by bapoumba on 2008-10-28
Moved to Wubi.

---

### Post by ago on 2008-10-28
Run chkdsk /r from windows in the drive where you installed ubuntu. Then check that you have c:\ubuntu\disks\root.disk. Otherwise look for a hidden folder called c:\found.000 and move the files in there to their original position

---

### Post by valikor on 2008-10-28
Ago--

you were right that these files had been deleted. The Found.001 folder also got deleted (or lost, I believe, due to hdd problem), but a data recovery utility was able to restore these. So, I put my root.disk and my swap.disk (the two files I found in Found.001) back into the ubuntu/disk directory. 

But, ubuntu still doesn't start. Any ideas for a next step? 

:)

thanks

David

---

### Post by ago on 2008-10-29
You also need c:\ubuntu\disks\boot\ and everything in there

---

### Post by valikor on 2008-10-29
Which files should be in there? It (\disks\boot) was empty. 

(There is, however, a C:\ubuntu\winboot folder with a menu.lst, wubildr, wubildr.mbr, and wubildr.exe.)

---

### Post by marlll on 2008-10-30
That's good,thx for sharing!

[[color=white]study in china[/color]](http://www.cuhk.edu.hk/clc/e_putonghua.htm)

---

### Post by ago on 2008-10-30
> **valikor said:**
> Which files should be in there? It (\disks\boot) was empty. 

(There is, however, a C:\ubuntu\winboot folder with a menu.lst, wubildr, wubildr.mbr, and wubildr.exe.)

There should be quite a few files in there. The important thing though is that you have retrieved root.disk, you can do a second installation (8.10) and access any file in there. If you reinstall with wubi make sure to move root.disk outside of C:\ubuntu\ as that folder gets deleted upon uninstallation.

---

### Post by Alfredo1234 on 2008-12-21
I also have the same problem, it works fine on an HP computer I have, everything starts up, but when i try it on my DELL, after finishing installing ubuntu while in windows, i rebbot and get that same thing, can anyone help me? :(

---

### Post by halzonski on 2009-10-27
> **alienprdkt said:**
> [http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD)

First of all, we burn a Hardy Heron (Ubuntu 8.04) ISO (on a CD(R , RW) or DVD (+R , +RW)) or make sure that we have one already.

Then, we change, in the BIOS, the boot load sequence and we put the CD/DVD option first.

After that, we boot the Live CD, we choose the first option and in a few minutes we have arrived at the Live CD Desktop.

So, we go :

 Applications --> Accessories --> Terminal 

Then, we have to remember which is our Ubuntu installation partition.

In our example, it is the second one (/dev/sda2), formatted as ext3, in the first HDD of a SATA controller. We suppose that it is the second one, since, in case we have Windows that demand to be in the first partition (/dev/sda1), this one is occupied.

Now, you have to be really careful. You have to enter the right partition, instead of sda2 (unless it is the same) In the terminal :

  cd /
  
 
  sudo -s -H

  mount -t ext3 /dev/sda2 /mnt

  mount -t proc proc /mnt/proc

  mount -t sysfs sys /mnt/sys

  mount -o bind /dev /mnt/dev

  chroot /mnt  /bin/bash

And now, you are actually &quot;running&quot; Ubuntu within the Hard Drive but through Live CD's terminal.

Now we restore GRUB like that:

1) Restoration to MBR

  grub-install /dev/sda

2) Restoration to partition (example: /dev/sda2)

  grub-install /dev/sda2

In the first case (that is the most usual) you have certainly installed GRUB on MBR after you receive, in the terminal, the message that there are no errors.

After you reboot, you have your favorite bootloader restored.

Much Thanks!! This answer saved my Bacon!!:popcorn:

---

