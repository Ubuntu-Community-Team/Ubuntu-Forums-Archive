---
title: "trying to mount 2nd harddrive - fat32"
date: 2009-07-20
forum: Hardware
---

### Post by deymer on 2009-07-20
hey, i just installed xubuntu on the primary hard drive and it works perfectly... but it can't mount the 2nd hard drive. fdisk -l recognizes both hard drives, but no mount...lshw -C disk also recognizes both hard drives. can anyone help me mount this 2nd hard drive so i don't lose my brother's entire music collection?

---

### Post by IcarusR on 2009-07-21
You need to use the 'mount' command. Something like this
```
mount -t vfat /dev/hda1 /mount/point
```
Change /dev/hda1 to what ever fdisk -l says your drive is. Change /mount/point to where ever you want it mounted.

Check the mount manpage
```
man mount
```

---

### Post by deymer on 2009-07-22
thank you, it worked like a charm

---

