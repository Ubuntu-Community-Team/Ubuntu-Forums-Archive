---
title: "Creating a 2nd Swap disk"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by LibraDragon on 2009-04-11
[FONT=Arial]For wubi installation, the swap.disk is created automatically during installation and the user is not able to specify its size.
What if you want to increase the size of the swap disk to increase swap memory? The most common and easy way out is to create a swap file. See
 [http://www.go2linux.org/Swap-memory-increase-with-swap-file](http://www.go2linux.org/Swap-memory-increase-with-swap-file)

However, this method eats up existing space on root.disk to squeeze out the swap file. If you have free space on the partition which you installed Ubuntu, why not use some of it for a second swap disk? This is what this article is all about: creating a second swap disk.

The following are step-by-step instructions for creating a second swap disk for your wubi ubuntu installation.


1. In Vista, go to programs -> accessories -> right-click on command prompt and select 'run as administrator'.
2. Go to the partition on your hard disk where Wubi Ubuntu is installed. Make sure that the free space on this partition is larger than the size of your intended second swap disk.  Go to ubuntu/disks directory. 
4. Type 
**fsutil file createnew filename filesize**
 where filename can be swap2.disk and filesize is specified in bytes.
 For example to create 2 GB of swap disk file, type
 **fsutil file createnew swap2.disk 2147483648**
 where the filesize is calculated from 2 GB = 2 * 1024 = 2048 MB * 1024 = 2097152 KB * 1024 = 2147483648 bytes
 refer to ([http://www.softwaretipspalace.com/how-to_features/software/how_to_create_empty_file_with_specific_size.html](http://www.softwaretipspalace.com/how-to_features/software/how_to_create_empty_file_with_specific_size.html))
 5. Use JKDefrag to defrag the file to ensure that it is contiguous enough for use as a swap file. JKDefrag can be downloaded free from [http://www.kessels.com/Jkdefrag/](http://www.kessels.com/Jkdefrag/)
 6. Reboot into Ubuntu.
 7. Go to terminal and type
**      sudo mkswap /host/ubuntu/disks/swap2.disk**
 You will see something like 
     Setting up swapspace version 1, size = 2097148 KiB
    no label, UUID=fd0e61d5-0d22-4b48-87e7-d741a19a91fa
 8. To mount the swap disk, type
**      sudo swapon /host/ubuntu/disks/swap2.disk**
 9. Now, we need to mount it every time Ubuntu boots. Type '**sudo gedit /etc/fstab**' (or use any other text editor)
 8. Append the line 
**       /host/ubuntu/disks/swap2.disk   none            swap    sw         0       0**
 just after a similar line for swap.disk. 
 9. Reboot
10. Under System -> Administrator -> system Monitor, you should be able to see the increased swap memory size. 
Another way is to type[/FONT]** swapon -s** in the terminal. You should see
Filename                                                                      Type             Size          Used          Priority
/host/ubuntu/disks/swap.disk                    file                976552        227820        -1
/host/ubuntu/disks/swap2.disk                  file               2097144       25760        -2

[FONT=Arial] 








  [/FONT]

---

