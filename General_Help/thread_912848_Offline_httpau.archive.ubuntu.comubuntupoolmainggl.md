---
title: "Offline: http://au.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/l"
date: 2008-09-07
forum: General Help
---

### Post by Panarchy on 2008-09-07
[http://au.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.16.4-0ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.16.4-0ubuntu2_i386.deb) 

Is offline

Just tried doing a sudo apt-get --fix-missing upgrade

And got these errors;

After this operation, 987kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main language-pack-en 1:8.04+20080708
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main language-pack-gnome-en 1:8.04+20080708
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main libglib2.0-0 2.16.4-0ubuntu2
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_8.04+20080708_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_8.04+20080708_all.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_8.04+20080708_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_8.04+20080708_all.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.16.4-0ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.16.4-0ubuntu2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]

Please bring the server back online or tell me a workaround!

Thanks in advance,

Panarchy

---

### Post by ichundu on 2008-09-07
hi panarchy, the server might be temporarily off (maybe because of site reconstruction). go to System => Administration => Software Sources. in the "Download from:" drop down list you should have selected "Server for Australia", right? Try to change the server, for example switch to "Main Server" or "Custom" until the Australian Server gets back to work.

ichundu

EDIT: ah, and after switching to another server close "software sources" and then a message should appear, click reload. then check for updates. let me now if this works, bye :)

---

### Post by ichundu on 2008-09-07
i just checked your server and that package isn't there anymore. there is a similar one "libglib2.0-0_2.16.4-0ubuntu3_i386.deb", (you can notice the difference, it has "...0ubuntu3..." and not "...0ubuntu2..." in the name), i'm not very competent on this thing so don't know whether to suggest you download that similar file manually or not.

try to run this on the terminal:
```
sudo apt-get update
```
hope this fixes it !

---

### Post by Panarchy on 2008-09-09
Thanks, perfect!

Just tried the above command followed by the command I originally had errors with. Took a long time, (the 2nd one) but finally finished, and worked (no errors).

Then I ran both again, first one still took a little bit of time, but second one said that there was nothing wrong!

WOOT

YAY

Thanks,

Panarchy

---

