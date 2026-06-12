---
title: "Duel boot with Vista issue"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by Trinity343 on 2009-10-22
hey i've gone threw and installed ubuntu 9.04 on my computer to do duel booting with my vista however it doesn't seem to want to give me the option at booting to choose which OS i want to use at the time. 

here is what i did -

i went into the vista disk manager and created an unallocated partition of about 6GB. i then proceeded to reboot the computer in order to start it from the disk so i can do a full install on that partition. i went through the steps doing the option for manually choosing the partition. i choose that 6 gig partition and it asked me if i wanted to set up a swap partition which i choose not to as of yet. (i'm not sure how important that is for this problem). i then finished the install and it said it completed and i rebooted. 

instead of giving me the option of which OS to boot from it went straight into vista. any ideas as to why this might be happening?

just to go ahead and get this out there. this will be my first time trying/using any sort of linux OS.

---

### Post by tr4sh on 2009-10-22
i smell something wierd here:
- how come you skip the swap partition creation while installing "jaunty" -> swap is important as it'll be needed to become a somekind of a "temporary storage" / "Virtual RAM", some might do as yours but usually they have a quite slow system respose after.
- on ur description, i assume that you didn't create any "boot" partition, so you directly install ur linux, especially ur "grub" into MBR? hmmm it'll need a lot of effort if someday u want to tear down any of your OS

cmiiw

I suggest u create another partition dedicated to swap and boot, here's my list of partition usage as example:




DISKPART> list partition

  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
  Partition 1    Primary             29 GB  1024 KB  -> WIN 7 Installed (NTFS)
  Partition 2    Primary             54 MB    29 GB   -> /boot (EXT3) -> my Jaunty boot partition
  Partition 0    Extended            68 GB    29 GB   -> Extended partition Prepared for Jaunty
  Partition 4    Logical           3812 MB    29 GB   -> /swap
  Partition 5    Logical             27 GB    33 GB    -> /root (EXT4)
  Partition 6    Logical             37 GB    61 GB    -> /Home (EXT4)
  Partition 3    Primary             50 GB    98 GB   -> DATA Storage (NTFS)




I don't know if any other way to "separate" ur grub from ur MBR, but assume u'll re-install ur OS's from the beginning

- install ur vista first (i know u don't have problem with it)
- restart ur vista in "safe mode using command prompt" (I presume u already now how to use the F8 button)
- once u got in the command prompt, type : "diskpart"
once succeed, ur prompt 'll change like this:

DISKPART>

here's some example using diskpart:

DISKPART> list disk \\showing ur physical disks

  Disk ###  Status         Size     Free     Dyn  Gpt
  --------  -------------  -------  -------  ---  ---
  Disk 0    Online          149 GB      0 B
  Disk 1    Online           37 GB      0 B

DISKPART> select disk 0 \\select disk 0 to perform any next steps to be done in disk 0

Disk 0 is now the selected disk.

if the idea here is to show u options that will enable you to select which OS u might use, than u must load ur grub, in my case, my grub installed in partition 2

so i'll perform this:

DISKPART> activate partition 2 \\transferring "first boot" from sector 0 of the MBR to partition 2 where i stored my /boot

Partition 2 is now the active partition


- type exit to get out of diskpart
- restart ur computer
- boot option appeared.

good-luck

---

### Post by PrePenguin on 2009-10-22
You did not install the grub bootlaoder.. which is what you need to do for dual boot.

---

### Post by Trinity343 on 2009-10-22
well i still have the option of being able to reformat the partition in which i installed the ubuntu OS on so...

basically what your saying is i should wipe ubuntu off and go at it again with similar partitioning as the ones mentioned above? when i was looking at the install instructions on the OS website it never said anything (that i noticed) about a bootloader or grub. is there a special file i need to d/l for it or is it a part of the .iso file i have on the disc i burnt?

---

### Post by Mark Phelps on 2009-10-22
> **Trinity343 said:**
> well i still have the option of being able to reformat the partition in which i installed the ubuntu OS on so...
No need to do something that extreme.

> basically what your saying is i should wipe ubuntu off and go at it again with similar partitioning as the ones mentioned above? when i was looking at the install instructions on the OS website it never said anything (that i noticed) about a bootloader or grub. is there a special file i need to d/l for it or is it a part of the .iso file i have on the disc i burnt?

Don't know about the instructions (haven't looked at them in a LONG time), but unless you're installing inside MS Windows (using Wubi), you have to install a boot loader for Ubuntu somewhere.

You will need to boot from the Ubuntu LiveCD and install GRUB using the following link:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by oldfred on 2009-10-22
If you are just starting out the standard install of / root and /swap is fine. 6GB is somewhat small for root as we normally recommend a minimum of 8-10GB more if you are installing large programs and or storing lots of data. swap used to be 2x memory when memory was only 256 or 512MB. Now swap can be the same size as memory so you can hibernate if a portable. Some users with 4GB or more or memory have run without swap but it is not recommended.

You need Grub installed in the MBR so that you have a choice on which system to boot, unless you have installed wubi. The grub install is the last part to the standard install from the liveCD.

/boot is more for advanced users, servers, special hard drive configurations, or users with very old computers that can only boot from the beginning of the drive.
/home is if you want to keep your settings with out backing up and recovering when you do a clean install of a new verison. You can do updates without losing data and I have since about 6.10 but will do a clean install for Karmic as I have built up too much cruft.
/data is for keeping your large files separate if formated as ext3 or ext4 or for sharing that data with windows when formated as NTFS.

---

