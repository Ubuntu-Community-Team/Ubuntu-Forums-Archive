---
title: "3M Touchdriver Installation"
date: 2010-06-13
forum: Hardware
---

### Post by koalauk on 2010-06-13
Hi there to everyone,

After spending the entire weekend I thought it was time to ask for a help.

Trying to install 3m touchware serial controller drivers for the Ubuntu Netbook edition I have,

I downloaded the linux drivers from the 3M site.
It was a .bin file which I managed to run the correct commands to g create a tar.gz file and then I run command 

tar xzvf twscreen.7.12.5.tar.gz -C /opt

whioch first didnt work and kept reading on the internet and managed to change chmod for the file directories etc and I got the command to work

Run install script: /opt/twscreen/Install

brings out this result

root@ubuntu:/opt/twscreen# /opt/twscreen/Install
update-rc.d: warning: /etc/init.d/TWDrvStartup missing LSB keyword 'required-start'

update-rc.d: warning: /etc/init.d/TWDrvStartup missing LSB keyword 'required-stop'

update-rc.d: warning: TWDrvStartup start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (2 5)
update-rc.d: warning: TWDrvStartup stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (0 1 3 4 6)
root@ubuntu:/opt/twscreen# 
AND here is the  TWDrvStartup


#!/bin/bash
#
# Copyright 2003-2009 3M. All rights reserved.
#
# TWDrvStartup
#
# Author: 3M Touch Systems, Inc., Methuen, MA 01488 USA
#
# processname: TWDrvStartup
# chkconfig: 5 20 05
# description: Installs X input driver for the MicroTouch MT 7 Software system
#
### BEGIN INIT INFO
# Provides: TwDriver
# Default-Start: 2 5
# Default-Stop: 0 1 3 4 6
# Description: Start the MT 7 touch screen driver
### END INIT INFO

#
# Define the install scripts
#
TWDRV_STARTSTOP=""
if test -f /etc/init.d/functions
then
   . /etc/init.d/functions
   START_DAEMON=daemon
   CHECK_STATUS=status
elif test -f /etc/init.d/functions
then
   . /etc/init.d/functions
   START_DAEMON=daemon
   CHECK_STATUS=status
elif test -f /lib/lsb/init-functions
then
   . /lib/lsb/init-functions
   START_DAEMON=start_daemon
   CHECK_STATUS=checkproc
elif perl /opt/twscreen/TwIsThere.perl start-stop-daemon
then
   TWDRV_STARTSTOP="1"
else
   START_DAEMON=""
   CHECK_STATUS=""
fi

TWDRV_OPTIONS=""

#
# Make sure everything is there
#
[ -d /opt/twscreen ] || exit 5
[ -x /opt/twscreen/TwDriver ] || exit 5
[ -x /opt/twscreen/TWXinputInstall.perl ] || exit 5

