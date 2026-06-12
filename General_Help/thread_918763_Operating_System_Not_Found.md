---
title: "Operating System Not Found"
date: 2008-09-13
forum: General Help
---

### Post by washburn311 on 2008-09-13
I was running the live demo portion of the CD and went to do an install.  The computer locked up and I had to shut down.  Now when I try to boot back to Windows it says "operating system not found."  the only way i can boot to anything is if i have the cd that i burned after downloading ubuntu inserted in the drive.  i need help.  i just want to get windows back right now and dont care about trying to install this anymore.

---

### Post by Ms_Angel_D on 2008-09-13
Well what kind of install we're you trying to do? Did  you select use entire disk? If so then your going to have to reinstall windows.

---

### Post by washburn311 on 2008-09-13
i did not select entire disk.

---

### Post by Ms_Angel_D on 2008-09-13
well more information would be helpful, what kind of install did  you attempt? partition? Before anyone can help your going to have to supply more information about what exactly you did during the install process.

---

### Post by washburn311 on 2008-09-13
i was going to do the partition install but never had a chance to select which partition.  as soon as i hit the install icon it locked up so i shut down.  that is when i turned it back on only to find that i get the message operating system not found.  if it lost windows is there any way to recover any documents that i had saved in it?

---

### Post by jjocsak on 2008-09-13
If you have additional drives, disconnect all but your boot drive, then try it again.
It may be trying to boot from the wrong drive.

Jeff

---

### Post by washburn311 on 2008-09-13
i have no other boot drives.  right now i guess i am just interested in trying to recover any files i had saved.

---

### Post by Urvish on 2008-09-13
I will say you that format the computer and reinstall windows and Ubuntu

---

### Post by jjocsak on 2008-09-13
Any other data drives?

Jeff

---

### Post by Predator106 on 2008-09-13
Boot to the LiveCD, select the "try" option/demo, then go to the terminal, Applications->Accessories->Terminal. Then type this following command in:

```
sudo fdisk -l
```

Post the output of this command, but please, when you post it, hit the # button after selecting what you pasted, to make it easier to read.

That command will list all of the hard drives that are registered on your computer.

It will also tell us the file format they are in, to be sure that it didn't get messed up at all.

Also, a way to get around using the terminal (if you really don't want to) then you can just goto places or Computer and select the size of your HDD, and see if your files are listed there, my guess is that it just simply got rid of the Windows MBR, which would be relatively easy to fix.

If you lost the data on your Windows (NTFS-3G) drive, from what I've seen, there are Ubuntu programs that can help you get it back, even if you formatted the entire thing, or just deleted the partition table. Now how well these work, I'm not at all sure as I haven't tried it myself.

[SIZE="1"]P.S. Hopefully I didn't make any mistakes in this post, I did one of those half-*** reads.[/SIZE]

---

