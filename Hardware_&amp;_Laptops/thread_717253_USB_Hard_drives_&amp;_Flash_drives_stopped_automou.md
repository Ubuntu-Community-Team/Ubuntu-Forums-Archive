---
title: "USB Hard drives &amp; Flash drives stopped automounting"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by darth_indy on 2008-03-06
First, my system info: Dell 1420n. It came with Feisty preinstalled, and I used the Dell pre-approved upgrade to Gutsy a month after it came out. I've had no problems with USB before now.

My WD MyBook was auto-mounting fine for a while, then I made the mistake of letting my aunt use it. She uses XP and she was copying video files I have. She unplugged it without doing save unmount and when I plugged it into my computer, it came up with an error message. I can't remember the entire thing, but it was something about not being shut down properly. I tried rebooting my computer , but when I plugged it in after reboot, it gave me the same message. This is when I found out that my aunt had just unplugged it (and I read her the riot act). The message included instructions to make it mount, and I followed the instructions. It had me clear some file that had saved the boot data, and mount it manually, and add an automount to fstab. It mounted inasmuch as I could get to the files read and write, but the icon no longer showed up on my desktop, and it didn't automount after that. Now, my USB flash drive no longer automounts either. I know the USB works, because my wireless mouse works.

My fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=063ca2ba-7913-4228-9bdb-3af3a995e1e0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=127f3851-c2ea-4c81-aa92-f66eec109804 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
UUID=a9bf4295-d4f1-499b-a5ee-927cb7bde6f7  /boot ext3 defaults 0 0
/dev/sdb1	/mdia/disk	ntfs-3g	defaults, force 0 0
```

Any help would be greatly appreciated.

---

