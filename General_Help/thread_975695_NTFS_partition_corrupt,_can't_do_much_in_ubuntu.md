---
title: "NTFS partition corrupt, can't do much in ubuntu"
date: 2008-11-08
forum: General Help
---

### Post by rancidstp on 2008-11-08
This morning I woke up to what seemed a dead computer... Windows Vista was stuck at boot; it begins to load up, but gets stuck at the green loading bar screen. It is then that I tried safe mode and it hung at crcdisk.sys. Nothing happens if I leave it alone, it simply rebooted and started the process again. The Windows recovery dvd that came with my laptop doesn't help either. It doesn't recognize my windows installation so I can't run chkdsk.

This brings me to my current situation. I decided I would boot into Ubuntu to see if I could at least grab important files (I don't backup, because I'm stupid). I tried installing 8.10 to no avail (it too hung at a crc error)
Luckily, Hardy installed just fine with no errors on the partition I had set aside a couple of days ago. I got in, everything worked as I expected it to. I suppose here I will post my fdisk output.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              13        1318    10485760    7  HPFS/NTFS
/dev/sda2   *        1319       37057   287073517+   7  HPFS/NTFS
/dev/sda3           37058       38914    14909440+   f  W95 Ext'd (LBA)
/dev/sda5           37058       37189     1056768   82  Linux swap / Solaris
/dev/sda6           37189       38914    13851648   83  Linux

```

I proceeded to try mounting /dev/sda2 (my Windows partition) to /media/Windows, but i got this:
```
ntfs_attr_pread: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```
I can't run chkdsk as stated earlier. Is there any way I can mount the partition or at least recover some files so I can get rid of Windows?

---

### Post by taurus on 2008-11-08
See if you can mount them, /dev/sda1 & /dev/sda2, from a terminal.

```
sudo mkdir /media/sda1 /media/sda2
sudo mount -t ntfs-3g /dev/sda1 /media/sda1 -o force
sudo mount -t ntfs-3g /dev/sda2 /media/sda2 -o force
df -h
```

---

### Post by rancidstp on 2008-11-08
Yeah I tried forcing them, too. sda1 works fine (it's the "recovery" partition that came with my laptop)

but sda2 results in the same error:
```
ntfs_attr_pread: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```

---

### Post by rancidstp on 2008-11-08
Alright, problem fixed. 

Booted off my Vista disk again. It still didn't recognize my installation, but running Startup Repair fixed it in 5 minutes. 

With that said, I'm gonna migrate over to Ubuntu completely.

Cheers!

---

