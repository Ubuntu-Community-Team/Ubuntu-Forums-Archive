---
title: "Blu Ray Drive Freezing Ubuntu 12.04x64"
date: 2013-02-24
forum: Hardware
---

### Post by ckyfreak1025 on 2013-02-24
Hello,

I have a new Asus BW-12B1ST Blu Ray drive that freezes Ubuntu whenever I try to eject the disc or watch a DVD. The system becomes unrecoverable and needs to be powered off hard. The only thing that comes up in /var/log/messages when attempting to eject is the following:

Feb 24 20:55:41 beast kernel: [  864.730013] type=1400 audit(1361757341.161:37): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1174 comm="cupsd" pid=1174 comm="cupsd" capability=36  capname="block_suspend"

Is this a bug? Is there some kind of manual driver installation needed for a drive like this?

Thanks in advance.

---

### Post by ckyfreak1025 on 2013-03-08
bump?

---

### Post by Firedahl on 2013-05-04
Same Issue here. I think ubuntu dont like this BW drive.

I always need to unplug the sata to the BW drive before booting from windows and into ubuntu

Running ubuntu 13.04 x64

---

