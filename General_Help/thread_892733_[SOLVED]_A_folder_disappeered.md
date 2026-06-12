---
title: "[SOLVED] A folder disappeered"
date: 2008-08-17
forum: General Help
---

### Post by MaPeD on 2008-08-17
Hi
I just lost a folder on one of my HDs. I haven't deleted it and its not hidden. If i check the contents of HD via terminal with dir it is there, in the list.
Could someone help me please i really need it back

---

### Post by Naatan on 2008-08-17
Could you please show the output of the following command in the parent directory of the directory that is having problems

$ ls -ahl

Please highlight the directory in question

---

### Post by MaPeD on 2008-08-17
```
drwxrwxrwx 61 root root  4.0K 2008-06-20 01:04 Artists
d?????????  ? ?    ?        ?                ? Projects
drwx------  2 root root   16K 2008-07-29 15:31 lost+found
```

Projects is the one thats missing

---

### Post by Naatan on 2008-08-17
Very odd.. hopefully you can repair it but it looks dangerous..

Try the following;

$ sudo chown -R root.root ./Projects
$ sudo chmod -R 755 ./Projects

Do this while you are in the parent directory.

Also try the following:

$ fsck -pv

This will scan your file system for errors and try to repair them, use at your own risk.

---

### Post by MaPeD on 2008-08-17
```
n0ize@Ratchet:/media/Storage$ fsck -pv
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=9a38a41e-65ff-4f88-87ea-e5fbbab68607'
```
thats what i get
chown and chmod just say No such file or directory

---

### Post by Naatan on 2008-08-17
sorry, use

$ sudo fsck -pv

---

### Post by MaPeD on 2008-08-17
After running sudo fsck -pv i got a message that its clean. Did a reboot and upon start up a disk check was initiated, somewhere at 35% it found an error, went into maintenance mode and asked me if i want to fix the found errors but it didnt give any result. Folder is still invisible and can't be accessed.

Btw i tried testdisk to recover the files and it seems to work but it renames all of the files

---

### Post by Sinkingships7 on 2008-08-17
Can you navigate inside of it using the cd command? If so, does it list the files (ls)? Also try copying it to a new location (cp).

---

### Post by MaPeD on 2008-08-17
ls gives me next
```
n0ize@Ratchet:~$ ls /media/Storage
ls: cannot access /media/Storage/Projects: No such file or directory
Artists  Projects  lost+found
```

cp 
```
n0ize@Ratchet:~$ sudo cp /media/Storage/Projects /media/Media
cp: cannot stat `/media/Storage/Projects': No such file or directory
```

---

### Post by MaPeD on 2008-08-18
i just noticed that fsck checked the wrong disk.
how to make it check the one that i need?

---

### Post by Naatan on 2008-08-18
$ sudo fsck -pv /path/to/mount/point

I think

---

### Post by MaPeD on 2008-08-18
thanks got it fixed :)

---

