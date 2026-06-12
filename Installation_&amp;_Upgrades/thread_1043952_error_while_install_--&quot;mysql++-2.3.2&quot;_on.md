---
title: "error while install --&quot;mysql++-2.3.2&quot; on  server 8.10"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by Eswarjava on 2009-01-19
Hi All,

I need mysql++-2.3.2 library file to run my MultiXTpmApplicationServer. it support only this version of mysql.

while installing i am getting error any one help me to come out this issuse.

_**This is the error i am getting**_


root@verity:/home/mysql/mysql++-2.3.2# make
/home/mysql/mysql++-2.3.2/bk-deps g++ -c -o mysqlpp_coldata.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/coldata.cpp
In file included from ./lib/coldata.h:37,
                 from ./lib/coldata.cpp:27:
./lib/const_string.h: In constructor âmysqlpp::const_string::const_string(const std::string&)â:
./lib/const_string.h:91: error: âmemcpyâ was not declared in this scope
./lib/const_string.h: In constructor âmysqlpp::const_string::const_string(const char*)â:
./lib/const_string.h:98: error: âstrlenâ was not declared in this scope
./lib/const_string.h:101: error: âmemcpyâ was not declared in this scope
./lib/const_string.h: In constructor âmysqlpp::const_string::const_string(const char*, unsigned int)â:
./lib/const_string.h:111: error: âmemcpyâ was not declared in this scope
./lib/const_string.h: In member function âmysqlpp::const_string& mysqlpp::const_string::operator=(const char*)â:
./lib/const_string.h:125: error: âstrlenâ was not declared in this scope
./lib/const_string.h:127: error: âmemcpyâ was not declared in this scope
./lib/const_string.h: In member function âmysqlpp::const_string& mysqlpp::const_string::operator=(const mysqlpp::const_string&)â:
./lib/const_string.h:137: error: âmemcpyâ was not declared in this scope
make: *** [mysqlpp_coldata.o] Error 1



Thanks & Regards,
Eswar.G

---

### Post by Fertech on 2009-01-19
reboot your machine and click on system> administration>
 synaptic package manager enter root password, and in the search box
type mysql. from this point just click to install

---

### Post by Eswarjava on 2009-01-20
> **Fertech said:**
> reboot your machine and click on system> administration>
 synaptic package manager enter root password, and in the search box
type mysql. from this point just click to install


Hi Fertech,

I am using server edition so it has only terminal
could you please suggest, how i can proceed steps in terminal(command prompt).

Thanks & Regards,
Eswar.G

---

### Post by Fertech on 2009-01-21
what version of ubuntu do you have?
here is a link that might help to install software.
[LIST]
[https://help.ubuntu.com/8.10/add-applications/C/index.html](https://help.ubuntu.com/8.10/add-applications/C/index.html)
[/LIST]
[LIST]
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
[/LIST]

---

