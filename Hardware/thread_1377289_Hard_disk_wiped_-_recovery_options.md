---
title: "Hard disk wiped - recovery options?"
date: 2010-01-10
forum: Hardware
---

### Post by Barrasmara on 2010-01-10
Hi everybody.  I posted this in the installation and upgrade section, but it probably belongs here as it is a data recovery issue.

My computer had two large media disks, connected in a RAID1 arrangement.  I upgraded from 9.04 to 9.10 and the disks have been wiped. I thought it would be a safe thing to do - I have moved from 8.04 to 8.10 to 9.04 with no problems.

I then went in to the RAID utility, removed the mirror arrangement and took one of the disks out (thinking that if worst comes to worst I can send it to a data recovery centre).  I looked at the disk using Palimpsest disk utility - it is still seeing it there but says that it is unallocated, and the same when I used Gparted.

I then did the following.

sudo lshw -C disk
  *-disk
     descrpition: ATA Disk
     product: SAMSUNG HD103UJ
     physical id: 0.0.0
     bus info: scsi@1:0.0.0
     logical name: /dev/sda
     version: 1AA0
     serial: S13PJ1BQ807868
     size: 931GiB (1TB)
     configuration: ansiversion=5

I figured that it is unlikely that the data would be deleted - more likely that the partition has died somehow.  So I tried to use parted to rescue it.
 
sudo swapoff -a
sudo parted /dev/sda
(parted) rescue
   Error: /dev/sda: unrecognised disk label
(parted) print
    Error: /dev/sda: unrecognised disk label

I got stuck at this point, so I burned off a copy of the Ubuntu-rescue-remix cd and had a go with testdisk.  It said that *"Partition sector* doesn't *have the endmark* 0xAA55". I am really out of my element here - what do I do next? The disk is one partition, not a boot disk and was in ext3 format. What has gone wrong, what do I do next? 

Any help would be greatly appreciated.  I had hundreds of gigs worth of pictures on there including my wedding!  I thought they would be safe as I was backing up in the RAID1 arrangement - I didn't consider wrecking them both at the same time!

Thanks,

Matt

---

### Post by Alex!!!! on 2010-01-10
I think, you didn't use the upgrade option. There must've been an upgrade disc iso on the ubuntu site. I'll check that. I think you should go to some support center and pay them to recover everything.

---

### Post by Alex!!!! on 2010-01-10
I just checked. The problem is, that to upgrade you needed to apply all updates on 9.04. If you didn't, that is very bad. Sorry, I will try to find out more.
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Barrasmara on 2010-01-10
I'm 99% sure I was up to date on the updates.

---

