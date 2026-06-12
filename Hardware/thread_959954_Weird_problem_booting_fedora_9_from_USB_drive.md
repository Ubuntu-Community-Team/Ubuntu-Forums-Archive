---
title: "Weird problem booting fedora 9 from USB drive"
date: 2008-10-26
forum: Hardware
---

### Post by moofang on 2008-10-26
Hi,

I have a peculiar problem. I have successfully installed KDE fedora 9 on a USB external hard drive, and set up grub so that I was able to boot into it. The hard drive presently contains two partitions, an ext partition for fedora, and an ntfs partition with some (non-os) data. The ntfs partition was the original partition that came with the drive.

Here's the problem. Whenever I successfully boot into fedora one time, the next time I try I fail - booting from USB wasn't even an option. When I boot into ubuntu (on my internal drive) and check it using gparted, everything looks fine except ubuntu refuses to read the ntfs partition - in the same way it would when windows had an unclean shutdown. So I tried booting into windows (also on internal drive) once, and did a proper shut down from there. This works : I am able to boot fedora one more time, but that's just it - only once, until I pop into windows and shut down again -_-

Any ideas?

---

### Post by moofang on 2008-10-27
bump

---

### Post by icanfly0307 on 2008-10-27
try deleting your ntfs partition on the external hdd. unless you have valuable info on it, you might as well format it and extend fedora onto it.

---

### Post by moofang on 2008-10-27
That's just the thing =( I have too much data in there (ntfs partition) and no intermediate medium to store it at the moment =x oh well, thx for the reply anw

---

