---
title: "Harddrive fails to mount after writing to it"
date: 2017-01-05
forum: Hardware
---

### Post by christiank11 on 2017-01-05
Hello :)

i have a problem with my WD Blue 1TB hard drive (NTFS-formatted). It is connected to a SATA-III-port on my ASUS H87-PRO-C2 motherboard. I am using Ubuntu 16.04. The HDD is not my boot drive, but /dev/sdb.

The drive is shown in my BIOS and displayed in the starter bar on the left. However, it doesn't show up when I click on it. When shutting down the system it shows the following messages:

```

[49.48...] ata5.00: exception Emask 0x0 SAct 0x6000083f SErr 0x0 action 0x0
[49.48...] ata5.00: irq_stat 0x40000008
[49.48...] ata5.00: failed command: READ FPDMA QUEUED
[49.48...] ata5.00: cmd 60/00:58:88:b5:5f/01:00:00:00:00/40 tag 11 ncq 131072 in
[49.48...]             res 41/40:00:b8:b5:5f/00:00:00:00:00/00 Emask 0x409 (media error) <F>
[49.48...] ata5.00: status: { DRDY ERR }
[49.48...] ata5.00: error: {UNC}
[49.48...] blk_update_request: I/O error, dev sdb, sector 6272440

```

The last thing i did was writing about 100GB of data to the drive. It was filled up ~80% afterwards. The 100GB came from a HFS+-formatted external hard drive. I had no hfsprogs or hfstools installed. I copied the data twice, because I forgot to add some folders to the process. But I realised that I couldn't stop the first transfer. Moreover all the file manager windows couldn't be closed by the "x"-button. So I let the transfer finish and copied the data again. After the transfer had finished the file manager windows reacted again.

I don't know whether the HFS+ thing is important. Is it possible, that the files coming from the HFS+-drive corrupted my NTFS-filesystem on my WD Blue HDD? I don't know much about that Apple stuff so this might be a stupid question :-k.

I really don't know, what to do now. Thanks in advance :).

If it's important: I have a dualboot system with GRUB bootloader. Ubuntu 16.04 boots normally and shows the drive (but I can't access the data), while Windows 7 doesn't finish booting. It is stuck at the windows flag.

---

### Post by SeijiSensei on 2017-01-05
The drive has at least one bad sector. Since it is NTFS-formatted I would only use Windows tools like chkdsk to fix it. If the data are backed up elsewhere, I'd use Windows to reformat the filesystem. Don't do a "quick" format. You want Windows to examine all the sectors so it can mark those that are bad.

---

### Post by efflandt on 2017-01-05
I don't know what it actually means, but when I see { DRDY ERR } I thing "dirty" [bad sector(s)]. That can especially happen as you fill a drive because the sectors near the center of the platters are physically smaller (same number of sectors in a smaller circle), so that is when/where errors are most likely to show up. So +1 using Windows to repair an NTFS partition. Drives usually reserve some space to automatically map good sectors in place of bad sectors, but if all of the reserve sectors get used up, things can only get worse. WD has what I think is called Data Lifeguard diagnostic software that can check or test your drive. "All error sectors used up" would be a bad sign.

That happened after about 3 years after I got my current desktop PC. I had Ubuntu on an sda4 partition at the end of the drive, and when I got into Linux Steam and started filling that with games, my drive began failing. But it did not affect the Windows utility, Recovery, or OS partitions. So I was able to image those and write them to a new drive, shrink Window's 7 OS partition with its own Disk Management tools (more room for Linux), fresh installed Ubuntu, and copied my home directory over using a drive caddy. Only a few game files were corrupted and Steam's VERIFY INTEGRITY OF GAME CACHE... replaced the bad files.

---

### Post by christiank11 on 2017-01-06
Hello, thank you very much for your answers :).

I cloned my WD blue to an external HDD (1) using the ddrescue-command. It showed an error size of 500KB that could be reduced to 176KB in a second read. Then I disconnected the WD blue and cloned the HDD (1) again to a second external HDD (2) using the dd-command. I wanted to keep one of these backups untouched while trying to recover files from the other one. This way the WD blue could stay disconnected from my PC. I think, I will replace this drive.

So I connected the HDD (2) to my USB-port and I was amazed, that it could be mounted. It showed my files and folders and I could copy them to another external HDD (number 3 :D). After that I also connected HDD (1) to USB as a test, but this drive couldn't be mounted. I didn't understand that, as it should be a 1:1 copy of HDD(1). Nevertheless I am very happy that I was able to recover my files.

After backing them up I performed ntfsfix and chkdsk on HDD (2). ntfsfix said that the drive was clean while chkdsk fixed a few errors. I'm unsure right now whether I should copy the files from HDD(2) again because of the file system errors it had. Is this necessary? Might the copied files be damaged/corrupted in any way?

Thanks guys.

---

