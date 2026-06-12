---
title: "Wubi and 48hr fsck on an ext2 drive?"
date: 2008-10-30
forum: General Help
---

### Post by pdaggitt on 2008-10-30
I recently installed a Kubuntu boot option onto my windows xp machine. Both of these sat on a ntfs formatted sata drive and everything was working great. I had an extra ext2 750gb sata drive that I plugged in one day, and without thinking I installed Ext2 IFS from [http://www.fs-driver.org](http://www.fs-driver.org) . This driver was supposed to let me access the drive from windows xp. I should have just booted to kubuntu to access the files (which worked in the past). Anyways, now I booted into kubuntu went into terminal, went to single user mode, unmounted the drive, and ran fsck on it. At this time fsck has been running for 48hrs. 

I'm afraid to cancel the fsck in fear of further corrupting the drive. How long should this take given its happening through a wubi install and the drive is so big?   :confused:

---

### Post by ago on 2008-10-30
That is quite strange, maybe the drive is fragmented but with such a large hd that should not be an issue. What version of wubi did you use?

---

### Post by pdaggitt on 2008-10-30
I think it is wubi 8.04.1 I forgot to add that the drive was working fine but said it was having corrupted block address errors when I tried to open it in xp.

---

### Post by ago on 2008-10-30
The drive is ext3, did you try to write to it from XP using an Ext2 drive? I might be wrong, but that might invalidate the journal, and then it takes time...

---

### Post by pdaggitt on 2008-10-30
Idk where ext3 came from. The drive that wubi is on is NTFS, and the drive I am running fsck on is a 750gb sata ext2 (sawp disk=linux/solaris main= linux).

---

### Post by ago on 2008-10-30
I do not understand do you have 750GB formatted as ext2???
Are you serious?

---

### Post by pdaggitt on 2008-10-30
Ya, is that bad? How long of a wait am I talking here? I will wait if it means saving the data.

---

### Post by ago on 2008-10-30
Yeah wait then turn it to ext3

---

### Post by pdaggitt on 2008-10-30
What is ext3? I just want my mp3's back... :P

---

