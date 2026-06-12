---
title: "Growing a Linux RAID Device (MDADM)"
date: 2010-04-07
forum: Hardware
---

### Post by AlexDBall on 2010-04-07
Growing a Linux RAID Device (MDADM)

This write-up explains how to grow or expand and existing MD device on your system.
Please note that this may not be the only way to achieve this and that i connot be held responsible if anything goes wrong! It worked for me, i cannot quarranty it will work for you though!
I also know that this may have been posted before, but after spending some time to do it myself, i think that i should post my findings!

This was basically needed for me to grow an existing MD device on my system consisting of 3x1TB drives to 4x1TB drives, then 5x1TB drives.

The layout of the system before the expansion was as follows:
    ```

Physical Disks:
        /dev/sda 160GB
        /dev/sdb 160GB
        /dev/sdc 931GB
        /dev/sdd 931GB
        /dev/sde 931GB

```As you see I have 2x160GB drives and 3x1TB drives.
The first 2 are in RAID1 (mirror) and the last 3 are in RAID5 (stripe with parity)    

    Logical layout/partitioning of disks:
The following lists the partitioning options created while initially setting up the server.

```

/dev/sda:
    /dev/sda1 500MB Linux Raid Autodetect -        /dev/md0
    /dev/sda2 1GB Linux Swap                            /dev/md1
    /dev/sda3 146GB ext4                                  /dev/md2
    
/dev/sdb:
    /dev/sdb1 500MB Linux Raid Autodetect -         /dev/md0
    /dev/sdb2 1GB Linux Swap                             /dev/md1
    /dev/sdb3 146GB ext4                                   /dev/md2
    
/dev/sdc:
    /dev/sdc1 931GB Linux Raid Autodetect -        /dev/md3
 
/dev/sdd:
    /dev/sdd1 931GB Linux Raid Autodetect -        /dev/md3

/dev/sde:
    /dev/sde1 931GB Linux Raid Autodetect -        /dev/md3
```So basically I had the following layout on my server:

        ```

        /dev/md0 500MB /boot            Using: /dev/sda1 & /dev/sdb1 Raid Level 1
        /dev/md1 1GB swap                Using: /dev/sda2 & /devsdb2 Raid Level 1
        /dev/md2 146GB /                  Using: /dev/sda3 & /dev/sdb3 Raid Level 1
        /dev/md3 1.8TB /var              Using: /dev/sdc1, /dev/sdd1 & /dev/sde1 Raid Level 5

```So now we have the layout of the partitions, we can proceed with the expansion of our MD (RAID) device which is /dev/md3.

Tools needed for the expansion:
    > fdisk, mdadm, fsck.ext4, e2fsck, resize2fsFirst we must prepare the new disk to join the array. In this case the new disk is detected as /dev/sdf. I will prepare it using fdisk.

```
    
Run fdisk /dev/sdf and enter the following values to prepare the disk:
    n &#8211; to create a new partition table
    p &#8211; to create a primary partition
    1 &#8211; to be the first partition
    Use the defaults for the First and Last sector, so we use the whole disk
    t &#8211; so we can enter the Type of the partitioned
    fd &#8211; to select &#8220;Linux raid autodetect&#8221; from the Type list.
    w -  to Write the changes and exit

```Now we have /dev/sdf1 ready to be added to the array.

Then we unmount the device that we will be using just to be on the safe side. Things can and may go wrong.

Unmount the device:
    ```
umount /var
```> Note: In my setup. I will be working on /dev/md3 which holds the /var directory. 
In order to unmount it, I initially had to enter single user mode by invoking the following command: 
/sbin/telinit 1Now the device is unmounted, we can start working on it. We will use mdadm to add an extra device and grow the array.

    ```
mdadm --add /dev/md3 /dev/sdf1
```Once the device is added, we grow the array by issuing the following command:
            ```
mdadm --grow /dev/md3 --raid-devices=4
```Now, after this command the array must and will be rebuilt.** DO NOT** proceed until the rebuild process is complete. On this server it took about 30 hours to rebuild.

To view the status of the rebuild process you can type the following command:
    ```
cat /proc/mdstat
```This will show you the status of the arrays on your computer.
You can also type: ```
watch cat /proc/mdstat 
```to show you the status on your screen and update every 2 seconds. To exit from this command press Ctrl+C

After the rebuild of the array is complete, run the following command to check the &#8220;new&#8221; file system of the array:    
    ```
e2fsk -f /dev/md3 
```Now that the file system is &#8220;clean&#8221; we can resize the partition using the following command:
    ```
resize2fs /dev/md3
```Re-mount the drive and check the new size with```
 df -h
```Now on the system /dev/md3 is 2.7TB Using: /dev/sdc1, /dev/sdd1, /dev/sde1 & /dev/sdf1! 

Hopefully your attempt was successful and no data was lost!

---

