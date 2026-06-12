---
title: "Help with booting dual operating systems"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by nate11120 on 2009-01-27
I got a Ubuntu disk from the local computer shop a while ago and since i had an external hard drive i decided i would install it well i tried and i failed so i just ran the OS of the disk for a few months whenever i wanted to mess around with the awesome Linux networking tools. So well anyway a few days ago i try out this new virus scanner and remove a few viruses from my computer I accidentally deleted a few parts of the boot section from WindowsXP. So now I am running Ubuntu of the disk. I really need help to get Windows working again but i would also be very appreciative if you could help me somehow with the installation of Ubuntu to my external drive permanently. 
my operating specs:
940G of memory on an external drive with a USB uplink
120G of memory on an internal drive
IG of RAM 
LanParty NF4 motherboard

---

### Post by caljohnsmith on 2009-01-27
How about from the Live CD, open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```
And for whichever is your Windows partition, next do:
```
sudo mount /dev/sdaX /mnt && ls -l /mnt
```
But replace sdaX with your Windows partition. Also, do you have any idea what files you deleted in Windows that were crucial? When you boot Windows now, what errors do you get?

---

### Post by nate11120 on 2009-01-27
```
Disk /dev/sda: 1000.2 GB, 1000204885504 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525167 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8934d1b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1947463559   973731748+  83  Linux
/dev/sda2      1947463560  1953520064     3028252+   5  Extended
/dev/sda5      1947463623  1953520064     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 515 MB, 515899392 bytes
16 heads, 32 sectors/track, 1968 cylinders, total 1007616 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32     1007615      503792    e  W95 FAT16 (LBA)

Disk /dev/sde: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8c718c71

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63   234420479   117210208+   7  HPFS/NTFS
ubuntu@ubuntu:~$ sh

```

thank you for your assistance i think that i managed to damage the boot drive because when i actually removed the files it gave me a notification that the files were corrupted i was pretty dumb and i didn't even run the chkdsk utility well anyway so i turn it of and i turn it on again and nothing after my BIOS boot so i am assuming that because there was no loading in the windows there must be no windows boot. However checking from here my system files seem intact. I haven't actually partitioned Ubuntu yet i am running the try Ubuntu option of the disk.

---

### Post by caljohnsmith on 2009-01-27
Do you have a Windows Install CD? I think you will need it if you want to get Windows working again. I would recommend booting that, go to the "recovery console" and run:
```
fixmbr
fixboot
chkdsk /r
```
And run the chkdsk command as many times as it takes until it reports no errors. Next reboot the Windows CD again, but this time choose the "install Windows" option, and after that you should be given the option to do a "Windows Repair". I would choose that. Good luck and let me know how that goes.

---

### Post by nate11120 on 2009-01-27
Thanks for all the help
I will do that as soon as i can get my friend to lend me his disk (for some reason my dad doesn't have his). after I am done fixing windows could you help me install Ubuntu fully as a secondary operating system? I really appreciate your help thank you again and i will tell you how that goes my friend should be bringing the disk over tomorrow.

---

