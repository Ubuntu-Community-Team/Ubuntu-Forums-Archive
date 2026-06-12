---
title: "Vista and Ubuntu program transfer"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by T3X on 2009-03-10
I installed Ubuntu as a second boot option beside Vista, and I must admit I very new to this.  It works, I can use it. My issue is I have no idea how to access any files I originally had on my Vista OS. If anyone can please help and (hopefully) give me a blow by blow on how to transfer my programs and files from vista to Ubuntu. At this point in time I'm afraid I may have to reinstall everything I have. Any help would be severely appreciated.:D

---

### Post by Mark Phelps on 2009-03-10
You can't transfer your programs from Vista.  Linux is not MS Windows.

As to the data, if you click Places, you should see your Vista partition in the list.  Just double-click it to open a Nautilus panel pointing to that partition.  You can then drag-and-drop your files into a companion Nautilus panel opened for your Ubuntu partition.

---

### Post by T3X on 2009-03-15
I can officially reach my files after having a friend walk me through; however, now every time I load Ubuntu, I have to type
**sudo mount /dev/sda2 home/***myusername***/Vista***the file I made*  Hoping this helps anyone wandering the forums out there.

---

### Post by SuperSonic4 on 2009-03-15
Does that really work? I always thought you needed to specify the filetype. Plus I prefer mounting in /media but that's personal preference. If you want it to mount each time you can add something like

```
/dev/sda2 /media/Vista ntfs-3g defaults 0 0
``` to your /etc/fstab

although there's bound to be a good reason why it isn't automounted

---

