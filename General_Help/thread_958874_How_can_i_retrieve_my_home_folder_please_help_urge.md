---
title: "How can i retrieve my home folder?? please help urgent..."
date: 2008-10-25
forum: General Help
---

### Post by mali2 on 2008-10-25
HI,
today evening, i just create the new user in ubuntu, and when i log-off the current user, it becomes halt, then after it, i restart my computer and ubuntu starts, but with no Graphical interface , it is just giving the prompt with ...

initramfs _______

now from this prompt , when ever i use to give command ls, then it is not showing the home folder, in which my user is created, i try to scan my drive from windows but no luck. i have very essential data in my home/ali/.. folder... but i dont know how to retrieve this home folder, because i m now going to re-install the ubuntu. but i dont know how to save my home folder. and one more thing, i would like to mention, my hard drive containing 2 partition with NTFS type... and C driving containing windows, and D drive having some data and UBUNTU.
any help would be welcome..

---

### Post by kevstar31 on 2008-10-25
Start up with  ubuntu livecd and post output of:
```
fdisk -l
```

---

### Post by geirha on 2008-10-25
It's possible you just need to run a filesystem check on your root partition. Boot the ubuntu CD, then run ```
sudo fdisk -l
``` and identify the partition ubuntu is installed on (/dev/sdXY), then run ```
sudo fsck /dev/sdXY
``` Then try booting normally again.

---

### Post by mali2 on 2008-10-25
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x23232323

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1104     8346208+   7  HPFS/NTFS
/dev/sda2            1105        5167    30716280    f  W95 Ext'd (LBA)
/dev/sda5            1105        5167    30716248+   7  HPFS/NTFS

Disk /dev/sdb: 8178 MB, 8178891776 bytes
33 heads, 63 sectors/track, 7683 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes
Disk identifier: 0x738c496a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7684     7987183    b  W95 FAT32

i think here /dev/sdb1 is the partition where ubuntu is installed.
now further what should i do ?

---

### Post by mali2 on 2008-10-25
ubuntu@ubuntu:~$ sudo fsck /dev/sdb1
fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Reclaimed 12 unused clusters (49152 bytes).
Free cluster summary wrong (1136644 vs. really 1136656)
1) Correct
2) Don't correct

I choosed 1 ... and now i m going to boot it...


no it is same... still same problem

---

### Post by geirha on 2008-10-25
Ah, you are using wubi, sorry didn't catch that. Try this: [https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?](https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?)

---

### Post by mali2 on 2008-10-25
OK let me try this one also...

---

### Post by mali2 on 2008-10-25
i am not getting this one... 
Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein 

can u please describe this ...

---

### Post by geirha on 2008-10-25
You need to replace /dev/sda1 with the partition ubuntu is installed in. If it is D: in windows, then it is probably /dev/sda5 based on your fdisk output.

Once mounted, see if you can find the ubuntu folder, then run the fsck command on the root.disk file.

---

### Post by mali2 on 2008-10-25
thanks, for ur so much corporation... but problem still there...

when i mount the drive first time... it was done... 
i-e sudo mount /dev/sda5 /win
now after above i did...
sudo mkdir /vdisk 
it do not give any thing... but after giving below.. it is saying..
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
no such file or directory
but i install ubuntu at D drive ..

---

### Post by geirha on 2008-10-25
Use the file browser to find the ubuntu folder inside /win, then go further into the disks folder where you should see a file named root.disk. In the terminal, type this, but do not press enter: "sudo fsck " < leave a space at the end. Then drag the root.disk file over to ther terminal, and it should fill in the correct path for you, then hit enter in the terminal to run the filesystem check.

---

### Post by mali2 on 2008-10-25
well!

d:ubuntu
My D drive having the ubuntu folder ... and in the disks folder... i have two subfolders and one file which are
boot , shared are folders
and swap.disk is file
but no root.disk

---

### Post by mali2 on 2008-10-25
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=89679&stc=1&d=1224988955[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=89681&stc=1&d=1224988955[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=89682&stc=1&d=1224988955[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=89683&stc=1&d=1224988955[/IMG]

here are my screen shots

---

### Post by geirha on 2008-10-25
Hm. No root.disk, that's odd. Try ```
sudo find /win -name "*.disk"
```

---

### Post by mali2 on 2008-10-25
it returns /win/ubuntu/disks/swap.disk

is it in.. D drive...


now i am giving the command

sudo mount -o loop /win/ubuntu/disks/swap.disk /vdisk
and in response...
mount you must specify the filesystem type

---

### Post by geirha on 2008-10-25
It sounds like it is gone somehow, which could explain why it won't boot ... I guess your best bet now is to find some recovery software that can recover deleted files on NTFS.

---

### Post by mali2 on 2008-10-25
can u please suggest me any one, and it should be run under windows... ?

and after finding the software , should i repeat the previous steps...

---

### Post by geirha on 2008-10-25
Well, there's foremost and photorec, but I don't think they are able to recover virtual disks, so I think you might need some windows undelete software, though my knowledge on windows is very low I'm afraid, so I don't know what to recommend. If you manage to recover the root.disk file though, you should try booting ubuntu again.

---

### Post by mali2 on 2008-10-25
OK , if i re-install the window, will it delete all the previous things... what u say ?

---

### Post by geirha on 2008-10-26
> **mali2 said:**
> OK , if i re-install the window, will it delete all the previous things... what u say ?

I don't quite understand ... do you mean reinstall windows? as long as you let the installer stay away from D: you should be ok, but I recommend you try recovering your wubi disk first.

---

