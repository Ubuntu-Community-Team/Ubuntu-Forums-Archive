---
title: "Transferring non-english filenames between ext3 and ntfs"
date: 2008-12-21
forum: Hardware
---

### Post by shadowskyx on 2008-12-21
Hi, 

I have some files which have Chinese filenames, when I try to transfer them to my external NTFS hard drive I get the message:

"Invalid or incomplete multibyte or wide character"

I suspect the problem is with the NTFS filesystem as I have no problems when transferring files to a usb FAT drive.

Is there some kind of settings for the language of the drive?

Thanks!

---

### Post by bdoe on 2008-12-21
I believe you need to specify UTF-8 character encoding when you mount the drive.

---

### Post by shadowskyx on 2008-12-21
Thanks I'll look that up and give it a try.  Does that mean I will need to mount it manually every time I plug in the external hard drive or is there a config file or something where I can tell ubuntu to do it automatically when it recognizes the drive?

---

### Post by bdoe on 2008-12-21
I honestly don't know how removable media is mounted by the system. You may need to add an entry to your fstab, but I don't know how well that will work with removable media. Hopefully someone else here can shed some light on that.

---

### Post by shadowskyx on 2008-12-24
I tried mounting the drive manually with iocharset=utf8 option and the problem is solved.
However, I would like ubuntu to mount with this option automatically.
Since it's a removable drive which isn't always plugged in, I shouldn't edit the fstab file for this?
I searched around and it seems like I might have to do something with udev...but it's a bit confusing.
Anyone have any idea what I need to do?

Thanks!

---

### Post by shadowskyx on 2008-12-24
After more searching, I found that this is problem with parsing mount options, Apparently this is a problem with kde/xfce, but not GNOME as it manages to do it successfully.

I found a workaround here:
[http://wiki.archlinux.org/index.php/HAL#Locale_issues]("http://wiki.archlinux.org/index.php/HAL#Locale_issues")

which replaces the ntfs-3g symlink with a shell script which calls the symlink but parsing the locale option explicitly.

Doesn't sound like the best solution...but it's working for now.

---

