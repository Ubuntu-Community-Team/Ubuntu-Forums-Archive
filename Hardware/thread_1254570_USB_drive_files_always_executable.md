---
title: "USB drive files always executable"
date: 2009-08-31
forum: Hardware
---

### Post by gorcq on 2009-08-31
I have a small flash USB drive which I use to hold files I want to be working on with my Ubuntu laptop or my Windows desktop depending upon where I am. When I connect the drive to the laptop, the files are always marked as executables, which I notice because I get a dialog when I try to open one asking whether I want to execute it or open in in gVim. I have removed the executable mod using chmod, but when I unmount the drive and later remount it, they are always executable again. This is somewhat annoying. Is there any way to fix this?

---

### Post by matsuzine on 2009-08-31
I've noticed this as well.  I think this has to do with the way FAT32 drives, because they don't have permissions support.  In that case, 777 is the default permission set, I think.  My guess is that you can't change the permissions for the files while on that drive, but copy them to a folder on your hard drive and you could chmod -x and it would probably stick.

Are you using a FAT32 flash drive?

---

### Post by gorcq on 2009-09-01
It is indeed a FAT32 drive. And, it's true that if I copy the files to a folder and change the permissions, they stick; but, if I then copy them back onto the drive, they go back to being executable as soon as I disconnect the drive, making the operation useless.

Would a different format make this stop happening? I could probably back up the files, then reformat the drive in another format, and put the files back on, but I do need to be able to access the files from my Windows computer as well, so I don't think I could use the UNIX format.

---

