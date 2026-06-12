---
title: "ubuntu doesn't see all of hard drive"
date: 2008-08-18
forum: General Help
---

### Post by junior73 on 2008-08-18
Installed Hardy Heron this weekend with the WUBI installer I have partitioned a 50 gig space thru windows vista for this install.  While getting everything loaded up it said there was only 9 gigs of available space left.  Booted up the windows side and it still shows 39 gigs free on the hard drive.  How do I get Ubuntu to recognize the rest of the free space.



TIA



Keith

---

### Post by junior73 on 2008-08-19
Would it work if I resized the partition again and moved my home folder to that drive since it would be the most space?

---

### Post by p_quarles on 2008-08-19
Could you boot up Ubuntu, run the following commands, and post the output?:
```
df -h
```
and
```
du -sh /
```

---

### Post by junior73 on 2008-08-19
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G  4.0G  8.3G  33% /
varrun               1009M  116K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   64K 1009M   1% /dev
devshm               1009M   12K 1009M   1% /dev/shm
lrm                  1009M   39M  970M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sda3              90G   75G   15G  84% /media/sda3
gvfs-fuse-daemon       13G  4.0G  8.3G  33% /home/keith/.gvfs



$ du -sh /
du: cannot read directory `/etc/ssl/private': Permission denied
du: cannot read directory `/etc/firestarter/outbound': Permission denied
du: cannot read directory `/etc/firestarter/inbound': Permission denied
du: cannot read directory `/etc/cups/ssl': Permission denied

I hope this helps.  I don't know what the permission denied is in reference to.

Keith

---

### Post by p_quarles on 2008-08-19
Okay, the first command indicates that your partition is only 13 GB, and you didn't post the total from the second command. 

It sounds like you only dedicated some of the free space on the drive to Ubuntu. The rest wasn't made available to Linux by the installer.

---

### Post by junior73 on 2008-08-19
Wow..I ran it again and got a whole lot more....I let the installer do the work.  Is there a way to let it see the rest of it without a fresh install??

