---
title: "hard drive"
date: 2008-11-20
forum: General Help
---

### Post by Engineer101 on 2008-11-20
Hey, I have a question about how to get ubuntu to show the files on my hard drive that are in the Vista partition.
I can access MEDIADIRECT (?, has windows stuff but my music, pictures, etc. are not there), my Recovery partition, and even my MyBook external hard drive (which it reads fine I can pull everything off of it).
I tried downloading NTFS-3G, but it said that I already had a new version installed.
I don't know what to do because I've been searching for a while and can't find any answers for this problem.
Thanks

---

### Post by taurus on 2008-11-20
Install ntfs-config and use it to configure your ntfs partitions.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by Engineer101 on 2008-11-20
I installed it and the only option it gave me was to enable write support for external hard drives. The write support for internal drives was grayed out.

---

### Post by taurus on 2008-11-20
Did you unmount your internal ntfs partition first?  What is the entry in /etc/fstab that you use to mount your internal ntfs partition anyway?

```
sudo fdisk -l
cat /etc/fstab
mount
```

---

### Post by Engineer101 on 2008-11-20
I'm not quite sure what you mean?
My Ubuntu is installed inside of Vista.
I assume that I need to find the location/mounting in Vista, but I honestly don't know how to do that?

---

