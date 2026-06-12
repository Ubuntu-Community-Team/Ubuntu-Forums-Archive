---
title: "USB card reader with Xubuntu"
date: 2006-09-09
forum: Hardware &amp; Laptops
---

### Post by jaywatkins on 2006-09-09
Hello,

I have Xubuntu running on a Dell Optiplex GX-240 (P4 1.6GHz, 256MB, 40GB HDD, DVD-ROM).  I also have an original SanDisk "Cruzer" sd card reader that I would like to use with Xubuntu.

I created a directory in /usr called "SD32".

then, I ran "mount /media/sda /usr/SD32" from the terminal.

After a few minutes, the prompt returned, but I am unable to add/remove files from the sd card.

I tried to change permissions with "chmod 755 /usr/SD32", but still no change.

What am I doing wrong?  Xubuntu does not automount devices like Ubuntu.

Thanks

---

### Post by meng on 2006-09-09
/media/sda is already a mountpoint. I imagine a device such as /dev/sda is mounted to it. Can you not already browse and read/write to /media/sda?

---

### Post by jaywatkins on 2006-09-09
No, I can't.  I did the same with a Cruzer1GB USB HDD, and had no problems.  How does mountpoint make the association?

thanx

---

