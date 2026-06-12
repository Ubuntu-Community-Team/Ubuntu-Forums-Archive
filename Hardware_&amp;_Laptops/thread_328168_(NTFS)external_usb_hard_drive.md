---
title: "(NTFS)external usb hard drive"
date: 2006-12-30
forum: Hardware &amp; Laptops
---

### Post by xGutsAndGloryx on 2006-12-30
i am having problems getting my NTFS formatted USB Hard Drive to work in Ubuntu.. what file should i need to download & what command should i ran to get it to work?

---

### Post by taurus on 2006-12-30
What happens if you run these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda1 /media/windows -o nls=utf8,umask=0222
df -h
```

---

### Post by mac.ryan on 2007-01-04
Although I am not the one who made the question, this is also my problem.

Following what above has the only effect of changing the ownership of the drive from my user to the user root.

Steps I already did so far:

I installed the ntfs-3g package, and it works smoothly with IDE HDD. When it comes to the USB external drive, I have read-only access and if I try to change it the system tells me that it's impossible because "it's a read-only disk".

I believe the problem could be in relation with what givrè wrote here:  [http://ubuntuforums.org/showthread.php?p=1601663](http://ubuntuforums.org/showthread.php?p=1601663) but the version I have of pmount is newer than the patched one, so the system doesn't download and install it...

[COLOR="Red"]**EDIT 23:05 CET**[/COLOR] - The pmount from givré has been updated on the repository, now that I installed it, everything works smoothly!

Many thanks in advance,
Mac.

---

