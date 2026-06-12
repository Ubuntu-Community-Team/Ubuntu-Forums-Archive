---
title: "Ext2 IFS for Windows"
date: 2006-02-28
forum: Hardware &amp; Laptops
---

### Post by Rizado on 2006-02-28
Again I need to ask something and I have absolutely no idea where to ask it, so I'm gonna use hardware.

[http://www.fs-driver.org](http://www.fs-driver.org)

Have anyone tried it? For those of you who haven't heard of it it's a windows ext2 driver (or something) with read and write support. Now if it works good I'm thinking of formating all my storage partitions as ext3 and still be able to use them in windows.
Is it possible not to "mount" a partition in windows? (Don't wanna let it ruin my kubuntu partition ;) )

---

### Post by Plexxxy on 2006-02-28
I use it. It works great and allows me to still use the drive in windows no prob. A very handy solution. But you need to be aware that it doesn't maintain access rights (will read regardless of file permissions and write with all permissions -- rwxrwxrwx). Also, and this is very important to know, using hibernation in windows could result in data loss/corruption on the ext volume. I ran into this problem myself and was none too happy about it.

I don't mean to scare you off, but definitely read through the troubleshooting and faq sections on the site before you commit to going 100% ext3 in windows.

---

### Post by Rizado on 2006-03-01
[QUOTE=Plexxxy]Also, and this is very important to know, using hibernation in windows could result in data loss/corruption on the ext volume. I ran into this problem myself and was none too happy about it.[/QUOTE]Hibernation is not a problem, or actually it is. Windows crashes when using it.

But is it possible to make windows not load my kubuntu partition, because don't want that to be completely open to windows.

---

### Post by Plexxxy on 2006-03-01
> But is it possible to make windows not load my kubuntu partition, because don't want that to be completely open to windows.
During installation of the driver, you'll be given the chance to assign drive letters to particular ext volumes. The driver also includes a control panel applet that allows for this after installation. Simply don't assign a letter to your Kubuntu drive and it won't be visible within Windows :)

---

### Post by Rizado on 2006-03-01
I just tried it and it seem to work great. It's time to format my partitions.

---

### Post by fangorious on 2006-03-01
works great for me. I haven't had any data corruption from hibernating under windows.

---

### Post by zapcojake on 2006-03-02
There is a program called paragon harddisk manager that lest you access, read and write ext partitions on a case by case basis. Not handy for quick access but I found usefull while making the switch to Linux.

---

