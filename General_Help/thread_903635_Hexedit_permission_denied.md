---
title: "Hexedit permission denied"
date: 2008-08-28
forum: General Help
---

### Post by CoderMan101 on 2008-08-28
I'm new to this forum, so my apologies if this has been covered before.

I have an HP Media Vault and the motherboard died. I don't want to have buy a new unit, but would like to retrieve the data on the hard drives (1 TB of MP3's).

I typed in the following and got a permission denied message. I'm new to Linux, so hopefully it's just something simple I'm missing.

hexedit /dev/sdb

Any help would be greatly appreciated.

Thanks

---

### Post by Taxman415a on 2008-08-28
/dev/sdb is the device file itself, so you don't want to edit that. If you did you'd want to preface your command with sudo. Instead you want to find what partitions are on it with ```
sudo fdisk -l
``` which will tell you there are things like sdb1 and sdb2 on it, then mount the partitions with ```
mount /dev/sdb1 /media/sdb1
``` and if needed, create the mount points with ```
sudo mkdir /media/sdb1
```

Also hexedit it not likely the tool you want. If you can't successfully mount and copy the files you want, you'll want to use some other file recovery tools. This article covers some of the available linux tools. You can install the tools mentioned there with aptitude or synaptic.

[http://www.informationweek.com/shared/printableArticle.jhtml?articleID=208403254](http://www.informationweek.com/shared/printableArticle.jhtml?articleID=208403254)

---

### Post by timcredible on 2008-08-28
assuming you have the drive connected to the machine, just go to Places->Filesystem, and click on the drive on the left window pane, it'll mount the drive and you can get your files off it.

---

