---
title: "data recovery HELP !!"
date: 2010-05-02
forum: Hardware
---

### Post by CheAmr on 2010-05-02
Hello , 
I was trying to get the grub to run ubuntu after upgrading it through update manager
and then after restarts it formatted the C partition ( I didnt choose to format it for any reason ) which contained my windows XP 

it contained LOTS of important stuff to me and I really need them back

any suggestions ? please

---

### Post by P4man on 2010-05-02
Run testdisk from a livecd. You can install testdisk while you are in a livesession (booted from the regular ubuntu cd) and then follow this howto:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Alternatively you can download ubuntu rescue remix:
[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

whatever you do, not not install anything on the harddrive, do not use an OS that might be installed on the harddisk and go buy an external drive to put your recovered files on (and use it later to make backups!).

If you only formatted the partition, you should be able to recover most things, if you overwrote it, then dont have high hopes.

BTW, ubuntu will not format anything unless you ask it to. If tell the installer to use the entire disk, it will, but not by its own accord.

---

### Post by ronnielsen1 on 2010-05-02
Are you sure you formatted it? Just because it doesn't show up in grub doesn't mean it formatted it. Look for it from a live cd

---

### Post by sakisds on 2010-05-02
Grab a parted magic live cd from ANOTHER computer and run it on yours. Check for the partition using gparted and if its not there, testdisk can probably recover it if you didn't write anything else on the disk. It saved me once.

---

### Post by P4man on 2010-05-02
> **ronnielsen1 said:**
> Are you sure you formatted it? Just because it doesn't show up in grub doesn't mean it formatted it. Look for it from a live cd

+1
You're right, there is a good chance the OP *thinks* his partition is gone because Windows doesnt show up in grub. I think we need a bit more information at this point

---

### Post by CheAmr on 2010-05-02
> **P4man said:**
> +1
You're right, there is a good chance the OP *thinks* his partition is gone because Windows doesnt show up in grub. I think we need a bit more information at this point

now I took my hard drive and plugged it to another pc  then i used " recover my files " from windows and it recovered the whole partition ( it was formatted but RAW ) 
now I'm copying the VIP stuff on it to a flash memory and I hope it works fine with me 

Thank you i think its solved :)

---

