---
title: "new harddrive stalls boot"
date: 2010-06-23
forum: Hardware
---

### Post by crowmobe on 2010-06-23
I just added a 1tb hard drive to my new ubuntu 10.04 install.  I added this line to my /etc/fstab

/dev/sda1    /media/tb   ext4    defaults     0        0

Then I did a:
sudo mount -a

The drive showed up, a df -h looked appropriate.  Everything was great.  But after a restart, it failed to boot properly.  It stalls during mountall and I don't get a prompt.  What am I doing wrong?

Thanks,
Clay

---

### Post by crowmobe on 2010-06-23
Also noteworthy is that I could not unmount once mounted.  This is the error that I get when the boot stalls:
/dev/sda1 was not cleanly unmountsed, check forced
mount: /dev/sda1 already mounted or /media/tb busy.
mountall: mount /media/tb [567] terminated with status 32
mountall: Filesystem could not be mounted: /media/tb

Then there are a few lines that say "codec 0 is not valid"

Picture is attached.

---

### Post by crowmobe on 2010-06-25
I can recover the system if I use the cd to login and remove the line I added to fdisk.  But I ultimately I need that line in fdisk so that my new harddrive shows up.
One detail I left out is that it is a SATA hard drive, and the motherboard does not support SATA.  So I have a Fasttrack card that supports raid (I turned raid on when it asked during install).  The drive is seen at boot time, and it mounts, it just does not unmount, even for a reboot.  I'm hoping someone has seen this before and can offer some advice.  Thanks.

---

