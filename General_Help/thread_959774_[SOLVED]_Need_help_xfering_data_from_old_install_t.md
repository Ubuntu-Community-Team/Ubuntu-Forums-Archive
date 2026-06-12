---
title: "[SOLVED] Need help xfering data from old install to new"
date: 2008-10-26
forum: General Help
---

### Post by Draylorre on 2008-10-26
Hello everyone, I seem to have a small issue here.

Currently I have Ubuntu installed on a server mainly used for FTP and as a home file server. It is installed on two 500 GB HDs in RAID 1. I am using 6.06 LTS.

Recently I decided it'd be nice to go from that to an 80 GB install and then put two seperate 1 TB drives into a RAID 1 setup and xfer the data from.

I installed 6.06 LTS and configured it all up on the 80 GB, made sure it could ping and called it a night. Now I plugged my two 1 TB drives in and everything goes nuts.

First off, I can't even boot into my working 80 GB install with the two drives attached. they aren't even RAIDed (which is what I wanted to do from the install, but again, I just get dumped into Busybox.

I decided to create the RAID from the alternate CD and proceeded to do so, all went smoothly and I kept my old files on my 80 GB (now referred to as /dev/sdc1)

When booting, I still get dumped into Busybox. I was able to make a directory "ubunturoot" and mount /dev/sdc1 to "ubunturoot" and access /dev/sdc1, but it will not boot to /dev/sdc1.

Does anyone know why I'm getting this? I don't even know what's going on.

Further more, will I be able to transfer my data from my old 500 GB RAID 1 install to the 1 TB RAID 1 install? I thought I could just boot into the 500 GB RAID 1 and simply dump the data from ~/ to the new RAID.

Please let me know what information you need to help me resolve this. It's really quite a doozy.

---

### Post by ryanhaigh on 2008-10-26
Well I can't be to sure about all this as it's been a long time since I was running dapper but my guess would be that your grub and fstab entries are incorrect. It sounds to me like your system is 'seeing' the two 1TB drives first and might be assigning them to /dev/sda/b respectively which is where your system is looking for /. I'm not sure if dapper used UUIDs so it may be a simple matter of changing the grub and fstab lines to point to /dev/sdc* but a better solution would be to assign labels to your filesystems and setup grub and fstab to mount based on the label, I am sure you can find a howto somewhere that will cover this.\

EDIT: I think you might also have to do something with initramfs but I believe that is only if you hibernate your system (you have to specify which filesystem to resume from).

---

### Post by Draylorre on 2008-10-27
I'll give this a try tomorrow.



Also, bumpity bump.

---

