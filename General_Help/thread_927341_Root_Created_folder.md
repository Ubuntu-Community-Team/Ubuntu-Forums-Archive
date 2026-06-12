---
title: "Root Created folder"
date: 2008-09-22
forum: General Help
---

### Post by Darthape on 2008-09-22
How do I copy files into a root created folder? Thanks!

---

### Post by x1a4 on 2008-09-22
Copy those files as root or change the directory's ownership.  Either by running your favourite file manager as root and r-clicking the directory and changing ownership, or from the command line: 
```
sudo chown user:group /path/to/directory
```

---

### Post by spibou on 2008-09-22
If the destination directory is owned by root then you need to be root to copy the files or use sudo. For example
```
sudo cp source dest
```

---

### Post by Darthape on 2008-09-22
@sipbou Tried that it gave me 
```
cp: omitting directory `/home/austin/Desktop/Joomla/'

```
@x1a4 Tried Your idea of changing the permissions of the directory and came up with 
```
chown: cannot access `/opts/': No such file or directory

``` Can't figure out how to run Nautilus as root.

---

### Post by mb_webguy on 2008-09-22
There is no "/opts/" directory, though there is an "/opt/" directory.  You really shouldn't usually change ownership or permission of root-owned files and folders unless you have a very good reason and know that it isn't going to cause problems with applications accessing that file or directory.

To copy the contents of a directory that contains subdirectories, use the -r option with cp to copy recursively.```
sudo cp -r source destination
```

---

### Post by Darthape on 2008-09-22
Figured out the problem. I looked at /opt/ so many times yet never realized that it wasn't /opts/. Thanks

---

