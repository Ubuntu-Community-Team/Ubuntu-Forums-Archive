---
title: "Reiserfs problem after 910 upgrade -- can't mount reiserfs"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by wortmanb on 2009-10-31
Did an upgrade of a large media server for my home.  Apparently 910 doesn't like my Reiserfs volume because I just lost my entire 200+GB iTunes library.  I'm trying various things to try to get the box to acknowledge the reiser partition but so far it just steadfastly refuses to mount it.

I just added some resier packages and am now seeing this:

[INDENT]```
root@marvin:/var/log# mount -a
mount: /dev/sdb2 already mounted or /media/audio busy
root@marvin:~# lsof /media/audio
root@marvin:~#
root@marvin:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              16G  8.1G  7.2G  54% /
udev                 1005M  276K 1005M   1% /dev
none                 1005M     0 1005M   0% /dev/shm
none                 1005M  332K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw
/dev/sdd1             107G   38G   64G  38% /media/pictures
/dev/sde1              71G   58G   11G  85% /media/documents
/dev/mapper/sil_agaedebjfbba1
                      185G  176G  8.8G  96% /media/videos
root@marvin:~# grep audio /etc/fstab
LABEL="audio"   /media/audio    reiserfs defaults 0 0
root@marvin:~# mount /dev/sdb2 /temp
mount: /dev/sdb2 already mounted or /temp busy
root@marvin:~# umount /dev/sdb2
umount: /dev/sdb2: not mounted
root@marvin:~#

```[/INDENT]
Reiserfsck turned up no errors, no corruptions on the filesystem so I'm kind of at a loss as to why it's suddenly unmountable.  Palimpset says there's no problem with the partition or its filesystem.

Any ideas from the smart people?  ;-)

BTW, apart from this, the upgrade went without a hitch, which is great because this is a headless box and I administer it via vnc so when things go wrong, it's a real headache.

---

### Post by bovinius on 2009-11-29
it is possible that temp really is busy so try making a new mountpoint that wont get used..eg...

sudo mkdir /mnt/drive-temp
sudo mount /dev/sdb1 /mnt/drive-temp

I just tried the same thing. no probs with mounting 9.10 reiserfs.
however I still cant get grub2 to see the OS on this partition.

---

