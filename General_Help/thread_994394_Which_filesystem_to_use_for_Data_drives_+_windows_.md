---
title: "Which filesystem to use for Data drives + windows compatibility?"
date: 2008-11-26
forum: General Help
---

### Post by kooldino on 2008-11-26
Currently my data disk runs NTFS, however I'm considering switching it to another file system.  I need a file system that...

-Doesn't have a 4GB file size limit (like Fat32 does)

-Linux can write to NATIVELY (whereas NTFS support in linux is not native, thus resulting in slow writes)

-Can be fully supported by Windows without much fuss.

I know of no file system that currently supports this.  Here's a list of what I do know, along with their shortcomings.

-NTFS - non-native in linux, slow.
-ext2/3 - no native windows support
-FAT32 - native to both, but file size is limited to 4GB


What are my options here?

---

### Post by silverglade00 on 2008-11-26
There is a ext2/3 driver for Windows that works great. I used it for a long time until I moved my data to an external drive. [http://www.fs-driver.org/](http://www.fs-driver.org/)

From the website:
> It installs a pure kernel mode file system driver Ext2fs.sys, which actually extends the Windows operating system to include the Ext2 file system. Since it is executed on the same software layer at the Windows NT operating system core like all of the native file system drivers of Windows (for instance NTFS, FASTFAT, or CDFS for Joliet/ISO CD-ROMs), all applications can access directly to Ext2 volumes. Ext2 volumes get drive letters (for instance O: ). Files, and directories of an Ext2 volume appear in file dialogs of all applications. There is no need to copy files from or to Ext2 volumes in order to work with them.

---

### Post by Luke has no name on 2008-11-26
silverglade, is it ext3 compatible?

---

### Post by Chunky Dunk on 2008-11-26
You can access ext2/3 partitions from windows. I've never tired it myself, so I can't vouch for it performance. Take a look at this link: [http://tombuntu.com/index.php/2007/08/14/ext3-file-systems-in-windows/](http://tombuntu.com/index.php/2007/08/14/ext3-file-systems-in-windows/)

Also, to answer your question to silverglade: "The Ext3 file system is the Ext2 file system which has been extended by journaling. Ext3 is backward-compatible to Ext2 - an Ext3 volume can be mounted and used as an Ext2 volume. Just as older Linux Kernels which do not know the Ext3 file system can mount Ext3 volumes (as Ext2 volumes), the Ext2 file system driver ext2fs.sys for Windows incorporated in this software package can do it without any problems, too. Of course you do not take advantage of the journaling of the Ext3 file system if you mount it as an Ext2 file system."
Source : [http://www.fs-driver.org/faq.html#acc_ext3](http://www.fs-driver.org/faq.html#acc_ext3)

---

### Post by uldo on 2008-11-26
In the FAQ it's all writen down:
[http://www.fs-driver.org/faq.html#acc_ext3](http://www.fs-driver.org/faq.html#acc_ext3)

---

### Post by silverglade00 on 2008-11-26
Yes and no. Ext3 is just ext2 with journaling. The underlying structure is the same. It will access it just fine, but you will not get the journaling of ext3. As long as you don't yank out your power cord, you should be fine. I never had any problems with it.

---

