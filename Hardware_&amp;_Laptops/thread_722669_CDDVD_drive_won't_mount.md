---
title: "CD/DVD drive won't mount"
date: 2008-03-12
forum: Hardware &amp; Laptops
---

### Post by Lateralis on 2008-03-12
Got a bit of a problem guys.  Here's the problem: 

All started the other night, when I was trying to install Ubuntu on my new computer system.  I have:

Asus P5KC motherboard.  BIOS version 0904
2 SATA hard drives
1 IDE hard drive (on which resides Ubuntu)
1 IDE DVD/CD combo writer drive.  

When I tried to install using the LiveCD, it would get as far as the splash screen, then go black once the bar gets up to the end and do nothing.  Fortunately I have an external CD drive I was able to hook up and set my motherboard to boot from USB.  Consequently I've been able to install Ubuntu quite happily.  

However, it turns out that my CD drive isn't being detected all in Ubuntu.  My /etc/fstab looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=e046f6bd-6692-435b-9696-44c6081312c9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=0408933A089329A6 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc1
UUID=BA6C0F276C0EDE4F /media/sdc1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc2
UUID=FA229C10229BD04D /media/sdc2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=1bb260b1-a903-458f-bf6c-011dbb712070 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

Going into System -> Preferences -> Hardware information I can see my two SATA hard drives and IDE disc drive, but my optical drive isn't listed anywhere as being recognised.  

I know that this CD/DVD drive works - I can use it in XP and Vista fine.  I was also using this DVD drive just a few weeks ago in my old system which was running Xubuntu.  I could even burn DVD's in Xubuntu.  

As there's only one IDE connection on the P5KC both my IDE hard drive and optical drive are connected together.  As I'm able to post this message using Ubuntu, it would seem as though it's detecting the IDE connection OK.  So I'm really quite confused. 

Doesn't anyone know what's going on and have any solutions?  Whilst using the external CD drive at the moment is a useful workaround, it's still only a work around.  It doesn't burn DVD's and that's something I'd rather like to have. :P  

Thanks in advance to anyone that can lend a hand.

---

