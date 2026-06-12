---
title: "PLease Help! Trying to install xp with ubuntu"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by DAllenSmith on 2009-03-10
Alright i have ubuntu on 1 partition then about 5 gigs of free space then my /user part, then my /home part. i m tryng to install xp onto the free space i am aware that this will delete my mbr my problem is when i load xp and tell it to install to the free space it tells me that it cannot because it needs to write the boot data to the disk and i have tried everything besides formating the whole disk which i would do but i have things in my home partition i need. i have been messing with this all day please some one help me!

---

### Post by Neo_The_User on 2009-03-10
Installing Windows will format your entire hard drive no matter what and it will erase everything and you can't do anything about it. Copy your home partition off onto something else. Install Windows, then do a fresh install of Ubuntu with a 50/50 partition with windows (nothing cute. just a '/' partition and swap) and copy everything inside the backed up home folder INSIDE the home folder on the fresh install.

---

### Post by Sef on 2009-03-10
Is the free partition, the first one?  Windows likes to install there.

---

### Post by DAllenSmith on 2009-03-10
well no it isnt the first partion, but i tried deleting all the partions except my /home  partion and still got the same message, as far as what neo said, i have seen many how tos on installing xp after ubuntu but none of them describe this problem

---

### Post by taurus on 2009-03-10
Are you still able to boot Ubuntu on the harddrive?  Post the layout of your harddrive.

```
sudo fdisk -lu
```

---

### Post by DAllenSmith on 2009-03-10
well no, i wasnt able to boot into ubuntu, i have had to reinstall it 3 times because xp partion editor ruined my mbr even though it didnt install, here is the out put:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002ddcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    70316504    35158221    5  Extended
/dev/sda2   *    70316568   312580239   121131836   83  Linux
/dev/sda5        27358758    58123169    15382206   83  Linux
/dev/sda6        58123233    70316504     6096636   82  Linux swap / Solaris
/dev/sda7             189    15856154     7927983   83  Linux

```

---

### Post by Neo_The_User on 2009-03-10
> **DAllenSmith said:**
> well no, i wasnt able to boot into ubuntu, i have had to reinstall it 3 times because xp partion editor ruined my mbr even though it didnt install, here is the out put:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002ddcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    70316504    35158221    5  Extended
/dev/sda2   *    70316568   312580239   121131836   83  Linux
/dev/sda5        27358758    58123169    15382206   83  Linux
/dev/sda6        58123233    70316504     6096636   82  Linux swap / Solaris
/dev/sda7             189    15856154     7927983   83  Linux

```

3 linux partitions?

---

### Post by DAllenSmith on 2009-03-10
well its / then /usr then /home, forgot to mention i had a /usr partition, i tried deleting that too so i dont think it matters much

---

### Post by Neo_The_User on 2009-03-10
> **DAllenSmith said:**
> well its / then /usr then /home, forgot to mention i had a /usr partition, i tried deleting that too so i dont think it matters much

You deleted /usr? eeeeyeah thats gunna cause problems.

---

### Post by DAllenSmith on 2009-03-10
well yeah i del /usr when i tried to install windows i have since reinstalled ubuntu a few times and created a new /usr partion and everything is back to normal now, but do u mean its gonna cause problems for me trying to install xp?

---

### Post by Neo_The_User on 2009-03-10
> **DAllenSmith said:**
> well yeah i del /usr when i tried to install windows i have since reinstalled ubuntu a few times and created a new /usr partion and everything is back to normal now, but do u mean its gonna cause problems for me trying to install xp?

Not for XP. I was talking about Ubuntu. /usr is a critical directory in linux.

---

### Post by DAllenSmith on 2009-03-10
yeah i know but it is fully restored and intact now, i dont mind losing all my system data, i just cant loose my /home partition and i dont really have anything to back it up on

---

### Post by Neo_The_User on 2009-03-10
> **DAllenSmith said:**
> yeah i know but it is fully restored and intact now, i dont mind losing all my system data, i just cant loose my /home partition and i dont really have anything to back it up on

Hmm... My approach would be to make /home un-erasable by taking away all write permissions to everything and everybody or somehow make it invisible and sneak undetected past the windows partitioning system.

---

### Post by avtolle on 2009-03-10
It appears that your "free space" is within the extended partition. While I've read that Windows will boot from a logical partition, the "common law" of Windows is that it wants to be on a primary partition.  Looking at your partitions, it seems to me (not a partitioning expert) that you would need to move the logical partitions within the extended partition to create some free space at the end of the extended partition, then shrink it to bring the free space outside the extended partition where a primary partition for XP could be created. You would then also need to edit /boot/grub/menu.lst to get the Windows partition into the list.

Sounds a bit daunting to me. You really do need to back up your /home, though; if I'm close on all the moving and resizing that will need to be done, your data will be at risk. And, as a final note, you would need to use a Live CD (the Ubuntu installation one, a GParted Live CD, as examples) from which to boot and do your partition management, as the drive will need to be unmounted for all this to occur.

I invite someone with more experience/knowledge about partitioning to correct any misstatements, errors, etc., that surely must exist above.

---

### Post by avtolle on 2009-03-10
[http://neosmart.net/forums/showthread.php?t=1360](http://neosmart.net/forums/showthread.php?t=1360) is an example of the "common law" about which I spoke. Note the post down thread there which explains that XP can be on a logical partition, so long as it is post SP2, and the partition exists; there is a need to edit boot.ini, it appears, and the Windows boot loader must be on a primary partition, as nearly as I could ascertain from reading there.

---

### Post by DAllenSmith on 2009-03-11
thanks for that avtolle it makes much more sense now, i could have sworn ive done it before but it must have been with a copy that was post sp2, i think im gonna wait untill i can back up my /home partition and then install xp and then put ubuntu on there, guess i should have done that a long time ago, thanks for all your help and info guys! at least it helped me come to a rational decision.

---

