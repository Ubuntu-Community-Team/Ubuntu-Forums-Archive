---
title: "Cannot remove package after manuall delete"
date: 2008-10-02
forum: General Help
---

### Post by tsmets on 2008-10-02
I manually removed Django 0.96 to upgrade to the new 1.0
 ```
rm -fR   /usr/lib/python2.5/site-packages/django 
```

Now when I want to do an update, I have the following error that bumps out :
```

E: /var/cache/apt/archives/python-django_0.96.1-2ubuntu2.1_all.deb: subprocess new pre-removal script returned error exit status 1

```


How do I force a removal ?
```

tsmets@ubuntu:~$ sudo dpkg  -i  python-django 
dpkg: error processing python-django (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 python-django
tsmets@ubuntu:~$ sudo dpkg -l | grep django
pFR python-django                              0.96.1-2ubuntu2                                            A high-level Python Web framework

```

Tx for your help :)

\T,

---

### Post by iponeverything on 2008-10-02
find python-django_0.96.1-2ubuntu2.1_all.deb, if that was what you rm'ed.

You might still have it in /var/cache/apt/archive if you don't use google

copy it to /tmp

extract it:

cd /tmp/
dpkg-deb --extract python-django_0.96.1-2ubuntu2.1_all.deb 

restore your directory:

cd /tmp/usr/lib/python2.5/site-packages/ 
mv django /usr/lib/python2.5/site-packages/ 

now remove it with "dpkg  -r  python-django"

that might fix things ups.. don't know as I have not tried it myself.

---

