---
title: "Jaunty will not mount external USB hard drive at boot"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by slockton on 2009-05-05
Hello,

I've read the other threads on this matter, but the solutions offered have not worked for me, suggesting this is a new problem - hence the new thread.

Basically, my external USB hard drive does not mount when jaunty boots. It used to in intrepid (I performed a clean install to upgrade). I have the drive correctly listed in fstab, and it mounts when I used "sudo mount -a".

I have added "usb_storage" to my /etc/modules file, as suggested elsewhere to no avail.

Here's my /etc/fstab file
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd1 during installation
UUID=e8784d5e-7473-4af9-bfe9-1a35cc3b5972 /               ext4    relatime,errors=remount-ro 0       
1
# /home was on /dev/sdb1 during installation
UUID=2e4d59c9-0a3f-42f2-b6aa-b15ea2b92735 /home           ext3    relatime        0       2
# swap was on /dev/sdd5 during installation
UUID=804c4e3c-8aab-42a2-8340-441a53f03793 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=a11a95f8-a6a6-4468-989f-cc64c7101973  /home/slockton/Media/        ext3    auto,user   0   0
UUID=30816506-0d6e-4d78-8a25-2b98e183fdd6  /home/slockton/Backup/       ext3    auto,user   0   0
```

The USB drive is the last entry...

Any help would be appreciated - this is driving me insane!

S

---

### Post by fballem on 2009-05-05
I'm having the same problem. This bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347034](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347034) has been filed.

You may wish to subscribe to it so that when it is fixed, you will be notified.

Regards,

---

### Post by pastalavista on 2009-05-05
I've found the easiest way to manage drives is with pysdm (Storage Device Manager)
```
sudo apt-get install pysdm
``` or use Synaptic Package Manager. It will be in System > Administration menu

---