#
# Do what we were asked to do
#
case "$1" in
   start)
      echo "Starting TwDriver"
      /opt/twscreen/TWXinputInstall.perl
      [ x != x ] && [ -r  ] && . 
      [ -d /dev/shm ] && rm -f /dev/shm/*TwConfig*
      if [ -z $TWDRV_STARTSTOP ]
      then
         $START_DAEMON /opt/twscreen/TwDriver $TWDRV_OPTIONS
      else
         [ x$TWDRV_OPTIONS != x ] && TWDRV_OPTIONS="-- $TWDRV_OPTIONS"
         start-stop-daemon --start --quiet --exec /opt/twscreen/TwDriver $TWDRV_OPTIONS
      fi
      RETVAL=$?
      ;;
   stop)
      echo "Stopping TwDriver"
      /opt/twscreen/TwDriver stop
      sleep 1
      if [ -z $TWDRV_STARTSTOP ]
      then
         killproc /opt/twscreen/TwDriver -TERM
      else
         start-stop-daemon --stop -oknodo --quit --exec /opt/twscreen/TwDriver
      fi
      RETVAL=$?
      /opt/twscreen/TWXinputInstall.perl -remove
      ;;
   status)
      echo "Checking for TwDriver"
      if [ -z $TWDRV_STARTSTOP ] && [ ! -z $CHECK_STATUS ]
      then
         /opt/twscreen/TwDriver
         RETVAL=$?
      else
         RETVAL=0
      fi
      ;;
   restart)
      $0 stop
      $0 start
      RETVAL=$?
      ;;
   try-restart)
      $0 status
      if test $? = 0
      then
         $0 restart
         RETVAL=$?
      else
         RETVAL=0
      fi
      ;;
   *)
      echo "Usage: $0 {start|stop|status|restart|try-restart}"
      exit 1
esac

exit $RETVAL

Unfortunately I HAVE NO idea what it needs changing in order to get the installation work :(

Please HELP :)

I was all excited but now feeling rather useless :(

Thanks for your help

---

### Post by koalauk on 2010-06-13
Just incase if it helps this is the install file


#!/bin/bash
#
# Copyright 2007-2009 3M. All rights reserved.
#
# This script installs the MT7 touch screen driver
# During installation, all directories must be writeable.
#

# These symbols point to where the MT7 software binaries and data reside.
# The script attempts to detect where the installation kit is. If this
# fails, you need to set BinDir.
# The data directory must be on writeable media. The script normally uses
# the directory where the installation kit resides as the data directory.
# If you need the data directory to be elsewhere, set DataDir.
BinDir=""
DataDir=""

# If desired, define a file to contain driver startup options and set
# the TwDrv_Cfg symbol to the full path of the file. Normally this is
# not needed.
TwDrv_Cfg=""

# This symbol points to where the Java VM binaries reside.
JavaBinDir=""

# These symobls point to system and applictaion directories other than
# those specific to the MT7 software
UdevDir="/etc/udev"
HotplugDir="/etc/hotplug"
XorgDir="/usr/lib/xorg/modules/input"
XFree86Dir="/usr/X11R6/lib/modules/input"
LibDir="/usr/lib"
SEDir1="/usr/selinux/booleans"
SEDir2="/selinux/booleans"
LSBDir="/lib/lsb"

# The InitDir symbol points to where this script places an 'init' script.
# If left blank, this script first looks for /etc/init.d and then /etc/rc.d.
# If this is not appropriate or this script otherwise fails, set this value.
InitDir=""

# This symbol enables permission for some MT7 shared objects on
# SELinux systems. On most systems SEGivePermission is texrel_shlib_t.
# Change this variable if another security type is appropriate.
SEGivePermission="texrel_shlib_t"

# This symbol affects when the X input driver converts raw touch screen
# coordinates into screen coordiates. Normally, the X input driver reports
# the raw coordinates to the X server which then calls an conversion
# routine. Some versions of the X server expect the initial report to
# contain converted coordinates. If your touch behavior is off and
# calibration does not address the problem, set ConvertAtRead to true.
ConvertAtRead="false"

# This symbol defines the name of the xorg.conf file to generate if one is
# not found. Starting with X server version 1.5, this file is not
# automatically generated. This file is needed for MT 7 for Linux to work.
# If you want the file to reside elsewhere, set this symbol.
XorgConf="/etc/X11/xorg.conf"

# These symbols define where the 50MT7-xinit script needs to go and what
# suffix it requires. The script places this file automatically in
# /etc/X11/xinit/xinitrc.d and /etc/X11/Xsession.d without a suffix. If
# your distribution requires another location or requires a suffix on the
# file, set these symbols.
XinitDir=""
XinitSuffix=""

# Determine the installation directory
if [ -z $BinDir ]
then
   if [ $(echo $0 | grep ^/) ]
   then
      BinDir=$0
   else
      BinDir=$(echo $PWD"/"$0 | sed s#[.]/##)
   fi
   BinDir=$(echo $BinDir | sed s%/[^/]*$%%)
fi

# Determine if the system is compatible
$BinDir/TwCompat
if [ $? != 0 ]
then
   echo "ERROR: MT7 for Linux not installed - shared memory support not detected"
   exit
fi

# Determine the data directory
[ -z $DataDir ] && DataDir=$BinDir

# Create the data and fifo directories
if [ $DataDir != $BinDir ]
then
   [ -e $DataDir ] || mkdir $DataDir
   chmod a+w $DataDir
   ln -s $DataDir $BinDir/data
else
   [ -e $BinDir/data ] || mkdir $BinDir/data
fi
chmod a+w $BinDir/data
[ -e $BinDir/data/fifo ] || mkdir $BinDir/data/fifo
chmod a+w $BinDir/data/fifo

# Determine the init script directories
if [ -z $InitDir ] && [ -d /etc/init.d ]
then
   if [ $(ls -l /etc/init.d/ | sed -e /functions/d -e /^total\ [0-9]*$/d | wc -l) != 0 ]
   then
      InitDir="/etc/init.d"
   fi
fi
if [ -z $InitDir ]
then
   if [ -e /etc/rc.d/rc.local ]
   then
      InitDir=/etc/rc.d
   else
      InitDir=$BinDir
   fi
fi

# Install the init script
[ -e $InitDir/TWDrvStartup ] && rm -f $InitDir/TWDrvStartup
sed -e s#%BINDIR%#$BinDir#g \
    -e s#%INITDIR%#$InitDir#g \
    -e s#%LSBDIR%#$LSBDir#g \
    -e s#%TWDRV_CFG%#$TwDrv_Cfg#g $BinDir/TWDrvStartup.ORIG \
    >$InitDir/TWDrvStartup
chmod a+x $InitDir/TWDrvStartup
if perl $BinDir/TwIsThere.perl chkconfig
then
   chkconfig --add TWDrvStartup >/dev/null
elif perl $BinDir/TwIsThere.perl update-rc.d
then
   update-rc.d TWDrvStartup defaults >/dev/null
elif [ -e $InitDir/rc.local ]
then
   sed -e '$ a\
%INITDIR%/TWDrvStartup start
' $InitDir/rc.local >$InitDir/rc.local.TEMP
   rm -f $InitDir/rc.local
   sed -e s#%INITDIR%#$InitDir# $InitDir/rc.local.TEMP >$InitDir/rc.local
   rm -f $InitDir/rc.local.TEMP
   chmod +x $InitDir/rc.local
else
   echo "Cannot install the init script"
fi

# Test for USB support
if [ -z $(uname -r | grep ^2\.4\.) ]
then
   # Copy the udev rules script
   Hotplug=0
   if [ -d $UdevDir/rules.d ]
   then
      if [ -e $UdevDir/rules.d/99-TwDriver.rules ]
      then
         rm -f $UdevDir/rules.d/99-TwDriver.rules
      fi
      sed s#%BINDIR%#$BinDir#g $BinDir/99-TwDriver.rules.ORIG \
         >$UdevDir/rules.d/99-TwDriver.rules
      Hotplug=1
   fi
   if [ -d $HotplugDir/usb ] && [ -e $HotplugDir/usb.agent ]
   then
      [ -e $HotplugDir/usb/TwHotplug ] && rm -f $HotplugDir/usb/TwHotplug
      sed s#%BINDIR%#$BinDir#g $BinDir/TwHotplug.ORIG > $HotplugDir/usb/TwHotplug
      chmod a+x $HotplugDir/usb/TwHotplug
      [ -e $HotplugDir/usb.usermap ] || echo "# Created by MT7" >$HotplugDir/usb.usermap
      sed <$HotplugDir/usb.usermap >$HotplugDir/usb.usermap.TEMP '$ a\
# TwHotplug is for the MT7 for Linux software\
TwHotplug            0x0001      0x0596   0x0000    0x0000       0x0000      0x00         0x00            0x00            0x06            0x00               0x00               0x00000000
'
      rm -f $HotplugDir/usb.usermap
      mv $HotplugDir/usb.usermap.TEMP $HotplugDir/usb.usermap
      Hotplug=1
   fi
   if [ $Hotplug == 0 ]
   then
      echo "Hotplugging of USB touch screen controllers is not supported"
   fi
else
   echo "USB touch screen controllers are not supported under kernel 2.4"
fi

# Test for the version of C++ standard libraries
if [ -e $LibDir/libstdc++.so.6 ]
then
   CppExt="6"
elif [ -e $LibDir/libstdc++.so.5 ]
then
   CppExt="5"
else
   echo "Cannot find needed libstdc++.so in $LibDir"
   CppExt=""
fi

# Link the libraries into /usr/lib
perl $BinDir/TwLibInstall.perl install $LibDir $BinDir/lib*.so
if [ x$CppExt != x ]
then
   perl $BinDir/TwLibInstall.perl install $LibDir $BinDir/so$CppExt/lib*.so
fi

# Link RnR sensitive files
if [ x$CppExt != x ]
then
   $BinDir/TwLibTest $LibDir/libTwSystemRnR12.so
   if [ x$? != x0 ]
   then
      rm -f $LibDir/libTwSystem.so
      ln -s $LibDir/libTwSystemRnR12.so $LibDir/libTwSystem.so
      ln -s $BinDir/TwMonitorRnR.bin$CppExt $BinDir/TwMonitor
   else
      $BinDir/TwLibTest $LibDir/libTwSystemRnR.so
      if [ x$? != x0 ]
      then
         rm -f $LibDir/libTwSystem.so
         ln -s $LibDir/libTwSystemRnR.so $LibDir/libTwSystem.so
         ln -s $BinDir/TwMonitorRnR.bin$CppExt $BinDir/TwMonitor
      else
         ln -s $BinDir/TwMonitor.bin$CppExt $BinDir/TwMonitor
      fi
   fi
fi

# Copy the X input driver
XCopyDefault=0
if [ -d $XorgDir ]
then
   XDir=$XorgDir
   if [ -z "$(X -version 2>&1 | grep X\.Org[^1]*1\.[4-9]\.)" ]
   then
      XSrc=$BinDir/twxinput_drv.so
   elif [ -z "$(X -version 2>&1 | grep X\.Org[^1]*1\.[5-9]\.)" ]
   then
      XSrc=$BinDir/twxinput_drv.so.1.4
   else
      XSrc=$BinDir/twxinput_drv.so.1.5.1
      XCopyDefault=1
   fi
elif [ -d $XFree86Dir ]
then
   XDir=$XFree86Dir
   XSrc=$BinDir/twxinput_drv.so
else
   XDir=""
   echo "Cannot install the X input module"
fi
if [ -d $XDir ]
then
   [ -e $XDir/twxinput_drv.o ] && rm -f $XDir/twxinput_drv.o
   [ -e $XDir/twxinput_drv.so ] && rm -f $XDir/twxinput_drv.so
   ln -s $XSrc $XDir/twxinput_drv.so
fi

# Install the xinit scripts
if [ -d /etc/X11/xinit/xinitrc.d ]
then
   sed s#%BINDIR%#$BinDir#g $BinDir/50MT7-xinit.ORIG \
      >/etc/X11/xinit/xinitrc.d/50MT7-xinit$XinitSuffix
   chmod a+x /etc/X11/xinit/xinitrc.d/50MT7-xinit$XinitSuffix
fi
if [ -d /etc/X11/Xsession.d ]
then
   sed s#%BINDIR%#$BinDir#g $BinDir/50MT7-xinit.ORIG \
      >/etc/X11/Xsession.d/50MT7-xinit$XinitSuffix
   chmod a+x /etc/X11/Xsession.d/50MT7-xinit$XinitSuffix
fi
if [ x$XinitDir != x ]
then
   sed s#%BINDIR%#$BinDir#g $BinDir/50MT7-xinit.ORIG \
      >$XinitDir/50MT7-xinit$XinitSuffix
   chmod a+x $XinitDir/50MT7-xinit$XinitSuffix
fi

# Set up the SELinux security types
if [ -d $SEDir1 ]
then
   SEDir=$SEDir1
elif [ -d $SEDir2 ]
then
   SEDir=$SEDir2
else
   SEDir=""
fi
if [ x$SEDir != x ]
then
   chcon -t $SEGivePermission $LibDir/libTwSystem.so
   chcon -t $SEGivePermission $LibDir/libTwConfig.so
   chcon -t $SEGivePermission $LibDir/libTwIO_Utilities.so
   chcon -t $SEGivePermission $LibDir/libTwAppIO_JNI.so
   chcon -t $SEGivePermission $LibDir/libTwCommon_JNI.so
   chcon -t $SEGivePermission $LibDir/libTwConfig_JNI.so
   chcon -t $SEGivePermission $LibDir/libTwUI_JNI.so
   chcon -t $SEGivePermission $LibDir/libTwUICP.so
   [ -e $XDir/twxinput_drv.so ] && chcon -t $SEGivePermission $XDir/twxinput_drv.so
fi

# Set up the configuration
[ -d /dev/shm ] && rm -f /dev/shm/*TwConfig*
sed s#%BINDIR%#$BinDir#g $BinDir/TwFramework.cfg.ORIG >$BinDir/TwFramework.cfg
$BinDir/TwCfgUtil /u $BinDir/TwFramework.cfg
$BinDir/TwCfgUtil /u $BinDir/TwFactory.cfg

# Produce the Remove script
sed -e s#%BINDIR%#$BinDir#g \
    -e s#ÞVDIR%#$UdevDir#g \
    -e s#%XDIR%#$XDir#g \
    -e s#%LIBDIR%#$LibDir#g \
    -e s#%SEDIR%#$SEDir#g \
    -e s#%HOTPLUGDIR%#$HotplugDir#g \
    -e s#%INITDIR%#$InitDir#g \
    -e s#%XINITDIR%#$XinitDir#g \
    -e s#%XINITSUFFIX%#$XinitSuffix#g \
    $BinDir/Remove.ORIG >$BinDir/Remove

# Produce the X input script
sed -e s#%CONVERT%#$ConvertAtRead#g \
    $BinDir/TWXinputInstall.perl.ORIG >$BinDir/TWXinputInstall.perl

# Produce the CP start script
sed -e s#%JAVABINDIR%#$JavaBinDir#g \
    -e s#%BINDIR%#$BinDir# \
    $BinDir/StartCP.ORIG >$BinDir/StartCP

# Set any necessary permissions
chmod a+x $BinDir/TwCalib
chmod a+x $BinDir/TWXinputInstall.perl
chmod u+x $BinDir/Remove
chmod a+x $BinDir/StartCP

# Copy the default xorg.conf
if [ $XCopyDefault == 1 ]
then
   $BinDir/TWXinputInstall.perl -find
   if [ $? == 1 ]
   then
      cp -a xorg.conf.ORIG $XorgConf
   fi
fi

---

### Post by koalauk on 2010-06-13
Here is the original instruction for linux 

[http://multimedia.3m.com/mws/mediawebserver?mwsId=SSSSSu7zK1fslxtUmY_UnxtSev7qe17zHvTSevTSeSSSSSS--](http://multimedia.3m.com/mws/mediawebserver?mwsId=SSSSSu7zK1fslxtUmY_UnxtSev7qe17zHvTSevTSeSSSSSS--)

---

### Post by koalauk on 2010-06-14
:guitar:

At the end I ditced using the drivers supplied by 3M and instead

test device

cat /dev/ttyS0

got garbildi gubbly on the screen showing my serial controller functioning correctly and then if you havent already got it

download package inputattach and terminal

inputattach -mtouch /dev/ttyS0

and your touchscreen should work but slightly not calibrated

reboot box

use the 3M driver package and from there Linux MT712 B5.bin should have the calibration tool in it complete the instructions and complete the driver installation /ignore all the warnings etc etc...

reboot

now before enabling inputattach -mtouch /dev/ttyS0

you must calibrate the screen,

Go and find the folder where your driver is installed /twscreen folder

you ll se startCP .... make sure you have JRE before this as this script depends on the Java Env...  Run script and wait you should see the calibration and options window popup this also should show your device port which on my case was ttyS0 and firmware etc etc now run Calibrate with your mouse (click)

although looks like you have no mouse movement etc complete calibration as touchscreen should recognise the touches during the calibration process, save and exit


Now Terminal  inputattach -mtouch /dev/ttyS0

and check the calibration results your touchscreen should be calibrated perfect.


Next step  run a script to enable inputattach starts my serial touchscreen everytime I reboot the box.

Anyone here to help how to enable this?

regards

---

### Post by koalauk on 2010-06-14
All seems sorted now

enabled the terminal command in order to get inputattach working by

terminal

su -

gedit /etc/rc.local

and added

inputattach -mtouch /dev/ttyS0

before the exit 0 and saved
reboot

now inputattach starts automatically mapping the input device touchscreen on ttyS0 directly Yuppieee



Hopefully this inforation will be come usefull to someone Ubuntu NooB like me :)):P

---

### Post by walterj89 on 2010-09-06
I've been trying for a very long time to get this to work in Ubuntu 10.04 Desktop.

I'm having big problems with the calibration software,  I cant get it to run correctly.

Usually when I run 'StartSP' what pops up (MT7 Software Control Panel, Verison 7) the first tab is all greyed out and I can't start the calibration.  Draw test and Controller are greyed out too. 

Also the Cotroller ID, Controller Type, Filmware Version, and touch screen Status are all greyed out and blank

If I try to run 'TwCalib' i just get "calibration cannot start" although I have been able to kind of get it to start perviously.

By default running 'inputattach -mtouch /dev/ttyS0' just moves the mouse to the top right corner when touching the screen.

Thank you for what you have posted,  It got me this far almost successfully

---

### Post by wagalaweia on 2010-09-09
Hi there!
I just ran into the same problem as described in the first post. However, after reading a lot about update-rc.d, I recognized where the problem is: The TW-driver is setting up itself as a service by using the update-rc.d tool. Therefore, the file  TWDrvStartup has to put some hints in its comment-header to notify update-rc.d on how to register itself as a service. See details here: [http://wiki.debian.org/LSBInitScripts/](http://wiki.debian.org/LSBInitScripts/)

So, the first two warnings are:

```
update-rc.d: warning: /etc/init.d/TWDrvStartup missing LSB keyword 'required-start'
update-rc.d: warning: /etc/init.d/TWDrvStartup missing LSB keyword 'required-stop'
```They will disappear when inserting the lines

```
# Required-Start: 
# Required-Stop:
```to the header. I assume they were left out, because the are no dependencies, so the values can just be empty.

So, the latter two warnings are:

```
update-rc.d: warning: TWDrvStartup start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (2 5)
update-rc.d: warning: TWDrvStartup stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (0 1 3 4 6)
```As far as I understood, they just tell us, that the TWDrvStartup script requests to register for run-leves 2 5 (Start) and 0 1 3 4 5 (Stop), but the system is recommending to register a standard script at run-levels 2 3 4 5 (Start) and 0 6 (Stop). See the header in TWDrvStartup:

```
# Default-Start: 2 5
# Default-Stop: 0 1 3 4 6
```So, the warnings will disappear, when we change those lines to

```
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
```So, altogether, the comment-header of TWDrvStartup.ORIG should be modified to:

```
### BEGIN INIT INFO
# Provides: TwDriver
# Required-Start: 
# Required-Stop: 
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Description: Start the MT 7 touch screen driver
### END INIT INFO
```Hopefully, this should still match the intention of the driver's programmer. If you now run ./Install, no warnings will appear.

And now (hopefully) the best news:

All this outputs were just warnings, no errors! So you probably already had a successful installation of the 3M-drivers, but didn't recognize it, since there is no final message like "installation successful finished". I just ran into the same trouble and thought there were some installation errors.

However, for the moment I do not have any 3M monitor to test it, but at least the tools TWCalib and StartCP are present (StartCP is generated during installation) and work, so I have the hope that all works fine as soon as I plug in a 3M touchscreen.

Perhaps you could already try it out?

---

