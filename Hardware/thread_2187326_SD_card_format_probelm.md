---
title: "SD card format probelm"
date: 2013-11-11
forum: Hardware
---

### Post by ads2996 on 2013-11-11
Hi,

I encountered a pronbelm with my micro sd card. I have a 64gb sandisk card in my s3 i use it to download torrents, and is exfat formatted. But recently torrents wernt actually saving to my sd card. So i booted up windowsx and copied all my files off, went off without a hitch. Then tried to format it and recieved an error. So i tried ubuntu but when ever i formatted the drive it wouldnt keep the format i had applied, it is as if it is write protected. Ant help greatly appreciated.

---

### Post by Jonor on 2013-11-12
What app was it formatted with ? Try with Gparted if not already done so and bear in mind 64gb down a slow connection is likely to take a *long* time to format.

---

### Post by ads2996 on 2013-11-12
I formatted it with gparted and it said it had completed, but then when it rechecks the card the exat partation is still there, ive also used windows format and fdisk, i have also ran the linux xheck disk command with no errors

---

### Post by Jonor on 2013-11-12
Could the file system be changed and still work for the torrents ? 
Exfat was greyed out as unavailable when i tried to format a 16GB SD card with Gparted but there were several others that could have been chosen such as btrfs, ext2, ext3, ext4, fat16, fat32 or NTFS.

---

### Post by ads2996 on 2013-11-12
At the moment I don't care what format the card is, the problem is that when I format it to fat32, it says competed then when in open gparted it is exfat again and all my stuff untouched, like bits in read only mode

---

### Post by andyfied on 2013-11-13
I have had this problem with gparted before. The only solution I found was to use the terminal (I deleted the partition and made a new one with parted).

There is also the possibility that your SD card has failed, in which case there is not much you can do with it.

---

### Post by ads2996 on 2013-11-13
i tried via terminal using fdisk, i have contacted sandisk but they haven't replied yet

---

### Post by SeijiSensei on 2013-11-13
After you created the partition with fdisk, did you format it with mkfs?  For instance, if you created a partition set for FAT32 on /dev/sdb, then you need to run

```
sudo mkfs -t vfat /dev/sdb1
```

I just reformatted a 32 GB SanDisk Cruzer Fit to ext4.  It took a very long time.  I kept thinking the device had a problem, but when I ran badblocks against it, it passed the test.  So I just let mkfs run for as long as it needed.  Eventually it was completely formatted.

---

### Post by ads2996 on 2013-11-14
I will try using mkfs when I get home tonight

---

### Post by ads2996 on 2013-11-15
After contacting Sandisk theyvhave said that the card needs replaced, so I m going to contact amazon and see if they will replace rather than sending it to the Czech Republic, thanks for all your help

---

