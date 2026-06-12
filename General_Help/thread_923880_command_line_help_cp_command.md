---
title: "command line help cp command"
date: 2008-09-18
forum: General Help
---

### Post by kv_home on 2008-09-18
I have family videos ina bunch of subdirectories I would like to copy all to one place.

I think

cp -r *.avi ~/copyvids

should copy all avi files to the directory copyvids, but the erro message I get is
kevin@kevin-desktop:/media/linux_hd/BackupFromAmby/My Pictures/2007$ cp -r *avi ~/copyvids cp: cannot stat `*avi': No such file or directory

but from the same location
kevin@kevin-desktop:/media/linux_hd/BackupFromAmby/My Pictures/2007$ find -iname *avi
./2007_08 Eastham 2/MVI_0019.avi
./2007_08 Eastham 2/MVI_0028.avi
./2007_08 Eastham 2/MVI_0117.avi
./2007_08 Eastham 2/MVI_0008.avi
./2007_08 Eastham 2/MVI_0067.avi
.....more files
so all the files name are there

what is teh syntax for walking through all teh subdirectories and copies all files of a type?

---

### Post by mb_webguy on 2008-09-18
If you're wanting to traverse directories, you need to use find with the exec option.  It's going to be something like: ```
find ./ -name *.avi -exec cp {} ~/copyvids \;
```
I haven't tested this command, but I think the syntax is correct.

---

