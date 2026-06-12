---
title: "I ask about Marvell Yukon driver"
date: 2010-02-19
forum: Hardware
---

### Post by tatung on 2010-02-19
Hi,
My problem is that I can use the wired internet in Windows 7 but in Ubuntu 9.10, the wired internet is not working. I thought may be there are something with the LAN card driver so I tried to install the driver provided by Marvell Yukon (my LAN card is Marvell Yukon 88E8057). I follow the suggestion from posst #9 in this thread
[http://ubuntuforums.org/showthread.php?t=885882&highlight=marvell+yukon+88e8057](http://ubuntuforums.org/showthread.php?t=885882&highlight=marvell+yukon+88e8057)
The installing is ok untill the step it said that I have another driver for the LAN already installed in Ubuntu, so I choose to deactivate it, and now I stuck here (sorry for my long quote):
```

 Do nothing:
  - The sk98lin will be installed
  NOTE: It may happen that the alternative driver will be loaded on 
  the next boot process. In this case the Marvell driver _WON'T_ be
  loaded.

Deactivate driver:
  - The alternative driver will be renamed to _skge.ko or _sky2.ko
  - All references in the /etc/modprobe.conf file will be changed to
    the sk98lin driver
  - The alternative driver will be unloaded
  - The sk98lin driver will be installed

Remove driver (recommended):
  - The alternative driver will be removed from your system
  - All references in the /etc/modprobe.conf file will be changed to
    the sk98lin driver
  - The alternative driver will be unloaded
  - The sk98lin driver will be installed


1) Do nothing
2) Deactivate diver
3) Remove driver
Action: 2

Disconnect alternative devices:  (done)                              [   OK   ]
Unload alternative driver (done)                                     [   OK   ]
Create tmp dir (/tmp/Sk98IIUfGgRFrNSrcqQGWbLCB)                      [   OK   ]
Check user id (0)                                                    [   OK   ]
Check kernel version (2.6.31-19-generic)                             [   OK   ]
Check kernel symbol file (/proc/kallsyms)                            [   OK   ]
Check kernel type (SMP)                                              [   OK   ]
Check number of CPUs (2)                                             [   OK   ]
Check architecture (found)                                           [   OK   ]
Set architecture (i386)                                              [   OK   ]
Check compiler (/usr/bin/gcc)                                        [   OK   ]
Check mcmodel flags (none)                                           [   OK   ]
Check module support (/sbin/insmod)                                  [   OK   ]
Check make (/usr/bin/make)                                           [   OK   ]
Check kernel gcc version (4.4.1) (Kernel:4.4.1 == gcc:4.4.1)         [   OK   ]
Check sk98lin driver availability (not loaded)                       [   OK   ]
Check kernel header files (/lib/modules/2.6.31-19-generic/build)     [   OK   ]
Check sources for .config file (none)                                [   OK   ]
Execute: make mrproper                                                 working./functions: line 1330: cd: /lib/modules/2.6.31-19-generic/source: No such file or directory
Execute: make mrproper (done)                                        [   OK   ]
Execute: make config                                                   working./functions: line 1555: cd: /lib/modules/2.6.31-19-generic/source: No such file or directory
Execute: make config (done)                                          [   OK   ]
cp: cannot stat `/lib/modules/2.6.31-19-generic/source/.config': No such file or directory
Copy and check .config file                                            workingcp: cannot stat `/lib/modules/2.6.31-19-generic/source/.config': No such file or directory
cp: cannot stat `/lib/modules/2.6.31-19-generic/source/.config': No such file or directory
grep: /tmp/Sk98IIUfGgRFrNSrcqQGWbLCB/config: No such file or directory
./functions: line 603: [: -gt: unary operator expected
sed: can't read /tmp/Sk98IIUfGgRFrNSrcqQGWbLCB/config: No such file or directory
Copy and check .config file (done)                                   [   OK   ]
Check the mem address space (lowmem)                                 [   OK   ]
Change IOMMU (enabled)                                               [   OK   ]
Create new .config filecp: cannot create regular file `/lib/modules/2.6.31-19-generic/source/.config': No such file or directory
 (done)                                                              [   OK   ]
diff: /tmp/Sk98IIUfGgRFrNSrcqQGWbLCB/config-bk2: No such file or directory
diff: /lib/modules/2.6.31-19-generic/source/.config: No such file or directory
[COLOR=red]Check modpost availability (not available)                           [  warn  ][/COLOR]

The kernel's modpost utility is not available. Addtionally we did not
even find the source code for the utility. For this situation it exists
only one reason: your kernel source tree is corrupted.

You may continue to check for the modpost.c file below the directory
/usr/src/linux/scripts/mod. Normally you should find here also a binary
called modpost. Both seem to be missing.

Please contact your distribution vendor or download a kernel from
kernel.org to build your own kernel manually. It then will contain the
missing utility.

```Does anyone has the idea for this? Thanks

---

### Post by Odur on 2010-03-17
Please see this post: [http://ubuntuforums.org/showpost.php?p=8982066&postcount=4](http://ubuntuforums.org/showpost.php?p=8982066&postcount=4)

---

### Post by soulitude on 2010-07-04
Odur,

I get the very same error as tatung while trying to install sk98lin driver on ubuntu 9.10, with ethernet Marvell Yukon ethernet card. That is modpost.c unavailable and interestingly the file is there in the mentioned directory.

Did you get to face the same error in the first place? that is before making that change from /source to /build on fuctions file? Please get back to me, i need a solution to this its driving me crazy.

---

### Post by soulitude on 2010-07-04
Tatung,

Did you fix that issue? what did you do for it?  If yes could you get back with the steps? Thanks in advace.

---

### Post by tatung on 2010-07-04
@soulitude: infact, I still get problem with this in wired LAN network. But I've install ubuntu 10.04, and moved to another house with broadband network, so it's ok now.

---

### Post by colin.p on 2010-07-04
This might not make any difference, but try 10.04. I have a Dell 1545 with a Marvel Yukon card and it installed correctly on a fresh install, no configuration needed at all.
As an aside, my wireless Dell 1397 (BCM4312 Broadcom) works great as well.
I must say that on two separate machines, a desktop and a laptop, lucid just works. Boring actually.

Colin

---

### Post by soulitude on 2010-07-05
Thanks a lot Tatung and Colin.p for getting back, i appreciate your concerns.

@Tatung : This is with my new sony vaio laptop and the default driver was sky2 which randomly crashed both with 9.10 and 10.04. I now somehow managed to install sk98lin on 9.10, after a guy from Marvell semiconductors confirmed it as the driver for linux 2.6.31 kernel. But eth0 is not displayed. The driver can't even identify the eth0. 

I am sure the issue is with the driver and my ethernet card. The cable is good as well as the connection. Do you have any idea on what driver I can use for this besides sky2 and sk98lin? Please give me these outputs from your machine.
"sudo ethtool -i eth0"
"sudo lspci | grep -i ethernet"

@Colin.p : i've even tried 10.04 but with the same trouble of sky2 randomly disconnecting every 5 seconds. You said that you are using sky2 driver, can you please get back to me with the folllowing informations?
"sudo ethtool -i eth0"
"sudo lspci | grep -i ethernet"

Thanks a lot guys.;)

---

### Post by tatung on 2010-07-05
Sorry, I dont have any suggestion about the driver. Anyway, the output:
```

tatung@tatung-laptop:~$ sudo ethtool -i eth0
[sudo] password for tatung: 
sudo: ethtool: command not found
tatung@tatung-laptop:~$ sudo lspci | grep -i ethernet
08:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)

```

Hope this help!:D

---

### Post by soulitude on 2010-07-05
tatung,

You are a pal, thnx for getting back. Its good that we both have the  same Marvell ethernet card 4380(rev 10). I need your patience and time to work this out. I assume you haven't installed sk98lin and you are still running on sky2.

I am sure this isn't about the broadband connection but the new kernel ubuntu 10.04 must be the one that got it working for you. So a comparison between our configurations could get my eth0 running. You don't have "ethtool" installed on your machine, so you will have to install that first. Can you try this and then execute the command?
1. "sudo apt-get install ethtool"  and then "sudo ethtool -i eth0"
2. lsmod | grep sk

Thanks again tatung, tc.;)

---

### Post by tatung on 2010-07-07
@soulitude: :D this is the output
```

tatung@tatung-laptop:~$ sudo ethtool -i eth0
driver: sky2
version: 1.25
firmware-version: N/A
bus-info: 0000:08:00.0
tatung@tatung-laptop:~$ lsmod | grep sk
sky2                   41040  0 
tatung@tatung-laptop:~$ 


```

---

### Post by mathia on 2010-09-17
Hi,

**[B]Installing Marvell Yukon 88E8057 driver on Ubuntu**:[/B]

Please install the following driver as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8057 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices	Linux 2.6 - Fedora v10.85.9.3

 $ sudo bash ./install.sh

and let me know if it works.

Have a lot of fun ...:razz:

---

### Post by soulitude on 2010-09-18
mathia,

Thank you for writing. I have tried that but with no good result. And I can't say my compilation was perfect, cause some things were missing. I am hoping to try again soon. Will let you know the result of the fresh install.

I managed to get a USB modem, that kept me busy and ignore cable modem for a while. But i can't forever, ethernet port is very imp.

Are you having the same card and driver? working fine? 

Any idea on Ubuntu's support for this driver in the 10.10 version? the scheduled one i mean.

---

### Post by mathia on 2010-09-18
> **soulitude said:**
> mathia,

Thank you for writing. I have tried that but with no good result. And I can't say my compilation was perfect, cause some things were missing. I am hoping to try again soon. Will let you know the result of the fresh install.

I managed to get a USB modem, that kept me busy and ignore cable modem for a while. But i can't forever, ethernet port is very imp.

Are you having the same card and driver? working fine? 

Any idea on Ubuntu's support for this driver in the 10.10 version? the scheduled one i mean.

Hi soulitude,
please post install.log file from /DriverInstall directory to see what is missing on your system?

---

### Post by snisarg on 2010-12-16
i am having a similar problem. Every time i try to connect using DSL, it tells me wired network is disconnected. I have to repeat the process several times, and, if lucky get connected. Using Marvell yukon 88E8059.

i tried installing the drivers from the website, but when i select 1. for installation, it gives me an error at 'compiling the kernel'
------------------------------------------------------
1) Do nothing
2) Deactivate diver
3) Remove driver
Action: 2

