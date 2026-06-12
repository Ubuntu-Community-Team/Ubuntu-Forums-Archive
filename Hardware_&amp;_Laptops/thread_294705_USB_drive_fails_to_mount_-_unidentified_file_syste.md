---
title: "USB drive fails to mount - unidentified file system and wrong size"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by citizenofnowhere on 2006-11-07
Here's my problem. It's an old 128MB Memodisk thumb, and Ubuntu (Edgy) refused to mount it. It gave me this error:

```
mount: /dev/sdb: can't read superblock
```


It used to work on Windows though, despite some errors, except yesterday when Windows (XP) mounted the thumb and I tried to access it it told me to insert a disk into the drive.

I tried formatting it in Windows (both the built in, and a tool that came with the thumbdrive). Windows options showed file system - RAW and 0bytes free OR available space.

Then I tried to format the thumb using Gparted. It recorgnized the drive as /dev/sdb, but didn't recognize a file system and told me I had 512bytes of available space.

I tried writing a new disk label, but the tool gave me an error saying it could not create a new msdos (or any other disk label - I've tried bsd, gpt)

I tried accessing the device through parted commandline, I got the following:

```
(parted) mklabel                                                          
New disk label type? msdos
Error: Input/output error during read on /dev/sdb                         
Retry/Ignore/Cancel? 
```   

disktype gave me the following output:

```
disktype /dev/sdb

--- /dev/sdb
Block device, size 512 bytes
disktype: Data read failed at position 0: Input/output error

```

And the testdisk interface tells me Partition:read error.

I've run out of ideas. Does anyone have any other suggestions? I would appreciate any help! Thanks in advance for your time

---

### Post by kidders on 2006-11-07
Hi there,

I remember seeing similar kinds of errors with a USB drive someone gave me a while ago. I told him to throw it in the trash. :-? For your sake, I hope I did the wrong thing, but it doesn't look hopeful.

---

### Post by citizenofnowhere on 2006-11-07
Heh it's only 128MB and very very old so I'm not afraid to chuck it away. It's all about the chase though :) Thanks for the reply!

---

### Post by kidders on 2006-11-07
No problem :-)

It's sort of a pity really ... I was half hoping my post would spark someone clever to life, who would laugh at me, and give you a one-line solution to your problem. Tbh though, I'd say your USB disk is ruined :-(

All the best.

---

### Post by citizenofnowhere on 2006-11-08
I just find it cool that someone actually replied even when there wasn't much to be done. I love these forums! Thanks again! I guess I'm closing this thread

---

