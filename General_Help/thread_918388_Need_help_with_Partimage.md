---
title: "Need help with Partimage"
date: 2008-09-12
forum: General Help
---

### Post by McTek on 2008-09-12
Here are my partitions:
>    Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2549    20474811    7  HPFS/NTFS
/dev/hda2            2550        6688    33246517+   5  Extended
/dev/hda5            2550        3827    10265503+   b  W95 FAT32
/dev/hda6            3828        5078    10048626   83  Linux
/dev/hda7            5079        5283     1646631   82  Linux swap / Solaris
/dev/hda8            5284        6688    11285631   83  Linux

I have an image file on /dev/hda5 and I want to install it on /dev/hda8.
what do I enter in "what file to use" location of Partimage?
The name of the file on /dev/hda5 is /backup/hda9.000

---

### Post by Herman on 2008-09-12
> I have an image file on /dev/hda5 and I want to install it on /dev/hda8.
what do I enter in "what file to use" location of Partimage?You forgot to mention whether you are doing this from an operating system in /dev/hda5, or if you are running a Live CD or some other operating system in a different hard disk or partition.

Assuming you are using a Live CD or an operating system in another hard disk, if /dev/hda5 is not already mounted then you should mount it.  
That's easy to do in Ubuntu Hardy Heron or newer, just look in the 'Places' menu for the icon for the file system you want and click on it and click on it.
Take a look in /media to see what the name of the mount point directory is.
Let's pretend your mount point is called '/media/storage/'
Open /media/storage' and navigate to your file that you want to restore and make a not of the file path, for example, something like '/media/storage/home/mctek/backup/hda9.000'.
That's what to enter in "what file to use" location of Partimage.

By the way, if you haven't already done so, you might need to change the /backup/hda9.000/ file's ownership and permisions or Partimage might not be allowed to open it.
```
sudo chown mctek.mctek /backup/hda9.000
``````
sudo chmod 777 /backup/hda9.000
```

---

### Post by McTek on 2008-09-13
I'm booted from partition hda6 with OS 8.04.1. The name of the partition with the image file has the label of fat32 and is partition hda5 and is formated as vfat32. The image file on hda5 is in folder backup and the file name is hda9.000.
Both partitions are mounted. On partition hda6 partition hda5 is mounted in the media folder as fat32.
I have tried: /media/fat32/backup/hda9.000 and hda5/backup/hda9.000 in both cases partimage is unable to find file. Any ideas?

---

### Post by rraj.be on 2008-09-13
> **McTek said:**
> 
I have tried: /media/fat32/backup/hda9.000 and hda5/backup/hda9.000 in both cases partimage is unable to find file. Any ideas?

This should be the path'

```
/dev/hda5/backup/hda9.000
```

---

### Post by McTek on 2008-09-13
Thanks for your suggestion. I've tried it with hda8 mounted but get error message "can't work with mounted partition". With hda8 unmounted partimage just crashes.

---

### Post by Herman on 2008-09-13
When you start Partimage did you just type 'partimage'? Or 'sudo partimage'? Try it with 'sudo partimage' and see if that helps. :)

---

### Post by McTek on 2008-09-13
Yes I do start Partimage with sudo.

---

### Post by Gannon8 on 2008-09-13
I think the partimage directory is relative to where you start it. For example, if I run partimage from /media/backup and enter in "backup-blah" it should create a file in that directory.

At least that is what I experienced in SystemRecoveryCD. I made a backup and just after it completed, my hard disk crashed.

and I do not believe /dev/hda5/backup/hda9.000 is even a valid path.

---

### Post by Herman on 2008-09-13
The partition where the stored backup files are needs to be mounted.

Try opening a terminal and using 'tab completion' to find out the proper file path to your file to be restored and then paste that into Partimage. 
('Tab completion is when you only type the first few letters of the file's name, then press your 'tab' key for it to automatically self-complete, (just for those who don't know that)).

The partition where you want to the restore to be performed needs to be unmounted, before it can be restored with partimage.

---

### Post by McTek on 2008-09-14
It would appear that my distro does not have "tab completion

---

### Post by Herman on 2008-09-15
Just find the files by navigating to them in GUI mode then if you like, and make a note of the file path as you do so.

---

### Post by Hobbez on 2008-12-13
As with anything I do it always starts with a story. 

I am using the partimage off of the system rescue-cd and it works great. There is an awesome [how to]("http://lifehacker.com/software/geek-to-live/partition-and-image-your-hard-drive-with-the-system-rescue-cd-292972.php#viewcomments") which shows you everything that you need except how to restore the image. What good is a backup if I don't even test that it works? So I decided to try a restore, just to see. Well I ran into trouble, and the trouble was of the most frustratingly simple kind that only newbies like me can ever find. No amount of words typed into google would help, and at an attempt to reach out to the ones who might come after me, I will try to display my searches here. 

how to select a checkbox partimage
Restore partition from an image file checkbox problem
mark a checkbox in partimage

I have had this same problem with another thing like this, I was convinced that it had to be triggered by some key on the keyboard, and partly in frustration I began mashing keys. Sure enough, I found it, but what key was it? I began a systematic pressing of every key on the keyboard, and sure enough the last one that i pressed worked. 

To select or mark a checkbox in partimage use the spacebar.

Thats it. Other than that I did include the full path with the zeros.
/mnt/windows/winrestore/nameofimage.partimg.000

Low and behold, my problem was solved. 

It really does work well, it reminds me of Norton Ghost, except it actually works with sata, and instead of taking 1/2 hour to boot into a crappy little gui, it boots into a really cool os with other valuable tools. 

Just correcting other solutions I found: no, it does not matter if you run partimage from the folder where the files are stored. You just need to include the full path. Since I haven't tried it without the full path I don't know if that even works, it could, but I'm sticking with my way.

-Hobbez

---

