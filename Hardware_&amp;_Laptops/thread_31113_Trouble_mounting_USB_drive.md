---
title: "Trouble mounting USB drive"
date: 2005-05-01
forum: Hardware &amp; Laptops
---

### Post by tarunium on 2005-05-01
I have a USB drive with a FAT32 filesystem. I mounted it exactly as described in the Ubuntu starter guide. Now when I start up Ubuntu I can access the drive just fine from the terminal. I can open files, move them around, whatever I need to do. But if I try to open a folder in any KDE app, say Konqueror or Krusader, it just stalls. After that, even the terminal stalls when I try to access folders. There is nothing in dmesg about it. I tried using Midnight Commander as my file manager, since its shell-based, but even MC stalls. It seems like I can only access the drive from the command line, which is, needless to say, extremely vexing. 

I encountered this problem first on Kubuntu. I thought it might have been a KDE bug so I switched to Gnome, but the problem persists. In case it helps, here is the relevant section of /etc/fstab: 
/dev/sda        /media/usb0        auto    rw,user,noauto  0       0
/dev/sda1       /media/windows  vfat    umask=000       0       0

I am a bit confused about the fact that the fstab contains an entry for /dev/sda. There is no corresponding entry for /dev/hda, only the partitions (hda1, hda2, etc). Could this be related to the problem or is it just a red herring?

Anyway apart from this I think Ubuntu is awesome. Ive been trying distros for the past couple of weeks and this has been the best so far. That said, it is very important to me that I have easy access to my external drive, so if I can't get this solved soon I will have to bid a sorrowful farewell to Ubuntu. So any help will be greatly appreciated.

- Tarun

---

### Post by defkewl on 2005-05-02
So the problem is in KDE. Have you tried it in Kubuntu?

---

### Post by tarunium on 2005-05-02
The problem isn't only in KDE. I have the same problem in Gnome, and also with Midnight Commander, which isnt GUI-based, when I just run the shell. It only seems to work right on the comman line.

- Tarun

---

### Post by Wubanga on 2005-05-02
[QUOTE=tarunium]I have a USB drive with a FAT32 filesystem. I mounted it exactly as described in the Ubuntu starter guide. [/QUOTE]

Sorry 'cause i don't have the answer to ur question, i have basically the same problem. The thing is that i don't even know ho to mount my USB drive.

U said that in the ubuntu guide it is explained how to mount a USB drive, but i can't see it. It just says how to mount internal drives formatted in FAT32 or NTFS.

If I add the lines u gave:

/dev/sda /media/usb0 auto rw,user,noauto 0 0
/dev/sda1 /media/windows vfat umask=000 0 0

to my etc/fstab, should it mount it? Do i need to create any folder previously? Because i don't see any sda in my computer.
Thxs, and sorry for just adding more questions and not an answer.

Wubanga

---

### Post by tarunium on 2005-05-02
Type "sudo fdisk -l" in the terminal to display your partition table. Do you see your external disk listed? You can also check to see if its being detected by typing "lsusb" which lists USB devices connected to the machine. If its actually not detected I can't offer much help because I'm a n00b myself  :) 

- Tarun

---

### Post by Jim Link on 2005-10-03
I am having the same issues and was wondering if you ever got this to work...

Thanks

---

### Post by Zimmer on 2005-10-03
Have you created the mount point folders in the /media folder?

/media/windows     and /media/usb0  must exist as locations for the mounting to work via fstab...
The entry in my fstab for my USB FAT32 MP3 player is:-

/dev/sda  /media/cfcard vfat user,noauto 0 0

there is a folder I created called    /media/cfcard.
A location  now appears in 'Computer' called cfcard (because fstab tells it so!)

When I plug it into the USB socket it mounts automatically and the contents displayed in the  'Computer' location cfcard....

Have you got 'Hotplug' installed. Check the Synaptic File manager and install it if necessary....

Your fstab entries of
/dev/sda /media/usb0 auto rw,user,noauto 0 0
/dev/sda1 /media/windows vfat umask=000 0 0

should show up as locations in 'Computer'. Provided the locations  /media/usb0 and /media/windows exist.(you must be root to create the folders).

Hope this helps, and does not confuse.....

Zimm

---

