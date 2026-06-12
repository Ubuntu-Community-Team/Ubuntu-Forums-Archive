---
title: "Hard Drive in Windows Ext4"
date: 2016-05-21
forum: Hardware
---

### Post by anon24 on 2016-05-21
I had chosen to do without Windows and boot Ubuntu with Legacy for a while. During that time, I formatted an internal TB drive to Ext4. Now, that I'm in Windows, I realize that I had forgotten to put the drive in NTFS. Windows does not recognize the drive. Is there a way to reformat the Ext4 drive in Windows to NTFS??? Or do I have to install Ubuntu in order to do that.

---

### Post by SuperFreak on 2016-05-21
You could try formatting from a live USB or DVD of Ubuntu without installing Ubuntu. Use GParted

---

### Post by SeijiSensei on 2016-05-21
The [ext2fsd](http://www.ext2fsd.com/) project offers a Windows driver that supports ext filesystems.

---

### Post by weatherman2 on 2016-05-22
> **SeijiSensei said:**
> The [ext2fsd]("http://www.ext2fsd.com/") project offers a Windows driver that supports ext filesystems.

I never got it to work with ext4 myself.

---

### Post by yancek on 2016-05-22
Windows will have computer management/disk management which you can use to reformat and overwrite everything on that disk if that's what you want.

---

### Post by SeijiSensei on 2016-05-24
> **weatherman2 said:**
> I never got it to work with ext4 myself.
I believe I got ext2fsd to work with ext4 on one system I tried.  One alternative is to use ext3 rather than ext4.

---

