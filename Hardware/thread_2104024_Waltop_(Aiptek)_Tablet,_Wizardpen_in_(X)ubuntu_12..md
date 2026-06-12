---
title: "Waltop (Aiptek) Tablet, Wizardpen in (X)ubuntu 12.04"
date: 2013-01-11
forum: Hardware
---

### Post by yulie on 2013-01-11
I've red a lot around this issue and I guess it's not to solve, as the Waltop  Slim Tablet 12.1 (or Aiptek 600u) isn't supported in Ubuntu 12.04. Does anybody know if there will be a solution in the nearest future or would it be better to send the tablet back?

Last thing I wanted to try was to install wizardpen, but after the first steps worked well, but make and make install did not work. Sorry, that's a long story, but maybe someone can help me:

make[1]: Betrete Verzeichnis '/home/julia/Downloads/xorg-input-wizardpen-0.8.0'
Making all in src
make[2]: Betrete Verzeichnis '/home/julia/Downloads/xorg-input-wizardpen-0.8.0/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -fvisibility=hidden -I/usr/include/pixman-1 -I/usr/include/xorg    -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c -o wizardpen.lo wizardpen.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -fvisibility=hidden -I/usr/include/pixman-1 -I/usr/include/xorg -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c wizardpen.c  -fPIC -DPIC -o .libs/wizardpen.o
In file included from wizardpen.c:77:0:
wizardpen.h:134:1: warning: parameter names (without types) in function declaration [enabled by default]
wizardpen.h:138:54: error: unknown type name 'IDevPtr'
wizardpen.h:141:5: warning: parameter names (without types) in function declaration [enabled by default]
wizardpen.h:142:5: warning: parameter names (without types) in function declaration [enabled by default]
wizardpen.h:144:55: error: expected ')' before 'int'
wizardpen.c:98:5: error: 'WizardPenPreInit' undeclared here (not in a function)
wizardpen.c:200:23: error: unknown type name 'LocalDevicePtr'
wizardpen.c:301:38: error: unknown type name 'IDevPtr'
wizardpen.c: In function 'DeviceOn':
wizardpen.c:602:5: error: unknown type name 'LocalDevicePtr'
wizardpen.c:602:29: error: 'LocalDevicePtr' undeclared (first use in this function)
wizardpen.c:602:29: note: each undeclared identifier is reported only once for each function it appears in
wizardpen.c:602:45: error: expected ',' or ';' before 'dev'
wizardpen.c:603:60: error: invalid type argument of '->' (have 'int')
wizardpen.c:605:51: error: invalid type argument of '->' (have 'int')
wizardpen.c:607:10: error: invalid type argument of '->' (have 'int')
wizardpen.c:607:37: error: invalid type argument of '->' (have 'int')
wizardpen.c:608:14: error: invalid type argument of '->' (have 'int')
wizardpen.c:610:74: error: invalid type argument of '->' (have 'int')
wizardpen.c:610:107: error: invalid type argument of '->' (have 'int')
wizardpen.c:614:18: error: invalid type argument of '->' (have 'int')
wizardpen.c:614:45: error: invalid type argument of '->' (have 'int')
wizardpen.c:615:18: error: invalid type argument of '->' (have 'int')
wizardpen.c:623:37: error: invalid type argument of '->' (have 'int')
wizardpen.c:626:34: error: invalid type argument of '->' (have 'int')
wizardpen.c:627:18: error: invalid type argument of '->' (have 'int')
wizardpen.c:636:25: error: invalid type argument of '->' (have 'int')
wizardpen.c:637:5: warning: passing argument 1 of 'xf86AddEnabledDevice' makes pointer from integer without a cast [enabled by default]
/usr/include/xorg/xf86Xinput.h:154:23: note: expected 'InputInfoPtr' but argument is of type 'int'
wizardpen.c: In function 'DeviceOff':
wizardpen.c:645:5: error: unknown type name 'LocalDevicePtr'
wizardpen.c:645:29: error: 'LocalDevicePtr' undeclared (first use in this function)
wizardpen.c:645:45: error: expected ',' or ';' before 'dev'
wizardpen.c:646:60: error: invalid type argument of '->' (have 'int')
wizardpen.c:648:52: error: invalid type argument of '->' (have 'int')
wizardpen.c:650:14: error: invalid type argument of '->' (have 'int')
wizardpen.c:652:35: error: invalid type argument of '->' (have 'int')
wizardpen.c:658:30: error: invalid type argument of '->' (have 'int')
wizardpen.c:662:5: warning: passing argument 1 of 'xf86RemoveEnabledDevice' makes pointer from integer without a cast [enabled by default]
/usr/include/xorg/xf86Xinput.h:155:23: note: expected 'InputInfoPtr' but argument is of type 'int'
wizardpen.c: In function 'DeviceClose':
wizardpen.c:670:5: error: unknown type name 'LocalDevicePtr'
wizardpen.c:670:29: error: 'LocalDevicePtr' undeclared (first use in this function)
wizardpen.c:670:45: error: expected ',' or ';' before 'dev'
wizardpen.c:672:54: error: invalid type argument of '->' (have 'int')
wizardpen.c: In function 'ControlProc':
wizardpen.c:680:5: error: unknown type name 'LocalDevicePtr'
wizardpen.c:680:29: error: 'LocalDevicePtr' undeclared (first use in this function)
wizardpen.c:680:45: error: expected ',' or ';' before 'dev'
wizardpen.c:682:54: error: invalid type argument of '->' (have 'int')
wizardpen.c: In function 'DeviceInit':
wizardpen.c:689:5: error: unknown type name 'LocalDevicePtr'
wizardpen.c:689:29: error: 'LocalDevicePtr' undeclared (first use in this function)
wizardpen.c:689:45: error: expected ',' or ';' before 'dev'
wizardpen.c:690:60: error: invalid type argument of '->' (have 'int')
wizardpen.c:695:46: error: invalid type argument of '->' (have 'int')
wizardpen.c:711:83: error: invalid type argument of '->' (have 'int')
wizardpen.c:717:82: error: invalid type argument of '->' (have 'int')
wizardpen.c:722:68: error: invalid type argument of '->' (have 'int')
wizardpen.c:735:14: error: invalid type argument of '->' (have 'int')
wizardpen.c:738:85: error: invalid type argument of '->' (have 'int')
wizardpen.c:767:17: error: too few arguments to function 'InitValuatorAxisStruct'
/usr/include/xorg/exevents.h:59:23: note: declared here
wizardpen.c:777:17: error: too few arguments to function 'InitValuatorAxisStruct'
/usr/include/xorg/exevents.h:59:23: note: declared here
wizardpen.c:787:17: error: too few arguments to function 'InitValuatorAxisStruct'
/usr/include/xorg/exevents.h:59:23: note: declared here
wizardpen.c:799:86: error: invalid type argument of '->' (have 'int')
wizardpen.c:803:5: warning: passing argument 1 of 'xf86MotionHistoryAllocate' makes pointer from integer without a cast [enabled by default]
/usr/include/xorg/xf86Xinput.h:168:23: note: expected 'InputInfoPtr' but argument is of type 'int'
wizardpen.c:821:48: error: invalid type argument of '->' (have 'int')
wizardpen.c: At top level:
wizardpen.c:829:15: error: unknown type name 'LocalDevicePtr'
wizardpen.c:1234:12: error: unknown type name 'LocalDevicePtr'
wizardpen.c:1284:19: error: unknown type name 'LocalDevicePtr'
make[2]: *** [wizardpen.lo] Fehler 1
make[2]: Verlasse Verzeichnis '/home/julia/Downloads/xorg-input-wizardpen-0.8.0/src'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/julia/Downloads/xorg-input-wizardpen-0.8.0'
make: *** [all] Fehler 2 </code>

---

### Post by Favux on 2013-01-11
Hi yulie,

Welcome to Ubuntu forums!


Your tablet should work out of the box in Precise, see:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

Let's verify what tablet you have by looking at the output of:
```
lsusb
```
in a terminal.  Also what is the output of?
```
xinput list
```

You shouldn't have to compile WizardPen, but instructions for that are here:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_WizardPen](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_WizardPen)

---

