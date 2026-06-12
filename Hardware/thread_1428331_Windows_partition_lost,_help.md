---
title: "Windows partition lost, help"
date: 2010-03-12
forum: Hardware
---

### Post by Khalyd on 2010-03-12
Hello everyone,

Sorry if I posted this wrong but I am going nuts right now. I did have a windows 7 installation on my laptop with 1 HDD 320 GB and 2 partitions, 85GB and 225 GB or something like that. My windows was installed on the 85 GB partition called ACER[C:] and my stuff/documents were saved on partiton DATA[D:] with 225 GB. Now I was just working and installed Partition Magic and wanted to delete it cause I didn't needed it anymore but then my laptop started to crash and when I started up again I got the Bluescreen. I started it again with my windows 7 installation disc and saw that the ACER partition was gone and there was only the DATA partition which turned from D: to C:

Now I do want to start system restore in windows but I can't cause the C: doesn't contain the program, the C: now has only documents from my DATA partition. So I though let's use the Ubuntu LiveCD I had and open a partiton manager to make the ACER partiton visible again. 

I did Sudo fdisk -l and got the following:

Disk /dev/sda: 320,1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbaacfcd5

Device Boot     Start    End       Blocks       ID  System
/dev/sda1       1        27707     222555453+   7   HPFS/NTFS
/dev/sda2       27707    38914      90021569    7   HPFS/NTFS

As you can see, The sda1 is now my DATA partition and the sda2 is my ACER partition which contains the windows installation. How can I fix it so my DATA partition becomes sda2 and ACER (bootable) partition becomes sda1 because I think that's the solution or am I completely wrong

---

### Post by Khalyd on 2010-03-12
Nobody knows how to fix it or help me further, here in the Netherlands it's already past midnight and I would love to fix it as soon as possible, please, help me

---

### Post by srs5694 on 2010-03-12
First, back up your partition table. Get a command prompt (aka terminal or bash) window in your recovery cd and type:

```

dd if=/dev/sda of=backup-sda.mbr bs=512 count=1

```

Be *sure* to type that correctly, especially the if= and of= options; if you reverse if= and of=, you'll copy from the file to the partition table, which will wipe it out (or would if the file were non-empty). Once you've got the file, copy it to an external medium (a USB flash drive, say, or even a floppy disk). If you end up making things worse, you can restore your partition table from the backup.

With that out of the way, it's conceivable that the problem is that your boot partition isn't marked as bootable (aka active). You can set a partition bootable with the 'a' option in Linux's fdisk. I'd therefore try that first.

If that fails, you can swap the /dev/sda1 and /dev/sda2 identities as follows:


[list=1]
[*]Launch fdisk
[*]Type 'u' to change the display units to sectors.
[*]Type 'p' to display the partition table. Write down the exact start and end points of both your partitions. Verify that your numbers are correct. Verify that your numbers are correct again. Verify that your numbers are correct a third time. If your numbers are wrong, it's Very Bad. Proceed at your own risk.
[*]Use 'd' to delete both your partitions.
[*]Recreate both your partitions by using the 'n' option, but create /dev/sda1 with the original /dev/sda2 numbers and vice-versa.
[*]Change both your partitions' type codes using the 't' option. Both should be type 7.
[*]Review the numbers you entered. If they're correct, type 'w' to save your changes.
[/list]


I recommend you then try mounting the partitions. If your emergency disc is capable of mounting NTFS, they should both mount OK. If they don't, and if you're sure your emergency disc can mount NTFS, then something is wrong; you may need to restore that backup you made earlier.

Good luck!

---

### Post by Khalyd on 2010-03-13
Thanks for your respond and help, I tried the things you said, creating a backup for the partitiontable didn't work because didn't have permission to do so. All the other things didn't work because I got a lot of messages I couldn't figure it out. In the meanwhile I got the idea to move all my data to the ACER drive and then in windows do the installation on the DATA drive. I think I can then open disk management and then make the ACER drive visible and then move the stuff back to DATA and reinstall everything. I don't see another quick solution. Thank you for your help

---

### Post by IcarusR on 2010-03-13
When you've resolved this get yourself an external drive & do a copy of your DATA drive. Then when something like this happens you can format & restore backup, which is much less painful than trying loads of things hoping it will work.

One can never have enough backups.

---

### Post by srs5694 on 2010-03-13
You must normally work on low-level tasks like this as root. Either log in as root (which is disabled in a default Ubuntu installation, but works with most recovery CDs) or type "sudo" before each command.

---

