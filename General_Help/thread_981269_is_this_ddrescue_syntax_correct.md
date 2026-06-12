---
title: "is this ddrescue syntax correct?"
date: 2008-11-13
forum: General Help
---

### Post by KhaaL on 2008-11-13
A friend of mine had his harddisk going haywire. I thought to be good enough to help him recover it since it has lots of photos stored on it among other things. It consists of one big NTFS partition, so I've run with the command:

```
**sudo ddrescue -r3 /dev/sdh1 iomega.img logfile**


Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:     1220 MB,  errsize:   81920 B,  current rate:    2883 kB/s
   ipos:     1220 MB,   errors:       2,    average rate:    5623 kB/s
   opos:     1220 MB
Copying data...

```

Now most examples i've seen of ddrescue use the whole drive (sdh and not sdh1) as a input... is the syntax I've typed correct and will I still be able to mount the image file once it's done?

---

### Post by KhaaL on 2008-11-16
I just realized that the harddisk i'm recovering from is 500GB and the free one is 300GB. is it possible to recover only a certain folder and its subfolders to the 300GB HD?

---

