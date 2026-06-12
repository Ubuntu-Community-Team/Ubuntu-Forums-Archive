---
title: "Restoring a XP image made with PartImage"
date: 2008-10-01
forum: General Help
---

### Post by palian on 2008-10-01
Everything goes well until I try to boot the XP partition that was made from a restored image.

I wanted to attempt a backup and restore of the XP partition that is part of my dual boot setup. I made the original image with Partimage in the SystemRescueCd. I save the image to a new drive after formatting the drive with several EXT3 partitions and one NTFS partition. The NTFS partition clean and freshly formatted. 

Everything goes smoothly till I try booting into the Recovered partition. XP hangs at the "Welcome" screen that precedes the log on screen. Nothing I do fixes the problem including "fixmbr" , "fixboot", and replacing the NTLDR and NTDETECT files. 

Running fixmbr and fixboot together only makes things worse to the point were the boot sequence automatically fails saying it cannot find the NTLDR file.

The only I have gotten it to boot is using a XP Pro CD and letting the CD recover the partition instead of overwriting the old one in the install process. When this is done the boot drive containing the OS is labeled E: instead of C: like in the original partition. Several programs do not work because of this, ironically they are all windows or windows-geared programs; the open-source programs have no problems as far as I can tell.

Any one have any ideas or suggestions? :confused:

---

### Post by dcstar on 2008-10-01
> **palian said:**
> 
..........
The only I have gotten it to boot is using a XP Pro CD and letting the CD recover the partition instead of overwriting the old one in the install process. When this is done the boot drive containing the OS is labeled E: instead of C: like in the original partition. Several programs do not work because of this, ironically they are all windows or windows-geared programs; the open-source programs have no problems as far as I can tell.

Any one have any ideas or suggestions? :confused:

If Windows boots up to E:, then does it also see C: and D: drives?

You may have to edit the boot.ini file on the original image to ensure that it is set to the correct partition that you have restored it to (unlikely to be the same).

Anyway, the best way to run XP is as a Virtual Machine under VMWare - you can even use their free converter to turn an existing working system into a VM (search the Virtualization forum for more).

---

### Post by palian on 2008-10-01
1)It does not see the C: and D: drives. Reason being is that the original XP partition is on SDA1. An image is made from SDA1 and is stored on SDB5, a EXT3 partition on a new and completely separate hard drive from that of which SDA1 resides. The Image on SDB5 is then restored to SDB1 on the same hard drive.

When I try to boot the newly restored partition, I disconnect the Drive that contains SDA1 because XP will boot to SDA1 after stumbling upon it when trying to boot SDB1.

2) I did not see anything a miss when looking at the boot.ini file.

3) I am going to be using virtualization but this is an experiment and I will still need a XP partition to connect to work, play AoC (if I don't quite soon), and play around with SQL Server for work.

---

### Post by palian on 2008-10-01
I guess one question I should ask is: what happens to the Windows MBR when Ubuntu and Grub are installed for dual booting. Is it replaced or modified?

---

### Post by bodhi.zazen on 2008-10-01
> **palian said:**
> I guess one question I should ask is: what happens to the Windows MBR when Ubuntu and Grub are installed for dual booting. Is it replaced or modified?

When you install Ubuntu the MBR is replaces, the windows boot program is replaced with grub.

---

### Post by palian on 2008-10-01
So the problem is quite possibly that there is no MBR associated with XP image. But would it even get as far the "welcome" screen if that was the case?

Does Ubuntu ditch the windows version completely or just push it off to the side?

Should I make use of Grub on that hard drive to get the XP to boot?

---

### Post by WWSmith36 on 2008-10-01
I just want to make a general comment.

I´m not sure if this will help, but windows is kinda funny about certain things.  Windows requires that is must installed on the first drive of the machine (hd0) plus it must reside on a primary partition, not a logical partition.

Hope this helps

---

### Post by palian on 2008-10-01
Thanks, for the record that is the state of the of the partition. The NTFS partition on the new drive is HD0 and is a primary partition.

This makes me wonder if there is a way to recreate the Windows MBR if Ubuntu replaced it completely.

---

