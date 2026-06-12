---
title: "Space used up on USB drive"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by hygraed on 2006-07-26
I have a 128MB Lexar Jumpdrive Sport USB flash drive. About 43MB of space is used up, but I don't know what by. When I browse it, either in the filesystem browser or in the terminal, it shows up as having no files on it but still having 43MB used up. Selecting "show hidden files" doesn't make anything appear either. Any suggestions?

---

### Post by philippe_carlo on 2006-07-26
Go to the terminal. Go to the root directory of the partition and do ```
ls -al 
```
If nothing turns up there, do
```
sudo fdisk -l /dev/<usb-device>
``` to list the partitions on the stick. Maybe the partition just does not fill up the entire disk.

---

### Post by hw-tph on 2006-07-26
If you delete something from the stick from Nautilus and don't use Shift+Del to remove it, it will not be deleted, only moved to a hidden .Trash directory  on the stick. Open a terminal and navigate to the stick and list the contents using **ls -al**.


Håkan

---

### Post by hygraed on 2006-07-26
Okay, I did ls -al on the drive.

```

marshall@marshall-laptop:/media/MARSHALL$ ls -al
total 9
drwx------ 2 marshall marshall 5120 1969-12-31 17:00 .
drwxr-xr-x 4 root     root     4096 2006-07-26 03:33 ..

```
Now what?

To avoid confusion, MARSHALL is the drive label, and marshall is my username.

---

### Post by it.henrik on 2006-07-26
to make this a bit user friendly .. lets do this the GUI way

Plug in your USB-stick.
Go to the PLACES menu.
Open the USB-stick (you should be able to see it there.
go to the VIEW menu .. check Show Hidden Files.

Now you should be able to see everything thats on the stick. If you cant see anything there and you only have one partition on it, I reccomend that you reformat the USB-drive.

Good luck.

---

### Post by jordilin on 2006-07-26
If there's nothing in the drive and 40 sth megas are used, then format your flash drive again. :wink:

---

### Post by hygraed on 2006-07-27
Actually, the drive appears to be fine. I tried using it on my dad's Windows box, and it showed up as being empty (except for the files I had just put on it). But when I plug it into my computer, the 43MB is used up again, leading me to believe that there's some crap on my hard drive somewhere that the system thinks is actually stored on the flash drive.

---

