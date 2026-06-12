---
title: "trying to get Epson TM-T88IV Thermal Receipt printer working with Ubuntu 14.04 LTS"
date: 2014-10-14
forum: Hardware
---

### Post by ZippyDan on 2014-10-14
Running a CUPS server.

I downloaded the latest drivers off Epson's website.  Epson only officially supports 12.04 so I'm trying something outside the documentation.

It has an install script ```
install.sh
```, but when I run it I get the following error: ```
 ./tmx-cups/install.sh: 393: ./tmx-cups/install.sh: Bad substitution
```

Any ideas?

---

### Post by ZippyDan on 2014-10-16
hi

---

### Post by howefield on 2014-10-16
Just on the off chance, try the solution in this thread ?

[http://ubuntuforums.org/showthread.php?t=1474591](http://ubuntuforums.org/showthread.php?t=1474591)

---

### Post by ZippyDan on 2014-10-16
My script already starts with !#/bin/bash :(

Here is line 393

```
392:  if [ "xUbuntu" = x$os ]; then
393:                if [ "12." = "${ver:0:3}" ]; then
394:                        ver=${ver:0:5}
```

I tried changing the 12. to 14. but I got the same error

---

