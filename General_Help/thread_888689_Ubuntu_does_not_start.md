---
title: "Ubuntu does not start"
date: 2008-08-13
forum: General Help
---

### Post by hhkilis on 2008-08-13
Hello.

I've used Ubuntu 8.04 for 2 months and in this period I've no problem with it. But today, it does not start.

When I select Windows from the Grub menu, it starts; but Ubuntu doesn't.

The messages on the screen :

init: /etc/event.d/control-alt-delete: No such file or directory
init: /etc/event.d/logd: No such file or directory
init: /etc/event.d/rc-default: No such file or directory
init: /etc/event.d/rc0: No such file or directory
init: /etc/event.d/rc4: Value too large for defined data type

What's the problem. It doesn't continue to boot, only I see these messages.

I've a program that uses Mysql. It is written in Php. I use it and it contains important data for me. There is valuable data on a mysql database. This program uses that database.

Please help me.
If you can do this, please help me to boot Ubuntu. If you cannot, is there any way to recover my database?

Please, help.

---

### Post by hhkilis on 2008-08-14
Please

---

### Post by unutbu on 2008-08-14
[list=1]
[*] Boot from the LiveCD, open a terminal ([http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)) and type
```

sudo fdisk -l         # '-l' is a hyphen followed by lowercase L, not a one.

```
Please post the output.
[*] The output of the command above will look something like this:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8         660     5245222+   b  W95 FAT32
[COLOR="Red"]/dev/sda3   *         661       38536   304238970   83  Linux[/COLOR]
/dev/sda4           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

```
Each line represents a partition on your hard drive. 
Find the line (partition) that ends with the word "Linux". Find the device name in the first column. The device name is /dev/sda3 in the example above. 

Once you have the device name, type

```

sudo mount /dev/sda3 /mnt   # change /dev/sda3 to your Linux partition's device name

```
Your Linux partition's filesystem should now be accessible at /mnt
[/list]

---

### Post by unutbu on 2008-08-14
The above instructions will allow you to at least check that your data is still there.
MySQL data is usually located at /var/lib/mysql. 

The error message 
> 
init: /etc/event.d/control-alt-delete: No such file or directory

is perplexing. If init is running, then you've gotten past the GRUB stage of the boot process. The error message complains that the file /etc/event.d/control-alt-delete is missing. Usually the /etc/event.d directory should look like this:
```

% ls -l /etc/event.d
-rw-r--r-- 1 root root 260 2007-09-16 22:13 control-alt-delete
-rw-r--r-- 1 root root 299 2007-09-16 22:13 logd
-rw-r--r-- 1 root root 552 2007-09-16 22:13 rc0
-rw-r--r-- 1 root root 342 2007-09-16 22:13 rc1
-rw-r--r-- 1 root root 403 2007-09-16 22:13 rc2
-rw-r--r-- 1 root root 403 2007-09-16 22:13 rc3
-rw-r--r-- 1 root root 403 2007-09-16 22:13 rc4
-rw-r--r-- 1 root root 403 2007-09-16 22:13 rc5
-rw-r--r-- 1 root root 422 2007-09-16 22:13 rc6
-rw-r--r-- 1 root root 689 2008-07-04 11:54 rc-default
-rw-r--r-- 1 root root 392 2007-09-16 22:13 rcS
-rw-r--r-- 1 root root 461 2007-09-16 22:13 rcS-sulogin
-rw-r--r-- 1 root root 558 2007-09-16 22:13 sulogin
-rw-r--r-- 1 root root 302 2007-09-16 22:13 tty1
-rw-r--r-- 1 root root 300 2007-09-16 22:13 tty2
-rw-r--r-- 1 root root 300 2007-09-16 22:13 tty3
-rw-r--r-- 1 root root 300 2007-09-16 22:13 tty4
-rw-r--r-- 1 root root 300 2007-09-16 22:13 tty5
-rw-r--r-- 1 root root 300 2007-09-16 22:13 tty6

```
Once you mount your Linux partition at /mnt, perhaps you should issue the command
```

ls -l /mnt/etc/event.d   # don't forget the /mnt

```
or use Nautilus to check that the etc/event.d directory is in place.

---

