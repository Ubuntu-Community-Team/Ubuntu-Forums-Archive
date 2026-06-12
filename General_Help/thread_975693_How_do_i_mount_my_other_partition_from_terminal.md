---
title: "How do i mount my other partition from terminal?"
date: 2008-11-08
forum: General Help
---

### Post by reinaldistic on 2008-11-08
I want to mount my other partition at startup i already know how to make terminal comands run at startup so how do i mount my other partition from terminal?

---

### Post by taurus on 2008-11-08
What are the filesystems of other partitions?

```
sudo fdisk -l
```

---

### Post by reinaldistic on 2008-11-08
Device boot|start|end|blocks|id|system,/dev/sda1|1|981|7877488+|c|w95 fat32 (lba),partition 1 does not end on cylinder boundary,/dev2*|981|20345|155542969|7|hpfs/nfts,/dev/sda3|20346|24321|31937220|5|extended,/dev/sda5|20346|24151|30571663+|83|linux,/dev/sda6|24152|24321|1365493+|82|linux swap / solaris       im doing this from a celphone (no internet) so it took me a while to write and thats why its on that format

---

### Post by taurus on 2008-11-08
```
Device boot|start|end|blocks|id|system,
/dev/sda1|1|981|7877488+|c|w95 fat32 (lba),
partition 1 does not end on cylinder boundary,
/dev/sda2*|981|20345|155542969|7|hpfs/nfts,
/dev/sda3|20346|24321|31937220|5|extended,
/dev/sda5|20346|24151|30571663+|83|linux,
/dev/sda6|24152|24321|1365493+|82|linux swap / solaris
```
I suppose you want to mount both /dev/sda1 & /dev/sda2.  Install ntfs-config and use it to mount your ntfs partition.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by reinaldistic on 2008-11-12
no, its already accesable, i e when i click on it it mounts it, BUT i have to CLICK on it or else it wont mount it what i wanna do is for it to be mounted when i start up... i know how to run commands in terminal at start up, i just dont know what the command would be

---

### Post by iKonaK on 2008-11-12
the cli version (i forgot the GUI)
```
cat /etc/fstab
sudo fdisk -l
mount new drive:
sudo mkdir /seconddrive
sudo mount /dev/sdb1 /seconddrive
```If you want it to mount automatically add this to the bottom of fstab:
/dev/sdb1 /seconddrive ext3 defaults 0 0

---

