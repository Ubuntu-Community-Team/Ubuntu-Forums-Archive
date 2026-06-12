---
title: "Data DVDs not mounting or reading"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by cyrusrayne on 2007-08-26
I have a laptop with an Optiarc DVD-RW AD-7530A DVD/CD combo drive which I have used to write several DVDs worth of data.  However, they will not mount at all under Feisty.  I was able to get them to run fine in another distro of linux (openSUSE) and have reports that friends with feisty have been able to get discs to work fine.

The DVDs were made in Vista Home Premium (in all cases).  I have a suspicion that it could be the drivers for my laptop drive, since my friend's desktop was able to mount them fine under feisty.

---

### Post by ddrichardson on 2007-08-27
Try specifying the filesystem type explicitly via the command line, e.g.```
sudo mount -t iso9660 /dev/hdc /media/dvd
```

You may need to look into the filesytem types (man mount) because I don't know too much about DVD/ISO9660/Joliet Extensions.

---

