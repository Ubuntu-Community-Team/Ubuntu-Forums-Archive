---
title: "Accessing my hard drive"
date: 2008-10-07
forum: General Help
---

### Post by kaze11 on 2008-10-07
Hello, sorry to be a bother here but I'm wondering if someone could help me.

I'm normally a windows user however for various reasons have decided to play around with ubuntu. I'm currently running it off the cd (weird experience) and all seems good. I'm writing this with it.
However, there is a major problem; I can't access my hard disk drives.
I've tried looking with the gui and looking in the terminal but there is no trace of c or d to be found anywhere.
Does anyone know how I could go about using them?

---

### Post by wolfen69 on 2008-10-07
it does not show up in places?

---

### Post by jerome1232 on 2008-10-07
Linux doesn't refer to partitions with drive letters so c: and d: are pretty meaningless in linux terms.

The live cd will not automatically mount any drives. There should be items you can click under the Places menu the will mount them though.


Failing this pop open a terminal (Applications->Accesories->Terminal) and post the output of 
```
sudo fdisk -l
``` and we can help you with mounting the drives

---

### Post by kaze11 on 2008-10-07
> **jerome1232 said:**
> Linux doesn't refer to partitions with drive letters so c: and d: are pretty meaningless in linux terms.

The live cd will not automatically mount any drives. There should be items you can click under the Places menu the will mount them though.


Failing this pop open a terminal (Applications->Accesories->Terminal) and post the output of 
```
sudo fdisk -l
``` and we can help you with mounting the drives

A-ha!
Thanks, I googled that stuff and found out how to do it to a ntfs file. I can now access what is clearly my c drive through the terminal.
However; I can't get near it on the gui which is a far nicer, easier way to get the things I want. How would I make my gui self a super user?


Also; my second hard drive is fat32. IIRC This was a windows only thing?
It says 2 things for it oddly, I don\t know whats what.
/dev/sda2    4106    4870     6144862+   f  W95 Ext'd (LBA)
/dev/sda5    4106    4870     6144831    b  W95 FAT32

---

### Post by jerome1232 on 2008-10-07
> **kaze11 said:**
> A-ha!
Thanks, I googled that stuff and found out how to do it to a ntfs file. I can now access what is clearly my c drive through the terminal.
However; I can't get near it on the gui which is a far nicer, easier way to get the things I want. How would I make my gui self a super user?


Also; my second hard drive is fat32. IIRC This was a windows only thing?
It says 2 things for it oddly, I don\t know whats what.
/dev/sda2    4106    4870     6144862+   f  W95 Ext'd (LBA)
/dev/sda5    4106    4870     6144831    b  W95 FAT32

Well from that output /dev/sda5 is the actual partition, /dev/sda2 you can ignore.

So to mount it:

```
sudo mkdir /mnt/fat32drive
sudo mount /dev/sda5 /mnt/fat32drive -o defaults
```

now you should be able to browser there by opening nautilus (that's the file browser, just click places->computer->filesystem->mnt->fat32drive)

You should be able to read/write, admittedly I don't use any fat32 partitions but that should work.

---

### Post by Ryadt on 2008-10-07
> **kaze11 said:**
> How would I make my gui self a super user?


Use ```
sudo
``` in the terminal and ```
gksudo
``` for gui.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kaze11 on 2008-10-07
Thanks. That works.
Its really weird stuff though, I can access d from the gui just fine. For c though I do not have the permissions (but I do through the terminal).
edit- I can't modify d though...just view.

---

### Post by jerome1232 on 2008-10-07
Well ntfs and fat file systems don't support Unix style permisions so it's all determined on how you mount it, I haven't worked with those for ahwile so I don't remember what mount options you have to specify to make them read/writeable by a normal user.

---

### Post by jerome1232 on 2008-10-07
There I found a spare usbkey and figured it out.
This is for a fat32 file system
```
sudo mount -o iocharset=utf8,umask=000 /dev/sdb1 /mnt/usbkey
```

---

### Post by kaze11 on 2008-10-07
Sorry but...I'm totally lost now. I've lost how to mount my ntfs permission and can't make much sense of that its /dev/sda1....Will look more in case its a hard thing to figure out.

And they're already mounted (badly),would this give me two copies of them or...?


OK...I'm understanding it. How would the command alter for a ntfs though?

---

### Post by jerome1232 on 2008-10-07
Sorry if I posted it in a confusing manner, post this info and I can help clear it up.When you post output from the terminal wrap it in [ code ] [ /code ] tags without the spaces so it is readable.

```
sudo fdisk -l
mount
```

---

### Post by kaze11 on 2008-10-07
```


Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4105    32973381    7  HPFS/NTFS
/dev/sda2            4106        4870     6144862+   f  W95 Ext'd (LBA)
/dev/sda5            4106        4870     6144831    b  W95 FAT32

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001    7  HPFS/NTFS
ubuntu@ubuntu:/$ gksudo
ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4105    32973381    7  HPFS/NTFS
/dev/sda2            4106        4870     6144862+   f  W95 Ext'd (LBA)
/dev/sda5            4106        4870     6144831    b  W95 FAT32
  


```


Its the biggest bit of the internal disk I can't get at,
The external one worked no trouble, just plug in and go.

---

### Post by davidryder on 2008-10-07
Is there anything in your /media folder? Like /media/drv0?

EDIT: Just booted the Live CD and I had my drive listed on the left as "503MB Drive" in nautilus.

---

### Post by kaze11 on 2008-10-07
> **davidryder said:**
> Is there anything in your /media folder? Like /media/drv0?

Just my external drive.

---

### Post by jerome1232 on 2008-10-07
To make sure nothing is mounted (you forgot to post the output of 'mount' I know I made a typo and accidently had an 's' at the end of it)

You  should have been able to mount everything via gui when you first booted into the live cd though.

```
sudo umount /dev/sda1
sudo umount /dev/sda5
mount (nothing should print out that has /dev/sda1 or /dev/sda5)
sudo mkdir /media/fatdrive
sudo mount -o iocharset=utf8,umask=000 /dev/sda5 /media/fatdrive
sudo mkdir /media/ntfsdrive
sudo mount -o iocharset=utf8,umask=000 /dev/sda1 /media/ntfsdrive
```

Should work

---

### Post by kaze11 on 2008-10-07
oh, its the same command for both.

It works perfectly now, thanks a lot, you're a life saver.

---

