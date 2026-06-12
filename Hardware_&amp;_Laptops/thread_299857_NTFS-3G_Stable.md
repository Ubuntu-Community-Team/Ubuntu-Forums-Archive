---
title: "NTFS-3G Stable?"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by FusionXN1 on 2006-11-14
Does anyone know if NTFS is stable using NTFS-3G for read AND write?

If it is / isn't, will i see a performance difference with FAT32 if I was to convert to it? I may want to come back to Windows so ext3 anit an option.

---

### Post by testube_babies on 2006-11-14
I haven't had any problems with ntfs-3g.  Even huge file transfers have worked flawlessly.  However, it is slightly slower than FAT32.  But the performance difference between the two filesystems isn't really that bad. 

There are tons of details about ntfs-3g here:
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by FusionXN1 on 2006-11-14
I was just thinking, Looking at this thread: [http://ubuntuforums.org/showthread.php?t=236274](http://ubuntuforums.org/showthread.php?t=236274)

It seems you can mount EXT2 (and 3 for that matter) into windows xp and vista perfectly no issues at all and access like a normal NTFS drive correct?

Would i better formatting and creating an ext3 space so both linux and windows can use it? If so, how do I create an EXT3 partition in windows?

As for NTFS-3G. So accessing and saving files via P2P program such as Azureus (bittorrent) and watching video files ona  day to day basis would be fine?

---

### Post by FusionXN1 on 2006-11-14
Looks like ill have to stick with windows doesn't it? :( Thanks anyway.

---

### Post by gh0st on 2006-12-11
> **FusionXN1 said:**
> I was just thinking, Looking at this thread: [http://ubuntuforums.org/showthread.php?t=236274](http://ubuntuforums.org/showthread.php?t=236274)

It seems you can mount EXT2 (and 3 for that matter) into windows xp and vista perfectly no issues at all and access like a normal NTFS drive correct?

Would i better formatting and creating an ext3 space so both linux and windows can use it? If so, how do I create an EXT3 partition in windows?

As for NTFS-3G. So accessing and saving files via P2P program such as Azureus (bittorrent) and watching video files ona  day to day basis would be fine?

In answer to your question, using NTFS-3G mounts with Azureus works fine for me. I have been using NTFS-3G for a few months now and never had a problem with it. I have heard people complain about it not being stable but I can only speak from personal expirience, it works great for me and I'm far from a Linux guru :-)

I also use it to mount an external NTFS hard disk in a USB caddy for backups, no problems there either. I have accessed my linux file systems from Windows but it wasn't that impressive or easy to be honest. I use Samba to access my ext3 drives from a VMWare Windows machine I use for .NET development. I have to support some .NET applications I wrote a while back.

Hope this info helps in some way :) If you need help setting up NTFS-3G let me know.

Dan

---

