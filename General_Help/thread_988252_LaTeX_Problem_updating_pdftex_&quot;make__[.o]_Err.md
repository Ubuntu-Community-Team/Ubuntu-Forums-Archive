---
title: "LaTeX: Problem updating pdftex &quot;make: *** [.o] Error 1&quot;"
date: 2008-11-20
forum: General Help
---

### Post by TobyReynolds on 2008-11-20
I am using Ubuntu 8.04. I have been trying to manually update pdftex to the latest version because it has synctex inbuilt whereas the older version supplied via TeX Live in the repositories does not.
  I have downloaded and unzipped the appropriate package
pdftex-1.40.9.tar.bz2
from [http://www.tug.org/applications/pdftex/](http://www.tug.org/applications/pdftex/)
then opened a terminal, navigated to the resulting folder pdftex-1.40.9/ and typed ./build.sh as per instructions in the `INSTALL' file. The first run through gave me some error about needing Bison, so I installed that using Synaptic. The second attempt ran for much longer but finally finished with the following error messages:
```
.
.
.
config.status: creating c-auto.h
Makefile:161: warning: overriding commands for target `.o'
make: warning: ignoring old commands for target `.o'
gcc -DHAVE_CONFIG_H  -I. -I/home/toby/Desktop/pdftex-1.40.9/src/texk/web2c/web2c -I../.. -I/home/toby/Desktop/pdftex-1.40.9/src/texk/web2c/.. -I.. -I/home/toby/Desktop/pdftex-1.40.9/src/texk/web2c/web2c/..  -g -O2  -c /home/toby/Desktop/pdftex-1.40.9/src/texk/web2c/web2c/kps.c
Expect one shift/reduce conflict.
bison -y -d -v /home/toby/Desktop/pdftex-1.40.9/src/texk/web2c/web2c/web2c.y
/home/toby/Desktop/pdftex-1.40.9/src/texk/web2c/web2c/web2c.y:871.25-881.38: warning: unused value: $2
conflicts: 1 shift/reduce
test -f y.tab.c && mv -f y.tab.c y_tab.c
test -f y.tab.h && mv -f y.tab.h y_tab.h
gcc -DHAVE_CONFIG_H  -I. -I/home/toby/Desktop/pdftex-1.40.9/src/texk/web2c/web2c -I../.. -I/home/toby/Desktop/pdftex-1.40.9/src/texk/web2c/.. -I.. -I/home/toby/Desktop/pdftex-1.40.9/src/texk/web2c/web2c/..  -g -O2  -c /home/toby/Desktop/pdftex-1.40.9/src/texk/web2c/web2c/main.c
gcc -DHAVE_CONFIG_H  -I. -I/home/toby/Desktop/pdftex-1.40.9/src/texk/web2c/web2c -I../.. -I/home/toby/Desktop/pdftex-1.40.9/src/texk/web2c/.. -I.. -I/home/toby/Desktop/pdftex-1.40.9/src/texk/web2c/web2c/..  -g -O2  -c y_tab.c
: /home/toby/Desktop/pdftex-1.40.9/src/texk/web2c/web2c/web2c.l
gcc -DHAVE_CONFIG_H  -I. -I/home/toby/Desktop/pdftex-1.40.9/src/texk/web2c/web2c -I../.. -I/home/toby/Desktop/pdftex-1.40.9/src/texk/web2c/.. -I.. -I/home/toby/Desktop/pdftex-1.40.9/src/texk/web2c/web2c/..  -g -O2  -c .c
gcc: .c: No such file or directory
gcc: no input files
make: *** [.o] Error 1
[toby@toby-laptop pdftex-1.40.9]$
```
Can somebody suggest how to overcome this, or alternatively where I might find pre-compiled versions of the files I'm after (pdftex, pdfetex, pdftex.pool and pdfetex.pool).

Thanks
Toby

---

