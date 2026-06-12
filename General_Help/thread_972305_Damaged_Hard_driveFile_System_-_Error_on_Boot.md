---
title: "Damaged Hard drive/File System - Error on Boot"
date: 2008-11-05
forum: General Help
---

### Post by super breadfish on 2008-11-05
Last week my desktop computer locked up and I had to reboot with the restart button. Now I get errors when booting. I think the restart might have damaged one of my hard drives (with /home on it :(). As it's booting I get the following errors:

```
ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata2.00: cmd c8/00:20:00:00:00/00:00:00:00:00/e0 tag 0 dma 16384 in
         res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
ata2.00: status [ DRDY ]
ata2: port is slow to respond, please be patient (Status 0xd0)
ata2: soft resetting link
ata2.00: revalidation failed (errno=-2)
ata2: failed to recover some devices, trying in 5 secs
ata2: soft resetting link
ata2.00: configured for UDMA/133
ata2: EH complete
```

which repeats several times, at one point with:

```
sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
sd 1:0:0:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
Descriptor sense data with sense descriptors (in hex):
        72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00
        00 00 00 00
sd 1:0:0:0: [sdb] Add. Sense: No additional sense information
end_request: I/O error, dev sdb, sector 63
printk: 2 messages suppressed.
Buffer I/O error on device sdb, logical block 0
Buffer I/O error on device sdb, logical block 1
Buffer I/O error on device sdb, logical block 2
Buffer I/O error on device sdb, logical block 3
Buffer I/O error on device sdb, logical block 4
Buffer I/O error on device sdb, logical block 5
Buffer I/O error on device sdb, logical block 6
Buffer I/O error on device sdb, logical block 7
Buffer I/O error on device sdb, logical block 8
Buffer I/O error on device sdb, logical block 9
ata2: EH complete
sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
```

booting then continues, until the file system check:

```
 * Checking file systems...
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: No such file or diretory while trying to open /dev/sdb1
/dev/sdb1:
The superblock could not be read or does not describe a correct ext2
filesystem. Is the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock
is corrupt, nd you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

 * File system check failed
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.
 * A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@kamon-desktop:~#
```

still printing this error:

```
 ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
 ata2.00: cmd c8/00:08:3f:00:00/00:00:00:00:00/e0 tag 0 dm 4096 in
 ata2.00: status: [ DRDY ]
```

How can I safely repair my disk (or at least work out if it can be repaired)? I didn't want to run commands blindly in case I made things worse. I've not had any problems like this under Linux so I'm a bit lost.
My other hard drive (where Linux is installed) appears to be ok.

I took some pictures of the screen as the errors appeared which I can upload if needed.

---

### Post by super breadfish on 2008-12-13
I've since tried using Seatools to look at the drive. The short test fails, but when I try to run the long test Seatools stops responding.
I also tried Hitachi's Drive Fitness Test, and their short test gives a a corrupt sector error, but do anything else because it's not a Hitachi drive.

Anyone have any ideas?

---

### Post by oldos2er on 2008-12-13
Have you tried doing what it suggested: "you might try running e2fsck with an alternate superblock:    e2fsck -b 8193 <device>" ?

---

