---
title: "Wubi maximum size"
date: 2008-11-12
forum: General Help
---

### Post by Jameshardy88 on 2008-11-12
is it posible to have a ubuntu install with wubi that has more than 30gb of space dedicated to it? cold u create additional virtual disks for example?

---

### Post by Orlsend on 2008-11-13
Yes you can create several other disk's while using Ubuntu (or if you hapen to be in windows)

[I]"How do I create a virtual disk in Ubuntu?

Open a terminal (Applications -> Accessories -> Teminal), and enter these commands (this will create a 10 GB extra.virtual.disk, adjust line 2 to change these):

cd /host/ubuntu/disks
sudo dd if=/dev/zero of=extra.disk bs=1MB count=1 seek=10000
sudo mkfs.ext3 -F extra.disk

How do I create a virtual disk in Windows?

You can use qemu-img for that. Another dirty trick (but working) is to copy any other file of the desired size to c:\wubi\disks and rename it "root.disk", "home.disk", "swap.disk" or "extra.disk". That's the wubi equivalent of buying (and installing) a new hard disk ;)

If you are running Windows XP (may work in Windows 2000 and Vista as well) you can create a file by using the fsutil that is included with Windows. The command format is fsutil file createnew filename filesize where filename is the file you wish to create and filesize is the size of the file to be created in bytes. "[/I]

For any other Wubi need make sure you check the Wubi guide.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20create%20a%20virtual%20disk%20in%20Ubuntu?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20create%20a%20virtual%20disk%20in%20Ubuntu?")

Enjoy your New space!

---

### Post by wordymusic on 2010-09-16
I had the same problem. My fix is below. Also, link to blog w mildly offtopic situational details. 

Boot from a livedisk. Then, 
quemu-img resize test.disk +1G
Then resize the file systems. 
resize2fs -f test.disk
In order to enlarge itself without overriding what's currently in it, add "skip" parameter = entire size of it. seek = current size + addition.

And, using dd, things were done and win was had. 
[http://geeklinda.blogspot.com/2010/09/wubi-ubuntu-installer.html](http://geeklinda.blogspot.com/2010/09/wubi-ubuntu-installer.html)

---

