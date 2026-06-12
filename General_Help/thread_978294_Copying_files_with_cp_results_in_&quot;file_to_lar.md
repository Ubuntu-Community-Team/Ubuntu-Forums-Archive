---
title: "Copying files with cp results in &quot;file to large&quot; error"
date: 2008-11-11
forum: General Help
---

### Post by waltons_pacman on 2008-11-11
I'm trying to copy two folders, one of size 4gb and one of 6.2gb from one partition to another using cp, and i get the following result:

```
USERNAME@COMPUTERNAME:~/Desktop$ cp -r FOLDERNAME/ /DESTINATION/
cp: writing `/DESTINATION/FOLDERNAME FILENAME': File too large

```

attempting to tar the file in order to cp it later results in:
```
tar: /media/disk/.fr-lsDMPX/FILENAME.tar: Wrote only 4095 of 10240 bytes
tar: Error is not recoverable: exiting now

bzip2: I/O or other error, bailing out.  Possible reason follows.
bzip2: File too large
	Input file = /media/disk/.fr-lsDMPX/FILENAME.tar, output file = /media/disk/.fr-lsDMPX/FILENAME.tar.bz2
bzip2: Deleting output file /media/disk/.fr-lsDMPX/FILENAME.tar.bz2, if it exists.
mv: cannot stat `/media/disk/.fr-lsDMPX/FILENAME.tar.bz2': No such file or directory
```


anyone have any ideas?
thanks

---

### Post by mdurham on 2008-11-11
What format is the destination?

---

### Post by hardyn on 2008-11-11
good point... 4gb file limit on fat32.

---

### Post by waltons_pacman on 2008-11-11
> good point... 4gb file limit on fat32.
well that is just stupid. why would you limit file sizes at all?

Hardyn - good guess, the destination is formated fat32.

luckily, i supose i can just put it on the ext3 spare i have lying around? will try that now and post back.

also, is there any way around the file limit?

---

### Post by spibou on 2008-11-11
> **waltons_pacman said:**
> well that is just stupid. why would you limit file sizes at all?
It makes the programmers' life easier because they know that certain variables associated with the file (i.e. its length or a position inside the file) can be stored in a (C) "unsigned long int" variable. Without that assumption and especially at a time where "unsigned long long" was not available they would need to write explicit code to do arithmetic on quantities larger than 32 bits.

---

### Post by hardyn on 2008-11-11
same reason that 4gb of addressing is the limit for a 32bit system.  the largest value representable with a 32bit unsigned integer is ~4bil.  and like mentioned above it is easier to impose a limit than get into some addressing tricks.
 




> **waltons_pacman said:**
> well that is just stupid. why would you limit file sizes at all?

Hardyn - good guess, the destination is formated fat32.

luckily, i supose i can just put it on the ext3 spare i have lying around? will try that now and post back.

also, is there any way around the file limit?

---

### Post by waltons_pacman on 2008-11-11
wow. those were very good, and very 'on-time' responces. thanks.

---

