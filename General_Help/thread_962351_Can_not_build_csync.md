---
title: "Can not build csync"
date: 2008-10-29
forum: General Help
---

### Post by Tobbera on 2008-10-29
I can not manage to build csync [http://www.csync.org/]("http://www.csync.org/") on my ubuntu box. 

I've apt-get smb and all thats needed. From the install-instructions:

```
In order to build csync, you need to install several components:

- A C++ compiler
- [CMake](http://www.cmake.org/) >= 2.4.4.
- [check](http://check.sourceforge.net) >= 0.9.5
- [log4c](http://log4c.sourceforge.net) >= 1.2
- [sqlite3](http://log4c.sourceforge.net) >= 3.4

- [libsmbclient](http://www.samba.org)

log4c and sqlite3 are runtime requirements too. libsmbclient is needed for
the smb plugin.
```


I get the following:
```
root@ubuntu:~/csync-0.41.95/build# cmake -DCMAKE_BUILD_TYPE=Debug ..
-- Found LOG4C: /usr/local/lib/liblog4c.so
-- Found Check: /usr/lib/libcheck.a
-- Found Iniparser: /usr/lib/libiniparser.a
-- Found Dlfcn: /usr/lib/libdl.so
-- Found RT: /usr/lib/librt.so
CMake Error: Could not find Libsmbclient
CMake Error: This project requires some variables to be set,
and cmake can not find them.
Please set the following variables:
INIPARSER_INCLUDE_DIR
SQLITE3_INCLUDE_DIR

-- Configuring done
```

---

### Post by geirha on 2008-10-29
To build something against a certain library, you need the development package (-dev) for that library. 
```
aptitude search smb.*-dev
```

libsmbclient-dev looks like the winner.

---

