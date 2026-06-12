---
title: "grub error 17 on new disk"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by Hansmc on 2009-10-10
I moved my disk portions to a new hard drive with gpart. But when I try to boot from the new disk I get:

```
Grub Loading stage1.5

Grub loading, please wait.
Error 17
```

I also resized the partitions when I moved them. Here is some code that might help.


```
xx-desktop:~$ sudo blkid
/dev/sda1: UUID="6aa10033-db31-4e37-82fd-07d094d281a5" TYPE="ext4" 
/dev/sda5: TYPE="swap" UUID="6a8388fd-c03d-4ace-9022-ea82fa774cc8" 
/dev/sda6: UUID="30ebb285-38a4-4604-a1da-6f9a1b6da6a3" TYPE="ext4" 
/dev/sdb1: UUID="6aa10033-db31-4e37-82fd-07d094d281a5" TYPE="ext4" 
/dev/sdb5: UUID="30ebb285-38a4-4604-a1da-6f9a1b6da6a3" TYPE="ext4" 
/dev/sdb6: UUID="6a8388fd-c03d-4ace-9022-ea82fa774cc8" TYPE="swap" 
```


 Thanks for your help.

---

### Post by Hansmc on 2009-10-10
fixed see:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub+live+ubuntu+cd](http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub+live+ubuntu+cd)

---

