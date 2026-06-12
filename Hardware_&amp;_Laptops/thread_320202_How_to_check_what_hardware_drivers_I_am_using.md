---
title: "How to check what hardware drivers I am using?"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by Burgresso on 2006-12-16
Is there a way to check what hardware I have - or more importantly, what drivers Ubuntu is using - for my installation or CPU? I'm curious how to figure out how to check this info in case I wish to change or tweak my distro or kernel in the future.

thanks,

burgresso

---

### Post by invalid on 2006-12-16
The following commands may be helpful for this
```
lshw
lsmod
```
along with some others for other information```
lspci
lsusb
```
See the man pages for info on each of them.

---

### Post by az on 2006-12-16
To see what kernel you are running type

uname -a

---

### Post by Burgresso on 2006-12-20
thanks azz and invalid. perfect!

---

