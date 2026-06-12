---
title: "Trouble installing ann python wrapper"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by sirjanselot on 2009-02-22
Hey guys, need some help.

I am trying to install ANN from this website:

[http://www.cs.umd.edu/~mount/ANN/](http://www.cs.umd.edu/~mount/ANN/)

I downloaded the ann_1.1.1 tar file, unloaded it and used the make command install it.

Then I tried to install the python wrapper from here:

[http://scikits.appspot.com/ann](http://scikits.appspot.com/ann)

and it wouldn't work. Take a look at my error message

------------------------------------------------------------------------
running install
running build
running scons
customize UnixCCompiler
Found executable /usr/bin/gcc
customize GnuFCompiler
Could not locate executable g77
Could not locate executable f77
customize IntelFCompiler
Could not locate executable ifort
Could not locate executable ifc
customize LaheyFCompiler
Could not locate executable lf95
customize PGroupFCompiler
Could not locate executable pgf90
Could not locate executable pgf77
customize AbsoftFCompiler
Could not locate executable f90
customize NAGFCompiler
Could not locate executable f95
customize VastFCompiler
customize GnuFCompiler
customize CompaqFCompiler
Could not locate executable fort
customize IntelItaniumFCompiler
Could not locate executable efort
Could not locate executable efc
customize IntelEM64TFCompiler
customize Gnu95FCompiler
Could not locate executable gfortran
customize G95FCompiler
Could not locate executable g95
don't know how to compile Fortran code on platform 'posix'
customize UnixCCompiler
customize UnixCCompiler using scons
Found executable /usr/bin/g++
running config_cc
unifing config_cc, config, build_clib, build_ext, build commands --compiler options
running config_fc
unifing config_fc, config, build_clib, build_ext, build commands --fcompiler options
running build_src
building extension "scikits.ann._ANN" sources
building data_files sources
running build_py
running build_ext
customize UnixCCompiler
customize UnixCCompiler using build_ext
customize UnixCCompiler
customize UnixCCompiler using build_ext
building 'scikits.ann._ANN' extension
compiling C++ sources
C compiler: g++ -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -fPIC

compile options: '-Iscikits/ann -I/usr/local/include -I/usr/lib/python2.5/site-packages/numpy/core/include -I/usr/include/python2.5 -c'
g++: build/src.linux-x86_64-2.5/scikits/ann/ANN_wrap.cpp
build/src.linux-x86_64-2.5/scikits/ann/ANN_wrap.cpp:2597:25: error: ANN/ANN.h: No such file or directory
In file included from build/src.linux-x86_64-2.5/scikits/ann/ANN_wrap.cpp:2598:
scikits/ann/kdtree.h:22:21: error: ANN/ANN.h: No such file or directory
scikits/ann/kdtree.h:101:3: warning: no newline at end of file
scikits/ann/kdtree.h:27: error: &#8216;ANNpointArray&#8217; does not name a type
scikits/ann/kdtree.h:28: error: ISO C++ forbids declaration of &#8216;ANNkd_tree&#8217; with no type
scikits/ann/kdtree.h:28: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
scikits/ann/kdtree.h:43: error: &#8216;ANN_KD_SUGGEST&#8217; was not declared in this scope
scikits/ann/kdtree.h: In constructor &#8216;_kdtree::_kdtree(double*, int, int, int, int)&#8217;:
scikits/ann/kdtree.h:44: error: &#8216;pts&#8217; was not declared in this scope
scikits/ann/kdtree.h:44: error: &#8216;annAllocPts&#8217; was not declared in this scope
scikits/ann/kdtree.h:53: error: &#8216;tree&#8217; was not declared in this scope
scikits/ann/kdtree.h:53: error: expected type-specifier before &#8216;ANNkd_tree&#8217;
scikits/ann/kdtree.h:53: error: expected `;' before &#8216;ANNkd_tree&#8217;
scikits/ann/kdtree.h: In destructor &#8216;_kdtree::~_kdtree()&#8217;:
scikits/ann/kdtree.h:57: error: &#8216;pts&#8217; was not declared in this scope
scikits/ann/kdtree.h:57: error: &#8216;annDeallocPts&#8217; was not declared in this scope
scikits/ann/kdtree.h:58: error: &#8216;tree&#8217; was not declared in this scope
scikits/ann/kdtree.h: In member function &#8216;void _kdtree::_knn2(double*, int, int, int, int, int*, int, int, double*, double) const&#8217;:
scikits/ann/kdtree.h:71: error: &#8216;tree&#8217; was not declared in this scope
scikits/ann/kdtree.h: In member function &#8216;const char* _kdtree::stringRep(bool) const&#8217;:
scikits/ann/kdtree.h:98: error: &#8216;tree&#8217; was not declared in this scope
scikits/ann/kdtree.h:98: error: &#8216;ANNtrue&#8217; was not declared in this scope
scikits/ann/kdtree.h:98: error: &#8216;ANNfalse&#8217; was not declared in this scope
build/src.linux-x86_64-2.5/scikits/ann/ANN_wrap.cpp:2597:25: error: ANN/ANN.h: No such file or directory
In file included from build/src.linux-x86_64-2.5/scikits/ann/ANN_wrap.cpp:2598:
scikits/ann/kdtree.h:22:21: error: ANN/ANN.h: No such file or directory
scikits/ann/kdtree.h:101:3: warning: no newline at end of file
scikits/ann/kdtree.h:27: error: &#8216;ANNpointArray&#8217; does not name a type
scikits/ann/kdtree.h:28: error: ISO C++ forbids declaration of &#8216;ANNkd_tree&#8217; with no type
scikits/ann/kdtree.h:28: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
scikits/ann/kdtree.h:43: error: &#8216;ANN_KD_SUGGEST&#8217; was not declared in this scope
scikits/ann/kdtree.h: In constructor &#8216;_kdtree::_kdtree(double*, int, int, int, int)&#8217;:
scikits/ann/kdtree.h:44: error: &#8216;pts&#8217; was not declared in this scope
scikits/ann/kdtree.h:44: error: &#8216;annAllocPts&#8217; was not declared in this scope
scikits/ann/kdtree.h:53: error: &#8216;tree&#8217; was not declared in this scope
scikits/ann/kdtree.h:53: error: expected type-specifier before &#8216;ANNkd_tree&#8217;
scikits/ann/kdtree.h:53: error: expected `;' before &#8216;ANNkd_tree&#8217;
scikits/ann/kdtree.h: In destructor &#8216;_kdtree::~_kdtree()&#8217;:
scikits/ann/kdtree.h:57: error: &#8216;pts&#8217; was not declared in this scope
scikits/ann/kdtree.h:57: error: &#8216;annDeallocPts&#8217; was not declared in this scope
scikits/ann/kdtree.h:58: error: &#8216;tree&#8217; was not declared in this scope
scikits/ann/kdtree.h: In member function &#8216;void _kdtree::_knn2(double*, int, int, int, int, int*, int, int, double*, double) const&#8217;:
scikits/ann/kdtree.h:71: error: &#8216;tree&#8217; was not declared in this scope
scikits/ann/kdtree.h: In member function &#8216;const char* _kdtree::stringRep(bool) const&#8217;:
scikits/ann/kdtree.h:98: error: &#8216;tree&#8217; was not declared in this scope
scikits/ann/kdtree.h:98: error: &#8216;ANNtrue&#8217; was not declared in this scope
scikits/ann/kdtree.h:98: error: &#8216;ANNfalse&#8217; was not declared in this scope
error: Command "g++ -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -fPIC -Iscikits/ann -I/usr/local/include -I/usr/lib/python2.5/site-packages/numpy/core/include -I/usr/include/python2.5 -c build/src.linux-x86_64-2.5/scikits/ann/ANN_wrap.cpp -o build/temp.linux-x86_64-2.5/build/src.linux-x86_64-2.5/scikits/ann/ANN_wrap.o" failed with exit status 1



[COLOR="Red"]I ran it appropriately using the make linux-++ and it compiled properly.  However, I don't know why the wrapper still can't find it.  It worked on my 8.04 LTS 32-bit, but not in Intrepid 64-bit.  [/COLOR]

cd src ; make linux-g++
make[1]: Entering directory `/home/supacreative/Desktop/ann_1.1.1/src'
make targets \
"ANNLIB = libANN.a" \
"C++ = g++" \
"CFLAGS = -O3" \
"MAKELIB = ar ruv" \
"RANLIB = true"
make[2]: Entering directory `/home/supacreative/Desktop/ann_1.1.1/src'
g++ -c -I../include -O3 ANN.cpp
g++ -c -I../include -O3 brute.cpp
g++ -c -I../include -O3 kd_tree.cpp
g++ -c -I../include -O3 kd_util.cpp
g++ -c -I../include -O3 kd_split.cpp
g++ -c -I../include -O3 kd_dump.cpp
g++ -c -I../include -O3 kd_search.cpp
g++ -c -I../include -O3 kd_pr_search.cpp
g++ -c -I../include -O3 kd_fix_rad_search.cpp
g++ -c -I../include -O3 bd_tree.cpp
g++ -c -I../include -O3 bd_search.cpp
g++ -c -I../include -O3 bd_pr_search.cpp
g++ -c -I../include -O3 bd_fix_rad_search.cpp
g++ -c -I../include -O3 perf.cpp
ar ruv libANN.a ANN.o brute.o kd_tree.o kd_util.o kd_split.o kd_dump.o kd_search.o kd_pr_search.o kd_fix_rad_search.o bd_tree.o bd_search.o bd_pr_search.o bd_fix_rad_search.o perf.o
ar: creating libANN.a
a - ANN.o
a - brute.o
a - kd_tree.o
a - kd_util.o
a - kd_split.o
a - kd_dump.o
a - kd_search.o
a - kd_pr_search.o
a - kd_fix_rad_search.o
a - bd_tree.o
a - bd_search.o
a - bd_pr_search.o
a - bd_fix_rad_search.o
a - perf.o
true libANN.a
mv libANN.a ../lib
make[2]: Leaving directory `/home/supacreative/Desktop/ann_1.1.1/src'
make[1]: Leaving directory `/home/supacreative/Desktop/ann_1.1.1/src'
cd test ; make linux-g++
make[1]: Entering directory `/home/supacreative/Desktop/ann_1.1.1/test'
make targets \
"ANNLIB = libANN.a" \
"C++ = g++" \
"CFLAGS = -O3" \
"MAKELIB = ar ruv" \
"RANLIB = true"
make[2]: Entering directory `/home/supacreative/Desktop/ann_1.1.1/test'
g++ -c -I../include -O3 ann_test.cpp
g++ -c -I../include -O3 rand.cpp
g++ ann_test.o rand.o -o ann_test -L../lib -lANN -lm
mv ann_test ../bin
make[2]: Leaving directory `/home/supacreative/Desktop/ann_1.1.1/test'
make[1]: Leaving directory `/home/supacreative/Desktop/ann_1.1.1/test'
cd sample ; make linux-g++
make[1]: Entering directory `/home/supacreative/Desktop/ann_1.1.1/sample'
make targets \
"ANNLIB = libANN.a" \
"C++ = g++" \
"CFLAGS = -O3" \
"MAKELIB = ar ruv" \
"RANLIB = true"
make[2]: Entering directory `/home/supacreative/Desktop/ann_1.1.1/sample'
g++ -c -I../include -O3 ann_sample.cpp
g++ ann_sample.o -o ann_sample -L../lib -lANN -lm
mv ann_sample ../bin
make[2]: Leaving directory `/home/supacreative/Desktop/ann_1.1.1/sample'
make[1]: Leaving directory `/home/supacreative/Desktop/ann_1.1.1/sample'
cd ann2fig ; make linux-g++
make[1]: Entering directory `/home/supacreative/Desktop/ann_1.1.1/ann2fig'
make targets \
"ANNLIB = libANN.a" \
"C++ = g++" \
"CFLAGS = -O3" \
"MAKELIB = ar ruv" \
"RANLIB = true"
make[2]: Entering directory `/home/supacreative/Desktop/ann_1.1.1/ann2fig'
g++ -c -I../include ann2fig.cpp
g++ ann2fig.o -o ann2fig -L../lib -lANN -lm
mv ann2fig ../bin
make[2]: Leaving directory `/home/supacreative/Desktop/ann_1.1.1/ann2fig'
make[1]: Leaving directory `/home/supacreative/Desktop/ann_1.1.1/ann2fig

The ANN libraries has to installed manually through their website since they are not available in the repositories.  Please help. 

THANKS!!!

---

