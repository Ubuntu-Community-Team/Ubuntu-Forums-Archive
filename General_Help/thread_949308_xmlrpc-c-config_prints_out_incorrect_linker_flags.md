---
title: "xmlrpc-c-config prints out incorrect linker flags?"
date: 2008-10-16
forum: General Help
---

### Post by mirrorbox on 2008-10-16
Hello General, sorry to bother you, I hope you can help to solve my problem.

Looks like xmlrpc-c-config scripts returns incorrect linker flags.

I create a simple C++ source file **foo.cc**:

```
int main(int argc, char **argv) { return 0; }
```

I want to compile it and link to xmlrpc-c. I have libxmlrpc-c3-dev package installed using apt-get, so I execute the following command and get an error:

```
(10:40) novel@hybrid:~/tmp/xmlrpc %> g++ `xmlrpc-c-config c++2 client --libs --cflags --ldadd` foo.cc          
/usr/bin/ld: cannot find -lcurl
collect2: ld returned 1 exit status
(10:40) novel@hybrid:~/tmp/xmlrpc %> 
```

Am I doing something wrong or is it a problem with xmlrpc-c package?

---

