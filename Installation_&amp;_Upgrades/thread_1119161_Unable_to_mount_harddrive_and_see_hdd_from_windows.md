---
title: "Unable to mount harddrive and see hdd from windows"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by kanolsen on 2009-04-07
I have 2 sata hdd. One is NTFS formatted (with misc music,data,etc), and one is ext3 formatted (contains the Ubuntu installation).

I can see the ntfs drive from my windows pc, but I can't see the other disk. I get an error message like: "The network folder is connected with another username and passord. To use another username/password unconnect the existing connection" (freely translated). When I try to mount the /media/store folder I get:
*kanolsen@Ubuntu:~$ sudo mount /dev/sda /media/store*
mount: /dev/sda already mounted or /media/store busy
An [forum mentioned device mapper]("http://www.linuxquestions.org/questions/red-hat-31/devsda1-already-mounted-or-mnt-busy.-sata-sil-3112-494987/"), but I don't know anything about it, haven't installed anything special on it.

The Ext3 drive partition I would like to share with windows is /media/store.

I have followed mostly this howto ([http://www.howtoforge.com/ubuntu-home-fileserver-p3]("http://www.howtoforge.com/ubuntu-home-fileserver-p3")

Could anybody point me to the right direction so I can start using the other disk as well? 
Thank you in advance
Kanolsen

I am unsure what info to add so here goes what I have found.
 Ubuntu Desktop with server installation on top v8.10.
Harddrive 1: NTFS (just misc data) Samsung 1tb.
Harddrive 2: ext3 (ubuntu + room for data). Samsung 1tb.

*kanolsen@Ubuntu:~$ sudo fdisk -l*
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b987c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433      121601   957224992+   5  Extended
/dev/sda5            2433        2797     2931831   82  Linux swap / Solaris
/dev/sda6            2798      121601   954293098+  83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31f4aa6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976759808    7  HPFS/NTFS

			
*kanolsen@Ubuntu:~$ df -h*
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  3.1G   15G  18% /
tmpfs                 236M     0  236M   0% /lib/init/rw
varrun                236M  556K  235M   1% /var/run
varlock               236M     0  236M   0% /var/lock
udev                  236M  2.7M  233M   2% /dev
tmpfs                 236M   12K  236M   1% /dev/shm
lrm                   236M  2.0M  234M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda6             896G  7.9G  843G   1% /home
/dev/sdb1             932G  661G  271G  71% /media/1TBsamsung

*# /etc/fstab: static file system information.*
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5de935ac-fa88-4157-83a2-135eedc83f1f /               ext3    relatime,erro$
# /dev/sda6
UUID=49b640d9-e3d5-4675-aee6-1834fabe6585 /home           ext3    relatime     $
# /dev/sda5
UUID=e021ceef-f24b-4408-a1e9-f59c10294214 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda /media/store ext3 defaults 0 0
/dev/sda /share/incoming ext3 defaults 0 0
/dev/sdb1 /media/1TBsamsung ntfs defaults 0 0

*kanolsen@Ubuntu:~$ nano /etc/samba/smb.conf*
[linux]
comment = Public Folder
path = media/store
public = yes
guest ok = yes
writable = yes
create mask = 0777
directory mask = 0777
# force user = nobody
# force group = nogroup

[ntfs]
comment = Public Folder
path = media/1TBsamsung
public = yes
guest ok = yes
writable = yes
create mask = 0777
directory mask = 0777
# force user = nobody
# force group = nogroup

---

### Post by kanolsen on 2009-04-13
Since nobody replies, maybe I am not being specific enough, is there any information I should include for you guys to help out?

Thanks in advance for any help.
Kanolsen

---

### Post by Aubergines on 2009-04-13
You seem to be getting yourself into a bit of a mess. There's some things you need to clarify

I understand you have 2 drives:

**drive 1:** linux is installed, has a folder /media/store which you want to access in windows.

**drive 2:** windows is installed

Now the questions:

a) are the 2 drives on 2 different machines or on the same machine?
b) is your only goal to access data from /media/store from your windows install?

---

### Post by kanolsen on 2009-04-14
Thank you for helping out :)
I understand I need to clarify. 
drive 1: linux is installed, has a folder /media/store which you want to access in windows. *Yes, Ubuntu desktop. Just want to be able to mapping /media/store from my windows client.* 
drive 2: *is a disk formatted as ntfs with no windows or linux on it, pure filestorage.*

Now the questions:

a) are the 2 drives on 2 different machines or on the same machine? *they are both on my ubuntu desktop box with server applications added.* 
b) is your only goal to access data from /media/store from your windows install? *Yes, If I do I would be more than happy. *

The NTFS formatted disk is mapping up just fine, but I can't with the linux formatted /media/store (or any other folder in that disk). 

Kanolsen

---

### Post by Aubergines on 2009-04-14
There might be a better way but you can try installing [this](http://www.fs-driver.org/index.html) on your windows machine to read the linux partitions.

---

### Post by kanolsen on 2009-04-15
Thanks for the tip, will try it tonight, and see if it helps.

Kanolsen

---

### Post by kanolsen on 2009-04-15
Sorry, it didn't work, it seems it only recognises drives physically on the disk. I recognised only the harddriv on the Vista computer and not the drive I have already mapped up from the ubuntu box.

Do you have any other suggestions?

Kanolsen

---

### Post by kanolsen on 2009-04-21
sorry for bumping, but I still have a problem, and somebody sits there with the solution but haven't seen my posting - I hope ;)

Kanolsen

---

