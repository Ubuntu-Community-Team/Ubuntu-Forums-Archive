---
title: "Removable HD unmountable"
date: 2008-09-05
forum: General Help
---

### Post by spazzfx on 2008-09-05
Hey im kind of new to linux but i know a few things. I had a removable hd and i had to unmount it to get access to all the locked files. now i cant get it mount back on my computer. says it cannot contain certain letters or something. any help would be appreciated.

---

### Post by cariboo on 2008-09-05
What is the name of your mount point eg:

```
/media/external
```

Jim

---

### Post by spazzfx on 2008-09-10
this is what it gives me.

Unable to mount the volume 'REMOVABL HD'.
mount point cannot contain the following characters:G_DIR_SEPARATOR (usually /)

thats the message i get.
cant open properties to see the mount point.

---

### Post by cariboo on 2008-09-10
You have a space in the volume name. Linux does not like space in file names as it sees a space as a seperator. To fix this problem just put an uderscore in the volume name eg:

```
REMOVABL_HD
``` 

If your external drive is formated as ext3 use e2label, like this: 

```
e2label device newlabel
```

If your external drive is formatted as NTFS install ntfsprogs

```
sudo apt-ge install ntfsprogs
```

Then use:

```
sudo ntfslabel device [label]
```

For more info on either program use the man pages:

```
man e2label
```

or

```
man ntfslabel
```

Jim

---

### Post by spazzfx on 2008-09-26
hey thanks for the tips. i tried all the stuff you suggested and it didnt work. i dont know if im doing it right but i think i am. not sure on what the format is of the drive. changed the hard drive name to NICKSHD and it didnt do anything else. any suggestions you have otherwise will be most helpful.

---

