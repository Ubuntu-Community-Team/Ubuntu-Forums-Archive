---
title: "Hard drive problem"
date: 2012-11-24
forum: Hardware
---

### Post by tatmark1 on 2012-11-24
I have a seagate 500gb hard drive. the problem is it is completely unrecognizable..I have it in a case with usb connection. I know it is good and works...I had done something to it to hide some information on it but i do not remember what i did...the problems with a brain injury i guess.... can anyone help me

---

### Post by The Cog on 2012-11-24
Are you trying to recover information from it, or just make it useable as a disk again?

Either way, what's the output from 
```
sudo fdisk -l
```
with the disk plugged in?

---

### Post by tatmark1 on 2012-11-24
I would like to attempt to recover any information on it first but if not i would like to make it useable again

I typed fdisk -l and I am getting nothing from that hard drive at all

---

### Post by The Cog on 2012-11-24
If fdisk doesn't even tell you the disk is there (and its size) then I think it's probably broken. I would suspect a failed controller.

---

### Post by tatmark1 on 2012-11-24
well it is running i know that i had it up for a min the otherday but now i cant get it

---

### Post by tatmark1 on 2012-11-24
with a disk utility all i get is this
hard disk
/dev/sdb
model ST3500820AS
size---
serial number 5QM1TSDF
assesment disk is ok, one bad sector

---

### Post by NikTh on 2012-11-24
Hi , 
you can use the [TestDisk Utility]("http://www.cgsecurity.org/wiki/TestDisk") to try recover of partitions/folders/files. 
Step by step guide can be found [here]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step").

You can test your drive (if supports s.m.a.r.t) with smart tools and see what happens. 
```
sudo apt-get intstall smartmontools --no-install-recommends
sudo smartctl -a /dev/sdX
```replace X with your disk's letter. /sda/ or /sdb/ ..etc. 
Compare the results with the attributes [here]("http://en.wikipedia.org/wiki/S.M.A.R.T.#ATA_S.M.A.R.T._attributes") to see if your Hdd fails. 

You can use various tools to try re-format the drive or even create a table (msdos preferred) from the scratch. 
You can use [Gparted]("https://help.ubuntu.com/community/GParted") (included on Live-Ubuntu) 

Thanks

---

### Post by tatmark1 on 2012-11-24
yeah gparted hasnt detected it yet I have it installed on my comp and a live disk

---

### Post by PapaNerd on 2012-11-24
About a month ago I was able to salvage data off an external USB drive by bypassing a bad controller in the case and temporarily connecting the drive directly to the motherboard with SATA cables.

If it isn't recognized by the BIOS at that point, then it is done for unless you engage one of the services that removes drive platters and reads them in another device (and that is quite expensive).

---

### Post by tatmark1 on 2012-11-24
well i tried hooking up like that too

i had changed the file system on this drive from ntsc to something else like ext4 or something stupid
i have no clue why i did this again i am blaming it on the brain injury

---

### Post by NikTh on 2012-11-25
> **tatmark1 said:**
> 

i had changed the file system on this drive from ntsc to something else like ext4 or something stupid
i have no clue why i did this again i am blaming it on the brain injury

Well , at my opinion the ext4 filesystem is light years away from the deprecated NTFS ms filesystem that corrupts and fill the disk with fragmented data. 

Is not the filesystem that did the damage. 

Please see post #7 and use smart tools to see if your disk is damaged. 

Thanks

---

