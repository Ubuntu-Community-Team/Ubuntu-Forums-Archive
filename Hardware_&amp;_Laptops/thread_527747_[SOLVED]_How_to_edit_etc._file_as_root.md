---
title: "[SOLVED] How to edit etc. file as root"
date: 2007-08-17
forum: Hardware &amp; Laptops
---

### Post by outtopasture on 2007-08-17
To get my scanner working, I need to add lines to the etc./sane.d/epson.conf file

It fails and may be seeking root privileges but that is not certain.

How can I approach that file logged in as root, or need I do so?

---

### Post by heimo on 2007-08-17
> **outtopasture said:**
> To get my scanner working, I need to add lines to the etc./sane.d/epson.conf file

It fails and may be seeking root privileges but that is not certain.

How can I approach that file logged in as root, or need I do so?

alt+F2 and Run:
```
gksudo gedit /etc/sane.d/epson.conf 
```

---

### Post by outtopasture on 2007-08-17
Thanks. I just got back to Ubuntu after an unfortunate detour and should have known that.

---

### Post by outtopasture on 2007-08-17
Now I find that I can edit that file with root privileges but Xsane still can't recognize the drivers.

Also, when I used gksudo I got nothing but a blank window, but I saw the file with all its data when instead I used: sudo ... then gedit /etc/sane.d/epson.conf 

On another Linux distro a while back I used this procedure and got the scanner going, and as part of the fix I had installed some other xsane accessory, I am not sure which one. I see no such extra xsane files in the repositories here.

---

