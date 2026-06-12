---
title: "Installing &amp; using Berkeley DB 4.7 on Jaunty"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by andor2 on 2009-07-11
Hi everyone,

I am new to these forums and am excited to do my first post; hopefully this will help some one.

To install Berkeley DB 4.7 on 9.04 if you follow these steps, programs including Berkeley DB's API calls will compile without any errors.

1. download berkeley db from [http://www.oracle.com/technology/products/berkeley-db/index.html](http://www.oracle.com/technology/products/berkeley-db/index.html)
2. create a dir in your home and un-tar the downloaded file there
3. go to ./build_unix directory in the root directory of the berkeley db source you just un-tarred
4. run this command at your shell:
    ../dist/configure --bindir=/usr/local/bin --libdir=/usr/lib/ --includedir=/usr/include/ --enable-cxx
5. run 'make' at your command prompt
6. next run 'make install'; if you are not an admin, do 'sudo make install' instead

7. To compile your source code, let us say a small file like 'insert.cpp' that contains calls to Berkeley DB API, you need to do this: g++ insert.cpp -ldb_cxx-4.7
   
Thanks.

---

