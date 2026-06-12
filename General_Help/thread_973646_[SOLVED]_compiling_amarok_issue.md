---
title: "[SOLVED] compiling amarok issue"
date: 2008-11-06
forum: General Help
---

### Post by James- on 2008-11-06
I'm having problems compiling the svn version of amarok(trying to see if they support ipod touch 2g yet)

Ran into this:
> 
james@james-laptop:~/Desktop/amarok/build$ cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` -DCMAKE_BUILD_TYPE=debugfull .. && make && make install 
-- The C compiler identification is GNU
-- The CXX compiler identification is unknown
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: CMAKE_CXX_COMPILER-NOTFOUND
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
CMake Error: Internal CMake error, TryCompile configure of cmake failed
-- Check for working CXX compiler: CMAKE_CXX_COMPILER-NOTFOUND -- broken
CMake Error at /usr/share/cmake-2.6/Modules/CMakeTestCXXCompiler.cmake:25 (MESSAGE):
  The C++ compiler "CMAKE_CXX_COMPILER-NOTFOUND" is not able to compile a
  simple test program.

  It fails with the following output:

   

  

  CMake will not be able to correctly generate this project.
Call Stack (most recent call first):
  CMakeLists.txt:1 (project)


CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Configuring done



---

### Post by Yellow Pasque on 2008-11-06
Are you trying to compile amarok2?
Do you have cmake and the basic software building tools installed?
```
sudo apt-get install cmake build-essential
```
Also, see if this helps (you may need to enable source code repos in System -> Administration -> Software Sources):
```
sudo apt-get build-dep amarok
```

---

### Post by James- on 2008-11-07
yeah I am I tried that(found it a little earlier) and its giving me errors that cmake files are missing I guess they didn't include in SVN version


fallowing this guide:
[http://amarok.kde.org/wiki/2.0_Development_HowTo](http://amarok.kde.org/wiki/2.0_Development_HowTo)


> 
james@james-laptop:~/Desktop/amarok/build$ cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` -DCMAKE_BUILD_TYPE=debugfull .. && make && make install 
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
CMake Error at /usr/share/cmake-2.6/Modules/FindKDE4.cmake:72 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/james/.kde/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:8 (find_package)


---

### Post by smaba on 2008-11-07
Did u install libtag 1.5, mysqld,gcc and g++?

---

### Post by James- on 2008-11-07
> **smaba said:**
> Did u install libtag 1.5, mysqld,gcc and g++?

I can't find mysqld or gcc in repo but i did do a build-dep which should download all the dependencies(i already had the g++ compiler(4.3))



EDIT: installed kdelibs5-dev and it's working

---

