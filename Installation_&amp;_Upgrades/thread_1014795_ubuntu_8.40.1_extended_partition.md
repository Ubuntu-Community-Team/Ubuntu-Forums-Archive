---
title: "ubuntu 8.40.1 extended partition"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by klein de usa on 2008-12-18
hi 
i'm kinda in a corner , i have a dell d620.

 
sda1 dell utilities 
sda2 is xp pro
sda3 ex3 /    ubuntu 8.40.1
sda4 extended
      sda5 swap 

my question is i would like to add vista, can i run ubuntu (ex3 /) in the extended partition? so it would look like this?

sda1 dell utilities                 47 mib
sda2 is xp pro                      37.24 gib
sda3 extended                       37 gib
     extended      sda4 ex3 /    ubuntu 8.40.1   36 gib
     extended      sda5 swap                     1 gib 
sda6 vista                          37 gib

---

### Post by taurus on 2008-12-18
Will vista install or run/boot from a logical partition?  How come you have to extended partitions?

Basically you take one of the primary partitions (you can only have four primaries) and convert it to extended partition.  Then under that extended partitions, you would create a bunch of logical partitions.

---

### Post by klein de usa on 2008-12-20
hi 
my first primary partition is a hidden dell utility
my second primary partition is xp pro 
my third primary partition is vista 
my forth primary partition is extended 
my fifth logical partition is ubuntu 8.04 
my sixth logical partition is linux/swap

normally you can only have four primary partition in less you install a boot loader.

if you do not have a hidden utility then you do not have to use a extended partition  caution!!!!!!!!!!! some hidden partition's are the restore files for the operating system and you don't want to loose them caution!!!!!!!!!!!!!!!!!! backing these hidden partitions up to cd is a hole different thing but it is possible  

so i needed more partitions so i made my fourth partition and extended partition and made two logical partitions inside that extended partition 
 
what i found is that if you install xp first and then install vista and 
then install ubuntu 
grub will boot ubuntu and vista and to get xp booted you have to edit your grub menu and add xp, some where i read that xp and vista were having problems, xp was wiping out vista restore points so i used the hide and unhide commands in grub, so xp doesn't see vista and vista doesn't see xp but ubuntu sees vista and xp

---

### Post by klein de usa on 2008-12-20
hi 
vista will not install on an extended/logical partition but ubuntu 8.04 and linux/swap work just fine in extended/logical partition

---

### Post by plarq on 2008-12-21
Well, I have a problem.
1st partition is GRUB
2nd partition is Dell Util.
3rd partition is Ubuntu
4th partition is extended, with a Linux swap inside.

Now I can reduce 3rd partition by Gparted, but I can't increase the size of extended to claim the extra space--meaning I cannot install any OS.

---

