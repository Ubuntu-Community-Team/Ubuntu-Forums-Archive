---
title: "Sharing Files Between ubuntu and Windows?"
date: 2008-09-12
forum: General Help
---

### Post by mikeMarek on 2008-09-12
Is it possible to share files between Windows and Ubuntu even though they're on separate partitions? I just want to have a single folder so I can place music and pictures downloaded from Windows or Linux (so when I download music off of Limewire from both OS's I can share them without placing megabytes worth of music on my USB, restart my computer, transfer files, then change back to my previous OS).

Cheers and thanks for any help,
-Mike

---

### Post by anjilslaire on 2008-09-12
put the shared folders on a FAT partition. Both OSes can access FAT without any issues.

---

### Post by snl2587 on 2008-09-12
> **anjilslaire said:**
> put the shared folders on a FAT partition. Both OSes can access FAT without any issues.
Or you can make a folder on the NTFS partition, mount it when you are in Linux and link to it. Then you don't need a FAT partition, but you won't be able to mount the NTFS partition if it wasn't shut down correctly. As a plus, you'll be able to access all of you Windows files from the linux side.

I can't remember the name of it, but there's an ntfs-config utility to do this since Ubuntu no longer mounts the NTFS partition by default.

---

### Post by HermanAB on 2008-09-12
Hmm, dual booting is so 20th century... ;)

You should install VMware Server and boot the Windows partition in Linux.  Then you'll have Windows running in a window, where it belongs.

Cheers,

Herman

---

