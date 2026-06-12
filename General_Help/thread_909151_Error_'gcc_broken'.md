---
title: "Error 'gcc broken'"
date: 2008-09-03
forum: General Help
---

### Post by thehungrylobster on 2008-09-03
Hi, can you help me to solve this ?


```
administrateur@proxan:~/edit$ cmake -DWITH_TSP=ON -DWITH_DD=ON .

-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- broken
CMake Error: The C compiler "/usr/bin/gcc" is not able to compile a simple test                                                                               program.
It fails with the following output:
 /usr/bin/make -f CMakeFiles/cmTryCompileExec.dir/build.make CMakeFiles/cmTryCom                                                                              pileExec.dir/build
make[1]: Entering directory `/home/administrateur/edit/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/administrateur/edit/CMakeFile                                                                              s/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec.dir/testCCompiler.o
/usr/bin/gcc   -o CMakeFiles/cmTryCompileExec.dir/testCCompiler.o   -c /home/adm                                                                              inistrateur/edit/CMakeFiles/CMakeTmp/testCCompiler.c
/home/administrateur/edit/CMakeFiles/CMakeTmp/testCCompiler.c:4:19: error:                                                                               stdio.h: No such file or directory
/home/administrateur/edit/CMakeFiles/CMakeTmp/testCCompiler.c: In function                                                                               âmainâ:
/home/administrateur/edit/CMakeFiles/CMakeTmp/testCCompiler.c:12: warning:                                                                               incompatible implicit declaration of built-in function âprintfâ
make[1]: *** [CMakeFiles/cmTryCompileExec.dir/testCCompiler.o] Error 1
make[1]: Leaving directory `/home/administrateur/edit/CMakeFiles/CMakeTmp'
make: *** [cmTryCompileExec/fast] Error 2


CMake will not be able to correctly generate this project.
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   P                                                                              lease set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Configuring done

```



I really have no idea what's going on..
What can i do ?

---

### Post by cszikszoy on 2008-09-03
Have you installed build-essential?

```
sudo apt-get install build-essential
```

---

### Post by justleen on 2008-09-03
seems like gcc is missing indeed..

---

### Post by thehungrylobster on 2008-09-03
Thanks, it's solved

---

### Post by cszikszoy on 2008-09-03
Would you mind going to Thread Tools > Mark Thread as Solved?

This helps other people solve similar problems without posting a new thread.

Thanks!

---

### Post by green69 on 2011-04-23
> **cszikszoy said:**
> Have you installed build-essential?

```
sudo apt-get install build-essential
```

Same error here, after some years. Still the solution is working. build-essential seem really essential!

:D

---

