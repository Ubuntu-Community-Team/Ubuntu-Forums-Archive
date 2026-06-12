---
title: "Installing glibc-2.3"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by srivathsan on 2009-02-06
Hi,
    I am trying to install a network simulator called "Qualnet-4.5". This has the requirement that I have glibc-2.3.x and gcc-3.4. The Makefile in Qualnet-4.5 says "ARCH = linux-glibc-2.3" and "COMPILER = gcc-3.4".

My current system runs Ubuntu-8.10 which has glibc-2.8 and gcc-4.3.2. I tried to "make" with the current configuration just to see if it compiles correctly. But, I go a LOT of warnings: "warning: deprecated conversion from string constant to &#8216;char*&#8217;". After a quick Google search on this, I found that replacing every instance of "char*" to "const char*" would fix this problem. But, I do not want to touch this large codebase of Qualnet-4.5 and fix every file. So, the alternate way was to abide by their 'Installation Manual' which recommends glibc-2.3 and gcc-3.2, 3.4, or 4.0.


I have installed gcc-3.4 using Synaptic and changed the link (in /usr/bin) to point gcc -> gcc-3.4. Now, when I do "gcc -v", I correctly get "gcc version 3.4.6". 

(Question: Is there a nicer way to "make" qualnet with gcc-3.4 instead of changing the link itself? export CC=gcc-3.4 doesn't seem to work. I need the system to use gcc-3.4 whenever I build anything related to Qualnet. Help needed here.)

Now, the next step is an issue. I am not sure how to get and install glibc-2.3 without breaking anything. I really do not know what the consequences will be and want to be sure in what I do as a root-user. I do not want to blindly download glibc-2.3 and build it and mess-up things.

Any suggestions to get this done in a controlled fashion would be very much appreciated.

Thanks again,
Sri.

---

### Post by snova on 2009-02-07
First of all, glibc is an extremely core library. Not only is it going to be a difficult thing to get installed, it's also going to mean a lot of tweaking to get it to use the new library.

Secondly, these are only warnings; they can be safely ignored. And given the complexity of this task... I suggest so. It will still work in the end.

---

### Post by asma-adn on 2009-04-06
Hello

I have the same problem

i try to install Qualnet-4.5.1 under ubuntu 8.10, but when i make it, i have several warning and error messages:

./main/app_util.cpp:2849: attention : deprecated conversion from string constant to ‘char*’
../main/app_util.cpp:2849: attention : deprecated conversion from string constant to ‘char*’
../main/app_util.cpp:2849: attention : deprecated conversion from string constant to ‘char*’
../main/app_util.cpp: In function ‘short int APP_GetFreePort(Node*)’:
../main/app_util.cpp:3044: attention : deprecated conversion from string constant to ‘char*’
g++ -I../include -I../libraries/developer/src -I../libraries/multimedia_enterprise/src -I../libraries/wireless/src -I../libraries/wireless/src/olsrv2 -DPARALLEL -DNEEDS_NETINET_IN_H -g -O3  -DENTERPRISE_LIB -DWIRELESS_LIB       -c ../main/application.cpp -o ../main/application.o
In file included from ../include/clock.h:27,
                 from ../include/api.h:29,
                 from ../main/application.cpp:27:
../include/main.h:521: attention : deprecated conversion from string constant to ‘char*’
../include/main.h:521: attention : deprecated conversion from string constant to ‘char*’
../include/main.h:521: attention : deprecated conversion from string constant to ‘char*’
../include/main.h:521: attention : deprecated conversion from string constant to ‘char*’
../include/main.h:521: attention : deprecated conversion from string constant to ‘char*’
../include/main.h:521: attention : deprecated conversion from string constant to ‘char*’
../include/main.h:521: attention : deprecated conversion from string constant to ‘char*’
In file included from ../include/api.h:30,
                 from ../main/application.cpp:27:
../include/qualnet_error.h: In function ‘void ERROR_ReportMissingAddon(const char*, const char*)’:
../include/qualnet_error.h:152: attention : deprecated conversion from string constant to ‘char*’
../include/qualnet_error.h: In function ‘void ERROR_ReportMissingInterface(const char*, const char*)’:
../include/qualnet_error.h:170: attention : deprecated conversion from string constant to ‘char*’
../include/qualnet_error.h: In function ‘void ERROR_ReportMissingLibrary(const char*, const char*)’:
../include/qualnet_error.h:188: attention : deprecated conversion from string constant to ‘char*’
In file included from ../include/api.h:35,
                 from ../main/application.cpp:27:
../include/coordinates.h: In function ‘int COORD_NormalizeAzimuthAngle(int)’:
../include/coordinates.h:292: attention : deprecated conversion from string constant to ‘char*’
../include/coordinates.h:292: attention : deprecated conversion from string constant to ‘char*’
../include/coordinates.h:293: attention : deprecated conversion from string constant to ‘char*’
../include/coordinates.h:293: attention : deprecated conversion from string constant to ‘char*’
../include/coordinates.h: In function ‘int COORD_NormalizeElevationAngle(int)’:
../include/coordinates.h:315: attention : deprecated conversion from string constant to ‘char*’
../include/coordinates.h:315: attention : deprecated conversion from string constant to ‘char*’
../include/coordinates.h:316: attention : deprecated conversion from string constant to ‘char*’
../include/coordinates.h:316: attention : deprecated conversion from string constant to ‘char*’
../include/coordinates.h: In function ‘int COORD_NormalizeAngleIndex(int, int)’:
../include/coordinates.h:342: attention : deprecated conversion from string constant to ‘char*’
../include/coordinates.h:342: attention : deprecated conversion from string constant to ‘char*’
../include/coordinates.h:343: attention : deprecated conversion from string constant to ‘char*’
../include/coordinates.h:343: attention : deprecated conversion from string constant to ‘char*’
In file included from ../include/api.h:36,
                 from ../main/application.cpp:27:
../include/splaytree.h: In function ‘SplayNode* SplayAllocateNode(Node*)’:
../include/splaytree.h:122: attention : deprecated conversion from string constant to ‘char*’
../include/splaytree.h:123: attention : deprecated conversion from string constant to ‘char*’
../include/splaytree.h:123: attention : deprecated conversion from string constant to ‘char*’
In file included from ../include/propagation.h:30,
                 from ../include/api.h:39,
                 from ../main/application.cpp:27:
../include/dynamic.h: In member function ‘void D_Object::Changed()’:
../include/dynamic.h:941: attention : deprecated conversion from string constant to ‘char*’
../include/dynamic.h:941: attention : deprecated conversion from string constant to ‘char*’
../include/dynamic.h:941: attention : deprecated conversion from string constant to ‘char*’
.............................. etc


Here is my configuration:
- intel 64 bit
- gcc 4.3.2
- java 6

do you have any idea ???

---

