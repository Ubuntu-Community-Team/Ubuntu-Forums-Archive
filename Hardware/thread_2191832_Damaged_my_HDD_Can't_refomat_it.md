---
title: "Damaged my HDD? Can't refomat it"
date: 2013-12-04
forum: Hardware
---

### Post by koffyr on 2013-12-04
So, a little previous history.

I have a cpu i use as a media center running xbmcbuntu. It has one SATA drive and one ATA drive. On the SATA drive is stored the OS and on the other the /home folder.

Last friday I added a IDE DVD drive on the same cable as the ATA drive. Since it was late, and I was feeling lazy, I didn't remove the HDD to propperly read the label and see which one was the jumper to set it to master mode, and I accidentally set it to max 32 GB (I realized this later). So I booted up xmbcbuntu, the DVD drive didn't work, but I say'd "f*ck it, its too late", preceeded to copy some files onto the /home folder and went to sleep.

Th following morning I kept feeling lazy, and watched a tv show which was sotred in the /home/TV Shows folder of the media center from my Netbook via samba (this is to refer that tha drive was working propperly, at least apparently).

Later that day, I opend the case and set the jumpers propperly (here is that I realized I had done it wrong earlier). I rebooted  to see if the DVD would work now. Instead, the OS halted at the splash screen.

I booted up lubuntu form a usb and checked the drives. The SATA drive seemed all fine, but the partititon on the ATA drive was missing, no partition table present.

The data on the drive was of no particular value, so I don't mind losing it, still, I tried testdisk to see if it did anything. Wasn't able to restore the data.

So I booted into lubuntu again and tried to repartition the drive. First, I created a new partiton table (default MS-DOS), and tried to add a ext4 partition the size of the drive. I got back an error message saying "The partiton can't reside outside the drive". If I tried to do this once again I got a message saying there was no partiton table present, and that I should create one.

So I tried with fdisk. I wrote a new partition, and tried to see it with gparted. Didn't work. I verified the partiton table with fdisk, and got an error message saying something was wrong and that it would be corrected upon writing, so I wrote the changes and tried to create the partition once again. Still, nothing. I zero filled the partiton table. Nothing.

On a side note, opening lubuntu's Drives tool and doing a SMART check returned "Drive ok. One bad sector."

Could it be that the bad sector is the sector where the partition table is to reside, and thus the drive is dead? Is there any way I can make it work again?

Cheers!

---

### Post by sudodus on 2013-12-04
From the manual page ```
man e2fsck
```

```

       -c     This option causes e2fsck to use badblocks(8) program  to  do  a
              read-only  scan  of  the device in order to find any bad blocks.
              If any bad blocks are found, they are added  to  the  bad  block
              inode  to  prevent them from being allocated to a file or direc&#8208;
              tory.  If this option is specified twice,  then  the  bad  block
              scan will be done using a non-destructive read-write test.

```

Make partitions with gparted. Unmount the partition (to become root partition). And then I would suggest that you run the following command

```
sudo e2fsck -cf /dev/sdxy
```

where ***x*** is the drive letter and ***y*** is the partition number (for example /dev/sda5 if the fifth partition on the drive a).

---

