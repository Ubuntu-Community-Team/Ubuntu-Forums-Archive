---
title: "Ubuntu PArtition Lost"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by ziaur25 on 2009-10-11
Hello, 
I have been in a Big Trouble.
I have been working Ubuntu Gusty Gibbon and
Windows XP OSs.
             I used Ext2IFS software to view Ext partition 
in Windows. Then Accidently I deleted that Linux
partition thro windows Disk Management Program.
          Then I recovered the Entire deleted partition
thro Partition Table Doctor(No data is lost).
But still i cannot able to use that ext partion 
as linux root. When I used Ubuntu live CD, fstab
command displays that ext partition. But does not 
takes as root partition. Even i am unable to access
thro' the 'su -' command, when I type the password
it displays 'Authentication Failure'.
       How can i restore my linux partion as /(root).
I need ur help....
my mail id [email]ziaur25@gmail.com[/email]

 Thanksss.

---

### Post by Intrepid Ibex on 2009-10-11
> fstab command displays that ext partition

you mean 'fdisk'? 

Also setting root password can be done by: ```
sudo passwd
```

You could also just use sudo or: ```
sudo -s
```

---

