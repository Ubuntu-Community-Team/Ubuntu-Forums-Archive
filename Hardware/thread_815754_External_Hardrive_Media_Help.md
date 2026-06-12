---
title: "External Hardrive Media Help"
date: 2008-06-01
forum: Hardware
---

### Post by coolskyfire on 2008-06-01
Alright so what im trying to do is to open up my FreeAgent Drive so i can upload my music files on ubuntu, but when i click on the FreeAgent Drive it comes up with an error saying

Cannot Mount Volume
Unable to mount volume on "FreeAgent Drive"

Do i need to type in a code into the terminal to register it or what, so can someone please help me

---

### Post by Rocket2DMn on 2008-06-02
What happens if you try mounting it from terminal?  Please post
```
sudo fdisk -l
mount
```
If the drive is sdb1 (and ntfs formatted, of course), try running
```
sudo mkdir /media/external
sudo mount -t ntfs-3g /dev/sdb1 /media/external
```

---

