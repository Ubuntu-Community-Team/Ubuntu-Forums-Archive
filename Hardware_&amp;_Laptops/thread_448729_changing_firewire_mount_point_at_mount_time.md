---
title: "changing firewire mount point at mount time"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by johncarter on 2007-05-19
Hi

background:
I've bough three external WD firewire drives to backup my 3 NAS's.
They show up on the desktop as ieee1394disk, ieee1394disk-1, ieee1394disk-2.
The problem is that the name they get depends on the order that are connect rather than each drive always having the same name.
I've tried renaming them but the name is when the drive is power cycled.

my proposed solution:
I could have a file called "name" in the root dir of each drive that would contain a word such as WD1b that could be used to id  the drive. this id could then be used to remap / mount the drive to /media/wd1b 

my questions:
1) how do i get my remounting script called before other scripts that write to /media/wd1b
2) how do i get my remounting script to be called when a drive is inserted.
3) how do i remount the new drive to /media/wd1b

thanks john

---

### Post by ola on 2007-05-19
Can you find the devices in /dev? USB-drives are usually located in something like /dev/sda* If you can you might be able to put tree entries in you /etc/fstab file.

I have never played around with Firewire disks but this might (if you are lucky) at least get you starting...

Good luck and hope you find a good solution to your problem.

---

### Post by johncarter on 2007-05-20
Hi 

Thanks ola. Problem solved, a simple solution really.

what you said got me thinking. I googled "ubuntu tree entries fstab"
and found this link in the results
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
the key idea is label. see "how to label" about 1/3 the way down the linked page.
when you label the drive, the drive will me mounted /media/<label> after the next boot.
NOTE: /media/<label> must NOT exist (its autocreated by pmount)

the steps i took were are as follows.
I had previously reformatted my drives to ext2.

1) note the folders in media that are not the prefered mount points. ieee1394disk , -1 , -2 in my case.

2) establish what your prefered mount point would be based on the contents of the drive eg music or movies or photos. 
In other words the drive currenly mounted in  /media/ieee1394disk-1 contains music so /media/music would be the prefered mount point
ieee1394disk      should be   wd3b
ieee1394disk-1  should be   wd2b
ieee1934disk-2  should be   wd1b

3) in the toolbar open system->administrator->disks
4) search the partition tab of each drive to find the existing  mount points mentioned in step #1
note the dev for each wrong mount point. for me it was 
dev_name        mount_point
/dev/sda1   ->  ieee1394disk
/dev/sdb1   ->  ieee1394disk-1
/dev/sdc1   ->  ieee1394disk-2

5) as mentioned above my drives were already re-formated to ext2, for non ext2 formated drives see the linked page above.
to labed your ext2 drive simply type
sudo e2label <dev_name> <bable>
for me this was
sudo e2label /dev/sda1 wd3b
sudo e2label /dev/sdb1 wd2b
sudo e2label /dev/sdc1 wd1b

6) thats it no need to update /etc/fstab. 
after a reboot my wd1b wd2b wd3b firewire icons showed upon my desktop.

---

