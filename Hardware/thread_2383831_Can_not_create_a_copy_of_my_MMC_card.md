---
title: "Can not create a copy of my MMC card"
date: 2018-01-30
forum: Hardware
---

### Post by kaltsu on 2018-01-30
Hi. I am trying to create a back-up copy of a MMC Card I know. It is a game for the Nokia N-Gage, named Pocket Kingdom. Whenever I try to use the dd if-command:

dd: error reading '/media/kalle/disk': Is a directory
0+0 records in
0+0 records out
0 bytes copied, 0.000217284 s, 0.0 kB/s
root@kalle-LIFEBOOK-S7210:/home/kalle# sudo mount -o remount -o rw /media/disk
mount: mount point /media/disk does not exist
root@kalle-LIFEBOOK-S7210:/home/kalle# sudo mount -o remount -o rw /media/kalle/disk
mount: cannot remount /dev/mmcblk0p1 read-write, is write-protected

I would ask for to how to create a copy of that MMC-card? When I go to properties and permissions, it says I can not change anything because I am not the owner of that file.

---

### Post by sudodus on 2018-01-30
Please post the output of the following commands, when the MMC card is connected. It will help us help you.

```

sudo lsblk -f
sudo lsblk -m
sudo parted -ls
df

```

Please post the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

---

### Post by kaltsu on 2018-01-30
```


sudo lsblk -f


output


```




NAME        FSTYPE LABEL UUID                                 MOUNTPOINT
sr0                                                           
sda                                                           
&#9500;&#9472;sda2                                                        
&#9500;&#9472;sda5      ext4         e01abfeb-f18a-4f88-a5c1-b76dcad2fd0e /
&#9500;&#9472;sda1      ntfs         B07008868A7981B8                     /media/kalle/B0700
&#9492;&#9472;sda6      swap         53680192-f608-468f-a4e4-3d0cdc2520cd [SWAP]
mmcblk0                                                       
&#9492;&#9472;mmcblk0p1 vfat                                              /media/kalle/disk

```


sudo lsblk -m


output


```



NAME          SIZE OWNER GROUP MODE
sr0          1024M root  cdrom brw-rw----
sda         149.1G root  disk  brw-rw----
&#9500;&#9472;sda2          1K root  disk  brw-rw----
&#9500;&#9472;sda5       43.5G root  disk  brw-rw----
&#9500;&#9472;sda1      102.5G root  disk  brw-rw----
&#9492;&#9472;sda6          3G root  disk  brw-rw----
mmcblk0      30.6M root  disk  brw-rw----
&#9492;&#9472;mmcblk0p1  30.6M root  disk  brw-rw----


```


sudo parted -ls

output


```

Model: ATA ST9160412AS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  110GB  110GB   primary   ntfs            boot
 2      110GB   160GB  50.0GB  extended
 5      110GB   157GB  46.7GB  logical   ext4
 6      157GB   160GB  3210MB  logical   linux-swap(v1)


Warning: Unable to open /dev/mmcblk0 read-write (Read-only file system).  /dev/mmcblk0 has been opened read-only.
Model: MMC  (sd/mmc)
Disk /dev/mmcblk0: 32.1MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      32.8kB  32.1MB  32.1MB  primary  fat16


```


df

output


```

Filesystem     1K-blocks     Used Available Use% Mounted on
udev             1506100        0   1506100   0% /dev
tmpfs             306476     5184    301292   2% /run
/dev/sda5       44803516  4602360  37902228  11% /
tmpfs            1532372    35040   1497332   3% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs            1532372        0   1532372   0% /sys/fs/cgroup
tmpfs             306476       80    306396   1% /run/user/1000
/dev/sda1      107501864 14554728  92947136  14% /media/kalle/B07008868A7981B8
/dev/mmcblk0p1     31056    24061      6995  78% /media/kalle/disk

---

### Post by sudodus on 2018-01-30
Please include the *real output of the commands* within the code tags to make it easier to read :-P

---

### Post by sudodus on 2018-01-30
Is the size of the MMC card only 32 MB?

You can clone the MMC card to a card of the same size or bigger, but not one single byte smaller, and you can create an image file, and 'extract' or 'recover' from the image file to the same or another MMC card.

You can use [Clonezilla](http://clonezilla.org) or [mkusb](https://help.ubuntu.com/community/mkusb) to create cloned copies of the card.

If you want to create an image, you can use [Clonezilla](http://clonezilla.org) or the following **dd** command line,

```

sudo dd if=/dev/mmcblk0 of=pocket-kingdom.img

```

You should be able to use [mkusb](https://help.ubuntu.com/community/mkusb) to clone from the dd-image-file to another MMC card. (It is also possible with dd, but dangerous.)

A Clonezilla-image is restored by Clonezilla.

---

### Post by kaltsu on 2018-01-30
So how do I install the Clonezilla thing? I downloaded the files from the link and pasted that command you typed, but nothing happened. I just started to use linux ubuntu today.

---

### Post by sudodus on 2018-01-30
What files did you download? The best method to get Clonezilla is to download a single iso file from the [Clonezilla](http://clonezilla.org/) web site, and clone it to a USB pendrive or burn it to a CD/DVD disk. Please tell me if you need more help with this.

Then you can boot a live system with Clonezilla. This is described with many details in links from the Clonezilla web site.

---

### Post by kaltsu on 2018-01-30
I burned the Clonezilla to a DVD and booted from it but nothing happened.

---

### Post by kaltsu on 2018-01-30
I got the thing working now, it said the image was created successfully. So how do I transfer it to another MMC Card?

---

### Post by sudodus on 2018-01-30
You use Clonezilla and instead of cloning or creating an image, you restore from your Clonezilla image to the other MMC card.

- Select the same options as when you created the image until **the menu 'Select mode', where you should select 'restoredisk'**

- At the next menu you should get the option to 'Choose the image file to restore' (it is actually a *directory* with several files) ...

[hr][/hr]
If you find this complicated, and you can connect two MMC cards at the same time, you can clone directly from one MMC card to another MMC card (for example one card in a built-in card reader and one card in a USB to card adapter). In this case it is extremely important that you can identify the cards, so that you clone in the correct direction.

---

