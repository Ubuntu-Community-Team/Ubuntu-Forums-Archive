---
title: "Formating IDE Master &amp; Grub"
date: 2008-11-28
forum: General Help
---

### Post by Merovius on 2008-11-28
On a system with two SATA drives used for Windows and Ubuntu, and, a ATA drive as the IDE Primary master, A previous install of Ubuntu is on this ATA drive. Grub installed on the ATA drive.

The PC is booting from the ATA drive, obviously. If I wanted to format the ATA drive for other uses, will I wipe out Grub?

If as I think, I will, How do I get grub either on one of the SATA drives or repair it?

Or, in the interest of simplicity should I not format this drive but just delete the files it contains and edit Grub to remove the old install?

Ideas appreciated. Thanks. :)

---

### Post by jerrykenny on 2008-11-28
Grub wont necessarily be wiped unless . . . . . you have /boot mounted on the ata drive.

Do you ?

If so . . . .then you should leave that /boot partition intact.

---

### Post by Merovius on 2008-11-28
:)

Whoosh,  that went right over my head. LOL

I honestly have no idea what that means. Sorry. I installed Ubuntu on to this drive after adding it to a computer with XP installed on a SATA drive. (XP installed when only the SATA drive was there.) Grub installed on the ATA drive with Ubuntu as it was the master of IDE 1. Then  the second SATA was added and Ubuntu was installed onto that drive. Grub was updated and stayed where it was. I (he) can now boot from XP or Ubuntu or Ubuntu II. 

Can you tell anything from that?

---

### Post by jerrykenny on 2008-11-28
Also , further advice will be dependant on your posting the results of "df" . . . so we can see how ubuntu reports your disk drives

Its a little obscured you see . . . cos ubuntu seems to report some pata hard drive partitions as sda1, sda5, . . . when youd expect it to say hda1 , hda5 etc etc

---

### Post by Merovius on 2008-11-28
I will get him to run "df"

---

### Post by jerrykenny on 2008-11-28
Yes thats better . . . it seems as though your system is booting the old ubuntu (on the PATA) drive, using the grub setup from the new Ubuntu (on the SATA drive).

Which is good . . . . but i'm still cautious because . . .

Even your new Ubuntu may be booting from the mbr of the PATA drive

Have a look at your BIOS, and see what the boot order is . . .

ie is the BIOS looking to boot from the SATA drive . . . some BIOS's incidentally dont like to boot from a SATA disk, if the SATA disk is on a SATA PCI card.

But if your SATA ubuntu is COMPLETELY located on the SATA drive, then you should be OK . . 

I'd also take the precaution of installing grub to the MBR of your first SATA drive . . . 

sudo grub-install (sd0)

and make sure that the SATA drive can be set as the first boot device on your BIOS . . . . in which case you could then physically remove the old PATA drive and still have a bootable system

---

### Post by caljohnsmith on 2008-11-28
How about open a terminal in Ubuntu (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like as far as where Grub is. Also, are you trying to keep the Ubuntu you have installed to your SATA drive? And what do you plan on doing with the ATA drive? Can you set your BIOS to boot the Ubuntu SATA drive or can you only boot the ATA drive?

---

### Post by Merovius on 2008-11-28
Now that made a lot of sense to me. The pc originally booted from the XP SATA drive. When the PATA drive was installed and Ubuntu was installed on it, the boot order was changed to boot from the ATA drive or it would go straight into XP.

Now that a second SATA drive has been installed with Ubuntu, It must be booting from the PATA as we did not change the bios boot order. 

"I'd also take the precaution of installing grub to the MBR of your first SATA drive . . . " 

 This sounds like what we need to do. Then set the bios to boot from the new SATA drive.

Sound right?

Thanks again.

---

### Post by Merovius on 2008-11-28
caljohnsmith,

I am not at the computer in question at the moment. Will try to get him to run the commands when I can get him on the phone.

I am trying to save the new SATA Ubuntu install. I believe that both installs of Ubuntu put GRUB onto the Primary Master (PATA) drive by default. I do not think I can boot from the SATA drive as of yet. 

If I do as sugeted above and install GRUB on the SATA drive I think I will be good to go.

The old PATA drive will just be for storage space when formated.

Thanks

---

### Post by jerrykenny on 2008-11-28
So id boot into ubuntu on the new SATA drive and run

sudo grub-install sd0 

Then turn off the pc . . . 

Unplug the PATA drive . . . 

And attempt a reboot . . . . just to se if the system is completely independant of the PATA drive, and crucially, this situation will be REVERSIBLE !  (by reconnecting the PATA)

You may have to enter BIOS and change the boot order

---

### Post by Merovius on 2008-11-28
Sounds like the ticket to me. When I get hold of him we will do this.

Thanks everyone for the help!  :popcorn:

---

### Post by jerrykenny on 2008-11-28
(thinks) should i have said . . 

sudo grub-install hd0   or hd1    ?

depends how the disks are seen by the bios . . . . hd0 is probably the PATA drive . . . and hd1 is probably the first SATA drive . . . 

so you probably want 

sudo grub-install hd1

---

### Post by Merovius on 2008-11-28
Will have to look in the bios first. Make sure which is which.

I believe the first SATA is the XP drive. 

The first PATA drive is the old Ubuntu drive.

The second SATA is the new Ubuntu drive.

I don't think it will matter which SATA GRUB is on as long as the bios is pointed there first.

---

