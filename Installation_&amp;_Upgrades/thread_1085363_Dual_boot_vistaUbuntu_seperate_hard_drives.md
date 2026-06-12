---
title: "Dual boot vista/Ubuntu seperate hard drives"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by dharmabum4732 on 2009-03-03
I'm having a hard time finding a method of dual booting Vista and Ubuntu on separate hard drives.  I have Vista installed on a (soft) raid 0 array, and would like to install Ubuntu on a separate internal sata hard drive without messing with the MBR on my Vista install.


I'm not quite sure what to do.  Any pointers?


Thanks!
-Max

---

### Post by Neo_The_User on 2009-03-03
Method... you mean formatting / partitioning? I shouldn't have posted... I'm lost. Sorry. Partition the hard drive without using the entire disk then on the last step of the installation ( 7 of 7 ) click Advanced and uncheck install grub to MBR (hd0,0) or whatever it is.

I most likely mis-understood your question. I do that a lot.

---

### Post by dharmabum4732 on 2009-03-03
Hey Neo_The_User,

I can successfully format the drive and install ubuntu on it, but I'm just not sure where to put the grub boot loader. (I hope that makes sense, I'm kind of a novice).

Thanks,
-Max

---

### Post by dharmabum4732 on 2009-03-03
I will give it a try and post the results.  Thanks, Neo_The_User.

---

### Post by Neo_The_User on 2009-03-03
Ah, so thats what the problem is. You want grub not to be in the MBR but bootable. /dev/sda1 might be your best bet. ...an hour as gone by. I hope you didn't come across any serious problem.

**_[SIZE="3"]DANGER! WHEN TRYING TO OPEN THE LINUX FILESYSTEM IN WINDOWS IT WILL ASK YOU IF YOU WANT TO FORMAT IT WITHOUT ANY CAUTION! BE SURE TO SELECT "NO"[/SIZE]_**

---

### Post by Mark Phelps on 2009-03-03
I have a similar situation, also multiple drives, also not wanting to mess with the Vista MBR, so I installed Ubuntu to its own drive, installed GRUB to the MBR of that drive, boot from that drive, and added a stanza to the menu.lst file for Vista -- booting Vista from GRUB.  Works fine for me, and if I have to restore the Vista mbr for any reason, I don't have to reinstall GRUB.

---

### Post by davidjhomeplate on 2009-03-27
Mark Phelps,

Which hdd do you have set as your default boot hdd in the BIOS? The Ubuntu drive?

You see, I totally hosed my system last night. I installed Vista on two WD 500 GBs in RAID_0 and had it going (very fast!) for a couple hours loading, installing, updating, etc. My last maneuver was going to be installing Ubuntu just as you described, by putting it on its own drive outside of the two disks in the RAID array. Installation to the third drive (NOT in the array) was successful (I didn't mess with any advanced settings - my bad), and when it went to re-boot, the array was broken and it wouldn't go anywhere. Now I'm totally without a bootable machine. I can't successfully sever the array and the only way around it I think is for me to do a clean full install of Ubuntu FIRST, and then format my two WD 500s, then install Vista in the RAID (again!), all the while keeping the Ubuntu drive unplugged. Then once I've got both OSs installed, either tell the BIOS which OS I want to load first each time by messing with the boot order, or by telling the BIOS to look at the GRUB loader on the Ubuntu drive after manipulating the menu.lst to give me a decision after the POST.

Can you guys think of any quicker ways of helping me get to a decent dual boot configuration?

Thanks!

DJHP

---

### Post by ronparent on 2009-03-27
Keep it simple. I am using such a system. I reset the bios to boot to the separate disk I intented to install ubuntu to. Use the live cd to install ubuntu to that drive. BE VERY CAREFUL! You can easily distroy your raid0 win install because the raid0 drive will show only unallocated space on the two component disks during the ubuntu install. To be completely safe you can temporarily unplug your two disk array. Once you have ubuntu up and running you can tempoarily dual boot by resetting the bios to select the desired operating system. At that point, you can choose to add the appropriate comment to grub (booting on the separate ubuntu drive) to enable it to boot windows. I can't over emphasize that unlees your very careful you can find yourself in davidjhomeplate's boat.

Note also that the win install will not show up in your ubuntu install until you enable the software raid driver (I use dmraid which has to be seperately downloaded and activated). Once activated, your array will show up in the partioner and it canbe safely used to reallocate space in the array if you so choose.

---

### Post by davidjhomeplate on 2009-03-28
ronparent,

Exactly. What I'm doing now is I actually wiped my smaller drive which used to have Ubuntu on it clean, and I reinstalled WinXP (yuck!), and at this moment I'm formatting my former RAID drives to NTFS so I can re-install Vista nice and clean. For some reason, "quick format" wasn't enough and when I would try to re-install Vista on the RAID_0, it would fail. There is one weird thing, and I know it's not entirely related to Ubuntu, but while I'm here, I thought I'd ask. When I look at the two drives which were formally part of the RAID, WinXP says that one drive is 465 GB (which is correct), and the other is 931 GB (which is incorrect). The 931 was the size of the two drives combined under the RAID array (2 X 465 GB), but I broke the array and the two drives show up separately (and their file system is listed as "RAW", which I've never seen before). So I'm hoping after the format is complete, I can go in and see that each drive is only 465 GB. Do you (or anybody else) know what is wrong here? Why is the one drive showing up as a 931 GB?

One thing I've learend - Windows is CRANKY that's for sure.

---

### Post by Mark Phelps on 2009-03-29
> **davidjhomeplate said:**
> Mark Phelps,

Which hdd do you have set as your default boot hdd in the BIOS? The Ubuntu drive?

Thanks!

DJHP
My default boot drive is the one containing Ubuntu.  I use stanzas in the menu.lst file to point to the MS Windows boot loaders.

Since you're apparently using RAID for your Vista OS, this is yet another reason to not mess with the Vista drive(s).

---

### Post by ronparent on 2009-03-29
davidjhomeplate "When I look at the two drives which were formally part of the RAID, WinXP says that one drive is 465 GB (which is correct), and the other is 931 GB (which is incorrect)."

Did you change the physical order of the drives? The 931GB probably refers to the definition of the original raid0 partition table. No matter - if you reformat the two disks seperately that will dissapear.

---

