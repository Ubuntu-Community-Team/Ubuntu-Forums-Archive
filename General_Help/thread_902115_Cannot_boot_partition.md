---
title: "Cannot boot partition"
date: 2008-08-27
forum: General Help
---

### Post by shamusl on 2008-08-27
I recently tried to install XP (and remove vista), and XP gave an error telling me I had exceeded partition limit. So I quit installation and rebooted.
XP wrote over the MBR, so I inserted a live-cd and replaced the broken xp boot loader with grub, and it seemed to have worked - Until I restarted. 

When I restarted and tried to boot to ubuntu, it fails and tells me it can't boot from it. If anyone needs the exact error I can get it for you. 

Reinstalling isn't really a problem because I have seperate / and /home partitions.

On a side-note, is the only way to get XP to install is if I install XP first (deleting my other ubuntu partitions and swap partitions) because of the rather arbitrary partition limit?

---

### Post by coffeecat on 2008-08-27
> **shamusl said:**
> so I inserted a live-cd and replaced the broken xp boot loader with grub, and it seemed to have worked - Until I restarted. 

When I restarted and tried to boot to ubuntu, it fails and tells me it can't boot from it. If anyone needs the exact error I can get it for you.

With separate / and /home partitions you may have pointed grub stage 1/1.5 to the wrong partition by mistake when you did the root (hdx,y) command. Or if you used the grub install/reinstall command (can't remember which it is - I never use it) it may have failed. It's not as reliable as doing it by hand. Yes, post the error; it will be helpful. Just the error number is enough. [The Grub Manual]("http://www.gnu.org/software/grub/manual/") can supply the rest.

> **shamusl said:**
> Reinstalling isn't really a problem

Hopefully not necessary. A simple reinstall of Grub to the mbr may be enough.

> **shamusl said:**
> On a side-note, is the only way to get XP to install is if I install XP first (deleting my other ubuntu partitions and swap partitions) because of the rather arbitrary partition limit?

I'm not sure what this 'arbitrary' partition limit is or why XP came up with that error. Boot up the live CD, open a terminal and post the output of:

```
sudo fdisk -l
```(Lower-case L, not one). Then we can see what your partition layout is like. It may give a clue as to why XP errored and what grub commands you need to execute. Please indicate which is your / and /home partitions - the output of fdisk won't tell us. By the way, if you can connect to the internet with the live CD, you can copy and paste the output of fdisk directly from the terminal to the firefox message field. If you can, it would also be helpful to open System > Administration > Partition Editor and post a screenshot of the Gparted window showing your main internal drive.

---

### Post by shamusl on 2008-08-27
> **coffeecat said:**
> With separate / and /home partitions you may have pointed grub stage 1/1.5 to the wrong partition by mistake when you did the root (hdx,y) command. Or if you used the grub install/reinstall command (can't remember which it is - I never use it) it may have failed. It's not as reliable as doing it by hand. Yes, post the error; it will be helpful. Just the error number is enough. [The Grub Manual]("http://www.gnu.org/software/grub/manual/") can supply the rest.



Hopefully not necessary. A simple reinstall of Grub to the mbr may be enough.



I'm not sure what this 'arbitrary' partition limit is or why XP came up with that error. Boot up the live CD, open a terminal and post the output of:

```
sudo fdisk -l
```(Lower-case L, not one). Then we can see what your partition layout is like. It may give a clue as to why XP errored and what grub commands you need to execute. Please indicate which is your / and /home partitions - the output of fdisk won't tell us. By the way, if you can connect to the internet with the live CD, you can copy and paste the output of fdisk directly from the terminal to the firefox message field. If you can, it would also be helpful to open System > Administration > Partition Editor and post a screenshot of the Gparted window showing your main internal drive.

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60546054

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           12159       28820   133837515   83  Linux
/dev/sda2           28821       30279    11719417+  83  Linux
/dev/sda3           30280       30401      979965   82  Linux swap / Solaris

```
Screenshot of gparted below.

---

### Post by sameerds on 2008-08-27
> **shamusl said:**
> ```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60546054

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           12159       28820   133837515   83  Linux
/dev/sda2           28821       30279    11719417+  83  Linux
/dev/sda3           30280       30401      979965   82  Linux swap / Solaris

```
Screenshot of gparted below.

Looking at this listing, I am guessing that you used to have windows partition too, from cylinder 0 to 12158 ... That would have been your actual /dev/sda1, until it got deleted.

From your live CD, have you tried to create a primary partition at the beginning of the drive again? Use the entire unallocated space. There can be only four primary partitions, and you already have three. So you can create only one more primary partition now.

Once you create the partition, set its type to the equivalent of "windows primary" ... I can't remember the actual type name or ID right now. Then reboot from your XP installer CD ... it should recognise it as the C: drive and install itself there. All this should definitely work if the new primarty partition gets numbered as sda1, and not sda4. If it becomes sda4, I dunno what to do next! :D

---

### Post by shamusl on 2008-08-27
> **sameerds said:**
> Looking at this listing, I am guessing that you used to have windows partition too, from cylinder 0 to 12158 ... That would have been your actual /dev/sda1, until it got deleted.

From your live CD, have you tried to create a primary partition at the beginning of the drive again? Use the entire unallocated space. There can be only four primary partitions, and you already have three. So you can create only one more primary partition now.

Once you create the partition, set its type to the equivalent of "windows primary" ... I can't remember the actual type name or ID right now. Then reboot from your XP installer CD ... it should recognise it as the C: drive and install itself there. All this should definitely work if the new primarty partition gets numbered as sda1, and not sda4. If it becomes sda4, I dunno what to do next! :D

Actually, no it's not a windows partition. A windows partition (vista) was once there, but I deleted it so that I can install XP, however when I clicked delete partition and clicked enter to make a new partition, it said I had too many partitions. So it's just unallocated space.

---

### Post by Garratt on 2008-08-27
lawl... need a boot team!

or boot forums :P


personally seeing as your main goal is to install XP, id use gparted to change partitions and try to delete that unallocated space, then reformat, then use XP disk to re-partition and install xp..

or wouldn't even bother with gparted just try to format, then re-partition with xp and install

---

### Post by coffeecat on 2008-08-27
Agreed - no evidence of Windows at all. There's over 90Gb of unused space at the beginning of the drive. The trouble with assigning that to a NTFS partition, is that, even if you could create it, it would be designated sda4, seeing as you already have sda1, 2 and 3. I don't know enough about the Windows installer, but I wonder if your exceeded partition limit error was something to with either not wanting to install to partition #4 or objecting to the partition numbers being out of order.

Yes, you could use Gparted in the live CD to partition that unused space to a primary NTFS partition (Windows won't boot from logical/extended partitions) and see if Windows will install to it. One objection to that is that you would then have four primary partitions (the maximum allowed) and no room for flexibility in the future, unless you converted one of your Linux partitions to an extended. And you would still have to reinstall Grub, and you haven't told us which is your / partition.

A suggestion for you if you want to start over. Use Gparted in the live CD to delete everything. Then create a primary NTFS partition of the size you need for Windows with the boot flag set. This will be sda1 - ideal for Windows. Then use the rest of the HD to create one big extended partition - which will be sda2. In sda2, create three logical partitions, swap, / and /home. Install Windows to sda1. Then install Ubuntu using the custom partitioning option, pointing the installer to the partitions you have already set up for it. Grub will then be installed correctly for you with a Windows/Ubuntu dual-booting menu.

---

### Post by Garratt on 2008-08-27
watever errors you recieved would be due to the pain in the A$$ vista boot-loader so, if you can remove that you should be in business.

---

### Post by shamusl on 2008-08-27
> **coffeecat said:**
> One objection to that is that you would then have four primary partitions (the maximum allowed) and no room for flexibility in the future, unless you converted one of your Linux partitions to an extended. And you would still have to reinstall Grub, and you haven't told us which is your / partition.


My / partition is the 11gb volume (sda2), my swap (sda3) is the 900mb volume and /home (sda1) is the 137gb partition.

I do not need flexibility in the future, as this is going to be the only 2 OS's I run, however I would like to convert my linux partitions to extended and make my /, /home and swap all logical anyway. I have no idea the differences between the partition types, but if it'll fix my problem I'm all for it.

---

### Post by shamusl on 2008-08-27
> **Garratt said:**
> watever errors you recieved would be due to the pain in the A$$ vista boot-loader so, if you can remove that you should be in business.

As I believe I have said before, I have reinstall grub to the MBR, it just won't boot my ubuntu partition, and grub is still picking up vista, however vista's partition was deleted.

---

### Post by coffeecat on 2008-08-27
> **shamusl said:**
> I do not need flexibility in the future, as this is going to be the only 2 OS's I run

Well, you might. Who knows what the future might bring? :wink:

> **shamusl said:**
> however I would like to convert my linux partitions to extended and make my /, /home and swap all logical anyway. I have no idea the differences between the partition types, but if it'll fix my problem I'm all for it.

It sounds like you might want to go with my suggestion of wiping the HD clean with Gparted from the live CD, and then using Gparted to create a new partition structure. As far as the partition types are concerned, the explanation is fairly straightforward but you'll come across some confusion between extended and logical in some threads here, so here goes:

You are limited to four primary partitions. Windows **must** boot from a primary partition (actually, that's not quite true, but you have to do some clever hacking to get it to boot from a logical), whereas Linux doesn't have this limitation. To get round the limit of 4 partitions only, instead of a primary partition you may have no more than one extended partition. An extended partition is really a type of primary with one purpose only, as a container for logical partitions. You don't access it directly for data storage purposes, so when you come across people talking about their Linux root or whatever partition being extended, they really mean logical.

Primary or extended partitions are numbered 1 to 4, so a primary/extended will be sda1, sda2, sda3 or sda4. Or sdb1, etc. Logical partititions are numbered sda5 upwards, so you can tell a logical at a glance. I can't remember what the limitation is on the number of logical partitions, but it's probably more than enough.

There's one other source of confusion: the Wikipedia page on partitions which I won't link. The last time I looked it referred to 'logical partition' being a synonym for primary partition, and what I've referred to as a logical partition they called a 'logical drive'. Whether there's been a change in terminology, or whether that's the influence of Windows thinking, or whether the author just got it wrong, I don't know.

---

