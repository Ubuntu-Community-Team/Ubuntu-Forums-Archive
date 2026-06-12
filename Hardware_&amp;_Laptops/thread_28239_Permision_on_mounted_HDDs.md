---
title: "Permision on mounted HDDs"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by XplOzIOn on 2005-04-19
Hi, first of all ill say that this new ubuntu its really good and you guys have improve a lot since the first release!!...
    Heres my problem:
               1) Im a noob in linux systems. 
               2) I mounted a HDD in /mnt/Downloads to save all my internet downloads in there. THe problem is that when Azureus try to make a Dir it says it has no permision and i know why. But is there a way to set up that folder where my hdd is mount to be like free of permisions? i know that if i mount the hdd in my home folder there would be no problems at all but i dont really want to mount it there. In my opinion its better to mount hdd on mnt and make shortcuts in desktop.
               3) The other problem is a HDD that i did convert with partition magic from ntfs to fat32 before i installed linux, using "sudo mount -t vfat /dev/hdb/ /mnt/Data/ shoul mount the hdd but since fdisk says this:

Disk /dev/hdb: 10.0 GB, 10005037568 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1215     9759483   54  OnTrackDM6

   Now i believe that im not able to mount the hdd because the fily system is corrupted or something it supposed to say fat32 and not OntrackDM6.

     Can someone tell me in  step be step how to fix this without deleting any of the data in the hdd?. And i really need anyone help because i need to finish ASAP a school work that is stored there.

    Thanks!

---

### Post by FluffyElmo on 2005-04-19
I can help with #2, to change the permissions try:
```
sudo chmod -R 777 /mnt/Downloads
```

This will recursively change the permissions on the folder so everyone can read/write /modify the files. For other options read *man chmod* and it should answer any questions.

---

### Post by XplOzIOn on 2005-04-19
Thanks a lot!, o really apresiate your help!

---

### Post by XplOzIOn on 2005-04-19
If anyone can help me with my others problem that would be great! 





/enjoy ubuntu

---

### Post by luca_linux on 2005-04-19
Yes, we are here...just post!

---

