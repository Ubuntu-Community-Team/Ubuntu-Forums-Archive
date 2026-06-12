---
title: "Split Gzip file as it's being created."
date: 2008-07-21
forum: General Help
---

### Post by Rolcol on 2008-07-21
I need to image a hard drive but the image is going to be saved to an external hard drive formatted as Fat32 so I have a 4GB file size limit.  Is there a way I can have gzip split the file every 4GB?  I'm running ubuntu from a live cd on a computer with 1GB of RAM.  I know another solution is to have dd only copy 4 GB and compress that but I'd like to have it ask for the least amount of user input.

---

### Post by iaculallad on 2008-07-21
> **Rolcol said:**
> I need to image a hard drive but the image is going to be saved to an external hard drive formatted as Fat32 so I have a 4GB file size limit.  Is there a way I can have gzip split the file every 4GB?  I'm running ubuntu from a live cd on a computer with 1GB of RAM.  I know another solution is to have dd only copy 4 GB and compress that but I'd like to have it ask for the least amount of user input.

```
tar -cvzf myfile.tar.gz Your_Drive_Image_Name
split -d -b4000m myfile.tar.gz myfile.tar.gz.

```

Output will be two files named, myfile.tar.gz.00 and myfile.tar.gz.01 of size 4 GB maximum size each.

---

### Post by Rolcol on 2008-07-21
> **iaculallad said:**
> ```
tar -cvzf myfile.tar.gz Your_Drive_Image_Name
split -d -b4000m myfile.tar.gz myfile.tar.gz.

```

Output will be two files named, myfile.tar.gz.00 and myfile.tar.gz.01 of size 4 GB maximum size each.
I can't save the image anywhere before compression so it has to be compressed as it is being copied with dd.  Will split work in this situation?
```

dd if=/dev/sda bs=1M | gzip --fast > /media/External/hd-image.gz
```

---

### Post by cdtech on 2008-07-21
Using tar you could use the tape length flag to split the tar into smaller sizes.

-L, --tape-length N
change tapes after writing N*1024 bytes

---

### Post by iaculallad on 2008-07-21
> **Rolcol said:**
> I can't save the image anywhere before compression so it has to be compressed as it is being copied with dd.  Will split work in this situation?
```

dd if=/dev/sda bs=1M | gzip --fast > /media/External/hd-image.gz
```

Split would not work in your situation since it needs the file to be "finished" with the compression before it could start splitting the archive to several sub-archives.
Though I'm not sure if there's a workaround on doing that since you're working with an "active" file in this situation.

---

### Post by wirelessmonkey on 2008-07-22
You can use partimage and compress on the fly, you can also set any split size you'd like. You also don't get compressed empty disk space like you do with dd.

---

