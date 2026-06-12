---
title: "help changing read only partitions for ntfs drives"
date: 2008-09-17
forum: General Help
---

### Post by cparx on 2008-09-17
Hello, I am only running Ubuntu, but I do have a second hard drive with ntfs partitions.  I have it automounted and all, but I can't write to the drive in Nicotine.  Permission denied: '/media/disk'

I know I need to add a "rw" thing in fstab - I just don't know where to add it.  Thanks for your help.

# Entry for /dev/sda1 :
UUID=1add3f49-b365-45c0-87c4-766fb511a89e / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=6c659742-213a-44e8-a4e1-434bab83bb56 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb6 /media/torrents\040-\0403 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb1 /media/sounds ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb5 /media/torrents\040-\0402 ntfs-3g defaults,locale=en_US.UTF-8 0 0

---

### Post by northern lights on 2008-09-17
What release are you running?

Since Gutsy (maybe even Feisty, don't remeber) NTFS partitions should automatically be read/write.

```
sudo apt-get update && sudo apt-get install ntfs-3g ntfs-config
```and the subsequent running of ```
ntfs-config
```should allow you to enable write support, anyhow.

---

### Post by cparx on 2008-09-17
Thanks for the prompt response, I added write support for internal and external device in ntfs config - but I still get the same error in Nicotine.

---

### Post by EmanresuusernamE on 2008-09-17
> **cparx said:**
> # Entry for /dev/sda1 :
/dev/sdb6 /media/torrents\040-\0403 ntfs-3g defaults[COLOR="Red"][SIZE="4"],rw[/SIZE][/COLOR],locale=en_US.UTF-8 0 0

/dev/sdb1 /media/sounds ntfs-3g defaults[COLOR="Red"][SIZE="4"],rw[/SIZE][/COLOR],locale=en_US.UTF-8 0 0

/dev/sdb5 /media/torrents\040-\0402 ntfs-3g defaults[COLOR="Red"][SIZE="4"],rw[/SIZE][/COLOR],locale=en_US.UTF-8 0 0
Try adding the large red text to your fstab file.  That should force it to be read/writable if there are no errors.

If that doesn't work, you'll need to force it to boot by using the manual mount command with the following:
-o force

---

### Post by cparx on 2008-09-17
I added the "rw" - thanks, that's what I thought I needed.  But for some reason I still get the same error in Nicotine.  

Where should I add "-o force" right after "locale=en_US.UTF-8 0 0"?

I'm heading out to work now, I appreciate your help.

---

### Post by EmanresuusernamE on 2008-09-17
Nope, it's mainly there if your windows didn't shutdown properly:

sudo mount /dev/<Windows Partition> /media/<Location for Partition> -o force -t ntfs-3g

You may need to use mkdir like so first though:
sudo mkdir /media/<Location for Partition>

---

### Post by cparx on 2008-09-18
So I went back and did the mkdir thing, and it turns out that I already have set up the directory.

mkdir: cannot create directory `/media/sounds': File exists

Any other thoughts?

---

### Post by EmanresuusernamE on 2008-09-18
The name is cosmetic, and can be anything.  It could be "Ireallyhatewindowsandandthinkitblows" and Linux wouldn't care.  So long as you type everything carefully, and make sure you have the proper case (lower vs. UPPER).

---

