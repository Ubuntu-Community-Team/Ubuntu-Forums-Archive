---
title: "Grub fails but boots !!!"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by Waq on 2009-06-21
It is a bit strange and I only noticed it after I tried to migrate to a new harddisk for my laptop (tx1000); The issue actually is that I am unable to reinstall GRUB. Currently, GRUB is installed in my boot partition's MBR (/dev/sda10) and it is booted via Vista's EasyBCD. The root partition resides in /dev/sda9. Following is the result of the commands when I try to reinstall GRUB:  
===============================================================
```

grub> find /grub/stage1
 (hd0,10)

grub> root (hd0,10)

grub> setup (hd0,10)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0,10)"... failed (this is not fatal)
 Running "embed /grub/e2fs_stage1_5 (hd0,10)"... failed (this is not fatal)
 Running "install /grub/stage1 (hd0,10) /grub/stage2 p /grub/menu.lst "... failed

Error 22: No such partition

grub> 

```


Interestingly, the system boots ok. I need to resolve this as I want to clone this whole disk to a bigger and better new disk and it fails to boot there, after cloning.

My fdisk output is as follows:
```

wap@waptop:~$ sudo fdisk -lu
[sudo] password for wap: 
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb83f8f4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   102398309    51199123+   7  HPFS/NTFS
/dev/sda3       102398310   312576704   105089197+   5  Extended
/dev/sda5       102398373   163830869    30716248+   7  HPFS/NTFS
/dev/sda6       163830933   225279494    30724281    7  HPFS/NTFS
/dev/sda7       225279558   229584914     2152678+  82  Linux swap / Solaris
/dev/sda8       229584978   280784069    25599546   83  Linux
/dev/sda9       280784133   312159014    15687441   83  Linux
/dev/sda10      312159078   312576704      208813+  83  Linux
wap@waptop:~$ 

```

Here,
```

/dev/sda8 is /home.
/dev/sda9 is /. 
/dev/sda10 is /boot.

```

I think if I am able to reinstall grub at this disk then I will be able to do it in the new one after cloning. So, How can i reinstall the GRUB here in the partition's MBR.

I am using jaunty on a tx1000 pavilion laptop from hp.
Thanks in advance.

---

### Post by merlinus on 2009-06-21
If / is sda9:

```

sudo grub
root (hd0,8)
setup (hd0)
quit

```

and restart.

---

### Post by presence1960 on 2009-06-21
sda10 = (hd0,9)

numbering for disks and partitions starts at 0 for GRUB. Thus sda1 = (hd0,0) sda2 = (hd0,1), etc

merlin beat me to the punch!

---

### Post by Waq on 2009-06-21
> **merlinus said:**
> If / is sda9:

```

sudo grub
root (hd0,8)
setup (hd0)
quit

```

and restart.

this fails too as follows ...

> grub> find /grub/stage1
 (hd0,10)

grub> root (hd0,8 )

grub> setup (hd0,8 )
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

grub> root (hd0,9)

grub> setup (hd0,9)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

grub> 


---

### Post by Waq on 2009-06-21
Moreover I do not want to install the GRUB in disk's MBR rather I want to have it in Partition's MBR.
/dev/sda8          <--- /home
/dev/sda9          <--- /
/dev/sda10         <--- /boot

---

### Post by merlinus on 2009-06-21
root (hd0,8). 

setup will be (hd0,9) if you want it to be in /boot.

Don't use any of the find commands, because you are reinstalling.

Give it a try....

---

### Post by Waq on 2009-06-21
same results:
```

grub> root (hd0,8)

grub> setup (hd0,9)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found


```

---

### Post by Waq on 2009-06-21
An update: grub-install script failed too. 
```

wap@waptop:~$ sudo grub-install /dev/sda10
[sudo] password for wap: 
Searching for GRUB installation directory ... found: /boot/grub
The file /boot/grub/stage1 not read correctly.

```

Cant this whole old grub be replaced with a fresh new install (only grub, I love my data)?
thanks,

---

### Post by merlinus on 2009-06-22
supergrub may help you to do this:

[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

---

### Post by Waq on 2009-06-22
Ok I got the bugger. The solution I followed is that I installed the newer version of bootloader i.e. grub 2 
```

sudo apt-get install grub-pc

```
then I setup the affected partition with it; in my case my /boot partition i.e. /dev/sda10
```

sudo grub-setup /dev/sda10

```
and thats it. Now, i have new grub in my partition and vista's bootloader fires it up.

---

### Post by presence1960 on 2009-06-22
Great, enjoy Ubuntu!

---

