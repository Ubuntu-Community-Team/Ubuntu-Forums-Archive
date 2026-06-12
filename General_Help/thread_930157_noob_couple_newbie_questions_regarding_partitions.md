---
title: "noob: couple newbie questions regarding partitions"
date: 2008-09-25
forum: General Help
---

### Post by thedanielmatt on 2008-09-25
hey guys, I did some searching but still have a couple questions I can't quite straighten out...

So, I've experimenting with linux for first time and would eventually like to setup a simple, full-time personal file server (using desktop for now) that is compatible with both windows and my mac.

Do I need two separate partitions to be able to write to them? Mac can read/write ext3, but windows cannot? I guess I'm just confused about "who said what about who"...

Also, if I create a /home on a separate partition, I can reinstall my os without losing any personal data, settings, etc?

---

### Post by fooman on 2008-09-25
windows can read and write to linux partitions (ext2 and ext3) if you install this software:

[http://www.fs-driver.org/](http://www.fs-driver.org/)


> **thedanielmatt said:**
> 
Also, if I create a /home on a separate partition, I can reinstall my os without losing any personal data, settings, etc?

yes, so long as you don't reformat over your /home partition...then your data and settings should be safely tucked away there. :)

---

### Post by jarondl on 2008-09-25
but now linux has better ntfs support than windows has ext3.
so you should make a "shared" ntfs partition..

---

### Post by thedanielmatt on 2008-09-25
just to make sure i have it straight: if i don't want to install the fs driver on every windows machine i want to dial ito the server with, I can make an ntfs partition on the server for the windows machines and keep an ext3 partition for the mac machines?

---

