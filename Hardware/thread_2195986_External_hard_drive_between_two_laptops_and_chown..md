---
title: "External hard drive between two laptops and chown..."
date: 2013-12-27
forum: Hardware
---

### Post by Deanobats on 2013-12-27
I work from two laptops, both Ubuntu Saucy. I keep most of my files on a portable 1TB hard-drive as I work with a lot of large data-acquisition files and the drives on both laptops are too small (the portable drives are formatted as Ext3). This external drive is backed-up onto an identical drive and both are protected by Trucrypt. However, when I work on laptop 1 (the main one) and then plug the drive into laptop 2, while I can see the files I can't work with them as I'm not the owner and have to Chown them. Is there a way around this every time I move the drive between two machines? Also, at some point in the future I may need to access the drives on a Windows machine, so I assume I'll have to re-format them to NTFS. Will there be any issues with doing this for access from my first two Ubuntu machines?

Ta!

---

### Post by vanadium on 2013-12-28
If you'd had the same user's ID on both machines, it would not be a problem. The first user created on an Ubuntu system has the user id 1000. The user id of an account can be changed with the command usermod.

ntfs formatted systems can be used under linux. The only issue is that linux ntfs reparation tools are allegedly limited, and thus you would need access to a Windows machine from time to time in order to check the ntfs file system.

---

