---
title: "crosstool ng installation in ubuntu9.04(jaunty)"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by guitsy on 2009-07-18
go to terminal
copy and paste the following in terminal

sudo apt-get install gawk
cd ~
wget [http://ymorin.is-a-geek.org/download/crosstool-ng/crosstool-ng-1.3.3.tar.bz2](http://ymorin.is-a-geek.org/download/crosstool-ng/crosstool-ng-1.3.3.tar.bz2)
tar -xjvf crosstool-ng-1.3.3.tar.bz2
cd crosstool-ng-1.3.3
./configure --prefix=$HOME/ctng
make
make install
export PATH=$PATH:$HOME/ctng/bin
cd ~
mkdir toolchain-build
cd toolchain-build
cp ../ctng/lib/ct-ng-1.3.3/samples/arm-unknown-linux-uclibcgnueabi/* .
mv crosstool.config .config
ct-ng menuconfig

#select path and misc options........go to  Prefix directory .....select..... change the path to.... ${HOME}/opt/ctng.....exit...go back to c compiler......uncheck c++....exit......go to tools facility.....uncheck sstrip.....exit.....exit.....choose yes.......


now on terminal..........copy & paste

ct-ng build.4
 

hope this will help without any errors..........thnks.....

---

