---
title: "linux partition viewed in windows..."
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by mwagz on 2007-04-15
ubuntu fiesty 7.04
I have access to windows ntfs partition in my thinkpad while in ubuntu.How can I view linux partitions in windows?
And how can I have 777  permissions to ntfs partitions while in ubuntu( or at least copy files to and from NTFS) ???


I also have an external HDD formatted in NTFS and would like to copy files to and from it while  running ubuntu.

---

### Post by raja on 2007-04-15
To be able to write to NTFS partitions from Ubuntu, you need to install ntfs-3g. It is still beta, but has been mostly reliable. For accessing ext partitions from windows, you have to install a driver from [here.]("http://www.fs-driver.org/")

---

### Post by mwagz on 2007-04-15
I have just installed ntfs-3g, but I cannot copy files to NTFS from Ubuntu linux partition. I can copy files from NTFS to ubuntu though; but I cant delete files in NTFS while I'm in ubuntu!!

---

### Post by mwagz on 2007-04-15
$apt-get install ntfs-3g
bla..bla...bla....

Setting up ntfs-3g (1.328-1) ...
Setting ntfs-3g suid root with group fuse...done
Users from 'fuse' group can now mount NTFS volume.

---

### Post by raja on 2007-04-15
Looks like you dont have write access to the NTFS partition. You have to configure fstab to mount the NTFS drive using ntfs-3g. You can use ntfs-config to do that in a relatively easy manner.

---

### Post by raja on 2007-04-15
> **mwagz said:**
> $apt-get install ntfs-3g
bla..bla...bla....

Setting up ntfs-3g (1.328-1) ...
Setting ntfs-3g suid root with group fuse...done
Users from 'fuse' group can now mount NTFS volume.
 Do```
sudo apt-get install ntfs-config
gksu ntfs-config
``` and it should be easy going from there.

---

### Post by mwagz on 2007-04-15
"Looks like you dont have write access to the NTFS partition."

Do I have to put the NTFS partition to "shared"? How do i gain permissions for read/write access??

---

### Post by mwagz on 2007-04-15
ntfs-3g /dev/sda1 /mnt/windows
fusermount: failed to access mountpoint /mnt/windows: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sda1 (Preload)

---

### Post by ubuntu27 on 2007-04-15
Do this:

```
sudo apt-get install ntfs-3g
```

```
sudo apt-get install ntfs-config
```

```
gksu ntfs-config
```



And if you want to have access to ext3 (Linux File system) from Windows. You can try this program:

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

---

### Post by mwagz on 2007-04-15
I have done all of the above....maybe i need to reboot....

---

### Post by Ebiggs on 2007-04-15
> **ubuntu27 said:**
> Do this:

```
sudo apt-get install ntfs-3g
```

```
sudo apt-get install ntfs-config
```

```
gksu ntfs-config
```



And if you want to have access to ext3 (Linux File system) from Windows. You can try this program:

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

```
ebiggs@ebiggs-gamingpc:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-config
```

Can't find it.

---

### Post by raja on 2007-04-15
ntfs-config is in the universe repos. ```
sudo gedit /etc/apt/sources.list
``` and uncomment the lines ending with universe.

---

### Post by mwagz on 2007-04-16
Thanks Raja....it works!!!

---

