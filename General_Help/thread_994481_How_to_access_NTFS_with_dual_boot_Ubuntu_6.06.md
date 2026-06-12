---
title: "How to access NTFS with dual boot Ubuntu 6.06"
date: 2008-11-26
forum: General Help
---

### Post by marsheng on 2008-11-26
I Looked at NTFS-3G and the forum recommended I get the version dependent software from Ububtu. As a beginners is there a foolproof method to mount my Windows drives ? Thanks Wallace

---

### Post by logos34 on 2008-11-26
[Here]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#Ubuntu%206.06%20LTS%20%28Dapper%20Drake%29") you go

enjoy

---

### Post by TeXtonyx on 2008-11-26
know

---

### Post by TeXtonyx on 2008-11-26
> **marsheng said:**
> I Looked at NTFS-3G and the forum recommended I get the version dependent software from Ububtu. As a beginners is there a foolproof method to mount my Windows drives ? Thanks Wallace

sudo mkdir /mnt/mswin

sudo mount -t ntfs /dev/sda1 /mnt/mswin

then cd to /mnt/mswin or browse to that directory 

This assumes you Windows partition is on sda1 which is the first
partition of your first drive. If it isn't there or you don't know,
sudo fdisk -l  (small case L)
displays all your partitions. Substitute sdax where x is the ntfs
partition reported by fdisk (not extended) in the /dev/sda1 step

So if fdisk reports Windows in sda3, use 
sudo mount -t ntfs /dev/sda3 /mnt/mswin

This works when Windows shuts down cleanly. If you don't shut down 
Windows properly, then Ubuntu won't mount the Windows partition.

---

### Post by marsheng on 2008-11-26
> **logos34 said:**
> [Here]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#Ubuntu%206.06%20LTS%20%28Dapper%20Drake%29") you go

enjoy

I did the following but still can't mount C Drive



added the following repository:

deb [http://flomertens.free.fr/ubuntu/](http://flomertens.free.fr/ubuntu/) dapper main main-all

Authorizing the Repository:

wget [http://flomertens.free.fr/ubuntu/givre_key.asc](http://flomertens.free.fr/ubuntu/givre_key.asc) -O- | sudo apt-key add 

sudo apt-get update
sudo apt-get upgrade

reboot

sudo apt-get install ntfs-config

What else is there to do ?

---

### Post by logos34 on 2008-11-27
> **marsheng said:**
> 
What else is there to do ?

read the next step 'Configurtion'

gksudo ntfs-config

go thru and create mount point and enable support for internal device

now you should have read+write access to ntfs partition.  May have to reload the desktop and or reboot to get it working

---

