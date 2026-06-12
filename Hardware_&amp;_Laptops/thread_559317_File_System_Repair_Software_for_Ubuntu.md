---
title: "File System Repair Software for Ubuntu?"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by jerremy-tamlin on 2007-09-25
What programs/tools exist for repairing corrupted file systems in Linux?

My /home partition crashed with multiple inode errors. I ran fsck and answered yes to multiple prompts:```
Inode 63506 ref count is 1, should be 2.  Fix? yes

Inode 95836 ref count is 58, should be 56.  Fix? yes

etc...
```
I have restored most of my data (to a new laptop) from lost+found but am missing a few important files.

I've been searching for recovery software but have only found one that runs on linux (destoprecovery) and it keeps crashing (its gui based and shareware licensed).
```
(destoprecovery:12178): Gtk-CRITICAL **: gtk_ctree_insert_node: assertion `GTK_IS_CTREE (ctree)' failed

(destoprecovery:12178): Gtk-CRITICAL **: gtk_ctree_collapse: assertion `node != NULL' failed

(destoprecovery:12178): Gtk-CRITICAL **: gtk_ctree_insert_node: assertion `GTK_IS_CTREE (ctree)' failed

(destoprecovery:12178): Gtk-CRITICAL **: gtk_ctree_collapse: assertion `node != NULL' failed
```

Can anyone tell me how to scan the partition and reconstruct the inodes?

Any help most appreciated.
Thanks

---

