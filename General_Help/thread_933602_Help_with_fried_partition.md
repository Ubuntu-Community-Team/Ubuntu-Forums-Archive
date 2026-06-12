---
title: "Help with fried partition"
date: 2008-09-29
forum: General Help
---

### Post by Alaric on 2008-09-29
Hey guys,

Murphy's law strikes again.  I was resizing some partitions the other day and... gparted killed my superblock on my ext3 drive one way or another.  So I popped in a boot CD of partition magic pro and it claimed to have fixed the errors, so I went ahead and tried repartitioning from there...  Guess I should have double checked. At this point I finally got the bright idea of dd'ing the entire partition to my server's hard disk.  Now whenever I run fsck I don't get a message about a superblock, I get lots of complaints about thousands of inodes being corrupted.  I let it run all night and eventually it got stuck in an infinite loop with text scrolling too fast for me to see (the log at the bottom had the last line obtained from a print screen).  The file data is still there when I check for it in a hex editor (managed to recover some of the more important things), but I still have encrypted (ubuntu encfs) logs from my girlfriend that I can't retreive from the foo-bar'd partition.  After the fsck I can't mount the drive anymore, so I usually use dd to recopy the first 20 megs of the partition back to the drive so I can mount it once more.  When I do mount the drive, I get...

```

ubuntu@ubuntu:/$ sudo mount /dev/sda5 /test
ubuntu@ubuntu:/$ cd test
ubuntu@ubuntu:/test$ ls
ls: cannot access var: Stale NFS file handle
ls: cannot access home: Stale NFS file handle
ls: cannot access boot: Stale NFS file handle
ls: cannot access etc: Stale NFS file handle
ls: cannot access bin: Stale NFS file handle
ls: cannot access mnt: Stale NFS file handle
ls: cannot access media: Stale NFS file handle
ls: cannot access sbin: Stale NFS file handle
ls: cannot access $RECYCLE.BIN: Stale NFS file handle
ls: cannot access lib: Stale NFS file handle
bin    initrd          mbr_backup  ps2hw.dat     sys       vmlinuz.old
boot   initrd.img      media       $RECYCLE.BIN  tmp
cdrom  initrd.img.old  mnt         Recycled      usbdrive
dev    keys            nohup.out   root          usr
etc    lib             opt         sbin          var
home   lost+found      proc        srv           vmlinuz
ubuntu@ubuntu:/test$ ls -lh
ls: cannot access var: Stale NFS file handle
ls: cannot access home: Stale NFS file handle
ls: cannot access boot: Stale NFS file handle
ls: initrd: Input/output error
ls: cannot access etc: Stale NFS file handle
ls: cannot access bin: Stale NFS file handle
ls: cannot access mnt: Stale NFS file handle
ls: cannot access media: Stale NFS file handle
ls: cannot access sbin: Stale NFS file handle
ls: cannot access $RECYCLE.BIN: Stale NFS file handle
ls: cannot access lib: Stale NFS file handle
total 152K
d?????????     ? ?          ?                 ?                ? bin
d?????????     ? ?          ?                 ?                ? boot
lrwxrwxrwx     1 root       root             11 2008-03-12 18:35 cdrom -> media/cdrom
drwxr-xr-x     4 root       root           4.0K 2008-04-21 21:12 dev
d?????????     ? ?          ?                 ?                ? etc
d?????????     ? ?          ?                 ?                ? home
?rw-rwSr--   139 2709782709   12694470        0 1970-05-25 16:28 initrd
lrwxrwxrwx     1 root       root             33 2008-08-15 13:46 initrd.img -> boot/initrd.img-2.6.24-21-generic
lrwxrwxrwx     1 root       root             33 2008-07-24 06:06 initrd.img.old -> boot/initrd.img-2.6.24-20-generic
b-wx--x-wT 63738 2529511409 2509911149  59, 139 1946-07-21 13:51 keys
d?????????     ? ?          ?                 ?                ? lib
drwx------     2 root       root            16K 2008-03-12 18:35 lost+found
drwxr-xr-x     2 root       root           4.0K 2008-06-15 21:27 mbr_backup
d?????????     ? ?          ?                 ?                ? media
d?????????     ? ?          ?                 ?                ? mnt
-rw-------     1 root       root            145 2008-08-24 04:38 nohup.out
?-------wT   257   16843266   16908545      17M 1971-01-25 21:13 opt
drwxr-xr-x     2 root       root           4.0K 2007-10-08 10:47 proc
-rw-r--r--     1 root       root           105K 2008-05-26 04:02 ps2hw.dat
d?????????     ? ?          ?                 ?                ? $RECYCLE.BIN
drwxr-xr-x     2 root       root           4.0K 2008-09-25 21:43 Recycled
?r-Sr-S--- 17487  677716029 1701660756        0 2012-09-19 05:13 root
d?????????     ? ?          ?                 ?                ? sbin
?-w-rwS--t 54736 3563564345 1671183466        0 1931-09-24 06:17 srv
b--S--sr-x 11641  112570113 3208530648 232,  51 2021-04-24 00:32 sys
drwxrwxrwt    18 root       root           4.0K 2008-09-27 04:07 tmp
?r-s-wsrwt 10303 2569411529 1961734970        0 1965-10-22 21:49 usbdrive
?rwS---r-t 41328 4187492625   16860105        0 2011-12-26 21:16 usr
d?????????     ? ?          ?                 ?                ? var
lrwxrwxrwx     1 root       root             30 2008-08-15 13:46 vmlinuz -> boot/vmlinuz-2.6.24-21-generic
lrwxrwxrwx     1 root       root             30 2008-07-24 06:06 vmlinuz.old -> boot/vmlinuz-2.6.24-20-generic
ubuntu@ubuntu:/test$ sudo mkdir testdir
ubuntu@ubuntu:/test$ ls -lh | grep testdir
ls: cannot access var: Stale NFS file handle
ls: cannot access home: Stale NFS file handle
ls: cannot access boot: Stale NFS file handle
ls: initrd: Input/output error
ls: cannot access etc: Stale NFS file handle
ls: cannot access bin: Stale NFS file handle
ls: cannot access mnt: Stale NFS file handle
ls: cannot access media: Stale NFS file handle
ls: cannot access sbin: Stale NFS file handle
ls: cannot access $RECYCLE.BIN: Stale NFS file handle
ls: cannot access lib: Stale NFS file handle
drwxr-xr-x     2 root       root           4.0K 2008-09-29 20:44 testdir

```

