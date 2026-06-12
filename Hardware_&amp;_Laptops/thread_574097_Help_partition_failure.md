---
title: "Help: partition failure"
date: 2007-10-12
forum: Hardware &amp; Laptops
---

### Post by derby007 on 2007-10-12
OK, the inevitable happened, a (ESB) power failure while I was working on the PC & I can now only boot into winXP !  :) aaaggghhhhh.

Background: I used to tripple boot, winXP, ubuntuEdgy & ubuntuFiesty, ie. I had 2 partitions in my extended partition to boot into Edgy & Fiesty.

But.....after the power cut, all I can boot into is winXP. I ran PartitionMagic & it shows the entire drive as 'BAD', bummer....  I did load the liveCD and it let me 'see' the two disks(disk-1=edgy, disk-2=fiesty), so I managed to save some data, thank goodness.

But.........what are my options now. I did see a link to 'testdisk.exe', so I'll try this tonite. I could do a restore, ie. to a restore point, but I am a total novice as to how that works, ie. how does that effect the linux partitions??? Also, I still have the original Dell partitions, ie. to restore to a factory install, as a last resort. 

If anyone has any other ideas pls reply to this thread. :)

---

### Post by waawaawee on 2007-10-12
Nah restore points won't help..
Wat I would suggest is to run that darn live CD and back up your data and then try to run fsck (do man fcsk for option checks) to see if that fixes ur bad sectors n all.

---

### Post by derby007 on 2007-10-15
I didnt see your post till now, so I didnt do 'fcsk'. What I ended up doing was running 'testdisk.exe' in XP and it seemed to fix the 'bad'ness. But I still had to use the partition manager in the live CD to delete the bad partition, part manager in XP couldnt do it. So on this bad/deleted partition I installed the '64Studio' distro & it also rejigged my MBR, so I now can boot into all 3 OS's again, phew.
PS. 64Studio is interesting, aespecially if youre into audio/music editing. It runs on a Gnome desktop with ALOT of audio/video software installed.

---