Disconnect alternative devices:  (done)                              [   OK   ]
Unload alternative driver (done)                                     [   OK   ]
Create tmp dir (/tmp/Sk98ImZgMPnSjZmLPHnXdZJhX)                      [   OK   ]
Check user id (0)                                                    [   OK   ]
Check kernel version (2.6.35-22-generic)                             [   OK   ]
Check kernel symbol file (/proc/kallsyms)                            [   OK   ]
Check kernel type (SMP)                                              [   OK   ]
Check number of CPUs (4)                                             [   OK   ]
Check architecture (found)                                           [   OK   ]
Set architecture (i386)                                              [   OK   ]
Check compiler (/usr/bin/gcc)                                        [   OK   ]
Check mcmodel flags (none)                                           [   OK   ]
Check module support (/sbin/insmod)                                  [   OK   ]
Check make (/usr/bin/make)                                           [   OK   ]
Check kernel gcc version (4.4.5) (Kernel:4.4.5 == gcc:4.4.5)         [   OK   ]
Check sk98lin driver availability (not loaded)                       [   OK   ]
Check kernel header files (/lib/modules/2.6.35-22-generic/build)     [   OK   ]
Check sources for .config file (/lib/modules/2.6.35-22-generic/build/[   OK   ]
Copy and check .config file (done)                                   [   OK   ]
Check the mem address space (highmem)                                [   OK   ]
Change IOMMU (disabled)                                              [   OK   ]
Create new .config file (done)                                       [   OK   ]
Execute: make oldconfig (done)                                       [   OK   ]
Check modpost availability (available)                               [   OK   ]
Unpack the sources (done)                                            [   OK   ]
Check firmware availability (done)                                   [   OK   ]
Check kernel header version (not recognized)                         [  warn  ]
Check kernel functions (Changed: nothing)                            [   OK   ]
Compile the kernel (error)                                           [ failed ]

An error has occurred during the compile proces which prevented 
the installation from completing.                              
Take a look at the log file install.log for more informations.  
Installation of package failed.
--------------------------------------------------

i am new to linux as a whole, so please help!

---

### Post by va_ko on 2010-12-27
> **mathia said:**
> Hi soulitude,
please post install.log file from /DriverInstall directory to see what is missing on your system?
```

+++ Install mode: User
+++ Driver version: 10.85.9.3 (Aug-13-2010)
+++ Kernel version 2.6.36.2-some-try
+++ smp_count=1
+++ cpu_number=4
+++ kernel_machine=i686
+++ Architecture: i386
+++ modpost available
+++ Unpack the sources
+++ ====================================
+++ tar xfv sk98lin.tar
2.6/
2.6/sky2.c
2.6/skethtool.c
2.6/skproc.c
2.6/Makefile
2.6/skge.c
2.6/h/
2.6/h/skdrv1st.h
2.6/h/skdrv2nd.h
2.6/skdim.c
common/
common/skaddr.c
common/fwos.c
common/skgeinit.c
common/skgehwt.c
common/skspi.c
common/sk98lin.htm
common/fwapp.c
common/sktimer.c
common/fwhci.c
common/fwptrn.c
common/flashfun.c
common/fwfunctions.c
common/skgemib.c
common/vpdcheck.c
common/skvpd.c
common/skpflash.c
common/sky2le.c
common/fwimage.c
common/fwoids.c
common/skgesirq.c
common/sk98lin.4
common/fwmain.c
common/sktwsi.c
common/skgepnmi.c
common/sklm80.c
common/skgespilole.c
common/skxmac2.c
common/sk98lin.txt
common/h/
common/h/sktimer.h
common/h/fwimage.h
common/h/sktypes.h
common/h/fwptrn.h
common/h/skdebug.h
common/h/skaddr.h
common/h/skversion.h
common/h/skgeasfapi.h
common/h/lm80.h
common/h/skvpd.h
common/h/skgetwsi.h
common/h/skgeinit.h
common/h/skgesirq.h
common/h/skpflash.h
common/h/skqueue.h
common/h/fwoids.h
common/h/skcsum.h
common/h/skgepnm2.h
common/h/skspi.h
common/h/fwapp.h
common/h/skpcidevid.h
common/h/fwos.h
common/h/mvyexhw.h
common/h/sktwsi.h
common/h/fwmain.h
common/h/xmac_ii.h
common/h/fwhci.h
common/h/skgehw.h
common/h/skgedrv.h
common/h/sky2le.h
common/h/skgepnmi.h
common/h/flash.h
common/h/fwcommon.h
common/h/skgehwt.h
common/h/skerror.h
common/skqueue.c
common/skgeasfapi.c
common/skcsum.c
misc/
misc/Kconfig
misc/Configure.help

+++ Compile the driver
+++ ====================================
make: &#1042;&#1093;&#1086;&#1076; &#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; `/home/vaio/src/linux-2.6.36.2'
make -C /lib/modules/2.6.36.2-some-try/build \
    KBUILD_SRC=/home/vaio/src/linux-2.6.36.2 \
    KBUILD_EXTMOD=&quot;/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all&quot; -f /home/vaio/src/linux-2.6.36.2/Makefile \
    
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo &quot;  ERROR: Kernel configuration is invalid.&quot;;        \
    echo &quot;         include/generated/autoconf.h or include/config/auto.conf are missing.&quot;;\
    echo &quot;         Run 'make oldconfig && make prepare' on kernel src to fix it.&quot;;    \
    echo;                                \
    /bin/false)
