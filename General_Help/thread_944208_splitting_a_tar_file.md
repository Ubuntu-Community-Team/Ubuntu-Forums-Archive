---
title: "splitting a tar file"
date: 2008-10-11
forum: General Help
---

### Post by thestig_992 on 2008-10-11
I have a file that i need to compress then put on a USB stick, only the file is about 10 times to big....
my question is about whether its possible to split a .tar file, i'd prefer cli method as well since im transferring from a very slow comp running on live cd...

---

### Post by geirha on 2008-10-11
Use split. The following will split the file into parts that are at most 1GiB, Naming them *base-name-of-splitted-files**aa***, *base-name-of-splitted-files**ab***, etc. 
```
split -b 1G tar-to-split.tar.gz *base-name-of-splitted-files*
```

To put them back together
```
cat *base-name-of-splitted-files** >tar-to-split.tar.gz
# Alternatively, you can decompress without recreating the tar
cat *base-name-of-splitted-files** | tar zxvf -

```

---

### Post by thestig_992 on 2008-10-11
Thanks, exactly what i wanted

---

