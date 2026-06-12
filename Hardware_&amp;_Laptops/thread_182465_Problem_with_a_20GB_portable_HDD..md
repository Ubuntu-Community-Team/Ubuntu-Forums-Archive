---
title: "Problem with a 20GB portable HDD."
date: 2006-05-26
forum: Hardware &amp; Laptops
---

### Post by DAXP on 2006-05-26
I can't get the thing to work. I originally had it as a FAT32 partition, as I thought both Linux and Windows could use that and I planned on using that to store programs I often used for either OS, add ons for things (like Firefox), mods for games, and the like. Linux couldn't access it, though. So I booted to XP, copied all it's files to an external HDD (NTFS file system), and tried formatting it in Windows. Didn't work, so I tried it with Partition Magic 8 (I think that was it). Still didn't work, so I tried making it an EXT3 partition since there are Windows drivers for it. STILL didn't work. However, I could get to the files I had copied to the second external Drive - the NTFS one. The error I get when trying to mount the smaller HDD I wanted to be Fat32 is:

Unable to mount the selected volume.

(under show more details)
Warning: device /dev/sde5 is already handled by /etc/fstab,
supplied label is ignored
mount: only root can mount /dev/sde5 on /media/sde5
Error: could not execute pmount


I would look the problem up myself, but I'm extremely tired. I plan to go to sleep as soon as I update everything (I just installed Ubuntu again).

---

### Post by xyz on 2006-05-27
Hi-
You could follow these steps here
[https://wiki.ubuntu.com/DebuggingRemovableDevices](https://wiki.ubuntu.com/DebuggingRemovableDevices)
so that someone may be better able to help you. Good luck and let us know.

and
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

