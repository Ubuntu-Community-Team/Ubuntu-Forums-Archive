---
title: "V4L-DVB syntax error"
date: 2014-11-27
forum: Hardware
---

### Post by Aleksandar_M on 2014-11-27
Hi,

I am using Ubutnu 14.04lts and while trying to compile media modules ( git://linuxtv.org/media_build.git)  [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers) I encountered the problem with running 


make menuconfig

```
./Kconfig:491: syntax error
./Kconfig:490: unknown option "Say"
./Kconfig:491: unknown option "To"
./Kconfig:492: unknown option "called"
./Kconfig:495: syntax error
./Kconfig:494:warning: multi-line strings not supported
./Kconfig:494: unknown option "If"
./Kconfig:762: syntax error
./Kconfig:761: unknown option "Say"
./Kconfig:762: unknown option "which"
./Kconfig:763: unknown option "The"
./Kconfig:766: syntax error
./Kconfig:765:warning: multi-line strings not supported
./Kconfig:765: unknown option "If"
```

Please help.

---

### Post by Tr4sHCr4fT on 2015-04-06
i have the exact same problem, but starting with line 762

"make xconfig" fails too! Ubuntu 14 64bit on Amazon EC2.

---

### Post by Tr4sHCr4fT on 2015-04-06
```

ubuntu@***:~/media_build$ sudo make menuconfig
make -C /home/ubuntu/media_build/v4l menuconfig
make[1]: Entering directory `/home/ubuntu/media_build/v4l'
make -C /lib/modules/3.13.0-44-generic/build -f /home/ubuntu/media_build/v4l/Makefile.kernel config-targets=1 mixed-targets=0 dot-config=0 SRCDIR=/lib/modules/3.13.0-44-generic/build v4l-mconf
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-44-generic'
make -f /lib/modules/3.13.0-44-generic/build/scripts/Makefile.build obj=scripts/kconfig hostprogs-y=mconf scripts/kconfig/mconf
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
  HOSTCC  scripts/kconfig/lxdialog/inputbox.o
  HOSTCC  scripts/kconfig/lxdialog/menubox.o
  HOSTCC  scripts/kconfig/lxdialog/textbox.o
  HOSTCC  scripts/kconfig/lxdialog/util.o
  HOSTCC  scripts/kconfig/lxdialog/yesno.o
  HOSTCC  scripts/kconfig/mconf.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/mconf
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-44-generic'
/lib/modules/3.13.0-44-generic/build/scripts/kconfig/mconf ./Kconfig
./Kconfig:778: syntax error
./Kconfig:777: unknown option "Say"
./Kconfig:778: unknown option "which"
./Kconfig:779: unknown option "The"
./Kconfig:782: syntax error
./Kconfig:781:warning: multi-line strings not supported
./Kconfig:781: unknown option "If"
make[1]: *** [menuconfig] Error 1
make[1]: Leaving directory `/home/ubuntu/media_build/v4l'
make: *** [menuconfig] Error 2

```

---

