---
title: "Failing hard drive"
date: 2013-10-28
forum: Hardware
---

### Post by mayagrafix on 2013-10-28
I used a NTFS formated external HDD for automatic backup with the Ubuntu Backup software provided in the OS. Said drive began to falter after a month, but works great when I bootup in M$ Windows. Are there any known issues regarding Ubuntu Backup and NTFS? 

I was thinking about reformatting in ext4 in order to solve issues with backup software and use again for that purpose, but not confident about reliability unless it is know issue about using NTFS and Ubuntu Backup. 

The drive itself is pretty new, with less than 500 hours of use (about a couple of months). 

Thanks for ur help :KS

---

### Post by sudodus on 2013-10-28
Check if there are hardware problems using the S.M.A.R.T. information. You can probably get a summary in the BIOS, but you get more details installing

***smartmontools*** and running ***smartctl***.

```
sudo apt-get install smartmontools
```
```

man smartctl
```
```
sudo smartctl
```

If there are 'only' file-system related problems, the S.M.A.R.T. information should look OK.

---

### Post by mayagrafix on 2013-11-01
thanx for ur suggestion of running smart controls. S.M.A.R.T. report is good. All test passed.

I'm still curious to know if there are any known issues of running Ubuntu "Deja-dup Backup Software" on an NTFS formated USB drive. is it a good idea to backup to USB2 drive? does it matter? what kind of formating is recommended? ext4? or should I stay with NTFS?

Its gonna take a while to re-format 1.5 TB (terrabyte) of HDD, so I wanna get it right the first time.

---

### Post by sudodus on 2013-11-01
I have not used ***Deja-dup***, but I think it is OK (from what I have read). It's a good idea to backup to a USB2 hard disk drive (or USB 3 or eSATA to get higher speed).

Linux works faster with ext4 compared to NTFS, and ext4 can also manage the file permissions properly, which is important if you backup your data with ***rsync*** or similar tools.

My backup drives are formatted with ext file systems, and I'm happy with that.

---

### Post by tgalati4 on 2013-11-01
Although theoretically possible to use NTFS to back up linux systems, there may be real performance issues.  I would split the disk in half and use NTFS for Windows and Ext4 for linux backups.  Having both Windows and Linux poke at the same data seems like a dangerous setup.

---

