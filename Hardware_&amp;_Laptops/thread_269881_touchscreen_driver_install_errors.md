---
title: "touchscreen driver install errors"
date: 2006-10-02
forum: Hardware &amp; Laptops
---

### Post by justifier on 2006-10-02
Hi

I have a 3M touchscreen and am trying to install the drivers folowing the readme from the website [http://solutions.3m.com/3MContentRetrievalAPI/BlobServlet?locale=en_US&univid=1114294724399&fallback=true&assetType=MMM_Image&blobAttribute=ImageFile&placeId=34513&version=current]("http://solutions.3m.com/3MContentRetrievalAPI/BlobServlet?locale=en_US&univid=1114294724399&fallback=true&assetType=MMM_Image&blobAttribute=ImageFile&placeId=34513&version=current")

But i keep getting the output: (sorry for writing the whole process but there may be bugs in the way i am doing it)  ```
justifier@moniter-PC:~$ sudo rpm -ivh ~/Desktop/TWDrv-5.64-1.0.src.rpm
Password:
   1:TWDrv                  ########################################### [100%]
justifier@moniter-PC:~$ cd /usr/src/rpm/SPECS/
justifier@moniter-PC:/usr/src/rpm/SPECS$ sudo rpmbuild -ba TWDrv.spec Executing(%prep): /bin/sh -e /var/tmp/rpm-tmp.11763
+ umask 022
+ cd /usr/src/rpm/BUILD
+ cd /usr/src/rpm/BUILD
+ rm -rf TWDrv-5.64
+ /bin/mkdir -p TWDrv-5.64
+ cd TWDrv-5.64
+ /bin/gzip -dc /usr/src/rpm/SOURCES/TWDrvSources.tgz
+ tar -xvvf -
drwxr-xr-x root/root         0 2006-04-11 20:47:06 bin/
-rwxr-xr-x root/root     12166 2006-04-11 20:48:39 bin/MultiMonitorTool
-rwxr-xr-x root/root     35075 2006-04-11 20:48:40 bin/TwCalib
drwxr-xr-x root/root         0 2006-04-11 20:48:39 common/
-rw-r--r-- root/root      7677 2006-04-11 20:48:39 common/tw_ioctl.h
-rw-r--r-- root/root      1497 2006-04-11 20:48:39 common/TWEvents.h
drwxr-xr-x root/root         0 2006-04-11 20:47:06 controlXInput/
-rw-r--r-- root/root      6439 2006-04-11 20:45:12 controlXInput/controlXInput.c-rw-r--r-- root/root       344 2006-04-11 20:45:12 controlXInput/makefile
drwxr-xr-x root/root         0 2006-04-11 20:47:04 daemon/
-rwxr-xr-x root/root     19587 2006-04-11 20:48:39 daemon/TWDrvStartup
-rwxr-xr-x root/root       554 2006-04-11 20:48:37 install
drwxr-xr-x root/root         0 2006-04-11 20:47:06 lib/
-rwxr-xr-x root/root     14131 2006-04-11 20:48:39 lib/libMultiMonitor.so
-rwxr-xr-x root/root     40709 2006-04-11 20:48:40 lib/libTwCaliblib.so
-rwxr-xr-x root/root    461488 2006-04-11 20:48:40 lib/libTwGraphics.so
-rw-r--r-- root/root      5887 2006-04-11 20:48:39 License.txt
drwxr-xr-x root/root         0 2006-04-11 20:47:06 mmtool/
-rw-r--r-- root/root       838 2006-04-11 20:48:39 mmtool/Makefile
-rw-r--r-- root/root      1725 2006-04-11 20:48:39 mmtool/TwMMTool.h
-rw-r--r-- root/root       414 2006-04-11 20:48:39 mmtool/Tool.cpp
-rw-r--r-- root/root     11376 2006-04-11 20:48:39 Readme.txt
drwxr-xr-x root/root         0 2006-04-11 20:47:06 TWCalib/
-rw-r--r-- root/root       926 2006-04-11 20:48:40 TWCalib/Makefile
-rw-r--r-- root/root      1700 2006-04-11 20:48:40 TWCalib/TwCalib.h
-rw-r--r-- root/root       391 2006-04-11 20:48:40 TWCalib/Calib.cpp
drwxr-xr-x root/root         0 2006-04-11 20:48:39 TwDrvKit/
-rw-r--r-- root/root     16894 2006-04-11 20:48:39 TwDrvKit/common.o.save
-rw-r--r-- root/root     48754 2006-04-11 20:48:39 TwDrvKit/TWDriver.c
-rw-r--r-- root/root      8663 2006-04-11 20:48:39 TwDrvKit/TWDriver.h
-rw-r--r-- root/root       736 2006-04-11 20:48:39 TwDrvKit/Makefile24
-rw-r--r-- root/root       916 2006-04-11 20:48:39 TwDrvKit/Makefile26
-rw-r--r-- root/root      1031 2006-04-11 20:48:39 TwDrvKit/makefile
-rwxr-xr-x root/root      1993 2006-04-11 20:48:37 TWDrvStartup
-rwxr-xr-x root/root      5882 2006-04-11 20:48:37 TWXinputInstall.perl
drwxr-xr-x root/root         0 2006-04-11 20:48:21 Xfree4.0.3/
-rw-r--r-- root/root     10158 2006-04-11 20:47:57 Xfree4.0.3/TWXinput_drv.o
+ STATUS=0
+ '[' 0 -ne 0 ']'
+ exit 0
Executing(%build): /bin/sh -e /var/tmp/rpm-tmp.7931
+ umask 022
+ cd /usr/src/rpm/BUILD
+ cd TWDrv-5.64
+ '[' -z '' ']'
++ uname -r
++ sed -e s/smp//g
+ KERNEL_RELEASE=2.6.15-27-386
+ echo 'using 2.6.15-27-386'
using 2.6.15-27-386
+ echo ''

+ rm -rf /var/tmp/TWDrv-5.64-root
+ KVER=2.6.15-27-386
+ export KVER
+ cd TwDrvKit
+ make clean
+ make
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit modules
make: *** /lib/modules/2.6.15-27-386/build: No such file or directory.  Stop.
make[1]: *** [default] Error 2
make: *** [makeit] Error 2
error: Bad exit status from /var/tmp/rpm-tmp.7931 (%build)


RPM build errors:
    Bad exit status from /var/tmp/rpm-tmp.7931 (%build)
justifier@moniter-PC:/usr/src/rpm/SPECS$


```

with those errors, 

I am a relativley experienced ubuntu user (aprox 1 year) but still require fairly detailed (simple) how to's

Please help as this isssue is bugging me and idont seem to be able to get this driver to work.

Many thanks 

justifier

---

