---
title: "directories suddenly appear as mp3-like files"
date: 2012-01-31
forum: Hardware
---

### Post by ieel on 2012-01-31
The story is this:
I had multiple directories in an external Hitachi disk ( ext3), and two of them suddenly became mp3-like files (no mp3 extension, but within nautilus thaey are defined as MP3 audio).  In fact, the files have specific mp3 titles (right mouse-> properties -> audio), of two mp3 files from another location. After the files became mp3, I was able to view their content from amarok player (weird), but they appeared as files. 
I tried to fix it with
umount /dev/sdb1
fsck -t ext3 /dev/sdb1

fsck found several problems and allegedly corrected them but the directories still appear as mp3, and the question is what to do. Now I can not even see them with my Amarok player (here I'm crying).

Maybe you have an idea how to get these lost directories back
:confused:
Avi

---

### Post by Paddy Landau on 2012-02-01
Oh dear, it looks as if you've had some horrid corruption. Perhaps the disk was disconnected from your computer before safely removing.

 You can try using [data recovery]("https://help.ubuntu.com/community/DataRecovery"), but that is a complex and unreliable process.

Open Disk Utility to see if the disk has any SMART data; the disk may be failing.

The command I'd use (after dismounting the disk) is:
```
sudo fsck -CMf /dev/sdb1
```But I don't think that would solve it.

I think you would be better off reformatting as ext4 and restoring from your backups (you do have backups, I hope).

---

