---
title: "SATA disks not mountable while booting, (too fast)"
date: 2010-04-15
forum: Hardware
---

### Post by pksings on 2010-04-15
Hello all;

Installed /boot and / on an OCZ 30GB SSD, reasonably priced from Egghead, machine now boots in about 15 seconds, 10 of which is the BIOS stuff, it actually puts the grub prompt up and then has a login in about 5 seconds. The problem is that my two SATA disks don't mount, they aren't ready, it offers to drop to a emergency shell, 'mount -a' then works fine, exit, it comes up. 

I'm stumped at how to get this to work and am open to any ideas other than removing the SSD disk.

Thanks in advance.

PK

---

### Post by dentman on 2010-04-15
WOW a problem we all wish we had to fast booting.
 I use a program to boot my 4 drives but I don't know if that would help. I just got it from synaptic under NTFS.

Rick

---

### Post by pksings on 2010-04-24
With the absence of help I came up with a very bad but workable workaround.

I removed the entries from /etc/fstab by commenting them out.
I added manual mount commands in /etc/rc.local

It works.

I had hoped that some how this would get to the devs and the scripts that control it would be modified, but oh well.

Someday probably, when somebody important has this problem.

PK

---

