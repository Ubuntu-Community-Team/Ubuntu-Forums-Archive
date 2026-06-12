---
title: "utility to check crc"
date: 2008-08-08
forum: General Help
---

### Post by miatawnt2b on 2008-08-08
Is there a utility to check CRC of a file?
thanks,
-J

---

### Post by iaculallad on 2008-08-08
> **miatawnt2b said:**
> Is there a utility to check CRC of a file?
thanks,
-J

On your terminal:

```
md5 filename.txt
```

Or

```
man md5
```

---

### Post by chazchaz101 on 2008-08-19
Another option would be to install the Perl module archive::zip

```

sudo apt-get install libarchive-zip-perl

```

This will allow you to check the crc by typing the command crc32 followed by the path to the file.

Ex:
```
crc32 '/home/bill/Desktop/file1.txt'
```

You can also add additional paths to check more files.

---