du: cannot read directory `/lost+found': Permission denied
du: cannot read directory `/root/.dbus': Permission denied
du: cannot read directory `/root/.synaptic': Permission denied
du: cannot read directory `/root/.gnome2': Permission denied
du: cannot read directory `/root/.gconfd': Permission denied
du: cannot read directory `/root/.config': Permission denied
du: cannot read directory `/root/.gnome2_private': Permission denied
du: cannot read directory `/root/.gconf': Permission denied
du: cannot read directory `/sys/fs/fuse/connections/2': Permission denied
du: cannot read directory `/sys/fs/fuse/connections/1': Permission denied
du: cannot read directory `/var/run/wpa_supplicant0': Permission denied
du: cannot read directory `/var/run/samba/winbindd_privileged': Permission denied
du: cannot read directory `/var/run/cups/certs': Permission denied
du: cannot read directory `/var/cache/system-tools-backends/backup': Permission denied
du: cannot read directory `/var/cache/ldconfig': Permission denied
du: cannot read directory `/var/lib/PolicyKit': Permission denied
du: cannot read directory `/var/lib/gdm': Permission denied
du: cannot read directory `/var/log/samba/cores': Permission denied
du: cannot read directory `/var/spool/cron/atspool': Permission denied
du: cannot read directory `/var/spool/cron/atjobs': Permission denied
du: cannot read directory `/var/spool/cron/crontabs': Permission denied
du: cannot read directory `/var/spool/cups': Permission denied
du: cannot read directory `/proc/tty/driver': Permission denied
du: cannot read directory `/proc/1/task/1/fd': Permission denied
du: cannot read directory `/proc/1/task/1/fdinfo': Permission denied
du: cannot read directory `/proc/1/fd': Permission denied
du: cannot read directory `/proc/1/fdinfo': Permission denied
du: cannot read directory `/proc/2/task/2/fd': Permission denied
du: cannot read directory `/proc/2/task/2/fdinfo': Permission denied
du: cannot read directory `/proc/2/fd': Permission denied
du: cannot read directory `/proc/2/fdinfo': Permission denied
du: cannot read directory `/proc/3/task/3/fd': Permission denied
du: cannot read directory `/proc/3/task/3/fdinfo': Permission denied
du: cannot read directory `/proc/3/fd': Permission denied
du: cannot read directory `/proc/3/fdinfo': Permission denied
du: cannot read directory `/proc/4/task/4/fd': Permission denied
du: cannot read directory `/proc/4/task/4/fdinfo': Permission denied
du: cannot read directory `/proc/4/fd': Permission denied
du: cannot read directory `/proc/4/fdinfo': Permission denied
du: cannot read directory `/proc/5/task/5/fd': Permission denied
du: cannot read directory `/proc/5/task/5/fdinfo': Permission denied
du: cannot read directory `/proc/5/fd': Permission denied
du: cannot read directory `/proc/5/fdinfo': Permission denied
du: cannot read directory `/proc/6/task/6/fd': Permission denied
du: cannot read directory `/proc/6/task/6/fdinfo': Permission denied
du: cannot read directory `/proc/6/fd': Permission denied
du: cannot read directory `/proc/6/fdinfo': Permission denied
du: cannot read directory `/proc/7/task/7/fd': Permission denied
du: cannot read directory `/proc/7/task/7/fdinfo': Permission denied
du: cannot read directory `/proc/7/fd': Permission denied
du: cannot read directory `/proc/7/fdinfo': Permission denied
du: cannot read directory `/proc/8/task/8/fd': Permission denied
du: cannot read directory `/proc/8/task/8/fdinfo': Permission denied
du: cannot read directory `/proc/8/fd': Permission denied
du: cannot read directory `/proc/8/fdinfo': Permission denied
du: cannot read directory `/proc/9/task/9/fd': Permission denied
du: cannot read directory `/proc/9/task/9/fdinfo': Permission denied
du: cannot read directory `/proc/9/fd': Permission denied
du: cannot read directory `/proc/9/fdinfo': Permission denied
du: cannot read directory `/proc/10/task/10/fd': Permission denied
du: cannot read directory `/proc/10/task/10/fdinfo': Permission denied
du: cannot read directory `/proc/10/fd': Permission denied
du: cannot read directory `/proc/10/fdinfo': Permission denied
du: cannot read directory `/proc/11/task/11/fd': Permission denied
du: cannot read directory `/proc/11/task/11/fdinfo': Permission denied
du: cannot read directory `/proc/11/fd': Permission denied
du: cannot read directory `/proc/11/fdinfo': Permission denied
du: cannot read directory `/proc/46/task/46/fd': Permission denied
du: cannot read directory `/proc/46/task/46/fdinfo': Permission denied
du: cannot read directory `/proc/46/fd': Permission denied
du: cannot read directory `/proc/46/fdinfo': Permission denied
du: cannot read directory `/proc/47/task/47/fd': Permission denied
du: cannot read directory `/proc/47/task/47/fdinfo': Permission denied
du: cannot read directory `/proc/47/fd': Permission denied
du: cannot read directory `/proc/47/fdinfo': Permission denied
du: cannot read directory `/proc/50/task/50/fd': Permission denied
du: cannot read directory `/proc/50/task/50/fdinfo': Permission denied
du: cannot read directory `/proc/50/fd': Permission denied
du: cannot read directory `/proc/50/fdinfo': Permission denied
du: cannot read directory `/proc/51/task/51/fd': Permission denied
du: cannot read directory `/proc/51/task/51/fdinfo': Permission denied
du: cannot read directory `/proc/51/fd': Permission denied
du: cannot read directory `/proc/51/fdinfo': Permission denied
du: cannot read directory `/proc/146/task/146/fd': Permission denied
du: cannot read directory `/proc/146/task/146/fdinfo': Permission denied
du: cannot read directory `/proc/146/fd': Permission denied
du: cannot read directory `/proc/146/fdinfo': Permission denied
du: cannot read directory `/proc/188/task/188/fd': Permission denied
du: cannot read directory `/proc/188/task/188/fdinfo': Permission denied
du: cannot read directory `/proc/188/fd': Permission denied
du: cannot read directory `/proc/188/fdinfo': Permission denied
du: cannot read directory `/proc/189/task/189/fd': Permission denied
du: cannot read directory `/proc/189/task/189/fdinfo': Permission denied
du: cannot read directory `/proc/189/fd': Permission denied
du: cannot read directory `/proc/189/fdinfo': Permission denied
du: cannot read directory `/proc/190/task/190/fd': Permission denied
du: cannot read directory `/proc/190/task/190/fdinfo': Permission denied
du: cannot read directory `/proc/190/fd': Permission denied
du: cannot read directory `/proc/190/fdinfo': Permission denied
du: cannot read directory `/proc/231/task/231/fd': Permission denied
du: cannot read directory `/proc/231/task/231/fdinfo': Permission denied
du: cannot read directory `/proc/231/fd': Permission denied
du: cannot read directory `/proc/231/fdinfo': Permission denied
du: cannot read directory `/proc/232/task/232/fd': Permission denied
du: cannot read directory `/proc/232/task/232/fdinfo': Permission denied
du: cannot read directory `/proc/232/fd': Permission denied
du: cannot read directory `/proc/232/fdinfo': Permission denied
du: cannot read directory `/proc/1516/task/1516/fd': Permission denied
du: cannot read directory `/proc/1516/task/1516/fdinfo': Permission denied
du: cannot read directory `/proc/1516/fd': Permission denied
du: cannot read directory `/proc/1516/fdinfo': Permission denied
du: cannot read directory `/proc/1517/task/1517/fd': Permission denied
du: cannot read directory `/proc/1517/task/1517/fdinfo': Permission denied
du: cannot read directory `/proc/1517/fd': Permission denied
du: cannot read directory `/proc/1517/fdinfo': Permission denied
du: cannot read directory `/proc/1583/task/1583/fd': Permission denied
du: cannot read directory `/proc/1583/task/1583/fdinfo': Permission denied
du: cannot read directory `/proc/1583/fd': Permission denied
du: cannot read directory `/proc/1583/fdinfo': Permission denied
du: cannot read directory `/proc/1587/task/1587/fd': Permission denied
du: cannot read directory `/proc/1587/task/1587/fdinfo': Permission denied
du: cannot read directory `/proc/1587/fd': Permission denied
du: cannot read directory `/proc/1587/fdinfo': Permission denied
du: cannot read directory `/proc/1588/task/1588/fd': Permission denied
du: cannot read directory `/proc/1588/task/1588/fdinfo': Permission denied
du: cannot read directory `/proc/1588/fd': Permission denied
du: cannot read directory `/proc/1588/fdinfo': Permission denied
du: cannot read directory `/proc/1590/task/1590/fd': Permission denied
du: cannot read directory `/proc/1590/task/1590/fdinfo': Permission denied
du: cannot read directory `/proc/1590/fd': Permission denied
du: cannot read directory `/proc/1590/fdinfo': Permission denied
du: cannot read directory `/proc/2346/task/2346/fd': Permission denied
du: cannot read directory `/proc/2346/task/2346/fdinfo': Permission denied
du: cannot read directory `/proc/2346/fd': Permission denied
du: cannot read directory `/proc/2346/fdinfo': Permission denied
du: cannot read directory `/proc/2379/task/2379/fd': Permission denied
du: cannot read directory `/proc/2379/task/2379/fdinfo': Permission denied
du: cannot read directory `/proc/2379/fd': Permission denied
du: cannot read directory `/proc/2379/fdinfo': Permission denied
du: cannot read directory `/proc/2380/task/2380/fd': Permission denied
du: cannot read directory `/proc/2380/task/2380/fdinfo': Permission denied
du: cannot read directory `/proc/2380/fd': Permission denied
du: cannot read directory `/proc/2380/fdinfo': Permission denied
du: cannot read directory `/proc/2381/task/2381/fd': Permission denied
du: cannot read directory `/proc/2381/task/2381/fdinfo': Permission denied
du: cannot read directory `/proc/2381/fd': Permission denied
du: cannot read directory `/proc/2381/fdinfo': Permission denied
du: cannot read directory `/proc/2676/task/2676/fd': Permission denied
du: cannot read directory `/proc/2676/task/2676/fdinfo': Permission denied
du: cannot read directory `/proc/2676/fd': Permission denied
du: cannot read directory `/proc/2676/fdinfo': Permission denied
du: cannot read directory `/proc/2712/task/2712/fd': Permission denied
du: cannot read directory `/proc/2712/task/2712/fdinfo': Permission denied
du: cannot read directory `/proc/2712/fd': Permission denied
du: cannot read directory `/proc/2712/fdinfo': Permission denied
du: cannot read directory `/proc/2714/task/2714/fd': Permission denied
du: cannot read directory `/proc/2714/task/2714/fdinfo': Permission denied
du: cannot read directory `/proc/2714/fd': Permission denied
du: cannot read directory `/proc/2714/fdinfo': Permission denied
du: cannot read directory `/proc/3008/task/3008/fd': Permission denied
du: cannot read directory `/proc/3008/task/3008/fdinfo': Permission denied
du: cannot read directory `/proc/3008/fd': Permission denied
du: cannot read directory `/proc/3008/fdinfo': Permission denied
du: cannot read directory `/proc/3432/task/3432/fd': Permission denied
du: cannot read directory `/proc/3432/task/3432/fdinfo': Permission denied
du: cannot read directory `/proc/3432/fd': Permission denied
du: cannot read directory `/proc/3432/fdinfo': Permission denied
du: cannot read directory `/proc/3469/task/3469/fd': Permission denied
du: cannot read directory `/proc/3469/task/3469/fdinfo': Permission denied
du: cannot read directory `/proc/3469/fd': Permission denied
du: cannot read directory `/proc/3469/fdinfo': Permission denied
du: cannot read directory `/proc/4617/task/4617/fd': Permission denied
du: cannot read directory `/proc/4617/task/4617/fdinfo': Permission denied
du: cannot read directory `/proc/4617/fd': Permission denied
du: cannot read directory `/proc/4617/fdinfo': Permission denied
du: cannot read directory `/proc/4911/task/4911/fd': Permission denied
du: cannot read directory `/proc/4911/task/4911/fdinfo': Permission denied
du: cannot read directory `/proc/4911/fd': Permission denied
du: cannot read directory `/proc/4911/fdinfo': Permission denied
du: cannot read directory `/proc/4912/task/4912/fd': Permission denied
du: cannot read directory `/proc/4912/task/4912/fdinfo': Permission denied
du: cannot read directory `/proc/4912/fd': Permission denied
du: cannot read directory `/proc/4912/fdinfo': Permission denied
du: cannot read directory `/proc/4914/task/4914/fd': Permission denied
du: cannot read directory `/proc/4914/task/4914/fdinfo': Permission denied
du: cannot read directory `/proc/4914/fd': Permission denied
du: cannot read directory `/proc/4914/fdinfo': Permission denied
du: cannot read directory `/proc/4916/task/4916/fd': Permission denied
du: cannot read directory `/proc/4916/task/4916/fdinfo': Permission denied
du: cannot read directory `/proc/4916/fd': Permission denied
du: cannot read directory `/proc/4916/fdinfo': Permission denied
du: cannot read directory `/proc/4918/task/4918/fd': Permission denied
du: cannot read directory `/proc/4918/task/4918/fdinfo': Permission denied
du: cannot read directory `/proc/4918/fd': Permission denied
du: cannot read directory `/proc/4918/fdinfo': Permission denied
du: cannot read directory `/proc/5102/task/5102/fd': Permission denied
du: cannot read directory `/proc/5102/task/5102/fdinfo': Permission denied
du: cannot read directory `/proc/5102/fd': Permission denied
du: cannot read directory `/proc/5102/fdinfo': Permission denied
du: cannot read directory `/proc/5151/task/5151/fd': Permission denied
du: cannot read directory `/proc/5151/task/5151/fdinfo': Permission denied
du: cannot read directory `/proc/5151/fd': Permission denied
du: cannot read directory `/proc/5151/fdinfo': Permission denied
du: cannot read directory `/proc/5152/task/5152/fd': Permission denied
du: cannot read directory `/proc/5152/task/5152/fdinfo': Permission denied
du: cannot read directory `/proc/5152/fd': Permission denied
du: cannot read directory `/proc/5152/fdinfo': Permission denied
du: cannot read directory `/proc/5220/task/5220/fd': Permission denied
du: cannot read directory `/proc/5220/task/5220/fdinfo': Permission denied
du: cannot read directory `/proc/5220/fd': Permission denied
du: cannot read directory `/proc/5220/fdinfo': Permission denied
du: cannot read directory `/proc/5276/task/5276/fd': Permission denied
du: cannot read directory `/proc/5276/task/5276/fdinfo': Permission denied
du: cannot read directory `/proc/5276/fd': Permission denied
du: cannot read directory `/proc/5276/fdinfo': Permission denied
du: cannot read directory `/proc/5278/task/5278/fd': Permission denied
du: cannot read directory `/proc/5278/task/5278/fdinfo': Permission denied
du: cannot read directory `/proc/5278/fd': Permission denied
du: cannot read directory `/proc/5278/fdinfo': Permission denied
du: cannot read directory `/proc/5300/task/5300/fd': Permission denied
du: cannot read directory `/proc/5300/task/5300/fdinfo': Permission denied
du: cannot read directory `/proc/5300/fd': Permission denied
du: cannot read directory `/proc/5300/fdinfo': Permission denied
du: cannot read directory `/proc/5316/task/5316/fd': Permission denied
du: cannot read directory `/proc/5316/task/5316/fdinfo': Permission denied
du: cannot read directory `/proc/5316/task/5665/fd': Permission denied
du: cannot read directory `/proc/5316/task/5665/fdinfo': Permission denied
du: cannot read directory `/proc/5316/task/5671/fd': Permission denied
du: cannot read directory `/proc/5316/task/5671/fdinfo': Permission denied
du: cannot read directory `/proc/5316/task/6295/fd': Permission denied
du: cannot read directory `/proc/5316/task/6295/fdinfo': Permission denied
du: cannot read directory `/proc/5316/fd': Permission denied
du: cannot read directory `/proc/5316/fdinfo': Permission denied
du: cannot read directory `/proc/5330/task/5330/fd': Permission denied
du: cannot read directory `/proc/5330/task/5330/fdinfo': Permission denied
du: cannot read directory `/proc/5330/fd': Permission denied
du: cannot read directory `/proc/5330/fdinfo': Permission denied
du: cannot read directory `/proc/5343/task/5343/fd': Permission denied
du: cannot read directory `/proc/5343/task/5343/fdinfo': Permission denied
du: cannot read directory `/proc/5343/fd': Permission denied
du: cannot read directory `/proc/5343/fdinfo': Permission denied
du: cannot read directory `/proc/5363/task/5363/fd': Permission denied
du: cannot read directory `/proc/5363/task/5363/fdinfo': Permission denied
du: cannot read directory `/proc/5363/fd': Permission denied
du: cannot read directory `/proc/5363/fdinfo': Permission denied
du: cannot read directory `/proc/5364/task/5364/fd': Permission denied
du: cannot read directory `/proc/5364/task/5364/fdinfo': Permission denied
du: cannot read directory `/proc/5364/fd': Permission denied
du: cannot read directory `/proc/5364/fdinfo': Permission denied
du: cannot read directory `/proc/5406/task/5406/fd': Permission denied
du: cannot read directory `/proc/5406/task/5406/fdinfo': Permission denied
du: cannot read directory `/proc/5406/fd': Permission denied
du: cannot read directory `/proc/5406/fdinfo': Permission denied
du: cannot read directory `/proc/5470/task/5470/fd': Permission denied
du: cannot read directory `/proc/5470/task/5470/fdinfo': Permission denied
du: cannot read directory `/proc/5470/fd': Permission denied
du: cannot read directory `/proc/5470/fdinfo': Permission denied
du: cannot read directory `/proc/5506/task/5506/fd': Permission denied
du: cannot read directory `/proc/5506/task/5506/fdinfo': Permission denied
du: cannot read directory `/proc/5506/fd': Permission denied
du: cannot read directory `/proc/5506/fdinfo': Permission denied
du: cannot read directory `/proc/5509/task/5509/fd': Permission denied
du: cannot read directory `/proc/5509/task/5509/fdinfo': Permission denied
du: cannot read directory `/proc/5509/fd': Permission denied
du: cannot read directory `/proc/5509/fdinfo': Permission denied
du: cannot read directory `/proc/5528/task/5528/fd': Permission denied
du: cannot read directory `/proc/5528/task/5528/fdinfo': Permission denied
du: cannot read directory `/proc/5528/fd': Permission denied
du: cannot read directory `/proc/5528/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5531/fd': Permission denied
du: cannot read directory `/proc/5531/task/5531/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5533/fd': Permission denied
du: cannot read directory `/proc/5531/task/5533/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5534/fd': Permission denied
du: cannot read directory `/proc/5531/task/5534/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5535/fd': Permission denied
du: cannot read directory `/proc/5531/task/5535/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5536/fd': Permission denied
du: cannot read directory `/proc/5531/task/5536/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5537/fd': Permission denied
du: cannot read directory `/proc/5531/task/5537/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5538/fd': Permission denied
du: cannot read directory `/proc/5531/task/5538/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5540/fd': Permission denied
du: cannot read directory `/proc/5531/task/5540/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5541/fd': Permission denied
du: cannot read directory `/proc/5531/task/5541/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5542/fd': Permission denied
du: cannot read directory `/proc/5531/task/5542/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5543/fd': Permission denied
du: cannot read directory `/proc/5531/task/5543/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5544/fd': Permission denied
du: cannot read directory `/proc/5531/task/5544/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5545/fd': Permission denied
du: cannot read directory `/proc/5531/task/5545/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5546/fd': Permission denied
du: cannot read directory `/proc/5531/task/5546/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5547/fd': Permission denied
du: cannot read directory `/proc/5531/task/5547/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5548/fd': Permission denied
du: cannot read directory `/proc/5531/task/5548/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5549/fd': Permission denied
du: cannot read directory `/proc/5531/task/5549/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5550/fd': Permission denied
du: cannot read directory `/proc/5531/task/5550/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5551/fd': Permission denied
du: cannot read directory `/proc/5531/task/5551/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5552/fd': Permission denied
du: cannot read directory `/proc/5531/task/5552/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5553/fd': Permission denied
du: cannot read directory `/proc/5531/task/5553/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5554/fd': Permission denied
du: cannot read directory `/proc/5531/task/5554/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5555/fd': Permission denied
du: cannot read directory `/proc/5531/task/5555/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5556/fd': Permission denied
du: cannot read directory `/proc/5531/task/5556/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5557/fd': Permission denied
du: cannot read directory `/proc/5531/task/5557/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5558/fd': Permission denied
du: cannot read directory `/proc/5531/task/5558/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5559/fd': Permission denied
du: cannot read directory `/proc/5531/task/5559/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5560/fd': Permission denied
du: cannot read directory `/proc/5531/task/5560/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5561/fd': Permission denied
du: cannot read directory `/proc/5531/task/5561/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5562/fd': Permission denied
du: cannot read directory `/proc/5531/task/5562/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5563/fd': Permission denied
du: cannot read directory `/proc/5531/task/5563/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5564/fd': Permission denied
du: cannot read directory `/proc/5531/task/5564/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5565/fd': Permission denied
du: cannot read directory `/proc/5531/task/5565/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5566/fd': Permission denied
du: cannot read directory `/proc/5531/task/5566/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5567/fd': Permission denied
du: cannot read directory `/proc/5531/task/5567/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5568/fd': Permission denied
du: cannot read directory `/proc/5531/task/5568/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5569/fd': Permission denied
du: cannot read directory `/proc/5531/task/5569/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5570/fd': Permission denied
du: cannot read directory `/proc/5531/task/5570/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5571/fd': Permission denied
du: cannot read directory `/proc/5531/task/5571/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5572/fd': Permission denied
du: cannot read directory `/proc/5531/task/5572/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5573/fd': Permission denied
du: cannot read directory `/proc/5531/task/5573/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5574/fd': Permission denied
du: cannot read directory `/proc/5531/task/5574/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5575/fd': Permission denied
du: cannot read directory `/proc/5531/task/5575/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5576/fd': Permission denied
du: cannot read directory `/proc/5531/task/5576/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5577/fd': Permission denied
du: cannot read directory `/proc/5531/task/5577/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5578/fd': Permission denied
du: cannot read directory `/proc/5531/task/5578/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5579/fd': Permission denied
du: cannot read directory `/proc/5531/task/5579/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5580/fd': Permission denied
du: cannot read directory `/proc/5531/task/5580/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5581/fd': Permission denied
du: cannot read directory `/proc/5531/task/5581/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5582/fd': Permission denied
du: cannot read directory `/proc/5531/task/5582/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5583/fd': Permission denied
du: cannot read directory `/proc/5531/task/5583/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5584/fd': Permission denied
du: cannot read directory `/proc/5531/task/5584/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5585/fd': Permission denied
du: cannot read directory `/proc/5531/task/5585/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5586/fd': Permission denied
du: cannot read directory `/proc/5531/task/5586/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5587/fd': Permission denied
du: cannot read directory `/proc/5531/task/5587/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5588/fd': Permission denied
du: cannot read directory `/proc/5531/task/5588/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5589/fd': Permission denied
du: cannot read directory `/proc/5531/task/5589/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5590/fd': Permission denied
du: cannot read directory `/proc/5531/task/5590/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5591/fd': Permission denied
du: cannot read directory `/proc/5531/task/5591/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5592/fd': Permission denied
du: cannot read directory `/proc/5531/task/5592/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5593/fd': Permission denied
du: cannot read directory `/proc/5531/task/5593/fdinfo': Permission denied
du: cannot read directory `/proc/5531/task/5780/fd': Permission denied
du: cannot read directory `/proc/5531/task/5780/fdinfo': Permission denied
du: cannot read directory `/proc/5531/fd': Permission denied
du: cannot read directory `/proc/5531/fdinfo': Permission denied
du: cannot read directory `/proc/5532/task/5532/fd': Permission denied
du: cannot read directory `/proc/5532/task/5532/fdinfo': Permission denied
du: cannot read directory `/proc/5532/fd': Permission denied
du: cannot read directory `/proc/5532/fdinfo': Permission denied
du: cannot read directory `/proc/5606/task/5606/fd': Permission denied
du: cannot read directory `/proc/5606/task/5606/fdinfo': Permission denied
du: cannot read directory `/proc/5606/fd': Permission denied
du: cannot read directory `/proc/5606/fdinfo': Permission denied
du: cannot read directory `/proc/5607/task/5607/fd': Permission denied
du: cannot read directory `/proc/5607/task/5607/fdinfo': Permission denied
du: cannot read directory `/proc/5607/fd': Permission denied
du: cannot read directory `/proc/5607/fdinfo': Permission denied
du: cannot read directory `/proc/5618/task/5618/fd': Permission denied
du: cannot read directory `/proc/5618/task/5618/fdinfo': Permission denied
du: cannot read directory `/proc/5618/fd': Permission denied
du: cannot read directory `/proc/5618/fdinfo': Permission denied
du: cannot read directory `/proc/5619/task/5619/fd': Permission denied
du: cannot read directory `/proc/5619/task/5619/fdinfo': Permission denied
du: cannot read directory `/proc/5619/fd': Permission denied
du: cannot read directory `/proc/5619/fdinfo': Permission denied
du: cannot read directory `/proc/5641/task/5641/fd': Permission denied
du: cannot read directory `/proc/5641/task/5641/fdinfo': Permission denied
du: cannot read directory `/proc/5641/fd': Permission denied
du: cannot read directory `/proc/5641/fdinfo': Permission denied
du: cannot read directory `/proc/5661/task/5661/fd': Permission denied
du: cannot read directory `/proc/5661/task/5661/fdinfo': Permission denied
du: cannot read directory `/proc/5661/fd': Permission denied
du: cannot read directory `/proc/5661/fdinfo': Permission denied
du: cannot read directory `/proc/5703/task/5703/fd': Permission denied
du: cannot read directory `/proc/5703/task/5703/fdinfo': Permission denied
du: cannot read directory `/proc/5703/fd': Permission denied
du: cannot read directory `/proc/5703/fdinfo': Permission denied
du: cannot read directory `/proc/5704/task/5704/fd': Permission denied
du: cannot read directory `/proc/5704/task/5704/fdinfo': Permission denied
du: cannot read directory `/proc/5704/fd': Permission denied
du: cannot read directory `/proc/5704/fdinfo': Permission denied
du: cannot read directory `/proc/5719/task/5719/fd': Permission denied
du: cannot read directory `/proc/5719/task/5719/fdinfo': Permission denied
du: cannot read directory `/proc/5719/fd': Permission denied
du: cannot read directory `/proc/5719/fdinfo': Permission denied
du: cannot read directory `/proc/5729/task/5729/fd': Permission denied
du: cannot read directory `/proc/5729/task/5729/fdinfo': Permission denied
du: cannot read directory `/proc/5729/fd': Permission denied
du: cannot read directory `/proc/5729/fdinfo': Permission denied
du: cannot read directory `/proc/5732/task/5732/fd': Permission denied
du: cannot read directory `/proc/5732/task/5732/fdinfo': Permission denied
du: cannot read directory `/proc/5732/fd': Permission denied
du: cannot read directory `/proc/5732/fdinfo': Permission denied
du: cannot read directory `/proc/5767/task/5767/fd': Permission denied
du: cannot read directory `/proc/5767/task/5767/fdinfo': Permission denied
du: cannot read directory `/proc/5767/fd': Permission denied
du: cannot read directory `/proc/5767/fdinfo': Permission denied
du: cannot read directory `/proc/5770/task/5770/fd': Permission denied
du: cannot read directory `/proc/5770/task/5770/fdinfo': Permission denied
du: cannot read directory `/proc/5770/fd': Permission denied
du: cannot read directory `/proc/5770/fdinfo': Permission denied
du: cannot read directory `/proc/5774/task/5774/fd': Permission denied
du: cannot read directory `/proc/5774/task/5774/fdinfo': Permission denied
du: cannot read directory `/proc/5774/fd': Permission denied
du: cannot read directory `/proc/5774/fdinfo': Permission denied
du: cannot read directory `/proc/5812/task/5812/fd': Permission denied
du: cannot read directory `/proc/5812/task/5812/fdinfo': Permission denied
du: cannot read directory `/proc/5812/fd': Permission denied
du: cannot read directory `/proc/5812/fdinfo': Permission denied
du: cannot read directory `/proc/5826/task/5826/fd': Permission denied
du: cannot read directory `/proc/5826/task/5826/fdinfo': Permission denied
du: cannot read directory `/proc/5826/fd': Permission denied
du: cannot read directory `/proc/5826/fdinfo': Permission denied
du: cannot read directory `/proc/5958/task/5958/fd': Permission denied
du: cannot read directory `/proc/5958/task/5958/fdinfo': Permission denied
du: cannot read directory `/proc/5958/fd': Permission denied
du: cannot read directory `/proc/5958/fdinfo': Permission denied
du: cannot read directory `/proc/6089/task/6089/fd': Permission denied
du: cannot read directory `/proc/6089/task/6089/fdinfo': Permission denied
du: cannot read directory `/proc/6089/task/6090/fd': Permission denied
du: cannot read directory `/proc/6089/task/6090/fdinfo': Permission denied
du: cannot read directory `/proc/6089/task/6091/fd': Permission denied
du: cannot read directory `/proc/6089/task/6091/fdinfo': Permission denied
du: cannot read directory `/proc/6089/fd': Permission denied
du: cannot read directory `/proc/6089/fdinfo': Permission denied
du: cannot read directory `/proc/6107/task/6107/fd': Permission denied
du: cannot read directory `/proc/6107/task/6107/fdinfo': Permission denied
du: cannot read directory `/proc/6107/fd': Permission denied
du: cannot read directory `/proc/6107/fdinfo': Permission denied
du: cannot read directory `/proc/6294/task/6294/fd': Permission denied
du: cannot read directory `/proc/6294/task/6294/fdinfo': Permission denied
du: cannot read directory `/proc/6294/fd': Permission denied
du: cannot read directory `/proc/6294/fdinfo': Permission denied
du: cannot read directory `/proc/6324/task/6324/fd': Permission denied
du: cannot read directory `/proc/6324/task/6324/fdinfo': Permission denied
du: cannot read directory `/proc/6324/fd': Permission denied
du: cannot read directory `/proc/6324/fdinfo': Permission denied
du: cannot read directory `/proc/7356/task/7356/fd': Permission denied
du: cannot read directory `/proc/7356/task/7356/fdinfo': Permission denied
du: cannot read directory `/proc/7356/fd': Permission denied
du: cannot read directory `/proc/7356/fdinfo': Permission denied
du: cannot access `/proc/7377/task/7377/fd/4': No such file or directory
du: cannot access `/proc/7377/task/7377/fdinfo/4': No such file or directory
du: cannot access `/proc/7377/fd/4': No such file or directory
du: cannot access `/proc/7377/fdinfo/4': No such file or directory
93G	/

---

### Post by junior73 on 2008-08-19
Alright, poked through the admin resourses, and opened up the storage manager.  It is showing the 39 gig that are free, but it is showing it as haveing no file system and there is no desigantion tagged to it.  How can I make it recogonize this as valid, uisable space?

---

