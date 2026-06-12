---
title: "Format NTFS External Hard Drive ?"
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by BennieBlount on 2008-02-26
I have a Maxtor external hard drive formatted with NTFS. Can anyone tell me what application(s) or command(s) I can use to format this drive for use with Ubuntu? I assume the format would need to be ext3?

Thank you,

Bennie

---

### Post by Claus7 on 2008-02-26
Hello,

this might help you :
[http://ubuntuforums.org/showthread.php?t=435870](http://ubuntuforums.org/showthread.php?t=435870)

Regards!

---

### Post by BennieBlount on 2008-02-26
Thank you, but, for a newbie like me..., well, does anyone know of an application to "simply" reformat a hard drive? Windows has many such programs - surely there is a Linux application that can do the same?

I have installed gparted, in hopes that it will do the trick, but all it does is just continues to "scan" for devices.

Help,

Bennie

---

### Post by Claus7 on 2008-02-26
Hello,

how about this :
[http://ubuntuforums.org/showthread.php?t=644014](http://ubuntuforums.org/showthread.php?t=644014)
and this:
[http://ubuntuforums.org/showthread.php?t=687376](http://ubuntuforums.org/showthread.php?t=687376)

they explain a lot on how to mount your ntfs hard drive and then proceed to format it.
Have you installed ntfs-3g?
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

It is not so easy that a ntfs partition will be recognised from linux.

Regards!

---

### Post by froy02 on 2008-02-27
You have to use gparted from live cd.  I think Gparted would not work on mounted drives.  When you boot from live CD gparted loads quicker because none of the drives are mounted yet.
There's no problem using ntfs for data inUbuntu but the Ubuntu OS has to be installed in ext2/ext3 partition.  Ubuntu 7.10 would read and write ntfs partitions without problems.
I use ntfs for all my other drives/partitions because I still have window$ and Ubuntu on one machine.  The wife does not want to learned Ubuntu.  I do not have any problem with ntfs partition.  Ubuntu's support for it has improved a lot.

---

