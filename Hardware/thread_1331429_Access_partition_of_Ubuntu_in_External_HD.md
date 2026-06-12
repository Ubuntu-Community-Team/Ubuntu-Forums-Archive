---
title: "Access partition of Ubuntu in External HD"
date: 2009-11-19
forum: Hardware
---

### Post by ThugaPT on 2009-11-19
How do i acess my ubuntu partition in a External HD from windows or in another ubuntu ?](*,)

---

### Post by iNaitvad on 2009-11-19
If you are in windows, you cant (if it is an "ubuntu" partition). Microsoft doesnt provide drivers for other Filesystems (just NTFS and FAT32 or just FAT, yeah..UDF,etc)
If your "ubuntu" partition is EXT2 or EXT3, you might read it on windows with "ext2fs" or Ext2 IFS, google them, they are very easy to find.

On ubuntu you should see your partition right away, go to Places (Lugares in Spanish), they should be there, just not mounted... click them to mount...
Hope this helps, sorry for my crappy english...

---

### Post by hal10000 on 2009-11-19
In windows you need a special driver, depending on the file system you want to access (usually ext3 for jaunty or older ubuntu-versions or ext4 for karmic). I don't know where to get this from, maybe you should take a look at the microsoft sites. I know there is an ext3-plugin fot the **total commander** file manager.

To access it from other linux systems, you just need to mount the device (with root permission)

---

### Post by iNaitvad on 2009-11-19
Thats exactly what i mean, ext2fs...work very well on windows...

---

