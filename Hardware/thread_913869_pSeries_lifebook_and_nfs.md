---
title: "pSeries lifebook and nfs"
date: 2008-09-08
forum: Hardware
---

### Post by Lary Grant on 2008-09-08
I previously posted this a long time ago, but I am still having the exact same problem, and no one ever answered my original question... should I open a bug on this, or is there any solution?  I am now on Hardy with all updates applied.

--------------

I have my pseries lifebook set up through my wireless network as an NFS client, using a line in /etc/fstab on the lifebook to mount my home directory on my desktop machine (which is also running Hardy with all updates applied). It appears to work fine... I can browse my desktop machine from the lifebook, see the files, open them, etc. However, when I try copy a directory from my desktop machine to my local home directory on the lifebook, it starts copying the files, then freezes. I can't even cancel the "copying" dialog. If I try to do the copy from a shell window using "cp -r" a very similar thing happens... some of the files get copied then the shell window freezes. Ctrl-C does not work.

Once that "freeze" happens, I can no longer access the desktop machine over NFS, even from a new window.... I need to reboot the lifebook. I've tried it several times with the same result.

---

