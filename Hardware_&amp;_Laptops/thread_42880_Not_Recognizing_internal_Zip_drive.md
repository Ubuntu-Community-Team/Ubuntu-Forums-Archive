---
title: "Not Recognizing internal Zip drive"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by muzzmastah on 2005-06-19
I recently installed Ubuntu 5.04 on my computer, and I've  been having a few hardware recognition problems. A memory stick wasn't recognized, but here's the wierd one. It's not recognizing my internal Zip drive - it shows up on the device manager, but I can't access it. Here's a picture of what it says in the device manager:

[img]http://img22.echo.cx/img22/7274/screenshot1tp.png[/img]

Also, if you guys have any tips about the memory stick, go ahead and tell.

Thanks for your help!

---

### Post by virgule on 2005-06-20
Read this thread: [http://ubuntuforums.org/showthread.php?t=29441](http://ubuntuforums.org/showthread.php?t=29441) 

Q: What have you tried so far to access the ZIP?

I could use a little more details. The first thing that comes in mind is that your ZIP is not registered in fstab. Please, show me the content of /etc/fstab
```

cat /etc/fstab

```
If it is, indeed, registered, you should see a line that start with /dev/hdd... 
If its not, do these:
```

sudo mkdir /mnt/zip
sudo nano /etc/fstab
# Insert this line in the file:
/dev/hdd        /mnt/zip   auto    rw,users,noauto 0       0

```
Changes will take effect instantly. Try to access it again.

---

