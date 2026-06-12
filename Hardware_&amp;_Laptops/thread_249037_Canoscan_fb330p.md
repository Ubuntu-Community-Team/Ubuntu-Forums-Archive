---
title: "Canoscan fb330p"
date: 2006-09-02
forum: Hardware &amp; Laptops
---

### Post by CameronCalver on 2006-09-02
Hello i have a canoscan fb330p and sane supports this scanner but when i run sane i cant scan and i really need this to work can someone plz give me a how to thankx in advance

---

### Post by zxee on 2006-09-02
Perthaps it works with sudo?
What does > sane-find-scanner return?
Sometimes you need to create a link to the actual device file.

---

### Post by CameronCalver on 2006-09-02
ok that command gives
command not found

---

### Post by zxee on 2006-09-04
> **CameronCalver said:**
> ok that command gives
command not found


Try > sudo sane-find-scanner

---

### Post by CameronCalver on 2006-09-06
its reports
```
sudo: sane-find-scanner  command not found
```

---

### Post by vthirukumaran on 2006-09-09
help needed plzzzzzzz:confused: :confused:

---

### Post by CameronCalver on 2006-09-09
yes so do i do you get the same command not found error

---

### Post by tobirius on 2006-09-20
To use the "sane-find-scanner" command you have to install the sane-utils package. But you won't realy need to use that anyway, you have to edit /etc/sane.d/dll.conf to uncomment canon_pp. Once you have done that, run "sudo xsane" and your scanner should be found. If not, turn the power of your scanner off and on, wait ten seconds and retry "sudo xsane".
As you have a parallel-port scanner, it will only work, if you are superuser or root.

Good luck.

---

### Post by CameronCalver on 2006-09-22
i did what u said it still says no devices avaliable do i need a special package

---

