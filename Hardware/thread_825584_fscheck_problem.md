---
title: "fscheck problem"
date: 2008-06-11
forum: Hardware
---

### Post by sambarluc on 2008-06-11
Hi everybody, after formatting (with gparted) in ext3 my previous windows-dedicated partition (sda1) on my Thinkpad T41, I get the following message on booting:

[FONT="Courier New"]fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=9688A52288A5023B'
/dev/sda4: clean, 23178/4578560 files, 6853237/9153033 blocks (check in 3 mounts)
fsck died with exit status 8[/FONT]


Anyway, if I exit from the root terminal I get, booting continues normally, and I can use sda1 with no apparent problem, even though I do not see it under "storage media".
I use kubuntu hardy.

Thanks!

---

### Post by Herman on 2008-06-11
Hello sambarluc,
I think your problem is probably in your /etc/fstab file.
You have deleted a file system and created a new one. 
Now you just need to edit your /etc/fstab file with the details.

You may need to delete the entry for what used to be there and replace it with a newer entry something like this,
```
# /dev/sda1
UUID=4f7aaf26-a20b-42f1-9838-1aa224afbf76 /media/sda1     ext3    defaults        0       2
```Run a command like, '[COLOR=#000000][FONT=Bitstream Vera Sans Mono]ls /dev/disk/by-uuid/ -alh' or 'sudo blkid' for a list of your partitions and UUID numbers.
[/FONT][/COLOR]```
ls /dev/disk/by-uuid/ -alh
```Copy the output from that command.
  
open your /etc/fstab file,
```
sudo kwrite /etc/fstab
```Paste your UUID numbers at the bottom of your /etc/fstab file just for now.

Compare the UUID numbers and partitions in your /etc/fstab with the UUID numbers and partitions in your file, and find the one in your file that needs updating. (sda1).
Copy your new file system UUID number and paste it over the top of the one I gave as an exapmple to overwrite it.

Save and close the file.

In case it's still not clear, here's a link, [About /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with").

---

### Post by sambarluc on 2008-06-11
Great!
Thanks

---

