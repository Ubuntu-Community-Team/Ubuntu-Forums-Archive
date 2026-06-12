---
title: "Ubuntu, and Upgrading Hard disks"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by suffer1989 on 2009-06-21
I have a lenovo 3000 n200 with a measly 60Gb Hdd. :( 
I am planning to get a 500 GB hdd to replace the 60 GB one, and installing windoze 7 onto it (when it comes out). I assume that after installling windows, i can install ubuntu 8.10 (my current one), and copy my stuff onto it. 


Is there anyway i can create a clone of my current setup (I.E - all the files,programs, settings, yadda yadda), and and replace the fresh install of the ubuntu (the same distro - 8.10) ? 
Will i be able to copy everything ? 

im sure its been done before, so if nyone has any experience/ has i guide, it would be greatly appreciated. :confused:

---

### Post by labinnsw on 2009-06-21
You can use your current hard disk as the back-up. (i.e. The system is already there in exactly the state you want it, no further need to back up.)

The only problem is to transfer the system to the new hard disk after installing Ubuntu.

Back up /boot and /etc/fstab from the new installation to a safe place.

Overwrite the new installation with the old system. (not sure how you will connect both HDDs at the same time. Some shops can convert the old HDD to a USB Drive)

Replace /boot and /etc/fstab on the overwritten system with the ones you saved earlier.

---

### Post by suffer1989 on 2009-06-21
> **labinnsw said:**
> You can use your current hard disk as the back-up. (i.e. The system is already there in exactly the state you want it, no further need to back up.)

The only problem is to transfer the system to the new hard disk after installing Ubuntu.

Back up /boot and /etc/fstab from the new installation to a safe place.

Overwrite the new installation with the old system. (not sure how you will connect both HDDs at the same time. Some shops can convert the old HDD to a USB Drive)

Replace /boot and /etc/fstab on the overwritten system with the ones you saved earlier.

Im going to copy my current setup  to another portable HDD, then copy it back onto the new ubuntu installation. So, exactly what do you have to copy ?
The boot menu will be different, as this time, im only using ubuntu, but on my new hard disk, ill be using ubuntu and windows 7.

---

### Post by suffer1989 on 2009-06-21
Bump ?

---

### Post by labinnsw on 2009-06-22
To keep it simple, copy the entire disk. Do this as Administrator. ("sudo nautilus" for GUI.)

After you install Ubuntu on the new HDD, you will only need to copy the boot directory and fstab (/boot and /etc/fstab) from that new installation to a safe place. 

You do this so that you can restore them after you copy the old system to the new drive. By so doing you will retain the partition ID, boot and GRUB settings of the new installation which you will use to replace the old one.

Using a live CD and "sudo nautilus" again, overwrite the new system with the old one. Then overwrite the boot directory and fstab with the ones you saved earlier from the new installation.

---

### Post by suffer1989 on 2009-06-22
> **labinnsw said:**
> **To keep it simple, copy the entire disk. Do this as Administrator. ("sudo nautilus" for GUI.)**

After you install Ubuntu on the new HDD, you will only need to copy the boot directory and fstab (/boot and /etc/fstab) from that new installation to a safe place. 

You do this so that you can restore them after you copy the old system to the new drive. By so doing you will retain the partition ID, boot and GRUB settings of the new installation which you will use to replace the old one.

Using a live CD and "sudo nautilus" again, overwrite the new system with the old one. Then overwrite the boot directory and fstab with the ones you saved earlier from the new installation.

The bolded part is the part that i dont get. Do  copy everything under /home, or Under /usr Or everything ? Do i copy everything on the attached screen ?

Thanks for your patience.

---

### Post by labinnsw on 2009-06-22
Copy everything on the attached screen

---

### Post by suffer1989 on 2009-06-23
> **labinnsw said:**
> Copy everything on the attached screen

Thanks, ill update this thread when i do the procedure.

---

### Post by suffer1989 on 2009-08-19
OK, thread Update.
For those who dont know, i wanna copy my current Ubuntu Installation onto a new (larger) hard disk, and i wanna dual boot it with windows. So far, what i Understand is to backup (I.E. Copy everything in the / directory, screenshot above) my current installation (to a USB HDD), then  install windows onto the new HDD, followed by a fresh installation of the distro I had running off the old HDD (8.10).

 Then i have to copy the boot directory and fstab (/boot and /etc/fstab). Then i have to use a live CD, and using "sudo nautilus", copy my old installation over the new fresh ubuntu installation. Then i have to overwrite the boot and Fstab directories with the backups i made.

Then, I should be able to boot up my PC, select Ubuntu from GRUB, and it should work EXACTLY like my current Installation ?

Im sorry im being so paranoid, it took me a great deal of time and effort to get my ubuntu system running the way i wanted it, with all the themes and Apps.

Also, i was told to copy EVERYTHING. What about the "/media" directory ? And what if i want different Partition Sizes in the new ubuntu installation ?

Please claer up these doubts, im really nervous.
Thnaks in advance

---

### Post by labinnsw on 2009-08-19
Actually I have been waiting for you to return. I am like you in that I spend a lot of time setting up my system to be just "so" and that is just the way I want it. I was trying to make things simple but it seems I have failed miserably. Forget what I gave you before. I am going to attach my back-up and restore notes and you can tell me if there is any part of it that you are having a problem with. 

[ATTACH]125462[/ATTACH]

Use the tar notes to do the back-up and restore steps below.

1. Back up the old system to a safe place.
2. Install the new one.
3. From the new system, back up the boot directory (/boot) and fstab (/etc/fstab)
4. From a live CD, restore the Old system overwriting the new one.
5. Overwrite the boot directory with the backed up one.
6. Overwrite fstab with the backed up one.

Except for steps 5 and 6, all these steps must be carried out in that order. You can interchange steps 5 and 6.

I have done them many times on Linux (Ubuntu 8.04), and the steps only vary slightly for Windows.

Once you do the backups, I will be able to help you through any other issues that might arise. (Nil from my experience. It usually just works.)

Additional Information:
On the matter of size
1. You may increase or decrease the partition size as you wish, provided you allow more space than the system will use.
2. I found that if I wanted XP to work, my Linux partition sizes had to have a maximum limit. (70 Gb works)

---

### Post by suffer1989 on 2009-08-19
Ok, i Followed steps 1, and 2, and directed it to a USB hard Disk. 

I got to these instructions :> 

To back up the entire system #Requires less updates to download and less applications to re-install.
===================================================================================================
Using tar
3.      tar cvpzf hardy200900815.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/
sys --exclude=/media / > log.txt

And i got the following Error Message : 

> root@sufy-laptop:/media/disk/Sufyan#         tar cvpzf hardy200900815.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/
tar: Cowardly refusing to create an empty archive
Try `tar --help' or `tar --usage' for more information.
root@sufy-laptop:/media/disk/Sufyan# sys --exclude=/media / > log.txt
The program 'sys' is currently not installed.  You can install it by typing:
apt-get install openafs-client
bash: sys: command not found


Wouldnt it be easier to (or  the same) to use "sudo nautilus" and then copy every directory (to attached HDD) except the ones mentioned in the commands ? I.E. Exclude "/proc", "/lost+found" , "/mnt" , "/sys", and "/media"  ?

---

### Post by presence1960 on 2009-08-19
[PING]("http://ping.windowsdream.com/") stands for Partimage is not Ghost. make images of each partition that can be restored or put onto a new partition.

---

### Post by labinnsw on 2009-08-19
> **suffer1989 said:**
> Ok, i Followed steps 1, and 2, and directed it to a USB hard Disk. 

I got to these instructions :

And i got the following Error Message : 



Wouldnt it be easier to (or  the same) to use "sudo nautilus" and then copy every directory (to attached HDD) except the ones mentioned in the commands ? I.E. Exclude "/proc", "/lost+found" , "/mnt" , "/sys", and "/media"  ?

This should all be in one line like so:

```
tar cvpzf hardy200900815.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media / > log.txt
```

This means exclude the entire system:
```
tar cvpzf hardy200900815.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/
```

Here, this is laid out better:
[ATTACH]125482[/ATTACH]

---

### Post by labinnsw on 2009-08-19
> Wouldnt it be easier to (or  the same) to use "sudo nautilus" and then copy every directory (to attached HDD) except the ones mentioned in the commands ? I.E. Exclude "/proc", "/lost+found" , "/mnt" , "/sys", and "/media"  ?

Yes, or you could delete them afterwards and make new empty ones. (6 of one, half a dozen of the other.)

---

### Post by suffer1989 on 2009-08-20
> **labinnsw said:**
> Yes, or you could delete them afterwards and make new empty ones. (6 of one, half a dozen of the other.)


WOW, talk about An Anticlimax ! The hard disk i bought is Defective. The disks dont even spin or anything. Anyways, ill update this thread when i (hopefully without incident) transfer my system to a new HDD. Thanks for all your help labinnsw, people like you keep the open source effort accessible to new (or like my case nervous) users. thanks all.

will update later.

---

### Post by suffer1989 on 2009-12-02
Ive finally got the courage to make the leap.... I installed a fresh copy of Ubuntu 8.10 onto my 500 GB hdd, then removed it,rebooted from the crusty old HDD and plugged it in VIA USB. However, i cannot copy any of my local files (in the root directory, screenshot in first page) onto the fresh HDD plugged in ... 

heres my fdisk results..

> sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3881d423

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12930   103860193+   7  HPFS/NTFS
/dev/sda3           12931       17909    39993817+   f  W95 Ext'd (LBA)
/dev/sda4           17910       19457    12434310    b  W95 FAT32
/dev/sda5           12931       17287    34997571   83  Linux
/dev/sda6           17288       17909     4996183+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007c49a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6847    54998496   83  Linux
/dev/sdb2            6848        7220     2996122+   5  Extended
/dev/sdb3            7221       28107   167774827+   7  HPFS/NTFS
/dev/sdb5            6848        7220     2996091   82  Linux swap / Solaris


---

### Post by labinnsw on 2009-12-04
Are you doing this as super user?. ("sudo nautilus" in a terminal or use the "sudo cp" command?)

---

### Post by suffer1989 on 2009-12-07
No worries, its all done ... I used partimage ...

---

