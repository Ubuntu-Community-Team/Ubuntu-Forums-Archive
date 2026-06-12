---
title: "Copy files and verify them"
date: 2008-08-14
forum: General Help
---

### Post by ThaddeusW on 2008-08-14
Hello everyone,

I am consolidating 3 NTFS formatted disks with all my data on them to a new linux file server I put together with a 3 drive mdadm raid 5 array. I already know how to mount up the disks and copy the data over with rsync but is there a way I can verify the files after they are copied? I want to be sure they are copied over 100% intact because I plan to format those disks and use them for other computers.   

Thanks

---

### Post by HermanAB on 2008-08-14
Rsync does that already.

Cheers,

Herman

---

### Post by ThaddeusW on 2008-08-14
Sorry but I am still a bit of a newbie. Does rsync do this automatically or with a switch?

---

### Post by fjgaude on 2008-08-16
No, lots of switches to use:

```
sudo rsync -r -t -p -o -g --progress --delete /home/raid/ /media/backup/raid/
```

That's what I use with great success. The man pages tell all, though I really use grsync, in the repositories.

---

