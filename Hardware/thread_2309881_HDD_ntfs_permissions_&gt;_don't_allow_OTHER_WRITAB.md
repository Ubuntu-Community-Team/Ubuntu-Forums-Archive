---
title: "HDD ntfs permissions &gt; don't allow OTHER_WRITABLE"
date: 2016-01-14
forum: Hardware
---

### Post by johannes15 on 2016-01-14
Hi all,

When I look at file permissions on my automatically mounted 2 TB-HDD with ntfs-filesystem, it shows:
```

[SIZE=2][COLOR=#0000ff]myusername@ubuntu: ~$[/COLOR]  ls -lA /media
drwxrwxrwx    5    myusername     mygroup  8469675507712   Dec 30 21:30    extern
lrwxrwxrwx    1    myusername     mygroup              4   Dec 30 21:30    usb0 -> /media/extern[/SIZE]

```

I use usbmount to automatically mount the drive. I don't want "others" to have writing permission on this drive. Can I switch that off? I already edited the /etc/usbmount/usbmount.conf, where it says:
```

[SIZE=2]FS_MOUNTOPTIONS="-fstype=ntfs,uid=myusername,gid=mygroup[/SIZE]

```
What do I have to specify here? Or will this have no effect anyway, since ntfs is not fully supported by linux (with respect to file permissions)? Will I see "[SIZE=2]drwxrwxrwx" no matter what I do? 
Thanks in advance.
[/SIZE]

---

### Post by yancek on 2016-01-14
I misread your post but what you need here is to change the umask in the /etc/fstab entries.  You can find lots of examples using an online search if all you want is to deny write permissions to others.  Take a look at the link below.  About half way down the page it explains what the different numbers in the umask entry do so you can select which you actually want in your /etc/fstab entry.

[http://www.computerhope.com/unix/uumask.htm](http://www.computerhope.com/unix/uumask.htm)

---

### Post by johannes15 on 2016-01-15
Thank you for the reply. 
> **yancek said:**
> 
Take a look at the link below. 
[http://www.computerhope.com/unix/uumask.htm](http://www.computerhope.com/unix/uumask.htm)


As stated on the website, I added
```

[SIZE=2]FS_MOUNTOPTIONS="-fstype=ntfs,uid=myusername,gid=mygroup,**umask=0002**"[/SIZE]

```
to the usbmount.conf
That did it - Now it shows the correct permissions. :o

In my /etc/fstab is no entry that belongs to my HDD, I've never created one (always used usbmount.conf). Is this still necessary?

---

### Post by yancek on 2016-01-15
> In my /etc/fstab is no entry that belongs to my HDD, I've never created  one (always used usbmount.conf). Is this necessary though? 		

If it works the way you want then I don't suppose and fstab entry is necessary.  I've always used fstab and have no idea what usbmount.conf is.

---