When I unmount it and then run fsck...

```

ubuntu@ubuntu:/$ sudo umount test
umount: test: not mounted
ubuntu@ubuntu:/$ sudo fsck /dev/sda5 -y
fsck 1.41.0 (10-Jul-2008)
e2fsck 1.41.0 (10-Jul-2008)
/dev/sda5 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes

Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks
Multiply-claimed block(s) in inode 327553: 41409
Multiply-claimed block(s) in inode 327555: 41410
Multiply-claimed block(s) in inode 327558: 41411
Multiply-claimed block(s) in inode 327563: 41412
Multiply-claimed block(s) in inode 327565: 41413
Multiply-claimed block(s) in inode 327567: 41414
Multiply-claimed block(s) in inode 327569: 41415
Multiply-claimed block(s) in inode 327571: 41416
Multiply-claimed block(s) in inode 327573: 41417
Multiply-claimed block(s) in inode 327575: 41418
Multiply-claimed block(s) in inode 327577: 41419
Multiply-claimed block(s) in inode 327579: 41420
Multiply-claimed block(s) in inode 327583: 41421
Illegal block number passed to ext2fs_test_block_bitmap #<big numbers> for multiply claimed block map.  
<seemingly infinite loop ensues after a few hours>

```

As far as I can tell, most of my inodes must be destroyed.  Lost cause?

---

### Post by Alaric on 2008-09-29
Hmm... I let the fsck run for a while longer and now it seems to be actually doing something again, I'll post an update once it finishes.

Looks promising, I'm now seeing messages for "copy to lost and found?" and "salvage?"

---

### Post by Alaric on 2008-09-29
I stopped it for a second, and sure enough I have a crapload of unnamed files in /lost+found.  Any ideas how I can restore their original places without having to search for the contents manually?

---

