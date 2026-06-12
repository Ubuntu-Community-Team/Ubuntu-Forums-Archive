---
title: "installing simpleutils-990811 in ubuntu"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by kukuken on 2009-04-03
I am a newbie to ubuntu and to ubuntuforums.com
I am trying to install simplescalar simulator
Hence, while installing simpleutils-990811, i am encountering the following error messages

make[3]: Entering directory `/home/sjaya/simplescalar/simpleutils-990811/binutils'
/bin/sh ./../ylwrap "bison -y" arparse.y y.tab.c arparse.c y.tab.h arparse.h --  -d
*** %n in writable segment detected ***
bison: subsidiary program `m4' failed
make[3]: *** [arparse.c] Error 1
make[3]: Leaving directory `/home/sjaya/simplescalar/simpleutils-990811/binutils'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/sjaya/simplescalar/simpleutils-990811/binutils'
make[1]: *** [all-recursive-am] Error 2
make[1]: Leaving directory `/home/sjaya/simplescalar/simpleutils-990811/binutils'
make: *** [all-binutils] Error 2
sjaya@sjayanirmala-desktop:~/simplescalar/simpleutils-990811$ 


I've already installed bison, m4 and flex. I am following the simplescalar installation instructions by Prof.Narahari at 
[http://www.seas.gwu.edu/~bhagiweb/cs211/SimpleScalar/simplescalar-ubuntu-install.txt](http://www.seas.gwu.edu/~bhagiweb/cs211/SimpleScalar/simplescalar-ubuntu-install.txt)

Need ur help!

---

