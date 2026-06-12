---
title: "Disk problems?"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by Morot313 on 2008-03-09
I am using Ubuntu 8.04 "Hardy Heron" (alpha).

Today my computer stopped working...
It started with Firefox 3.0b3 crashed.
Then when I tried to open it, and other software, it just said "Starting Firefox..." and waited...

Then I couldn't start anything, and things got unresponsive.
The HDD led on the case just shined.

I killed X with Ctrl+Alt+Backspace and my console had lots of errors...

EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read
node block - inode=1599522, block=3211298 stuff like that...

I couldnt login from console either...
Then I restarted computer, and it started X and GNOME, but then it wouldn't work again...

And the console spitted lots and lots of errors like;
EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read
node block - inode=1599522, block=3211298 stuff like that...
continuanitly..

Now I am scared... :(

Ubuntu is on sdb1, its a 250 gb Samsung SpinPoint T166 (7200rpm, SATA-2, 16 mb cache) hard disk, its not so old. Just some months ago, I bought it when 7.10 Feisty Fawn came...

---

### Post by Morot313 on 2008-03-09
I downaded HUTIL v2.10 from Samsung website, a disk diagnostic tool.
It scanned through and said no errors.

---

### Post by Morot313 on 2008-03-09
Hmm...

I think I might have solved it by running stuff like;

$ fsck /dev/sdb1
$ e2fsck /dev/sdb1
$ badblocks /dev/sdb1

With various command line parameters such as -p -y -c -f, etc...
From a Ubuntu Live CD.

---

### Post by Morot313 on 2008-03-12
ata2.00: revalidation failed (errno=-5)

Buffer I/O error on device sdb1, logical block 3948797

ext3_abort called

---

