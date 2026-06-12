---
title: "Ubuntu installed to drive now showing as mass storage drive"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by wwynn on 2009-10-04
Trying to get access to a drive on which I installed Ubuntu 9.04 Desktop. Steps/info:
- Main drive was Windows XP Pro, 2 partitions, C: important
- Second drive added, 250 GB, also SATA2 
- Ubuntu live CD booted and Ubuntu installed to second drive
- 8 GB swap was first partition and the rest was ext3
- When asked to install GRUB, said Yes (Maybe not good!)
- Used the system several times, preparing to back up the Windows C: drive
- Using fdisk and dd, backed up Windows C: to the Ubuntu drive
- Shut down system and unplugged the Ubuntu drive
- Windows boot failed with Grub error 21
- Windows boot with XP CD in USB-connected DVD drive also failed, same error
- Copied zeros to the first 446 bytes of the MBR
- Windows boot still failed from USB-connected DVD drive 
- Windows boot with XP CD in IDE DVD drive worked (Finally tried that!)
- With XP Recovery Console, ran FIXMBR. Grub removed.
- Also quick-formatted the partition (DUMB! I assumed that the Ubuntu drive would be accessible)
- Shut down system. Disconnected XP drive; connected Ubuntu drive
- Now, booting with Ubuntu live CD or Knoppix shows Ubuntu drive as "Mass Storage Drive" and is not readable.
- Running the first install steps of Ubuntu to partition editor (manual setup) shows no partitions installed, just /dev/sda. The only partition buttons enabled are "New partition table" and "Undo changes to partitions".

Is the Ubuntu drive info recoverable and if so, how?

---

### Post by wwynn on 2009-10-11
More info:

When the drive is attached to a secondary SATA channel in a Windows XP system, FTK Imager Lite can see the drive and show the hex contents.

The first 32 lines are zeroes. "Grub" appears later once or twice, and one phrase is "Grub level 2".

I can copy lines from FTKI but they do not paste as viewed, with the hex on the left and text on the right. Anyone know of an app that will format this as viewed? A screen shot captures only a few lines; a text paste would handle more.

---

### Post by mechro on 2009-10-11
First of all, some of those procedures you've listed are quite astounding. What made you cobble together such a brilliant sequence of events? ;)

Anyway, as far as I can tell you've messed up the partition table for your second drive (Ubuntu). Some data may be recoverable using something like *testdisk* available via synaptic.

Good Luck.

---

### Post by louieb on 2009-10-11
> Copied zeros to the first 446 bytes of the MBRGood the partition table is still intact. Partition table starts at byte 467.
The  [Super Grub Disk]("http://linux.softpedia.com/progDownload/Super-Grub-Disk-Download-8071.html") is probably the easiest fix. It at least will be able to boot you your Ubuntu install.

And from there you can alter the MBR to load Grub .(super grub can do it too) or  see [3.2 Installing GRUB natively]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively") from the [GNU GRUB Manual 0.97]("http://www.gnu.org/software/grub/manual/grub.html")

---

### Post by louieb on 2009-10-11
> - Also quick-formatted the partition (DUMB! I assumed that the Ubuntu drive would be accessible)

Which drive the one with XP or ubuntu? 
May be able to recover with [TestDisk - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk")  available or the  [SystemRescueCd]("http://www.sysresccd.org/Main_Page")

---

### Post by mechro on 2009-10-11
[QUOTE="wwynn"]- Ubuntu live CD booted and Ubuntu installed to second drive
- 8 GB swap was first partition and the rest was ext3
- Using fdisk and dd, backed up Windows C: to the Ubuntu drive[/QUOTE]

To me, that implies Ubuntu has gone, but perhaps I'm wrong. :confused:

---

### Post by wwynn on 2009-10-12
Thanks for the suggestions. I will follow up with them in the next day or two.

Just to answer questions above:

- The "dd" steps are partly from _Backup and Recovery_ by Preston. His "backupcentral.com" had more info. That might be where I got the info on zeroing out 446 (466?) bytes instead of 512. The boot info is gone but the partition table should be there. I also have some help from a computer security expert at work. 

- The drive that was quick-formatted is now fully formatted. That was the Windows drive. The Ubuntu drive is untouched, unless Windows has done something to it automatically.

Again, I will post results later, as I have them. Thanks for your help.

---

### Post by mechro on 2009-10-12
> **wwynn said:**
> Thanks for the suggestions. I will follow up with them in the next day or two.

Just to answer questions above:

- The "dd" steps are partly from _Backup and Recovery_ by Preston. His "backupcentral.com" had more info. That might be where I got the info on zeroing out 446 (466?) bytes instead of 512. The boot info is gone but the partition table should be there. I also have some help from a computer security expert at work. 

- The drive that was quick-formatted is now fully formatted. That was the Windows drive. The Ubuntu drive is untouched, unless Windows has done something to it automatically.

Again, I will post results later, as I have them. Thanks for your help.

Yes, but you are saying you *"Using fdisk and dd, backed up Windows C: to the Ubuntu drive"*. Did you make a separate partition on the drive for the back-up? If you've just copied over Ubuntu then no matter how intact the partition table is, Ubuntu is lost and only recoverable using a data recovery tool.

---

### Post by wwynn on 2009-11-25
TestDisk recovered the partitions and file structure. I now have four copies of the critical data, two directly readable.

Mechro and Louieb, thank you for your suggestions. I see now that I could have saved you and me some time by being clearer in my original description. Instead of
  "- Using fdisk and dd, backed up Windows C: to the Ubuntu drive",
I should have said,
 "- Used fdisk-l to save a description of the WinXP partition data on the Ubuntu drive
  - Used dd to copy the WinXP mbr to the Ubuntu drive
  - Used ntfsclone to copy the 80 GB WinXP partition to the Ubuntu drive."

I would have looked at TestDisk sooner but I though that FTK Imager would do more. FTKI was the program that my friend at work had suggested, and I was working with him on it, from time to time.

Louieb, I made a SuperGRUB disk but did not get anywhere with it. At that point I did not have a copy of the drive to be recovered and I did not want to alter it. I don't know if that would have worked or not, but thanks for the suggestion.

Over and out.

---

