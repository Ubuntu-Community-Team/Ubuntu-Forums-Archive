---
title: "Problem Installing Mbox2Mysql"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by mrmaster on 2009-07-06
Hello,

I'm using Ubuntu 9.04 and I have mysql installed already. I'm trying to compile mbox2mysql.

Every time I try to make the file I get the error stated below.

~/Desktop/mbox2mysql-0.3$ sudo make
gcc -g -Wall -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/gmime-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -c mysql.c
In file included from mysql.c:31:
db.h:23:25: error: mysql/mysql.h: No such file or directory
db.h:24:26: error: mysql/errmsg.h: No such file or directory
make: *** [mysql.o] Error 1

I checked the installation folder(mbox2mysql-0.3) and mysql.h and errmsg.h are in it. I'm not sure why it's not proceeding with the make. How may I fix this?


This is what I get when I try to run ./configure
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for mysql_init in -lmysqlclient... no
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for memory.h... (cached) yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for ANSI C header files... (cached) yes
checking for stdlib.h... (cached) yes
checking for working malloc... yes
checking for working memcmp... yes
checking for gettimeofday... yes
checking for memset... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for strcspn... yes
checking for strdup... yes
checking for strpbrk... yes
checking for strrchr... yes
checking for strspn... yes
checking for strstr... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating utils/Makefile
config.status: creating config.h
config.status: config.h is unchanged


Thank you

---

### Post by Partyboi2 on 2009-07-10
Hi, try installing libmysqlclient16-dev or libmysqlclient15-dev packages then running ./configure and make again.
[B]
[/B]

---

### Post by mrmaster on 2009-07-11
> **Partyboi2 said:**
> Hi, try installing libmysqlclient16-dev or libmysqlclient15-dev packages then running ./configure and make again.
[B]
[/B]

Hi,

I installed libmysqlclient15-dev and it fixed that problem but now it is giving me this one after i do sudo make install. 

install -m 755 --strip mbox2mysql /usr/local/bin
install -m 755 doc/mbox2mysql.1 /usr/local/man/man1

Is this a permission problem?

---

### Post by Partyboi2 on 2009-07-11
Is that the whole output to "sudo make install"?

---

### Post by mrmaster on 2009-07-12
> **Partyboi2 said:**
> Is that the whole output to "sudo make install"?

Hi,

Yes it is the whole output:


mrmaster@mrmaster-laptop:~/Desktop/mbox2mysql-0.3$ sudo make
gcc -g -Wall -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/gmime-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     mysql.o mbox.o db.o -lmysqlclient -lglib-2.0   -lgmime-2.0 -lz -lnsl -lgobject-2.0 -lglib-2.0    -o mbox2mysql

mrmaster@mrmaster-laptop:~/Desktop/mbox2mysql-0.3$ sudo make install
install -m 755 --strip mbox2mysql /usr/local/bin
install -m 755 doc/mbox2mysql.1 /usr/local/man/man1

---

### Post by Partyboi2 on 2009-07-12
According to that, it should now be installed. In the terminal type
```
mbox2mysql
```

---

### Post by mrmaster on 2009-07-12
> **Partyboi2 said:**
> According to that, it should now be installed. In the terminal type
```
mbox2mysql
```

That did work, thank you.

But what are the 2 lines for? And how was I able to finish without completing sudo make install?

install -m 755 --strip mbox2mysql /usr/local/bin
install -m 755 doc/mbox2mysql.1 /usr/local/man/man1

---

### Post by Partyboi2 on 2009-07-13
From what it looks like, those two lines are setting the attributes for Mbox2Mysql.
```
man install
```

>  And how was I able to finish without completing sudo make install?
According to your previous post you did run 'sudo make install' ;)

---

### Post by mrmaster on 2009-07-13
Thank you so much for helping me out. I guess i was just missing the libmysqlclientdev libraries.

---

