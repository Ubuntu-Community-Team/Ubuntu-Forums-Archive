---
title: "rsync compression?"
date: 2008-07-28
forum: General Help
---

### Post by JSHN on 2008-07-28
As I understand, when you use rsync with the -z option the
data is being compressed, transfered and the uncompressed at
the destination? Is there anyway to make rsync keep the compression
at the destination resulting in a much smaller backup?

If not, is there any other great program that can do this?

Thank you!

---

### Post by tamoneya on 2008-07-28
i think you are best off writing a script to put it into a tar.gz and then transferring over rsync.

EDIT: better yet use rsync but on the server end us the ZFS filesystem.  It supports filesystem compression and therefore compresses everything automatically.

[http://www.tech-recipes.com/rx/1446/zfs_ten_reasons_to_reformat_your_hard_drives](http://www.tech-recipes.com/rx/1446/zfs_ten_reasons_to_reformat_your_hard_drives)

---

### Post by JSHN on 2008-07-29
Oh, did not know about the ZFS, will try that out, seams like a good idea.

Thank you! :)

---

