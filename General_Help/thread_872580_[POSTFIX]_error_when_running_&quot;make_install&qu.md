---
title: "[POSTFIX] error when running &quot;make install&quot;"
date: 2008-07-28
forum: General Help
---

### Post by sanocli on 2008-07-28
Hello guys,

I have a problem with postfix. I have installed mysql client 5.0 on my ubuntu and downloaded postfix with the patch per_user_uce. Then I executed the command ```
make -f Makefile.init makefiles 'CCARGS=-DHAS_MYSQL -I/usr/include/mysql' 'AUXLIBS=-L/usr/lib/mysql -lmysqlclient -lz -lm'
```
 after that I compiled postfix doing "make". Until here no problem, everything goes well. So , finally, I do "make install". Postfix began to ask me some questions and when it asks me the question :
```
Please specify the destination directory for installed Postfix configuration files
``` I entered the path of a directory I created to save the configuration files and error messages appears : 
```
bin/postconf: error while loading shared libraries: libmysqlclient.so.16: cannot open shared object file: No such file or directory 
```
I don't know how to solve this issue. So please can someone help me.

Thank very much and have a good day ;)

---

### Post by Nikitas350 on 2008-07-28
Type in the terminal sudo apt-get install postfix

---

