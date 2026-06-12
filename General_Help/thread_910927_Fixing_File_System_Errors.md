---
title: "Fixing File System Errors"
date: 2008-09-05
forum: General Help
---

### Post by EricDallal on 2008-09-05
My file system has apparently run into some troubles today. The grub takes a long time to load and ubuntu sometimes doesn't load at all, often takes an eternity to load, and frequently crashes. All this began today. Running e2fsck told me that there were errors. Obviously, it is ill advised to try to fix errors on a currently mounted operating system. I imagine that I can fixe the errors by running e2fsck from the Ubuntu CD. Can someone tell me how? Also, is there some way to run it without the Ubuntu CD?

---

### Post by quibbler on 2008-09-05
> **EricDallal said:**
> My file system has apparently run into some troubles today. The grub takes a long time to load and ubuntu sometimes doesn't load at all, often takes an eternity to load, and frequently crashes. All this began today. Running e2fsck told me that there were errors. Obviously, it is ill advised to try to fix errors on a currently mounted operating system. I imagine that I can fixe the errors by running e2fsck from the Ubuntu CD. Can someone tell me how? Also, is there some way to run it without the Ubuntu CD?
From the terminal type

sudo touch /forcefsck

then:
reboot

This will run e2fsck at the bootup.

Regards quibbler

---

### Post by EricDallal on 2008-09-08
Thanks. It ran fsck but that didn't seem to solve the problem. I tried running it at least 3 times but the problems nevertheless persist. Is there something else I can try? I now have access to the Ubuntu CD too. I am considering just reinstalling Ubuntu entirely.

---

### Post by rbmorse on 2008-09-08
Be prepared for the possibility that your drive is dying. 

Uncorrectable disk errors resulting solely from software errors (or user tricks) do occur, but they are rare. You might want to adjust the budget a bit is case you have a need to replace the driver sooner than later.  

Might want to make sure the backups of your critical user data are in good shape, too.

---

