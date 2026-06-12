---
title: "[SOLVED] Resizeing Logical Volume (lvm2) While FS is Online"
date: 2008-10-17
forum: General Help
---

### Post by jerome1232 on 2008-10-17
Ok well Basically I started using LVM because of it's expandability and the ability to resize filesystem while they are online. The fact that if any logical volume fills up, or my entire disk fills up I can add a new disk and expand the volume group onto it. Very sweet I thought.

I want to create a new volume (Ubuntu/data), move some data over to it, then shrink the old volume (Ubuntu/home). Can this be done with the filesystem online? (that notation is (VG/LV)) Everything is on one PE right now.

I purposefully started out with smaller partitions than I normally do with intent to grow them as necessary. 

here's my current setup, all formatted as ext3. I make good backup's so as long as you warn me that something is 'potentially dangerous' go ahead and give me the info ;)

```
  ACTIVE            '/dev/Ubuntu/root' [8.00 GB] inherit
  ACTIVE            '/dev/Ubuntu/swap' [512.00 MB] inherit
  ACTIVE            '/dev/Ubuntu/home' [80.00 GB] inherit
```

They aren't very full at all yet

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Ubuntu-root
                      8.0G  4.2G  3.4G  56% /
varrun                503M  108K  502M   1% /var/run
varlock               503M     0  503M   0% /var/lock
udev                  503M   52K  502M   1% /dev
devshm                503M   12K  502M   1% /dev/shm
lrm                   503M   36M  467M   8% /lib/modules/2.6.24-21-generic/volatile
/dev/sda1             950M   57M  846M   7% /boot
[COLOR="Red"]/dev/mapper/Ubuntu-home
                       80G   24G   52G  32% /home[/COLOR]
gvfs-fuse-daemon      8.0G  4.2G  3.4G  56% /home/jeremy/.gvfs
/dev/scd0             699M  699M     0 100% /media/cdrom0
```

---

### Post by bodhi.zazen on 2008-10-17
May I suggest a few links ?

I have played with LVM and it has some very nice features. I would caution you that I have had some issues with it as well.

[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

[http://tldp.org/HOWTO/LVM-HOWTO/](http://tldp.org/HOWTO/LVM-HOWTO/)

[http://tldp.org/HOWTO/LVM-HOWTO/addpvstovg.html](http://tldp.org/HOWTO/LVM-HOWTO/addpvstovg.html)

[http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html](http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html)

If you would like a brief summary , take a look here :

[ResizeEncryptedPartitions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ResizeEncryptedPartitions#preview") 

Yes, that last link is for LUKS, but it uses LVM as well and will walk you through resizing.

---

### Post by jerome1232 on 2008-10-17
Thanks, in the first guide it recommends playing in a VM first I just might very well do that to get a feel for what can be done and what can't. Especially when it comes to dealing with multiple physical extends.

It seems ext3 must be taken offline for a reduction in size, which is fine since generally I will only be expanding partitions in the future.

---

### Post by bodhi.zazen on 2008-10-17
You are most welcome. The two problems I have had are:

1. Fragmentation. There can be fragmentation of the PV/LV and the only way to defrgment is manually (which is a pain). This has only an issue if you need to downsize.

2. I have had problems when adding to a LV. The resizing does not always go as flawless as it sounds in the documentation.

I think the major advantage of LVM is in snapshots and restoration.

---

### Post by _sAm_ on 2008-10-18
> 1. Fragmentation. There can be fragmentation of the PV/LV and the only way to defrgment is manually (which is a pain). This has only an issue if you need to downsize.
bodhi.zazen could you please tell us how you do that?

> I think the major advantage of LVM is in snapshots and restoration. 
I have read that the "snapshots" isnt good at all for LVM. I have 1.5TB with data on LVM, and so far its been working very good. I have created, resized and deleted several LV(with ext3) and with no trouble at all.

The biggest problem I can see is that if _one_ disk fails the _hole_ LVM will fail. I have backup, but still this means a lot of work(comapred to *mhddfs* where only the data on the disk that fails will be lost). I have used the vgcfgbackup command(as explained here; [http://kbase.redhat.com/faq/FAQ_85_5843.shtm](http://kbase.redhat.com/faq/FAQ_85_5843.shtm)), but never tried it and hope I dont need to. I use LVM on my fileserver, but think I will go for mdhddfs next time.

---

### Post by jerome1232 on 2008-10-18
Well you can also create striped/mirrored LV's (think like a raid array) I'm pretty sure if a disk goes down you only lose any LV's that happen to touch that PE. (I'm going to test that out in my VM actually)

I'm pretty sure by manually defraging bodhi.zazen means moving the files off the drive then moving them back on the drive.

---

### Post by bodhi.zazen on 2008-10-18
It is difficult to find documentation re: LVM and fragmentation of the LV on the PV.

Yes, in general you need to manually move the PV / LV, ie back up your date, delete, and then recreate the LV on the PV.

There is a tool you can look at :

[http://bisqwit.iki.fi/source/lvm2defrag.html](http://bisqwit.iki.fi/source/lvm2defrag.html)

In general I do not think fragmentation affects performance and has / is only an issue when you need to resize, and in particular,down size your PV.

I agree, the time to learn how LVM works is NOT when a hard drive fails. If you use LVM please become familiar with it. Fedora / Centos / RHEL are good sources of information on LVM.

---

### Post by jerome1232 on 2008-12-24
> **bodhi.zazen said:**
> 
I think the major advantage of LVM is in snapshots and restoration.

I know I'm bringing up an old thread but I had a question I'm not sure if I'm understanding snapshots correctly or not. I just recently started going over the threads that you linked me again and wanted to make sure I'm coming away with the right idea.

Say I create a snapshot of my root partition. 

1. So the snapshot is a frozen version of my root partition at the time the snapshot was taken right?

2. Does this mean I could actually make a disk image of that snapshot? I can make an image of my root partition without bringing the system down?

In other words this below would make an image of my root partition /dev/direbane/root? 

```
lvdisplay
  --- Logical volume ---
  LV Name                /dev/direbane/root
  VG Name                direbane
  LV UUID                VVpo54-aQxZ-b3nN-3Bsa-4DGG-Iqud-Bpm2Pg
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                100.00 GB
  Current LE             25600
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:1

lvcreate -L 10G -s -n rootsnapshot /dev/direbane/root
dd if=/dev/direbane/rootsnapshot of=/mnt/Backup/direbaneroot.img bs=10M conv=notrunc
lvremove /dev/direbane/rootsnapshot
```

---

### Post by bodhi.zazen on 2008-12-25
It appears you can (I have not tried it).

I found a link that may help a bit (it is shorter then the others)

[http://www.cyberciti.biz/tips/consistent-backup-linux-logical-volume-manager-snapshots.html](http://www.cyberciti.biz/tips/consistent-backup-linux-logical-volume-manager-snapshots.html)

In that link they claim that snapshots can only be restored to a LVM.

---

