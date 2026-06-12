---
title: "GLIB missing problem"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by shariefbe on 2009-02-20
Hello,
    when i try to install xmms player in my system i found the below errors...i dont know what id this....can anyone help me...


[B]checking pthread.h presence... yes
checking for pthread.h... yes
checking for glib-config... no
checking for GLIB - version >= 1.2.2... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***
[root@localhost xmms-1.2.11]# [/B]

---

### Post by Partyboi2 on 2009-02-20
You can install xxms2 from the ubunu repos. If you need to compile it then you need to install  libglib1.2-dev
```
sudo apt-get install  libglib1.2-dev
```

---

### Post by shariefbe on 2009-02-21
hi,
   I am getting the below error..i dont know why..please help me

[root@localhost xmms-1.2.11]# sudo apt-get install libglib1.2-dev
sudo: apt-get: command not found
[root@localhost xmms-1.2.11]#

---

### Post by Partyboi2 on 2009-02-21
What is the output to
```
dpkg -l apt
```

---

### Post by shariefbe on 2009-02-22
This is the output

[root@localhost 2.6.26]# dpkg -l apt
bash: dpkg: command not found
[root@localhost 2.6.26]#

---

### Post by Partyboi2 on 2009-02-22
Maybe the path has been changed. What is the output to
```
echo $PATH
```

---

### Post by shariefbe on 2009-02-22
This is output of that command

[B][root@localhost 2.6.26]# echo $PATH
/usr/lib/qt-3.3/bin:/usr/kerberos/sbin:/usr/kerberos/bin:/usr/lib/ccache:/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/usr/X11R6/bin:/root/bin
[root@localhost 2.6.26]# [/B]

---

### Post by snova on 2009-02-22
> **shariefbe said:**
> This is output of that command

[B][root@localhost 2.6.26]# echo $PATH
/usr/lib/qt-3.3/bin:/usr/kerberos/sbin:/usr/kerberos/bin:/usr/lib/ccache:/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/usr/X11R6/bin:/root/bin
[root@localhost 2.6.26]# [/B]

```
whereis dpkg
whereis apt-get
```

This is not looking good so far...

---

### Post by shariefbe on 2009-02-23
yes apt-get is not working..i am newbie...what to do for that?

---

