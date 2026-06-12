---
title: "Building drivers - help needed :)"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by DaveAK on 2007-07-19
I'm building drivers for my 3M TouchScreen.  Can someone take a look and see if this will work for Feisty?

[http://solutions.3m.com/wps/portal/3M/en_US/3MTouchSystems/TS/TechnicalInformation/TouchDrivers/](http://solutions.3m.com/wps/portal/3M/en_US/3MTouchSystems/TS/TechnicalInformation/TouchDrivers/)

I get so far and after issuing 'rpmbuild -ba TWDrv.spec' get this as the first of many errors : 

/usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit/TWDriver.c:12:35: error: linux/devfs_fs_kernel.h: No such file or directory

What do I need to do next?

---

### Post by pauls13 on 2007-09-19
Bump!

I'm getting this too... kernel version 2.6.18

Thanks,
Paul

---

### Post by geraldm on 2007-09-19
The linux/devfs_fs_kernel.h was present in linux kernels when the devfs filesystem was used.
It has been deleted, and the package needs to be modified.
Check back with your 3m source to see if there is a package that is not dependant on devfs.

Gerald

---

### Post by pauls13 on 2007-09-20
Hi guys,

I called 3M and was able to talk with someone who could help me. He emailed me a document that details the changes you'll need to make to the various source files to get it compiling under different kernel versions & distros.

I've attached it with this post as a plaintext file.

Hope this helps you,

Paul

---

### Post by gigasai on 2007-10-17
Hi everyone,

I am running Ubuntu 6.06 Dapper drake and I have a peculiar problem with building the drivers. It says:

[FONT="Courier New"]TWDriver.c:107: error: syntax error before string constant[/FONT]

Did anyone else have this problem? Help is appreciated! Thanks!

---

### Post by kdoggydog on 2007-12-28
Hi All,

So, I have a system with an NEC LCD with integrated 3M USB Touchscreen – EXII.

I have spent the last day and a bit hacking the driver source code available on the 3M site and now have the driver module building against kernel 2.6.23.1-42.fc8 (yes i'm running fedora ;).  The RPM seems to install OK and the TWDrv module seems to insert without complaining.  However I have no touchscreen response.

I'm hoping someone with it working on an older "3M supported kernel" could shed some light on what modules i should see loaded.  Also some diagnostic things i could try.

SYSTEM INFO

1. The touchscreen device seems to be physically there (#cat /proc/bus/usb/devices yields an entry for the touchscreen device).

2. The RPM install has modified my xorg.conf file with the (apparently) necessary entries:
	Section “ServerLayout”
	…
	InputDevice	“TouchScreen” “SendCoreEvents”
	EndSection

	Section “InputDevice”
	Identifier	“TouchScreen”
	Driver		“TWXinput”
	Option		“Device” “/dev/twscreen0”
	Option		“Mapping” “ “
	EndSection

3. /dev/twscreen[0-9] are present

4. dmesg reports: “usbcore: registered new interface driver TWDrv”

5. lsmod reports that TWDrv is loaded.  No other ‘touch modules’ are present (eg usbtouchscreen, mtouch, mutouch, etc)

I'll post my 'hacked' RPM after i make sure it actually works.

Thanks in advance for your help.

---

### Post by torstenkarusseit on 2008-04-15
Hi kdoggydog,
did you get the 3M USB Touchscreen to work ?
I'm trying for debian 2.6.24 with no luck.
The first trouble is:
make is saying .. /lib/modules/2.6.18-6-686/build does not exist
May you describe your way ?
Thank you

---

### Post by KuroSatsu on 2008-04-19
Wow...what a hassle!

I've followed the instructions in the Known Issues txt and made every change with the exception of the first one for "unresolved symbol print_tainted" which wasn't necessary.

During my test run, I ran the make (just 'make' in the command line).  It ran with a couple of warnings, but no errors.  I then installed the module (insmod TWDrv.ko) like in the guide.  After doing an lsmod, TWDrv was at the top of the list.  Assuming that everything worked, I tarred the data up and put it back into the SOURCES folder.  

I also made the recommended changes to the .spec file.  After that I did the rpmbuild -ba TWDrv.spec and received the following (it failed):

> team1@team1-desktop:/usr/src/rpm/SPECS$ sudo rpmbuild -ba TWDrv.spec 
Executing(%prep): /bin/sh -e /var/tmp/rpm-tmp.37741
+ umask 022
+ cd /usr/src/rpm/BUILD
+ cd /usr/src/rpm/BUILD
+ rm -rf TWDrv-5.64
+ /bin/mkdir -p TWDrv-5.64
+ cd TWDrv-5.64
+ /bin/gzip -dc /usr/src/rpm/SOURCES/TWDrvSources.tgz
+ tar -xvvf -
drwxr-xr-x team1/team1       0 2006-04-11 14:47 bin/
-rwxr-xr-x team1/team1   12166 2006-04-11 14:48 bin/MultiMonitorTool
-rwxr-xr-x team1/team1   35075 2006-04-11 14:48 bin/TwCalib
drwxr-xr-x team1/team1       0 2006-04-11 14:48 common/
-rw-r--r-- team1/team1    7677 2006-04-11 14:48 common/tw_ioctl.h
-rw-r--r-- team1/team1    1497 2006-04-11 14:48 common/TWEvents.h
drwxr-xr-x team1/team1       0 2006-04-11 14:47 controlXInput/
-rw-r--r-- team1/team1    6439 2006-04-11 14:45 controlXInput/controlXInput.c
-rw-r--r-- team1/team1     344 2006-04-11 14:45 controlXInput/makefile
drwxr-xr-x team1/team1       0 2006-04-11 14:47 daemon/
-rwxr-xr-x team1/team1   19587 2006-04-11 14:48 daemon/TWDrvStartup
-rwxr-xr-x team1/team1     554 2006-04-11 14:48 install
drwxr-xr-x team1/team1       0 2006-04-11 14:47 lib/
-rwxr-xr-x team1/team1   40709 2006-04-11 14:48 lib/libTwCaliblib.so
-rwxr-xr-x team1/team1  461488 2006-04-11 14:48 lib/libTwGraphics.so
-rwxr-xr-x team1/team1   14131 2006-04-11 14:48 lib/libMultiMonitor.so
-rw-r--r-- team1/team1    5887 2006-04-11 14:48 License.txt
drwxr-xr-x team1/team1       0 2006-04-11 14:47 mmtool/
-rw-r--r-- team1/team1     838 2006-04-11 14:48 mmtool/Makefile
-rw-r--r-- team1/team1    1725 2006-04-11 14:48 mmtool/TwMMTool.h
-rw-r--r-- team1/team1     414 2006-04-11 14:48 mmtool/Tool.cpp
-rw-r--r-- team1/team1   11376 2006-04-11 14:48 Readme.txt
drwxr-xr-x team1/team1       0 2006-04-11 14:47 TWCalib/
-rw-r--r-- team1/team1     926 2006-04-11 14:48 TWCalib/Makefile
-rw-r--r-- team1/team1     391 2006-04-11 14:48 TWCalib/Calib.cpp
-rw-r--r-- team1/team1    1700 2006-04-11 14:48 TWCalib/TwCalib.h
drwxr-xr-x team1/team1       0 2008-04-19 05:11 TwDrvKit/
-rw-r--r-- root/root       916 2008-04-19 05:11 TwDrvKit/Makefile
-rw-r--r-- root/root    200725 2008-04-19 05:11 TwDrvKit/TWDrv.ko
-rw-r--r-- root/root      2363 2008-04-19 05:11 TwDrvKit/TWDrv.mod.c
-rw-r--r-- root/root       229 2008-04-19 05:11 TwDrvKit/.TWDrv.o.cmd
-rw-r--r-- team1/team1   49578 2008-04-19 05:11 TwDrvKit/TWDriver.c~
-rw-r--r-- team1/team1     736 2006-04-11 14:48 TwDrvKit/Makefile24
-rw-r--r-- root/root       230 2008-04-19 05:11 TwDrvKit/.TWDrv.ko.cmd
-rw-r--r-- team1/team1     916 2006-04-11 14:48 TwDrvKit/Makefile26
-rw-r--r-- root/root    172745 2008-04-19 05:11 TwDrvKit/TWDrv.o
-rw-r--r-- root/root     17367 2008-04-19 05:11 TwDrvKit/.TWDriver.o.cmd
-rw-r--r-- team1/team1    1031 2006-04-11 14:48 TwDrvKit/makefile
-rw-r--r-- root/root     16894 2008-04-19 04:56 TwDrvKit/common.o
-rw-r--r-- root/root         0 2008-04-19 05:11 TwDrvKit/Module.symvers
-rw-r--r-- root/root    158316 2008-04-19 05:11 TwDrvKit/TWDriver.o
-rw-r--r-- root/root     29216 2008-04-19 05:11 TwDrvKit/TWDrv.mod.o
drwxr-xr-x root/root         0 2008-04-19 05:11 TwDrvKit/.tmp_versions/
-rw-r--r-- root/root       143 2008-04-19 05:11 TwDrvKit/.tmp_versions/TWDrv.mod
-rw-r--r-- root/root     11492 2008-04-19 05:11 TwDrvKit/.TWDrv.mod.o.cmd
-rw-r--r-- team1/team1   49578 2008-04-19 05:11 TwDrvKit/TWDriver.c
-rw-r--r-- team1/team1    8663 2006-04-11 14:48 TwDrvKit/TWDriver.h
-rw-r--r-- team1/team1   16894 2006-04-11 14:48 TwDrvKit/common.o.save
-rwxr-xr-x team1/team1    1993 2006-04-11 14:48 TWDrvStartup
-rwxr-xr-x team1/team1    5882 2006-04-11 14:48 TWXinputInstall.perl
drwxr-xr-x team1/team1       0 2006-04-11 14:48 Xfree4.0.3/
-rw-r--r-- team1/team1   10158 2006-04-11 14:47 Xfree4.0.3/TWXinput_drv.o
+ STATUS=0
+ [ 0 -ne 0 ]
+ exit 0
Executing(%build): /bin/sh -e /var/tmp/rpm-tmp.37741
+ umask 022
+ cd /usr/src/rpm/BUILD
+ cd TWDrv-5.64
+ [ -z  ]
+ uname -r
+ sed -e s/smp//g
+ KERNEL_RELEASE=2.6.22-14-generic
+ echo using 2.6.22-14-generic
using 2.6.22-14-generic
+ echo 

+ rm -rf /var/tmp/TWDrv-5.64-root
+ KVER=2.6.22-14-generic
+ export KVER
+ cd TwDrvKit
+ make clean
make[1]: Entering directory `/usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit'
make[1]: Leaving directory `/usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit'
+ make
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit modules
cp /usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit/common.o.save /usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit/common.o
  CC [M]  /usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit/TWDriver.o
In file included from include/asm/uaccess.h:9,
                 from /usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit/TWDriver.c:11:
include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
include/linux/prefetch.h:62: warning: pointer of type &#8216;void *&#8217; used in arithmetic
/usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit/TWDriver.c: In function &#8216;TWDrv_enable_interrupt&#8217;:
/usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit/TWDriver.c:855: warning: &#8216;deprecated_irq_flag&#8217; is deprecated (declared at include/linux/interrupt.h:66)
/usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit/TWDriver.c:855: warning: &#8216;deprecated_irq_flag&#8217; is deprecated (declared at include/linux/interrupt.h:66)
/usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit/TWDriver.c:855: warning: &#8216;deprecated_irq_flag&#8217; is deprecated (declared at include/linux/interrupt.h:66)
/usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit/TWDriver.c:856: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
/usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit/TWDriver.c: In function &#8216;TWDrv_UsbFillUrb&#8217;:
/usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit/TWDriver.c:1848: warning: passing argument 6 of &#8216;usb_fill_int_urb&#8217; from incompatible pointer type
  LD [M]  /usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit/TWDrv.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit/.common.o.cmd for /usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit/common.o
WARNING: modpost: GPL-incompatible module TWDrv.ko uses future GPL-only symbol 'usb_deregister'
WARNING: modpost: GPL-incompatible module TWDrv.ko uses future GPL-only symbol 'usb_register_driver'
  CC      /usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit/TWDrv.mod.o
  LD [M]  /usr/src/rpm/BUILD/TWDrv-5.64/TwDrvKit/TWDrv.ko
+ echo 2.6.22-14-generic
+ awk /^..6../
+ [ 2.6.22-14-generic !=  ]
+ MODULE_EXT=ko
+ mkdir -p /var/tmp/TWDrv-5.64-root/lib/modules/2.6.22-14-generic/kernel/drivers/input/touchscreen
+ install -o root -g root -m 555 TWDrv.ko /var/tmp/TWDrv-5.64-root/lib/modules/2.6.22-14-generic/kernel/drivers/input/touchscreen
+ cd ..
+ cd mmtool
+ make
gcc -fPIC -I./ -c Tool.cpp -o Tool.o
gcc  Tool.o -L../lib -lMultiMonitor -o MultiMonitorTool
+ cp MultiMonitorTool ../bin
+ cd ..
+ cd TWCalib
+ make
gcc -fPIC -I./ -c Calib.cpp -o Calib.o
gcc  Calib.o -L../lib -lTwCaliblib -lpthread -lTwGraphics -lstdc++ -o TwCalib
+ cp TwCalib ../bin
+ cd ..
+ echo reference kernel 2.6.22-14-generic
+ rpm -qa
+ grep gcc
error: Bad exit status from /var/tmp/rpm-tmp.37741 (%build)


RPM build errors:
    Bad exit status from /var/tmp/rpm-tmp.37741 (%build)


I can't see any debug information related to the "error"...it just seems to error out and give me the finger! ](*,)

However, I am a less than seasoned programmer and I only have about 8 hours experience in building my own drivers... all 8 hours spent on this so far.  I'm hoping that one of you all will see a line that means something to you.

I've also attached my TWDrvSources.tgz and the .spec file in a ZIP if anyone would like to take a look and cross check the additions that needed to be made.  For the .c file, I commented when I began and ended an addition.

---

### Post by KuroSatsu on 2008-04-19
...wow, ubuntu is now randomly detecting the LCD and i can move the mouse around a little.  i see the module usbtouchscreen working...but it needs to be calibrated.  I'll update if i can figure out how to calibrate it now even though I didn't install it properly.

---

### Post by rmrf on 2008-04-30
did you ever find a program for calibrating the screen?

---

### Post by plusbryan on 2008-06-08
> **KuroSatsu said:**
> ...wow, ubuntu is now randomly detecting the LCD and i can move the mouse around a little.  i see the module usbtouchscreen working...but it needs to be calibrated.  I'll update if i can figure out how to calibrate it now even though I didn't install it properly.

did you ever get this working?

---

