---
title: "fd0"
date: 2004-12-08
forum: Hardware &amp; Laptops
---

### Post by art-777 on 2004-12-08
There's no fd0 in my /dev directory . I have a line: /dev/fd0 /media/floppy... in /etc/fstab . It was created by the installer of Ubuntu & it was working.  I've  upgraded Ubuntu some days ago and :confused: what a surprise, there's no /dev/fd0. I can't mount a floppy. What is wrong ? (Ubuntu 4.1 , kernel linux-k7 )

---

### Post by jeremy on 2004-12-09
I had the same. In my case there was a /.dev/fd0 , and I had to alter the fstab line to read;
/.dev/fd0 /media/floppy

(note the '.' before 'dev')

---

