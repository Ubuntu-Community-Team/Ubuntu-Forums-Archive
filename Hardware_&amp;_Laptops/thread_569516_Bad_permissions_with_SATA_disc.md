---
title: "Bad permissions with SATA disc"
date: 2007-10-07
forum: Hardware &amp; Laptops
---

### Post by m4rku5 on 2007-10-07
Disc have an option "read only" so i can't copy any files to my secondary sata disc (It writes: You do not have permissions to write to this folder.) I tried to change it in disc properties and it wrote: You are not the owner, so you can't change these permissions:).

What it means:confused: I need to copy files on disc:(. Please somebody help.

---

### Post by PmDematagoda on 2007-10-07
What is the filesystem of that hard disk?

---

### Post by nawitus on 2007-10-07
sudo chmod should be able to change them, or sudo nautilus.

---

### Post by PmDematagoda on 2007-10-07
It maybe a solution but you can solve your problem completely by opening up Synaptic, searching for ntfs-config and installing it.

Sorry, but what is your filesystem in the USB?

---

### Post by m4rku5 on 2007-10-07
Filesystem is on first disc ( some IDE 13,5gb) and my secondary disc is sata Seagate Barracuda 160gb.

---

### Post by m4rku5 on 2007-10-07
I installed ntfs-config, i can change permission for writing to external devices, but not internal :(.

---

### Post by m4rku5 on 2007-10-07
I tried sudo nautilus, but owner of second disc is still root and I can't change it "because the disc is for read-only".

---

### Post by PmDematagoda on 2007-10-07
In the NTFS-config GUI there must be an option to allow external volumes to be read, enable that and try again.

---

### Post by m4rku5 on 2007-10-07
> **PmDematagoda said:**
> In the NTFS-config GUI there must be an option to allow external volumes to be read, enable that and try again.

Brilliant, I used an option for write to internal devices (this option doesn't work before), but I must be fu*ckin' idiot, 'cos when i opened ntfs-config it asked me for some mount point and I did someone in filesystem/media than i chose right option and restart PC, than disc didn't mount. I think this will be the last problem, please help me again.

---

### Post by m4rku5 on 2007-10-08
I can't mount that sata disc, probably i have to make some mount point or something like that and i don't know where,  i have already ntfs-config adjusted for writing and reading from ntfs devices. Please help me somebody. I'm beginner with Ubuntu, so please tolerate my mistakes.

When I tried mount floppy 2, it said "only root can do that". How can I solve that problem?

---

