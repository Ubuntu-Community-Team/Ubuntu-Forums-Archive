---
title: "Mounting my hdd"
date: 2008-09-06
forum: General Help
---

### Post by MTy on 2008-09-06
Alright this is my first time setting up a linux system so i need some help. First order of business is to mount my secondary hdd. 

When entering the bios both of my hdds are there but when i try to mount it its nowhere to be found, no /dev/hda hdb hdc or hdd what have i done wrong here?

Not sure what info you need to pin point the problem, just tell me and i'll look it up.


thx / mty

---

### Post by Gerlads Mod on 2008-09-06
Enter "sudo fdisk -l" to see all the partitions on your hard drive. (I have no clue if it display's other hard drives.)

---

### Post by Vivaldi Gloria on 2008-09-06
To begin with hardy uses /dev/sdx rather than /dev/hdx. 

Open a terminal and post the results of the commands

```
sudo fdisk -l
ls /dev/disk/* -lah
cat /etc/fstab
```

Please use code tags around the code.

---

### Post by MTy on 2008-09-07
Thanks! Okej the this is what the commands revealed, i cant really copy-paste the results since its the server edition im setting up.

Anyway the "sudo fdisk -l" commando revealed to me that my hdd is located at "/dev/sdb" and the "ls /dev/disk/* -lah" revealed that there where 3 parts of that hdd. Not sure what this means but you surely do. And fstab file only shows the cd-rom and floppy..

Now when i try to mount this it wants me so specify a filesystem and since i did use this hdd with my linux server last time it should be FAT right because linux cant run NTFS.

thanks / mty

---

### Post by hyper_ch on 2008-09-07
sure you can copy'n'paste that (if you have two computers)

(1) install ssh server
```

sudo apt-get install openssh-server

```

(2) with the other computer, open a terminal and log into the server
```

ssh USER@SERVER_IP

```

[(3) when running a ssh-server you might also want to install denyhosts or fail2ban]

---

### Post by MTy on 2008-09-07
ok but then i first need to get my network up and running, my motherboard have no built-in network card so im using a PIC network card. How do i go about to install this?

thanks / mty

---

### Post by Paul41 on 2008-09-07
> **MTy said:**
> Thanks! Okej the this is what the commands revealed, i cant really copy-paste the results since its the server edition im setting up.

Anyway the "sudo fdisk -l" commando revealed to me that my hdd is located at "/dev/sdb" and the "ls /dev/disk/* -lah" revealed that there where 3 parts of that hdd. Not sure what this means but you surely do. And fstab file only shows the cd-rom and floppy..

Now when i try to mount this it wants me so specify a filesystem and since i did use this hdd with my linux server last time it should be FAT right because linux cant run NTFS.

thanks / mty

Sorry if I am not following this correctly but it sounds like you have a drive already formatted and just need to mount it. If that is correct hopefully this will help.

The fdisk command shows you if the partition is fat32. Under "System" it will say FAT32. Linux can read NTFS. It can now write to NTFS also but I have never used this so I don't know how reliable it is. FAT32 works for sure.

If your drive has 3 partitions you should see /dev/sdb1, /dev/sdb2, and /dev/sdb3 in fdisk. If say sdb2 is the one you want to mount and it is FAT32 then you would do the following (where "/your/mount/point" is where you want the drive to show up).

```
sudo mount -t vfat /dev/sdb2 /your/mount/point
```

---

