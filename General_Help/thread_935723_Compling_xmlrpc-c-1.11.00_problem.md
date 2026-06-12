---
title: "Compling xmlrpc-c-1.11.00 problem"
date: 2008-10-02
forum: General Help
---

### Post by peppage on 2008-10-02
I can't seem to get this, I've been trying for the last hour to get this to compile and I seemed to have hit a brick wall.  I got it to compile most of the way and ./configure runs fine but it won't get past this part.  I've searched google for anything that could be related but my search has turned up nothing.  Any suggestions would be great, thanks.  It shouldn't be an issue but I'm running 8.04.

```
gcc -shared  resource.lo trace.lo xmlrpc_data.lo xmlrpc_datetime.lo xmlrpc_string.lo xmlrpc_array.lo xmlrpc_struct.lo xmlrpc_build.lo xmlrpc_decompose.lo xmlrpc_expat.lo xmlrpc_parse.lo xmlrpc_serialize.lo xmlrpc_base64.lo xmlrpc_utf8.lo xmlrpc_authcookie.lo  -L.libs -L/home/pepp/Desktop/xxx/xmlrpc-c-1.11.00/lib/libutil -lxmlrpc_util -L/home/pepp/Desktop/xxx/xmlrpc-c-1.11.00/lib/expat/xmlparse/.libs -lxmlrpc_xmlparse -lc  -Wl,-soname -Wl,libxmlrpc.so.3 -o .libs/libxmlrpc.so.3.11.0
/usr/bin/ld: cannot find -lxmlrpc_xmlparse
collect2: ld returned 1 exit status
make[1]: *** [libxmlrpc.la] Error 1

```

---

### Post by Shai Hulud on 2008-10-02
```
/usr/bin/ld: cannot find -lxmlrpc_xmlparse
collect2: ld returned 1 exit status
make[1]: *** [libxmlrpc.la] Error 1
```

Same here... :confused:

---

### Post by peppage on 2008-10-03
Well I've got this to compile on many other machines so I give up trying to install it on this one.  I never figured out what was the problem.  None of the other machines had any problems at all.

---

### Post by snowwolf725 on 2009-04-14
The solution is
```

apt-get remove libxmlrpc-c3

```

---

### Post by khellific on 2010-09-07
I encountered this problem today doing the same thing on 9.10. The solution is to install this package: libxmlrpc-core-c3-dev

---

