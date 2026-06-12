---
title: "New Hard drive, GRUB broken"
date: 2010-04-03
forum: Hardware
---

### Post by sodra on 2010-04-03
Hi guys
I recently got a new hard drive, coppied all the partitions on to the new drive, I tried to boot it, but Its not working. I try to boot, but all I see is the word GRUB at the top left hand corner

What do I do?

Its a WD Green 1TB drive

---

### Post by drs305 on 2010-04-03
You post says you are using Intrepid, but sometimes users don't update their profiles. If you are using Grub2 there are ways to boot from the Grub command line. Here is the community doc for doing this:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode")

If this doesn't work, you can run meierfra's boot info script and post the results here between "code" tags (click on the # icon in the post's menu):
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by oldfred on 2010-04-03
Depending on how you copied you may have the same UUIDs and then grub can get confused. Or you have new UUIDs and both grub & fstab need to be updated. If you copied partitions you did not copy the MBR so either way you need to reinstall grub.

Post the script if you need help to see what is where.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

ls -l /dev/disk/by-uuid/
or 
sudo blkid

---