mkdir -p /tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/.tmp_versions ; rm -f /tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/.tmp_versions/*
make -f /home/vaio/src/linux-2.6.36.2/scripts/Makefile.build obj=/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all
   rm -f /tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/built-in.o; ar rcs /tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/built-in.o
  cc -Wp,-MD,/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/.skge.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include -I/home/vaio/src/linux-2.6.36.2/arch/x86/include -Iinclude  -I/home/vaio/src/linux-2.6.36.2/include -include include/generated/autoconf.h   -I/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -g -femit-struct-debug-baseonly -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack   -I/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE  -D&quot;KBUILD_STR(s)=#s&quot; -D&quot;KBUILD_BASENAME=KBUILD_STR(skge)&quot;  -D&quot;KBUILD_MODNAME=KBUILD_STR(sk98lin)&quot;  -c -o /tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/.tmp_skge.o /tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/skge.c
  cc -Wp,-MD,/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/.sky2.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include -I/home/vaio/src/linux-2.6.36.2/arch/x86/include -Iinclude  -I/home/vaio/src/linux-2.6.36.2/include -include include/generated/autoconf.h   -I/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -g -femit-struct-debug-baseonly -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack   -I/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE  -D&quot;KBUILD_STR(s)=#s&quot; -D&quot;KBUILD_BASENAME=KBUILD_STR(sky2)&quot;  -D&quot;KBUILD_MODNAME=KBUILD_STR(sk98lin)&quot;  -c -o /tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/.tmp_sky2.o /tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/sky2.c
  cc -Wp,-MD,/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/.skethtool.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include -I/home/vaio/src/linux-2.6.36.2/arch/x86/include -Iinclude  -I/home/vaio/src/linux-2.6.36.2/include -include include/generated/autoconf.h   -I/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -g -femit-struct-debug-baseonly -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack   -I/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE  -D&quot;KBUILD_STR(s)=#s&quot; -D&quot;KBUILD_BASENAME=KBUILD_STR(skethtool)&quot;  -D&quot;KBUILD_MODNAME=KBUILD_STR(sk98lin)&quot;  -c -o /tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/.tmp_skethtool.o /tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/skethtool.c
  cc -Wp,-MD,/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/.sky2le.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include -I/home/vaio/src/linux-2.6.36.2/arch/x86/include -Iinclude  -I/home/vaio/src/linux-2.6.36.2/include -include include/generated/autoconf.h   -I/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -g -femit-struct-debug-baseonly -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack   -I/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE  -D&quot;KBUILD_STR(s)=#s&quot; -D&quot;KBUILD_BASENAME=KBUILD_STR(sky2le)&quot;  -D&quot;KBUILD_MODNAME=KBUILD_STR(sk98lin)&quot;  -c -o /tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/.tmp_sky2le.o /tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/sky2le.c
/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/skge.c: In function ‘SkGeSetRxMode’:
/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/skge.c:4497: error: ‘struct net_device’ has no member named ‘mc_list’
/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/skge.c:4498: error: ‘struct net_device’ has no member named ‘mc_count’
/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/skge.c:4498: error: dereferencing pointer to incomplete type
/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/skge.c:4500: error: dereferencing pointer to incomplete type
make[2]: *** [/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/skge.o] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[2]: *** &#1054;&#1078;&#1080;&#1076;&#1072;&#1085;&#1080;&#1077; &#1079;&#1072;&#1074;&#1077;&#1088;&#1096;&#1077;&#1085;&#1080;&#1103; &#1079;&#1072;&#1076;&#1072;&#1085;&#1080;&#1081;...
  set -e ; perl /home/vaio/src/linux-2.6.36.2/scripts/recordmcount.pl &quot;i386&quot; &quot;little&quot; &quot;32&quot; &quot;objdump&quot; &quot;objcopy&quot; &quot;cc&quot; &quot;ld&quot; &quot;nm&quot; &quot;&quot; &quot;&quot; &quot;1&quot; &quot;/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/sky2le.o&quot;;
  set -e ; perl /home/vaio/src/linux-2.6.36.2/scripts/recordmcount.pl &quot;i386&quot; &quot;little&quot; &quot;32&quot; &quot;objdump&quot; &quot;objcopy&quot; &quot;cc&quot; &quot;ld&quot; &quot;nm&quot; &quot;&quot; &quot;&quot; &quot;1&quot; &quot;/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/skethtool.o&quot;;
  set -e ; perl /home/vaio/src/linux-2.6.36.2/scripts/recordmcount.pl &quot;i386&quot; &quot;little&quot; &quot;32&quot; &quot;objdump&quot; &quot;objcopy&quot; &quot;cc&quot; &quot;ld&quot; &quot;nm&quot; &quot;&quot; &quot;&quot; &quot;1&quot; &quot;/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all/sky2.o&quot;;
make[1]: *** [_module_/tmp/Sk98ISAUNbiZWnOmmqkafIiAm/all] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
make: *** [sub-make] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
make: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/home/vaio/src/linux-2.6.36.2'
+++ Compiler error

```

---

### Post by va_ko on 2010-12-28
I solve my problem in following way:
Ubuntu 10.10 2.6.36.2 kernel
in skge.c replace / add following code
```

 
-            struct dev_mc_list    *pMcList;*/
+           struct netdev_hw_addr    *ha; [INDENT]int            i; 
............

            ("Number of MC entries: %d ", dev->mc_count)); 
         
