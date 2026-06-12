---
title: "How you remove cd/dvd drive from ubuntu?"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by 97cobra on 2007-12-01
My dvd burner died and I removed if from my pc, I had 1 cd/dvd-rw and 1 cd/dvd drive installed. For some reason ubuntu still shows it on my system but its not even physically in my computer.  The problems arise when i try to install files with Synaptic and it asks for me to put my ubuntu cd in.  Its looking at my old cd drive.  So I can't get it to read the cd in my other dvd drive.

---

### Post by dgray_from_dc on 2007-12-02
Look in fstab

```
sudo gedit /etc/fstab
```

There's probably still an entry for the drive you removed there.  If you know which drive it is, (i.e. /dev/sdb or /dev/hdb) you can simply delete the corresponding line in fstab.  

Also, to fix the Synaptic problem, look into sources.list

```
sudo gedit /etc/apt/sources.list
```

Fix the entry for the cdrom there.

---

