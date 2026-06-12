---
title: "Floppy not automounting in Gnome"
date: 2005-11-17
forum: General Help
---

### Post by mdrop on 2005-11-17
Hello all!

I'm installing Ubuntu for a friend to use, he's new to Linux so I chose Ubuntu as a hassle-free distro. So far, that's been mostly correct. However, there is one problem. The floppy is not automounting properly. 

We first had the problem of not being able to mount floppy at all from Nautilus, but that was fixed by installing pmount 0.9.6-1, as demonstrated on other threads. Now we can mount the floppy, but merely inserting it does not do anything, it needs to be manually mounted and unmounted (this works via Nautilus tho, so not a huge issue). 

I myself don't care about this much, my own box doesn't even have a floppy drive anymore. However, my friend is a newcomer to the world of *NIX and I'm afraid he'll get confused with having to tell the system that he has inserted a floppy and again remember to manually unmount it.

I've checked the removable media settings and they should be okay, CD automount works fine.

Is anyone else experiencing this problem and is there a way to fix it? I myself am not afraid to get down and dirty with the command line if that's needed to fix it :D

---

### Post by canadianwriterman on 2005-11-17
I believe that there is currently no way for the floppy to automatically mount simply by putting a floppy disc in the drive. If you followed the thread on upgrading pmount, then the best that can happen is that you put a disc in, go to "Computer," right click on the Floppy icon and select mount. 

It's a bit less convenient than Windoze, which mounts the floppy as soon as you insert the dic, but it's better that it was prior to the pmount fix. At that time, you had to mount through a command line. I think I read somewhere that automounting of the floppy may be part of Dapper, but I'm not sure.

---

### Post by BatsotO on 2005-11-17
you can use mtoolsfm, it allows you to browse the disk without mounting them

---

### Post by mdrop on 2005-11-17
Thanks guys. I suppose I'll just show my friend how to mount/unmount it throught Nautilus and then hope he learns it fast, so he doesn't have to call me everytime he saves something to a disc :D

---

### Post by slux on 2005-11-18
well, there is supermount and submount which some other distros use and you can get by compiling a custom kernel but in your case it might be a bit too much work.

---

