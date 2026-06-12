---
title: "[In windows] can't read files pulled in linux in my external hard drive"
date: 2018-04-19
forum: Hardware
---

### Post by dsupy on 2018-04-19
I pulled some files on Linux in my 2T external hard drive. Then I dual-boot to windows and opened the same file. However, it doesn't want me to and return error. Could you please help me to resolve it? My external hard drive is formatted by NTFS.

---

### Post by yancek on 2018-04-19
> I pulled some files on Linux in my 2T external hard drive

What do you mean by "pulled"?  Do you have both Ubuntu/Linux and some unknown version of windows installed on another drive?  Your external drive is formatted with the windows ntfs filesystem so is this a data/backup drive.  You need to explain what you did, what you mean by pulled.  Written to from Linux?  You indicate that you get an error when you try to open the file in windows but neglect to indicate what that error is??

---

### Post by Mark Phelps on 2018-04-19
Although Linux can read NTFS volumes, it's not a good choice for storing Linux files, as Windows does not understand Linux filesystem permissions.

Also, if you are running Win10 and you access this NTFS volume using it, when you then close Windows, this volume will remain MOUNTED, and that will prevent you from reading it in Linux.

---

