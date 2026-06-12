---
title: "DVD video are unreadable"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by TuTToWeB on 2007-02-09
Hi to all ubuntist.
I've a question for you. I've installed dapper on my machine and DVD videos weren't mount neither automatically nor manually (using mout). Now, i'm using edgy and the problem is yet here. What's the problem?  

[B][17181304.124000] hdb: tray open
[17181304.124000] end_request: I/O error, dev hdb, sector 1036
[17181304.124000] hdb: tray open
[17181304.124000] end_request: I/O error, dev hdb, sector 1036
[17181304.128000] hdb: tray open
[17181304.128000] end_request: I/O error, dev hdb, sector 1036
[17181304.128000] hdb: tray open
[17181304.128000] end_request: I/O error, dev hdb, sector 1036
[17181305.512000] VFS: busy inodes on changed media.
[17181305.520000] VFS: busy inodes on changed media.
[17181307.524000] VFS: busy inodes on changed media.
[17181307.532000] VFS: busy inodes on changed media.
[17181309.536000] VFS: busy inodes on changed media.
[17181309.544000] VFS: busy inodes on changed media.
[17181311.548000] VFS: busy inodes on changed media.
[/B]

this is a piece of dmesg...

thanks to everyone

P.S.: i've libdvdread3 installed.

---

### Post by klugja on 2007-02-13
I am getting the same errors reading and writing a mounted DVD-RAM disk with edgy, just trying to copy files.  Are you using DVD-RAM?  It's nice to know I am not alone.  I have a work-around, but it's not fun.  I have seen people complain over and over again that UDF in Linux is broken, which is what DVD video uses, I believe.

My sample errors:
Feb 13 20:41:10 brimson kernel: [ 3002.884381] hdc: tray open
Feb 13 20:41:10 brimson kernel: [ 3002.884416] end_request: I/O error, dev hdc, sector 6145704
Feb 13 20:41:10 brimson kernel: [ 3002.884437] Buffer I/O error on device hdc, logical block 1536426
Feb 13 20:41:11 brimson kernel: [ 3004.309849] VFS: busy inodes on changed media.



I am using a UDF 1.5 DVD-RAM disk.

I can write a disk perfectly if I create an image on the hard drive with the loop driver, and then copy the image with growisofs.  Likewise, I can copy an existing DVD to an image, and use the loop driver to access the files.

Otherwise, I get into trouble reading and writing.  This sort of defeats the purpose of DVD-RAM.

And needless to say Windows XP and my Panasonic UDF drivers work just fine.

A work-around might be to copy the DVD to an image file (assume /dev/dvd is the DVD drive):

$ dvd+rw-mediainfo /dev/dvd
  ...
Read Format Capacities
  ...
 00h(800):              2295072*2048=4700307456
  ...

$ # (make sure /tmp has 4GB+ of space left)
$ dd if=/dev/dvd of=/tmp/image bs=2048 size=2295072
2236704+0 records in
2236704+0 records out
4580769792 bytes (4.6 GB) copied, 1001.83 seconds, 4.6 MB/s
$ mkdir /tmp/loop
$ mount -o loop /tmp/image /tmp/loop
$ cd /tmp/loop
$ # Now I can read the copy of the disk, update it, then write it out again using growisofs with
$ # the -Z option.

---

### Post by klugja on 2007-02-14
Found another complaint.  Note that the work-around is to mount the DVD on windows, and use Samba to read it.  The obvious stupid question is why doesn't this get fixed?

[http://ubuntuforums.org/showthread.php?p=918613#post918613]("http://ubuntuforums.org/showthread.php?p=918613#post918613")

---

