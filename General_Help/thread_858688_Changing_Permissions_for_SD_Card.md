---
title: "Changing Permissions for SD Card"
date: 2008-07-13
forum: General Help
---

### Post by SlalomMan on 2008-07-13
I have a MicroSD card and I use an SD adapter to use it in my laptop, a Toshiba Satellite A205-S4617. The way the current situation is, on my account I can view the files on the disk and copy them to my hard drive, however, I cannot write files. I have read only access. In order to write files to the SD card, I have to run "sudo nautilus" or "sudo thunar" to gain r/w access. This is fine, but it's very inconvenient and when I go to disk properties as root, it won't let me change the settings. I can select my account and try to make it read and write, but it immediately reverts to read only. Any suggestion? Is there any way that I could erase the settings for this and start over?

My usb microSD reader has an invalid mount option; i can't mount it to remove the option. Any suggestions on this?

Thanks in advance!

---

### Post by Afkpuz on 2008-07-15
Well, I know the actual mount place of your sd card is going to be in /media/

If you don't have any other external media, your SD will be listed as "disk".  Here's how to change permissions on it.


```
sudo chown yourusername /media/disk/ 
```

If your sd card is listed as something other than disk, just change "disk" to whatever its called.

Now, you should be able to right click on /media/disk/ and change permissions.  Please note, I don't think you can ever get into permissions by clicking on the desktop icon. Make sure to go through /media/disk/

---

### Post by SlalomMan on 2008-07-17
I just tried that, and I get the following result:

```
chown: changing ownership of `/media/disk-3': Operation not permitted

```

Also; the SD card is the only media I have in but every time I reinsert it, I get another folder in the media folder. It used to be that everything was "disk" and if I put in an additional media device it was "disk-1" and so on; now it creates a new "disk-#" folder every time I reinsert my card.

---

### Post by evets25 on 2008-07-17
Because removable media are automagically mounted and handled for you, you can't change their permissions - even as root. Just ignore the permissions completely and let ubuntu manage it, and you'll find everything will work.

---

### Post by SlalomMan on 2008-07-17
The only problem with that is that I can't read or write files as a normal user, I have to run "sudo nautilus" to be able to manage my files on the MicroSD card. It's not a huge problem, but it's inconvenient.

(on a side note, my XP partition on my hard drive won't let me modify files either, unless I run nautilus as root)

---

### Post by Afkpuz on 2008-07-17
Thats strange because I had to do that with my external usb drive and used that method.  Did you use sudo?

---

### Post by SlalomMan on 2008-07-17
Yes, I used sudo. I've tried everything; mounting with sudo then changing permissions as my normal user (you can't change permissions as root through nautilus, I don't think). I also can't change permissions on my XP partition; is that different because it's NTFS? My MicroSD is FAT16. I tried the chown, and I found something that suggested chmod, but I don't know the use of it. Should I put an entry in fstab for the MicroSD? If so, what should I do with it? A few days ago I made the mistake of editing mtab; but I fixed that.

---

### Post by SPARTAN-118 on 2009-07-28
I have the exact same problem; however, I use my Micro SD card for my R4DS, and I'm not sure *what* it's formatted as.

This has really screwed me up, as I can no longer add/delete my files (not even through sudo nautilus, I don't think.... I tried Alt+F2 "gksu nautilus" and "gksu nautilus /" and neither worked).

My Micro Sd card is listed as /media/disk/, and is read-only.

All my files are in the .Trash-1000 folder, which means I can't use them with the R4...

I've just had the R4 since yesterday, help!

SPARTAN-118

**_EDIT**_:
Okay that's just weird, tried my SD card adapter and worked perfectly fine...

USB adapter for some reason is messed up.

Now I can use my Micro again, but how do I change the USB adapter's permission?

Or should I just buy another adapter? They sell for cheap at Staples, right?

---

