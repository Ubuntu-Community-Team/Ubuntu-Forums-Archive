---
title: "epson sx100 with scanner-need scanner drivers"
date: 2009-05-01
forum: Hardware
---

### Post by Paulo Carvalho on 2009-05-01
hello there. I am a absolute beginner in any lixux os , after downloading ubuntu 9.04 and tried it , i switched form xp without any doubt.
my only problem so far is my sx100 epson printer.
i have downloaded drivers and installed them with success but my scanner does not work.
nedd help to sort that issue.

---

### Post by Mortesins93 on 2011-07-23
I know it's been a while, but if you install ubuntu 10.10 it works out of the box, and if you install the 10.04 LTS version it works if you update all the packages (probably only some of them but I don't know which). After that I had to run this command for the scanner:
```
sudo apt-get install sane sane-utils xsane
```

---

