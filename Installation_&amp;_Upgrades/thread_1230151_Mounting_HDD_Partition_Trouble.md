---
title: "Mounting HDD Partition Trouble"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by Aericron on 2009-08-03
So I was stuck with Vista on my laptop. It started messing up, wouldn't let me log in or let alone click anything. So I heard I could scan my windows files using Ubuntu. So I wiped a useless partition (it was sent from toshiba with 3 partitions) to install Ubuntu into. But since I had to force shut down my laptop when it was last in Vista, Ubuntu won't let me see what's in the Windows partition. Is there any way I can force mount this?

My partitions go something like:
device       boot   start         end             blocks        id    system
/dev/sda1           37879      38913         8313637+    83   Linux
/dev/sda2    *     192          37878         302716928  7     HPFS/NTFS
/dev/sda3           1             191             1534176+   5     extended
/dev/sda5           1             191             1534144+   82   Linux swap / Solaris


I just want to get all my crap off my hard drive, then just do a full format. I had the plan of making a torrent consisting of the files I want to keep, and have a second computer download it for storage, then after I reformat and reinstall my os's just seed it back. But first I need access to said files, which means I need it to mount my windows partition.
I don't know a whole lot about Linux based systems, but I'm kinda easy flowing with computers, any help is very much appreciated, thanks

---

### Post by prshah on 2009-08-03
> **Aericron said:**
> won't let me see what's in the Windows partition. Is there any way I can force mount this?

device       boot   start         end             blocks        id    system
/dev/sda2    *     192          37878         302716928  7     HPFS/NTFS


You can do a forcemount with the terminal (Applications-Accessories-Terminal) command```
sudo mount /dev/sda2 /mnt -o defaults,rw,force
``` this will forcemount your windows partition to the /mnt directory.

---

### Post by Aericron on 2009-08-03
> **prshah said:**
> You can do a forcemount with the terminal (Applications-Accessories-Terminal) command```
sudo mount /dev/sda2 /mnt -o defaults,rw,force
``` this will forcemount your windows partition to the /mnt directory.
Thank you very much prshah, I don't know why my commands weren't working... I think my options weren't the same...

---

