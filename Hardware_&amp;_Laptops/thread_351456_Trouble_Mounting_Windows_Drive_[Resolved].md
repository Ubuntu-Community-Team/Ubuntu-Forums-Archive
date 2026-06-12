---
title: "Trouble Mounting Windows Drive [Resolved]"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by chris.durham on 2007-02-02
I'm kind of new so please bear with. I am trying to mount a windows drive so I did a little looking and found the code for doing it:

```
sudo mount /dev/hda1 /media/Data1/ -t ntfs - nls=utf8,unmask -0222
```

But, when I do, this is the message I get:
> 
Mount: wrong fs type, bad option, bad superblock on dev//hda1,
              missing codepage or other error In
              some cases useful info is found in syslog - try 
              dmesg | tail or so

I really have no clue what any of that means. Any help would be appreciated.

---

### Post by Sarisar on 2007-02-02
Is the windows drive formatted NTFS or FAT?

Sounds like it's a fat drive and that is why you're getting the error - you're saying it's NTFS.

---

### Post by aysiu on 2007-02-02
I believe you have some syntax errors in there.

This is what you wrote: ```
sudo mount /dev/hda1 /media/Data1/ -t ntfs - nls=utf8,unmask -0222
``` This is what you *should* have written: ```
sudo mount /dev/hda1 /media/Data1 -t ntfs -o nls=utf8,umask=0222
```

---

### Post by chris.durham on 2007-02-02
Sorry. I actually did have what you suggest. Same error

---

### Post by chris.durham on 2007-02-02
> **Sarisar said:**
> Is the windows drive formatted NTFS or FAT?

Sounds like it's a fat drive and that is why you're getting the error - you're saying it's NTFS.

If I do fdisk it tells me NTFS. Any other way I can tell?

---

### Post by aysiu on 2007-02-02
> **chris.durham said:**
> Sorry. I actually did have what you suggest. Same error
Are you sure? It's case-sensitive.

Also, you did do */media/Data1* and not just *media/Data1*, right?

Try this: ```
sudo mkdir /media/Data1
``` and when you "do" this command, copy and paste it in instead of retyping it: ```
sudo mount /dev/hda1 /media/Data1 -t ntfs -o nls=utf8,umask=0222
```

---

### Post by chris.durham on 2007-02-02
Okay. Looks like my system was lying to me.
I entered:
```
sudo fdisk -l
```
and got
> /dev/hda1 1 30401 244196001 7 HPFS/NTFS
in regards to that particular drive.
However, when I ignored the NTFS stuff and entered
```
sudo mount /dev/hda1 /media/Data1
```
it mounted.

Thanks for the help

---

### Post by aysiu on 2007-02-02
Your system wasn't lying to you. In your original command, you had bad options. My guess is that even in your revised command you retyped instead of copying and pasting the command I gave you. Retyping generally leaves more room for error than copying and pasting.

Glad it all worked out in the end, though. I'm kind of amazed that mounting without the *-o nls=utf8,umask=0222* allowed you to read what was in /media/Data1...

---

