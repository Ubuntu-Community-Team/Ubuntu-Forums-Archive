---
title: "Installing Ubuntu for the first time problems"
date: 2008-07-23
forum: General Help
---

### Post by dober368 on 2008-07-23
Hi, I'm trying to install Ubuntu for the first time (without removing Windows Vista).

I get to the part where I select the partition info [http://i37.tinypic.com/2d2c3zs.png]("http://i37.tinypic.com/2d2c3zs.png")

After I select it I get this error: [http://i38.tinypic.com/dwbfb8.jpg]("http://i38.tinypic.com/dwbfb8.jpg")

And then I get this: [http://i38.tinypic.com/dxb8s6.png]("http://i38.tinypic.com/dxb8s6.png")

Can someone please tell me where I'm going wrong with this?
Thanks

---

### Post by WRDN on 2008-07-23
The first thing you should do if defragment the NTFS, as this could cause such issues.

Rather than using the partition editor in the installer, I would recommend using GParted Partiton Editor (System > Administration > GParted). Once you have opened this, please post a screenshot of your partitions.

In GParted, you could create the partitions for Ubuntu OR if you resize the Windows partition and leave the "unpartitioned space", then during the installation you can use the option "Use largest free continuous space", if available. Alternatively, if you create the partitions in GParted, you need to at least create a swap partition formatted as "linux-swap" and a root partition- for this the ext3 filesystem is recommended. During the installation process, you can select Manual partitioning and select the partitions you created, then give the root partition the mount point "/". Swap however does not have a mount point.

---

### Post by overdrank on 2008-07-23
> **dober368 said:**
> Hi, I'm trying to install Ubuntu for the first time (without removing Windows Vista).

I get to the part where I select the partition info [http://i37.tinypic.com/2d2c3zs.png]("http://i37.tinypic.com/2d2c3zs.png")

After I select it I get this error: [http://i38.tinypic.com/dwbfb8.jpg]("http://i38.tinypic.com/dwbfb8.jpg")

And then I get this: [http://i38.tinypic.com/dxb8s6.png]("http://i38.tinypic.com/dxb8s6.png")

Can someone please tell me where I'm going wrong with this?
Thanks

Hi and welcome, it may be a simple issue of to many partitions, as you can only have 4 main partitions on a drive unless you create a extended partition. 
Do post what WRDN suggested.

---

### Post by dober368 on 2008-07-23
Many thanks for your replys.

Here's GParted: [http://i36.tinypic.com/5aqpow.png]("http://i36.tinypic.com/5aqpow.png")

---

### Post by WRDN on 2008-07-23
Thanks for posting :)

It appears you currently have 3 primary partitions, and as overdrank mentioned, you can have a maximum of 4.
So, first resize the largest partition (sda3) and then, create a new partition from the unpartitioned space. Select to create as "Extended Partition" and then, right click on this and create another new partition. This will be a "Logical" partition. Create at least 2 logical partitions in the Extended Partition. You must have 1 swap partition (some say this should be double RAM) and 1 other partition. The other partition which you will install the OS on should be formatted to ext3 filesystem. You may want to create a 3rd ext3 partition, and during the installation, this can be given the mount point /home. This means, you can reinstall Ubuntu without losing files and settings.

EDIT:

A graphical tour of partitioning.

[http://i77.photobucket.com/albums/j49/WRDN/1.png](http://i77.photobucket.com/albums/j49/WRDN/1.png)

You must resize sda3 so that you have unpartitioned space, seen in grey in the above image. Note that I have created a fat16 and 2 fat32 partitions. This is because, I am partitioning a flash drive, and cannot give it the NTFS filesystem. 

[http://i77.photobucket.com/albums/j49/WRDN/2-1.png](http://i77.photobucket.com/albums/j49/WRDN/2-1.png)

In the unallocated space, create an extended partition.

[http://i77.photobucket.com/albums/j49/WRDN/3.png](http://i77.photobucket.com/albums/j49/WRDN/3.png)

Finally, create a linux-swap and ext3 partition from the extended partition.

---

### Post by dober368 on 2008-07-23
This is confusing :???:, can you tell me if I have followed your instructions correctly?

[http://i35.tinypic.com/i1frsg.png]("http://i35.tinypic.com/i1frsg.png")

---

### Post by WRDN on 2008-07-23
I'm guessing it could work, but I would restart the process (just close and reopen GParted, as you have yet to apply the changes).

- First, if /dev/sda3 is mounted, unmount it (right click > unmount)
- Click on /dev/sda3 and click "Resize/Move" button
- Drag the slider from the right to the left, and this will leave you with unallocated space
- Click on the unallocated space and click the "New" button
- Select to create an "Extended" partition from the drop down (top right)
- Click again on the unallocated space that will appear under the Extended partition, and click "New"
- Use the slider to create a new partition- I would recommend creating a partition of around 1Gb. Set this as linux-swap
- Now, click again on the unallocated space, and select "New"
- Select to use the "ext3" filesystem and click OK (by default, it will use all unallocated space)

Post the GParted image here before applying.

EDIT: I've created a quick video on how to create the partitions, and have uploaded the file (2.1Mb) [here]("http://dann18.dann18.karoo.net/partitioning.ogg").

---

