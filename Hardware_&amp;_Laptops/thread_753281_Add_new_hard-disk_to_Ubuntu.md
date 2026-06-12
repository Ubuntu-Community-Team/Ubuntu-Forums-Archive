---
title: "Add new hard-disk to Ubuntu"
date: 2008-04-12
forum: Hardware &amp; Laptops
---

### Post by tamoneya on 2008-04-12
ionce you have it installed you need to partition and format the drive.  This can be done with either fdisk or gparted.  gparted it a gui partitioner and may be easier if you are not familiar with partitioning.  ```
sudo apt-get install gparted
sudo gparted
```Here you will see your newly installed harddisk and unless you have specific needs I would suggest that you just make it one big ext3 partition. 

After partitioning you need to mount the drive to your filesystem.  A common place to do this is /home.  The problem with doing this right away is that you wont have anything in your home directory if you do this.  Therefore you should do something like this```
sudo mkdir /newhdd
sudo mount /dev/sdb1 /newhdd
sudo cp /home /newhdd -r
sudo umount /dev/sdb1
sudo mount /dev/sdb1 /home
``` This is assuming that your new partition is /dev/sdb1.  Now all that is left to do is to make it boot automatically.  Add the following line to /etc/fstab
```
/dev/sdb1 /home ext3 defaults 0 0
```

---

