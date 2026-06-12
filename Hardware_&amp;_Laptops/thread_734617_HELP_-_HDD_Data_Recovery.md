---
title: "HELP - HDD Data Recovery"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by sil3nt on 2008-03-24
Hi Guy's I have an external HDD eSATA which I use to back up and store my core data etc. Up untill now this has been accessable for both Vista and Ubuntu (Duel boot)

Yesterday the Drive stopped apearing in Ubuntu, and when I checked the volume in drive management in Vista it is flagged as unalocated space. 

I can no longer access this drive and I feel like crying because its not backed up and it contains important info.

here is the info from : fdisk -l

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 320.0 GB, 320071851520 bytes
256 heads, 63 sectors/track, 38761 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Disk identifier: 0x8b75067c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      266306  2147483647+  ee  EFI GPT
```

Is there a way of recovering this drive or mounting it  so I can copy over the data? any info or direction on this one would be much appreciated.

Sil3nt

---

### Post by bren on 2008-03-24
yes, dont cry

it is extremely likey that you can recover your data via the testdisk utility..... in the best case scenario the partion table is corrupted / damaged and this is extremely easy to recover.

normally it it best to boot from LIVE CD (System Rescue CD is a good one) but since your drive is external there is no risk to installing some thing new on your normal partition - it will not harm the data you are trying to get .... therefore install via

sudo apt-get install testdisk

it is a console base utility and takes some time to work out what is happening but my experience with this utlitiy is very good

let us know how you get on or if you have specific questions on testdisk

---

### Post by sil3nt on 2008-03-25
Hey Bren,
                 Thanks for your promt repsonse mate I have installed testdisk and I have analysed the drive in question but I am not sure of the steps to take from here. I would under normal circumstances play around with it but I dont want to risk loosing any data.

Here is the output after analysing the drive, where do I go from here?

```
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
TestDisk 6.6, Data Recovery Utility, February 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdd - 320 GB / 298 GiB - CHS 38913 255 63
     Partition               Start        End    Size in sectors


Structure: Ok.


Keys A: add partition, L: load backup, Enter: to continue]
```

Before I run the Analysis client I get this output:```
Disk /dev/sdd - 320 GB / 298 GiB - CHS 38913 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P EFI GPT                  0   0  2 267349  89  4 4294967295

Warning: Bad ending head (CHS and LBA don't match)
No partition is bootable

```

It seems the EFI GPT Dynamic Disk only works in a 64bit enviro which my OS is not, I am not sure if I can change this with testdisk? 

Thanks in advance

Sil3nt

---

### Post by sil3nt on 2008-03-25
Good new's I can get access to the data now with a Deep scan of the drive it finds the NTFS partition containing my files.

I can then copy them to one of my other drives. 

I wonder if there is not a way of fixing it so i may mount it again as normal?

---

### Post by housam on 2008-03-25
Try this guide :[[COLOR="Red"]_https://help.ubuntu.com/community/DataRecovery_[/COLOR]]("https://help.ubuntu.com/community/DataRecovery")

---

### Post by sil3nt on 2008-03-25
Oh Dear things where going so well, I copied my data off the drive to my local drive with Ubuntu installed, I rebooted my machine and I recieved a Grub error 22.

I googled the error and came up with this little gem: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I followed the steps on how to preserve the windows bootloader but it failed when I ran the ```
grub> setup (hd1,1)
``` command.

I then followed the initial steps to write over the windows bootloader so I could get back into Ubuntu.

I used ```
>grub> find /boot/grub/stage1
```
to find my root partition which gave me the drive (hd1,1). I then used the following commands.

```
grub> root (hd1,1)
grub> setup (hd0)
```

This was successful as the bootloader was successfully rewriten, I rebooted from the live CD and I got the Grub Boot screen with Ubuntu but when I selected any of the Ubuntu options I get no partion found error 22 again. 

Much to my suprise though I was able to boot into Wndows, where the hell did I go wrong ? I am assuming this has something to do with the "Setup (hd0) command.

Any pointers or direction would be much appreciated.

Thanks Again

Sil3nt

---

