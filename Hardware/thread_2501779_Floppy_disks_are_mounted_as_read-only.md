---
title: "Floppy disks are mounted as read-only"
date: 2024-10-20
forum: Hardware
---

### Post by peyre on 2024-10-20
I've plugged in a USB floppy drive to my Xubuntu 24.04 desktop.  It mounts disks successfully, but read-only.  (Oddly, it mounted a disk properly the first time, but not afterward.)  I've tried several different USB floppy drives but they all do the same thing.

My mount settings for the floppy drive in Disks are:
rw,user,noauto,exec,sync,gid=floppy,umask=007,x-gvfs-show

I am a member of the floppy group, and have floppyd installed.

The contents of /mnt are:
```
drwxr-xr-x  2 leon root   4096 Sep 29  2023 pci-0000:00:1f.1-ata-1.1
drwxrwxrwx 15 leon leon   4096 Aug 10 12:15 Storage
drwxrwx---  3 leon floppy 7168 Dec 31  1969 usb-TEAC_TEAC_FD-05PUB
drwxr-xr-x  2 leon root   4096 Oct 20 10:59 usb-TEACV0.0_TEACV0.0
```

And /media:
```
lrwxrwxrwx  1 root root     7 Sep 23  2023 floppy -> floppy0
drwxrwxr-x  2 leon users 4096 Sep 23  2023 floppy0
drwxr-x---+ 4 leon users 4096 Oct 20 11:46 leon
drwx------  2 leon users 4096 Sep 25 20:34 veracrypt1
```

I've also run thunar as root, and it won't let me paste into it - so it must be mounting it read-only, since it's not a permissions thing, even though I've told Xubuntu to mount it with the **rw** option.  Anyone have any ideas?

---

### Post by guiverc on 2024-10-20
Have you tried mounting it at terminal?

I booted a local system that had Xubuntu 24.04 LTS installed, and actually had a floppy drive, and my *fstab* or *file system table* options differ to yours, being simplier

```

/dev/fd0     /media/floppy0     auto    rw,user,noauto,exec,utf8  0 0

```

and I'm getting responses as I'd expect.

If it's not mounted, I can mount at terminal using only

```

sudo mount /media/floppy0/

```

and I get no errors (at mount anyway).

Have you tried terminal mount, ie. to get messages without having to explore logs? 

