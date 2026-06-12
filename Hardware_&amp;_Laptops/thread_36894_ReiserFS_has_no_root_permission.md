---
title: "ReiserFS has no root permission"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by DFreeze on 2005-05-25
I've experienced some trouble trying to add e.g. WiFi and USB, and sometimes the system froze. Hard shutdown did the job, and ReiserFS uses journalling so it should be able to restore possibly damaged files. Yet during boot I get a message like:

```
ReiserFS: filesystem NOT clean
ReiserFS has no root permission, so I'll skip this part [my parafrasing]
```

How do I make ReiserFS root, or whatever is necessary to benefit from the journalling?

---

### Post by Kamping_Kaiser on 2005-05-25
[QUOTE=DFreeze]I've experienced some trouble trying to add e.g. WiFi and USB, and sometimes the system froze. Hard shutdown did the job, and ReiserFS uses journalling so it should be able to restore possibly damaged files. Yet during boot I get a message like:

```
ReiserFS: filesystem NOT clean
ReiserFS has no root permission, so I'll skip this part [my parafrasing]
```

How do I make ReiserFS root, or whatever is necessary to benefit from the journalling?[/QUOTE]

some questions - 
1. Do you get that error while booting?
2. Is that your root partition (" / ")

if its *not* the root partition, when you boot, make sure its *unmounted* and then use 
chkdisk
to check (and i think fix) the partition. Or you could try 
fsck
but I am reasonably sure you will need to have unmounted for that as well.
if its the root i guess checking as part of boot is all you can try.

---

