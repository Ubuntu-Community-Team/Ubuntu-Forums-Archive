---
title: "printer problems"
date: 2012-10-29
forum: Hardware
---

### Post by Vithant on 2012-10-29
Pretty new to Ubuntu. Downloaded Cups wrapper and driver for Brother HL-3040CN color networking printer attached by USB. Software installer installed it. ran following on terminal

jim@jim-SX2801:~$ sudo dpkg -i --force-all mfc495cwlpr-1.1.3-1.i386.deb
dpkg: error processing mfc495cwlpr-1.1.3-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc495cwlpr-1.1.3-1.i386.deb
jim@jim-SX2801:~$ 


what am I doing wrong.

Thanks

Jim Warren

---

### Post by pdc on 2012-10-31
that is a very nice printer you have got

Brother provide an installer script; that should do things for you

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr)

try it and let us know how things go

---

