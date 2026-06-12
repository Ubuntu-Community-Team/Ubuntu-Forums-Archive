---
title: "Backups to new 1TB external HDDs running extremely slowly"
date: 2019-03-15
forum: Hardware
---

### Post by stig on 2019-03-15
Hi, I'm having trouble with new Seagate and Toshiba 1TB external HDDs running extremely slow when trying to do backups. My old 500MB Toshiba still works fine and access to other storage such as USB sticks etc is normal. I'm on Ubuntu 18.04LTS and using two identical PCs and they both show the same problem. I've searched these forums but not found a solution and I wonder if other people are having any similar trouble? I've been using Ubuntu for many years and haven't encountered this problem before.

A friend has a similar problem and he thinks it might be something to do with shingled magnetic recording (SMR) used on these new disks. My backups are a mixture of documents and photos and between 10 and 20GB in size and 20,000 to 30,000 files. I do the transfer by copy and paste.

I asked Seagate support about suitability of their external drives for Linux and they replied: `For Linux compatibility, All our external drives work properly with any system. They simply require the generic drivers provided by the Operating Systems. So no specific model works better with Linux or not.'

---

### Post by Autodave on 2019-03-15
Did you format the drive before using it?  If so, what did you format it to: what file system?

---

### Post by oldfred on 2019-03-15
I find copy & paste to be slow.
And if external drive, it will be doubly slow if NTFS as it is not a native Linux format. And you lose all ownership & permissions.

I use rsync to copy to my external flash drives, but they are slow since flash drives. Rsync to external USB3 SSD with ext4 format is very fast.

Post this:
sudo parted -l

---

### Post by stig on 2019-03-16
Thanks for the quick responses and I apologise for being late replying.

Autodave: Initially I used the disks as received (ntfs) as I've read that Ubtuntu should work with that and also it allows the disk to be read, if necessary, using Windows. Both Seagates have been returned to the retailer (after formatting to remove my personal data). I've since tried formatting (in gParted) the Toshiba to ext4. But on mounting the disk I found it was no longer possible to copy & paste files to it, or to create folders on it etc. Therefore I've formatted it back to ntfs.

oldfred: Copy & paste works fast enough for me when backing up to my old 500MB Toshiba: 11.5GB/~18,000 files & folders in 12 minutes (and that's USB2.0, the new disks and my PC are USB3.0). The odd thing is that my first attempts at backing up the data with the two new Seagate disks were fast, at about 6 minutes, but in each case the next backup with the same data would take over 30 minutes and subsequent attempts to back up to them failed (cancelled after about an hour), which is why I returned them to the retailer. With the Toshiba the first run was 16 minutes but, again, subsequent backups were much slower.

Output for sudo parted -l
```
Model: ATA CT500MX500SSD1 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 
Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  538MB  537MB  fat32        EFI System Partition  boot, esp
 2      538MB   500GB  500GB  ext4
Model: TOSHIBA External USB 3.0 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 
Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs         boot
```

---

### Post by oldfred on 2019-03-16
As mentioned, NTFS not recommended for Linux backups as you lose ownership & permissions. If just your data files, it will work but you have to manually reset permissions. But all system files have various owners & permissions and not really possible to reset. So backup of system files to NTFS is not a backup.

Also NTFS needs defrag & chkdsk periodically and you cannot do that from Linux. So only if dual booting from Windows or can connect to a Windows system for those repairs, can you use NTFS. And if connected to Windows you have to make sure the hibernation flag is not set. Windows fast start up auto sets hibernation flag on all NTFS partitions.

---

### Post by stig on 2019-03-16
As mentioned above, I formatted it to ext4 but then couldn't copy & paste files to it, or create folders on it etc via the file manager.

---

### Post by Dennis N on 2019-03-16
> **stig said:**
> As mentioned above, I formatted it to ext4 but then couldn't copy & paste files to it, or create folders on it etc via the file manager.
You most likely just need to change the owner on the ext4 file system you are copying to:

if your user name is john, and the partition in question mounts at /mnt/data,
```
sudo chown -R john:john /mnt/data
```
This will make you the owner of all the files and folders therein, and give you all the needed access.

---

### Post by stig on 2019-03-16
Thanks for that John, I'll note down the command so I can use ext4.

My problem with the slow transfers seems to be resolved. If I use `Compress' in the file manager to make a zip file of my backup files and folders it takes 5 minutes to compress 11.5GB and then 1 minute to transfer it to the external disk. I can do this repeatedly with no loss of speed. Completely different behaviour from when I copy & paste the data.

---

### Post by stig on 2019-03-17
I've realised that readers might be wondering why I didn't try making and transferring an archive before I started this thread. I did try, but Archive Manager isn't working for me. It's only a few weeks since I upgraded from 16.04LTS to 18.04LTS and if I click on the Archive Manager/File Roller icon I get a window but the menu bar words are greyed out and the actual window is blank white. I re-installed via Software Centre and Synaptic but neither way made any difference. Also there is no longer an Archive Manager option in the context right-click menu of the File Manager. I couldn't find anything about it on the web but yesterday another Ubuntu user pointed out that `Compress' in the context menu allows me to make an archive. I guess that would be obvious to a professional but it wasn't obvious to a low-grade user like me!

It seems odd to leave an active Archive Manager icon in the applications list and to have it showing as installed in the Software Centre but not having it work.

---

### Post by rbmorse on 2019-03-17
The archive manager works fine for me.  When you open the application you get a blank window and the options are grayed out.  Drag the archive you want to decompress/extract from the file manager into the archive manager window. The extract button will light up and click on that will get you to the extract options. 

Creating an archive works the same way. Select the files you want to include in the file manager and drag them to the archive manager window. Answer the question to open the options.

---

### Post by stig on 2019-03-17
So it does! Thanks for that, rbmorse. I'm beginning to feel a bit foolish but I've never been a drag-and-dropper, always copy-and-paste, and the window just seemed dead. As they say, you live and learn (and I'm only in my 70s so I've got a lot of learning still to do!).

---

### Post by rbmorse on 2019-03-17
That's Ok. As long as you're learning you're living.  I just turned 66 and got my first social security check last month. I was going to put it toward a new AMD Threadripper powered PC, but the wife had other ideas. Sometimes discretion is the better part of valor. I learned _that_ a long time ago. 

We should open a section here for us geezers.

---