-       pMcList = dev->mc_list; 
-        for (i=0; i<dev->mc_count; i++, pMcList = pMcList->next) { 
-            SkAddrMcAdd(pAC, pAC->IoBase, PortIdx, 
-                (SK_MAC_ADDR*)pMcList->dmi_addr, 0); 
-            SK_DBG_MSG(NULL, SK_DBGMOD_DRV, SK_DBGCAT_DRV_MCA, 
-                ("%02x:%02x:%02x:%02x:%02x:%02x\n", 
-                pMcList->dmi_addr[0], 
-                pMcList->dmi_addr[1], 
-                pMcList->dmi_addr[2], 
-                pMcList->dmi_addr[3], 
-                pMcList->dmi_addr[4], 
-                pMcList->dmi_addr[5])); 
-        }

+        i=0; 
+        netdev_for_each_mc_addr (ha, dev){ 
+            SkAddrMcAdd(pAC, pAC->IoBase, PortIdx, 
+                (SK_MAC_ADDR*)ha->addr, 0); 
+            SK_DBG_MSG(NULL, SK_DBGMOD_DRV, SK_DBGCAT_DRV_MCA, 
+                ("%02x:%02x:%02x:%02x:%02x:%02x\n")); 
+            i++; 
+        } 
 
        SkAddrMcUpdate(pAC, pAC->IoBase, PortIdx);
[/INDENT]
```I don't know about multicast, but at least, i've got wired iNet on my notebook

---

