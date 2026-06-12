---
title: "pcmcia,CF Disk  mounting issues"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by nrune on 2006-11-16
Hey folks have a CF card into a PCMCIA card reader that is not being mounted on insertion. It does not work manualy either, and it does not show up in /media. Any ideas??  

here is output of dmesg:
```
[17197782.276000] pcmcia: registering new device pcmcia0.0
[17197782.316000] Probing IDE interface ide2...
[17197782.604000] hde: TOSHIBA THNCF128MAA, CFA DISK drive
[17197783.276000] ide2 at 0xc100-0xc107,0xc10e on irq 3
[17197783.276000] hde: max request size: 128KiB
[17197783.276000] hde: 250368 sectors (128 MB) w/2KiB Cache, CHS=978/8/32
[17197783.276000] hde: cache flushes not supported
[17197783.276000]  hde: hde1
[17197783.280000] ide-cs: hde: Vcc = 3.3, Vpp = 0.0

```

The card is also found in the Disks gui utility but does nothing when I click enable.  Any help apprecated. 

OH!  Running Dapper

---

### Post by K.Mandla on 2006-11-17
If you're willing to try the terminal, try this. ...

Double check that it's hde1, which is what it looks like in dmesg.

```
sudo fdisk -l
```
The cfcard should show up as hde1; you can double-check the size to be sure.

Now make sure there's a destination to mount to.

```
sudo mkdir /media/cfcard
```
It's possible you already have a directory made for it; if so, you can skip that last command.

Now mount it.

```
sudo mount /dev/hde1 /media/cfcard
```
If you get an error message about the file format, try this.

```
sudo mount -t vfat /dev/hde1 /media/cfcard
```
That usually works for FAT16 (which is what CF cards are supposed to use, if I recall correctly), FAT32 and some other older Windows-type stuff. If you used ext3 or something else replace the word 'vfat' with it.

Check that it works with 

```
ls /media/cfcard
```
That might do the trick.

---

### Post by nrune on 2006-11-17
Thanks for the help.  Okay

Fdisk -l    gives me

```
   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1          14      112423+   b  W95 FAT32

```

here is the result from mounting
```
nrune@nrune:~$ sudo mount /dev/hde1 /media/hde -t ext3
mount: special device /dev/hde1 does not exist

```

Try a diffrent mount point
```
nrune@nrune:~$ sudo mount /dev/hde1 /media/CF -t ext3
mount: special device /dev/hde1 does not exist

```

Any other ideas?

---

### Post by K.Mandla on 2006-11-17
Hmm. :-k Something's not quite right there. Your fdisk shows it as a FAT32 partition, but you've told it it's ext3. Try this instead.

```
sudo mount -t vfat /dev/hde1 /media/hde
```
Remember, you have to have a folder called /media/hde already made before you give it that command.

What kind of computer are you working with? Just curious.

---

### Post by nrune on 2006-11-17
Thanks for sticking with me on this

```
nrune@nrune:~$ sudo mount -t vfat /dev/hde1 /media/hde
mount: special device /dev/hde1 does not exist
```

Toshiba laptop A15-S129.

Mike

---

### Post by nrune on 2006-11-19
Bump... help.

---

### Post by zo3adams on 2007-01-12
Bump . . . same issue; after mount I'm getting error message:

bad fs type, bad option, bad superblock on dev/hde

then dmesg gives:

17181714.472000] hde: SanDisk SDCFB-128, CFA DISK drive
[17181715.144000] ide2 at 0x3100-0x3107,0x310e on irq 4
[17181715.144000] hde: max request size: 128KiB
[17181715.144000] hde: 250880 sectors (128 MB) w/1KiB Cache, CHS=980/8/32
[17181715.144000] hde: cache flushes not supported
[17181715.144000]  hde: hde1
[17181715.148000] ide-cs: hde: Vcc = 3.3, Vpp = 0.0
[17181989.104000] FAT: invalid media value (0x01)
[17181989.104000] VFS: Can't find a valid FAT filesystem on dev hde.
[17182035.536000] VFS: Can't find ext3 filesystem on dev hde.

 any help or ideas appreciated, i believe the cf card is FAT32

---

### Post by zo3adams on 2007-01-12
apologies, had the wrong hde # in my mount line.


posting now in case that helps anyone else :)

---

