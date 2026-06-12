---
title: "How can I recover missing HD space?"
date: 2008-11-20
forum: General Help
---

### Post by joe56 on 2008-11-20
Using a livecd and gparted I tried to shrink sda5 and grow sda7 by about 25G. It shrunk my ubuntu(sda5) partition but I'm not seeing the transferred free space on my Arch(sda7) partition. There was a warning during the process: 'please run e2fsck2' although everything seems to have finished. If I run gparted it shows my Arch parition to be about 50G(with approx. 38G used) but when I boot Arch it only shows my drive to be 25G. 

sda1 is primary
5,6(swap), and 7 are logical

```
[joe@jdesk ~]$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              25G   13G   11G  55% /
none                  502M     0  502M   0% /dev/shm
/dev/sda5              24G   15G  8.0G  65% /mnt/ubuntu
/dev/sda1             110G   80G   31G  72% /mnt/windows
[joe@jdesk ~]$
```

I intend to wipe the logical partition and reinstall Arch with primary root/swap partitions but I would like to have the space as it may be a month or two before I get around to it. Any suggestions? Thanks!

Edit: Also feel free to let me know which commands could provide useful info. I'm not sure what might be helpful.

---

