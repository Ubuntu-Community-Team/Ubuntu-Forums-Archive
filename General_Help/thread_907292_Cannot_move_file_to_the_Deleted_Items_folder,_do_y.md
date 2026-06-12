---
title: "Cannot move file to the Deleted Items folder, do you want to delete permanently?"
date: 2008-09-01
forum: General Help
---

### Post by capo1949 on 2008-09-01
Hi All
I keep getting this message although the folder is empty

I have followed previous post about emptying trash folders, to no avail.

P4 processor, with 3Gb ram and 2x250 Gb sata drives running ubuntu 8.04
with vmware for XP 

graham@graham-desktop:~$ df -Th | sort
/dev/sda1     ext3    223G   16G  197G   8% /
/dev/sdb1  fuseblk    199G  4.1G  195G   3% /media/DRV4_VOL1
/dev/sdb5     ext3     33G   30G  1.7G  95% /media/disk
/dev/sdc1  fuseblk    233G   58G  176G  25% /media/WD USB 2
devshm       tmpfs    1.5G  128K  1.5G   1% /dev/shm
Filesystem    Type    Size  Used Avail Use% Mounted on
fuse.gvfs-fuse-daemon    223G   16G  197G   8% /home/graham/.gvfs
gvfs-fuse-daemon
lrm          tmpfs    1.5G   39M  1.5G   3% /lib/modules/2.6.24-19-generic/volatile
udev         tmpfs    1.5G   84K  1.5G   1% /dev
varlock      tmpfs    1.5G     0  1.5G   0% /var/lock
varrun       tmpfs    1.5G  148K  1.5G   1% /var/run

the media disk looks like the problem?

graham@graham-desktop:~$ sudo find / -type d -iname *Trash* | grep Trash/media/disk/home/graham/.local/share/Trash
/media/disk/.Trash-0
/home/graham/.local/share/Trash
**find: [B]/home/graham/.gvfs**: Permission denied[/B]
graham@graham-desktop:~$ 

I have deleted the contents of trash at these locations.  I dont understand the line in bold, above, is it relevant?

Any ideas to fix this problem?
Graham

---

