---
title: "OCRAD installation error"
date: 2008-08-05
forum: General Help
---

### Post by dave_didlydodo on 2008-08-05
Hi, I'm still an Ubuntu newbie and I'm just starting to install new things. One of them is the OCRAD OCR package that works with the Kooka scan program (which can be installed with the Synaptic Package Manager).

The 'configure' part of the installation is fine, but when I come to

 make install

I get this:

if test ! -d /usr/local/share/info ; then install -d /usr/local/share/info ; fi 
install -p -m 644 ./doc/ocrad.info /usr/local/share/info/ocrad.info 
install-info /usr/local/share/info/ocrad.info /usr/local/share/info/dir 
install-info(/usr/local/share/info/ocrad.info): **too many arguments **

Can anyone help? Maybe I've unpacked the package in the wrong place - it's in 

/home/family/downloads  where 'family' is the account name.

---

### Post by cariboo on 2008-08-05
Are you running make install as root?

```
sudo make install
```

Jim

---

### Post by dave_didlydodo on 2008-08-05
Thanks, but I was running as root, having previously typed 'su'. But I've just tried again using sudo and it makes no difference - same error.

---