Have you looked in your system logs for clues (*that's where I'd look next, but I'd try in terminal just to save the time needed to look*).

In my case I tried copy/pasting data to the floppy in thunar, and operation appeared to start fine, no issues with RO media, but I was getting problems which actually don't surprise me!

To see what was happening, a quick view of `dmesg` output shows constant I/O errors on dev fd0, and sector read errors....  In my case the floppy data will be corrupted and I know this, the actual floppy on this system was last used in testing a `calamares` problem many releases ago where it wrote data to *floppy* instead of *hdd* and thus corruption on this floppy is expected..  The floppy in my drive is BAD.

Either way I'd explore system logs, or better just mount from terminal so you're seeing all output (*without needing to go look for it*).  Start with the drive unmounted too.

Are you sure your drive is working?  getting sufficient power? etc  Whilst a failing drive may still show clues in system logs, you cannot guarantee that.  I didn't use an external floppy disk, as I'd have go hunt for that, but I'd expect similar results.

---

### Post by peyre on 2024-10-21
Sorry for the delay, guiverc.  I have several USB floppy drives and they're all doing the same thing. Plus at least one of them works properly on my laptop.  Power shouldn't be a problem; I've tried it with both a PCI-E card full of USB3 ports, and a built-in USB2 port.

dmesg is full of these.  Any idea what they mean?

```
[ 2545.428343] sd 7:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_OK cmd_age=0s
[ 2545.428366] sd 7:0:0:0: [sdd] tag#0 Sense Key : Medium Error [current] 
[ 2545.428376] sd 7:0:0:0: [sdd] tag#0 Add. Sense: Unrecovered read error
[ 2545.428387] sd 7:0:0:0: [sdd] tag#0 CDB: Read(10) 28 00 00 00 00 04 00 00 01 00 00 00
[ 2545.428393] critical medium error, dev sdd, sector 4 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[ 2545.428453] FAT-fs (sdd): FAT read failed (blocknr 4)
[ 2546.228250] sd 7:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_OK cmd_age=0s
[ 2546.228274] sd 7:0:0:0: [sdd] tag#0 Sense Key : Medium Error [current] 
[ 2546.228284] sd 7:0:0:0: [sdd] tag#0 Add. Sense: Unrecovered read error
[ 2546.228294] sd 7:0:0:0: [sdd] tag#0 CDB: Read(10) 28 00 00 00 00 04 00 00 04 00 00 00
[ 2546.228301] critical medium error, dev sdd, sector 4 op 0x0:(READ) flags 0x80700 phys_seg 4 prio class 0
[ 2547.028177] sd 7:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_OK cmd_age=0s
[ 2547.028201] sd 7:0:0:0: [sdd] tag#0 Sense Key : Medium Error [current] 
[ 2547.028211] sd 7:0:0:0: [sdd] tag#0 Add. Sense: Unrecovered read error
[ 2547.028259] sd 7:0:0:0: [sdd] tag#0 CDB: Read(10) 28 00 00 00 00 04 00 00 01 00 00 00
[ 2547.028268] critical medium error, dev sdd, sector 4 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[ 2547.028332] FAT-fs (sdd): FAT read failed (blocknr 4)
```

---

### Post by guiverc on 2024-10-22
> **peyre said:**
> 
dmesg is full of these.  Any idea what they mean?

```
[ 2545.428343] sd 7:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_OK cmd_age=0s
[ 2545.428366] sd 7:0:0:0: [sdd] tag#0 Sense Key : Medium Error [current] 
[ 2545.428376] sd 7:0:0:0: [sdd] tag#0 Add. Sense: Unrecovered read error
[ 2545.428387] sd 7:0:0:0: [sdd] tag#0 CDB: Read(10) 28 00 00 00 00 04 00 00 01 00 00 00
[ 2545.428393] critical medium error, dev sdd, sector 4 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[ 2545.428453] FAT-fs (sdd): FAT read failed (blocknr 4)
[ 2546.228250] sd 7:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_OK cmd_age=0s
[ 2546.228274] sd 7:0:0:0: [sdd] tag#0 Sense Key : Medium Error [current] 
[ 2546.228284] sd 7:0:0:0: [sdd] tag#0 Add. Sense: Unrecovered read error
[ 2546.228294] sd 7:0:0:0: [sdd] tag#0 CDB: Read(10) 28 00 00 00 00 04 00 00 04 00 00 00
[ 2546.228301] critical medium error, dev sdd, sector 4 op 0x0:(READ) flags 0x80700 phys_seg 4 prio class 0
[ 2547.028177] sd 7:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_OK cmd_age=0s
[ 2547.028201] sd 7:0:0:0: [sdd] tag#0 Sense Key : Medium Error [current] 
[ 2547.028211] sd 7:0:0:0: [sdd] tag#0 Add. Sense: Unrecovered read error
[ 2547.028259] sd 7:0:0:0: [sdd] tag#0 CDB: Read(10) 28 00 00 00 00 04 00 00 01 00 00 00
[ 2547.028268] critical medium error, dev sdd, sector 4 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[ 2547.028332] FAT-fs (sdd): FAT read failed (blocknr 4)
```

Look like media errors to me, ie. the floppies have sector issues (data level); which can occur because the floppies were allowed to sit too near a power source, speaker, electronic appliance etc & the magnetic fields from electronics and time have corrupted the data...

I'm heading to bed currently, as I've got stuff to do tomorrow, but I'll aim to go find a decent floppy ([I]and not just the one sitting in the machine underneath the one I'm currently using; as that floppy was used for QA testing where I knew data was being written to the device, thus I know sectors of the diskette are corrupted even if the directory itself shows as clear (data was written on a block level & not as files, so directory still shows as valid).  Errors like what I see in your paste are what I'd expect to see if I tried to use the datafiles on the floppy in my system..


[/I]Do NOTE..  Your errors show reference to device SDD, I'd expect a floppy to show up as FDD/FD0 and not a SDD device; however that difference could be the result of you using a USB floppy drive; where as I'm mostly using floppies connected to the motherboard.

I'll endeavour to return with more late tomorrow (ie. a day hopefully).

---

### Post by peyre on 2024-10-22
Oh yes, I missed "sdd"!  I wonder if my system drive is starting to fail - better fsck it.

I'll try a different floppy.  It's possible there's a problem with that one.  Floppies aren't a very stable medium; they do have a tendency to develop filesystem errors.

---

### Post by peyre on 2024-10-22
Hang on, it may have fixed itself (on its own?).  I'll have to do a bit more testing...

---

### Post by peyre on 2024-10-26
Well guiverc, I don't know how it happened, but several days and reboots later and the drive is still RW.  Somehow it fixed itself.  Thanks for your help!  I've marked it Solved.

---

