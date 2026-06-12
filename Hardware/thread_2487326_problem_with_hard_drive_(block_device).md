---
title: "problem with hard drive (block device)"
date: 2023-05-30
forum: Hardware
---

### Post by jgw on 2023-05-30
I just installed a hard drive which I removed from another computer.  I seemed to be fine on the other machine but, now, its become a "block device".  As far as I know the drive is empty but, now, I am no longer sure.  I doesn't want to mount and just sits there.  I tried to run gparted and just re-partition, etc.  but am not really sure and maybe it just needs to go away.

Thoughts?

---

### Post by Autodave on 2023-05-30
What operating system was the machine running that you pulled that from?

---

### Post by jgw on 2023-05-30
Thank you for the reply.......

I am running with ubuntu 22.04

I also removed the drive and installed it on another machine.  That machine just mounted it as if nothing was wrong.  I have yet to remount it.  This is getting a bit strange.  Oh, the machine it just mounted on was also running 22.04   That being the case I now suspect that it might be the machine and where it gets logged into.  Mine tried to mount at mnt I went there and took a look.  There seems to be more than 20 things.  Out of those 20 things only 3 (hard drives) are connected and all the rest are not.  I tried to delete those not being used but couldn't do that.  I think it might be that mess that has the problems (there was stuff there I had no idea what they were or how they got there).  Most of these names had '0' items attached.

---

### Post by jgw on 2023-05-30
OK, Its fixed.  First I had to learn about removing the empty names in mnt (sudo rmdir /mnt/empty-name).   After that I shut the machine down and re-installed the offending drive.  Then I went to Disks to see what was going on.  I had to check all my connections as I was missing a couple of drives but, after that they were all there!  I then and gave the offending drive a nice short name (in Disks  (in Disks Edit Firesystem) and mounted it.  It mounted!  I checked the drive and everything was there!

Thanks again for the reply - woke me up!

---

