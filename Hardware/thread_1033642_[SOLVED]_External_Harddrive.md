---
title: "[SOLVED] External Harddrive"
date: 2009-01-07
forum: Hardware
---

### Post by yarn on 2009-01-07
ok so i purchased a external hard drive enclosure so that I can use my old desktop hard drive for my notebook running Ubuntu Intrepid. When i plug in the hard drive it mounts fine and i am able to unmount it. The problem is that when i try to do something on it, it is saying that it is read only. It is formated in fat32. Also when i check the permissions on it it says it can not be determined?  i am still fairly new when it comes to using the terminal so please be very exact about what to do. Thank you. Also there are pictures posted about the problems. The name of the harddrive is sdb.   thanks in advance.

---

### Post by cariboo on 2009-01-07
You can open an Applications-->Accessories-->Terminal and change the permissions on the mount point:

```
sudo chmod -R 777 /media/disk
```

The above command should allow you to read/write and delete files and directories.

JIm

---

### Post by yarn on 2009-01-07
i tried that ...out put was

yarn@yarn-laptop:~$ sudo chmod -R 777 /media/SWISNIFE1
chmod: cannot access `/media/SWISNIFE1/.>&#9617;\002/>&#9617;\002.0>&#9617;': No such file or directory
chmod: cannot access `/media/SWISNIFE1//ñ&#9569;\0024ñ&#9569;\002.5ñ&#9569;': No such file or directory
chmod: cannot access `/media/SWISNIFE1/.c¼\002/c¼\002.0c¼': No such file or directory
chmod: cannot access `/media/SWISNIFE1/.¼&#8976;\002/¼&#8976;\002.0¼&#8976;': No such file or directory
chmod: cannot access `/media/SWISNIFE1//&#9555;ª\0020&#9555;ª\002.1&#9555;ª': No such file or directory
chmod: cannot access `/media/SWISNIFE1/&#9570;-ò\002&#9558;-ò\002.&#9565;/ò': No such file or directory
chmod: cannot access `/media/SWISNIFE1/2.ò\0023.ò\002.\020/ò': No such file or directory
chmod: cannot access `/media/SWISNIFE1/\026/ò\002\027/ò\002.\030/ò': No such file or directory
chmod: cannot access `/media/SWISNIFE1/$/ò\002%/ò\002.Ç2ò': No such file or directory
chmod: cannot access `/media/SWISNIFE1/14ò\00224ò\002.&/ò': No such file or directory
chmod: cannot access `/media/SWISNIFE1/,/ò\002-/ò\002../ò': No such file or directory
chmod: cannot access `/media/SWISNIFE1/4/ò\0025/ò\002.6/ò': No such file or directory
chmod: cannot access `/media/SWISNIFE1/</ò\002=/ò\002.>/ò': No such file or directory
yarn@yarn-laptop:~$ 



any ideas?

---

### Post by taurus on 2009-01-07
Assuming your external harddrive is /dev/sdb1, you can unmount it and then remount with again.

```
sudo umount /dev/sdb1
sudo mount -t vfat /dev/sdb1 /media/SWISNIFE1 -o umask=000
```

---

### Post by yarn on 2009-01-08
ok i figured out what it was...something went wrong when i formated it to fat32. i reformated it and all is well. It mounts and unmounts fine now and has all its permissions...thanks for all the help !!!

---

