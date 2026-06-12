---
title: "Don't have privilege to mount HDD."
date: 2008-11-16
forum: Hardware
---

### Post by tomek142 on 2008-11-16
Let my start of by saying that I have three HDD and that I'm running XP and Ubuntu(dual boot). I mounted my HDD in Ubuntu using NTFS Configuration tool but I'm always running Ubuntu now. So I booted XP to play a game and then in the morning when I booted Ubuntu, none of my HDD are mounted. I click on the NTFS Configuration tool but it only gives me the option to enable write support for internal or external devices. So I go to Places -> Removable Media and there are my four HDD (four cause I got one HDD partioned into two) but it says I'm not privileged to mount. Please help me. I'm a total newbie.

I also typed in the terminal sudo fdisk -l and it shows my three HDD.

> 
Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32583   261722916    7  HPFS/NTFS
/dev/sda2           35325       36481     9293602+   c  W95 FAT32 (LBA)
/dev/sda3           32584       35324    22017082+   5  Extended
/dev/sda5           32584       32707      995998+  82  Linux swap / Solaris
/dev/sda6           32708       35324    21021021   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa95ca95c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       24321   195350400    f  W95 Ext'd (LBA)
/dev/sdb5               2       12162    97683201    7  HPFS/NTFS
/dev/sdb6           12163       24321    97667136    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10241023

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2      121601   976752000    f  W95 Ext'd (LBA)
/dev/sdc5               2      121601   976751968+   7  HPFS/NTFS


---

### Post by finito on 2008-11-16
basically, 

do the following 
```
sudo mkdir /media/disk-1 # you can name disk-1 whatever you want
sudo mkdir /media/disk-2 # you can name disk-2 whatever you want
sudo mkdir /media/disk-3 # you can name disk-3 whatever you want

```

then do 
```

sudo fdisk -l
```

you should get somthing like :
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a45f299

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40254024

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         248     1992028+  82  Linux swap / Solaris
/dev/sdb2   *         249       18241   144528772+  83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

```

now what you do is look at the drives you want to mount and do the following

sudo mount /dev/<your drive> /media/disk-1 # or whatever you named it

Good luck

---

### Post by MasterSander on 2008-11-16
You need to add them to /etc/fstab. First make directories where you would like to mount them.
```
 sudo mkdir /media/XP
```
You can choose that for your xp partition.

Then edit /etc/fstab

```
 sudo gedit /etc/fstab 
```

add this to it

```
 /dev/x /media/XP defaults 0 0
```

where x represents the device name, this is sda1 if you have a SATA drive and it's your primary HD and the first primary partition on it. You can check the gnome partition editor to check the names.

---

### Post by MasterSander on 2008-11-16
and reboot, when you're done editing /etc/fstab, what finito said will only work for that session and I think you'd like them to show up every time you boot.

---

### Post by finito on 2008-11-16
I forgot to mention if your drive is ntfs which i think it is you will need to add
-t ntfs-3g 
i.e. 
mount -t ntfs-3g /dev/<your drive> /media/disk-1 ,force 0 0

try without force if it doesnt work use force.

as for MasterSandars method you will need to do the following in fstab
/dev/x /media/XP  ntfs-3g defaults,force 0 0

good luck,

---

### Post by tomek142 on 2008-11-16
I tried to mount it via terminal and not change fstab. I got this

> $LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdc5 /media/HDD3 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdc5 /media/HDD3 ntfs-3g force 0 0


---

### Post by finito on 2008-11-16
do what it says

mount -t ntfs-3g /dev/sdc5 /media/HDD3 -o force

Or add the option to the relevant row in the /etc/fstab file:

/dev/sdc5 /media/HDD3 ntfs-3g force 0 0

---

### Post by tomek142 on 2008-11-16
Yes, I tried that and I know what the problem is. It's one of my HHD has problems. When I turned on Windows the disk checking turned on and scanned it. It turned out that some segments are un-readable and Windows froze then. I assume that this is the problem cause I plugged in other HHD and Ubuntu mounted them. But what I don't get is that if one HHD is broken or not working probably then why is Ubuntu not mounting the working HDD?

---

### Post by finito on 2008-11-17
Probably because the mounting script has the bad HDD as the first HDD, so when the mounting starts it finds an error and stops.

---

