---
title: "Problems with permissions on ntfs drives"
date: 2005-12-26
forum: Hardware &amp; Laptops
---

### Post by Bloody_Mary on 2005-12-26
I'm having problems with write protection on the  ntfs partitions on my
drives. They are mounted like this:

/dev/hda1       /media/dataPata     ntfs    nls=utf8,umask=000        0
0

What is missing? I thought "unmask=000" gave both read och write
permission.

---

### Post by Sutekh on 2005-12-26
[QUOTE=Gentoo-Wiki]
 umask: octal file permissions

You can change permissions using the parameter umask. But be aware that it must be the bitmask of permissions that are not present for the mountpoint. It is an octal number, formed like this:

    * character '0': Indicates that this is an octal number, not decimal.
    * first digit: owner user permissions
    * second digit: owner group permissions
    * third digit: world permissions (every other user on the system) 

The modes are as follows (the first column is the mode octal number):

M | R W X
-------------
0 | * * *
1 | * * - 
2 | * - * 
3 | * - -
4 | - * *
5 | - * -
6 | - - *
7 | - - -

For example, if you want that everybody be able to read, write, and execute every file in your /mnt/c, you should specify the mask 0000: [/QUOTE]

Try an extra 0
```
/dev/hda1 /media/dataPata ntfs nls=utf8,umask=000**0** 0
0
```

---

### Post by Bloody_Mary on 2005-12-26
I am sorry to say that it's not working. I'm trying:

/dev/hda1       /media/dataPata     ntfs    nls=utf8,umask=0000        0       0

And this: 

/dev/sda6       /media/dataSata     ntfs    nls=utf8,user,owner,ro,umask=0000        0       0

Don't exactly know what "user,owner,ro" does but I know I seen it somewhere and it worked for him. But nothing of this seems to solve my problem. I have both written mount -a as rootuser after written this and restarted the computer. Is there somebody who has another solution?

And I wanna say thank you Sutekh for your time and advice! Now I understand more of the text in that file thanks to you. :-D

---

### Post by kaamos on 2005-12-26
Err.. if the drives are ntfs, you can't write to them under linux. MS has never published the specs how ntfs works, and although there are some projects where the ntfs driver has been (somewhat) reverse-engineered it REALLY is not safe to write to ntfs drives with them.

---

### Post by Sutekh on 2005-12-26
[QUOTE=kaamos]Err.. if the drives are ntfs, you can't write to them under linux. MS has never published the specs how ntfs works, and although there are some projects where the ntfs driver has been (somewhat) reverse-engineered it REALLY is not safe to write to ntfs drives with them.[/QUOTE]
Very true, you don't want to try to write to the NTFS partition.  But would that cause a problem in mounting it?

Try a umask of 0222, that allows reading and executing for everyone, but no writing.

---

