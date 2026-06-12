---
title: "Problem with compiling SmartLink modem driver"
date: 2008-05-29
forum: Hardware
---

### Post by MortezaJS on 2008-05-29
Hi
I have a zoltrix modem with SmartLink chipset. i have installed the  sl-modem-source package from ubuntu repo (Hardy), and want to compile and install it by module-assistant using this command:
```

sudo module-assistant auto-install sl-modem

```
as explained at [https://help.ubuntu.com/community/DialupModemHowto/Smartlink](https://help.ubuntu.com/community/DialupModemHowto/Smartlink) but module assistant returns an error like "operation failed" :(
i have read the operation log, somewhere there is an error : "there is no rule to make the target 'clean' " or something similar to, you can test yourself :)
someone told me to install "fakeroot",and i did, but there is no difference :mad:
what's wrong?

---

### Post by MortezaJS on 2008-05-30
somebody help me please! i have no experience in module/kernel compiling. which packages must be installed for compile modules? i think all needed packages are installed, but why it don't work?

---

### Post by MortezaJS on 2008-05-31
i need only a small guidance :( i don't think it be a hard question!

---

### Post by zekica on 2008-05-31
have you tried only installing sl-modem-daemon package:

sudo apt-get install sl-modem-daemon

If that doesn't work, you can install libc6-dev package:

sudo apt-get install libc6-dev

But first try only by installing sl-modem-daemon.

---

### Post by MortezaJS on 2008-05-31
Firstly thanks for answer :) , then about sl-modem-daemon, i installed it at first and AFAIK and have read in [package description]("http://packages.ubuntu.com/hardy/sl-modem-daemon"):
> The SmartLink modem daemon is the **application part** of the driver for recent modems produced by Smart Link Ltd.
so i think sl-modem-daemon won't work lonely(as i tested it and didn't work). it needs the module. And about libc6-dev, i have it installed and linux-libc-dev, too (about the last one, i read somewhere in source package, it is necessary in debian and ubuntu)

---

### Post by MortezaJS on 2008-06-01
ok! at least, someone say me how to compile it by kenel-package (manualy).
Note: a have compiled and installed another module (cdfs) successfully, so i think the problem is with sl-modem package, not me.

---

### Post by housam on 2008-06-01
I've used the following guide in installing the sl-modem driver long time ago. try to use it.

> 
==========Very Short Usage summary===============
# su - root
# chmod a+x slmodemd
  unless using a bootable CD
# cp slmodemd /usr/bin/
  BUT for Debian related Linux distirbutions, instead do:
# cp slmodemd /usr/sbin
The above completes slmodemd installation. 
# find /usr -name slmodemd
should ONLY report the newly copied slmodemd  
Should another older slmodemd copy be found rename it slmodem.old
 
First insert an ALSA modem driver.
# modprobe low_level_driver
among low_level_ drivers listed below
# slmodemd --alsa -c YOUR_COUNTRY modem:1 
If using a CD boot, instead:
# ./slmodemd --alsa -c YOUR_COUNTRY modem:1

This creates the modem ports 
       /dev/ttySL0 --> /dev/pts/N  
and prepares for later High Level  slmodemd functions.  

Should there be an error report like:
--------
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
error: alsa setup: cannot open playback device 'hw:1': No such device
error: cannot setup device 'hw:1'
--------
Try unloading the driver:
    modprobe -r low_level_driver
Reload:
    modprobe low_level_driver
If there is now a line with "modem" within output of:
    cat /proc/asound/pcm
Then there should be success during a repeat of:
    slmodemd --alsa -c YOUR_COUNTRY modem:1






A separate dialer utility (wvdial, kppp, kinternet, pon  etc) is needed to configure a dialout.
In case of problems, send an email with details to: [email]discuss@linmodems.org[/email]
Details and minor variants follow.



===========Details=====================
This package is derivative of slmodem-2.9.11-20051101.tar.gz maintained by "Sasha Khapyorsky" <sashakh@gmail.com>. 
1) The slmodemd is supplied already compiled as its functioning is not KernelVersion specific:
2) the compilation resources have been deleted to decrease package size.
  
Only the low_level_drivers serving interface roles are  kernel version specific. 
They are supplied with kernel+modules package installations for 2.6.n kernels

Should you wish to compile your own slmodemd, get the most recent slmodem-Version.tar.gz,
or an update thereof from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
The comilation requires prior installation of the library package:
     libasound2-dev
alternatively named
     libalsa2-devel 
in Mandrake/Mandiva distrbutions.
A typical compile is show below, for illustration.

To make sure slmodemd  is executable, do
# su - root
# chmod a+x slmodemd
The slmodemd is typically copied to /usr/sbin/,
which is on the COMMAND PATH.  
Alternatively for RAM disk installations like the KNOPPIX CD boots, 
it can be executed from a local folder with
# ./slmodemd + variables 
as described below.

# slmodemd --help
to see capabilties
# slmodemd --countrylist
to pick out your CountryName (USA,FRANCE, URUGUAY, etc). 
The list can be written to a file CountryCodes.txt with:
#  slmodemd --countrylist &> CountryCodes.txt 

Slmodemd was initially written to complement the slamr driver of SmartLink modems.
But functionality was extended to work with modem drivers provided as part of the
 ALSA (Advanced Linux Sound Architecture) package.  This enabled
usage with a broad range of non-Smartlink chipset soft modems.
POTENTIALLY  supported modems in this family operate under soft modem controllers. 
Compatible primary modem controllers currently are :
      PCI  ID       modem controller  name/source     low_level_driver
    =======        ===============    =======         =================       
    1002:434d          ATI                            snd-atiixp-modem
    1002:4379          ATI                                 "
    1106:3068          VIA                            snd-via82xx-modem
    10b9:5451          ALI 5451 audio with modem      snd-ali5451
    8086:????           many Intel controllers        snd-intel8x0m
    10de:00d9          Nvidia Corp                          "
    1039:7013          SIS 630                              "
     Others?                                                "
Under each of these controllers, may different Subsystems can be hosted, 
and having a variety of modem codecs, with most meeting a mc97 standard.  
All are potentially supported by slmodemd with one exceptional family.

Conexant modem codecs ( CXTnm ) are not mc97 compliant,
The hsfmodem software from [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers) MUST instead be used.
  
A first test is to insert the low_level_driver:
# modprobe  snd-intel8x0m
  OR the low_level_driver for your Controller type, among those above. 
This provides the contact between the kernel and the modem hardware, 
This is a concurrent appearance of new files in /proc/asound files.  You can find them with:
# find /proc/asound -name "mc97*" 
If an alsa-utils package is installed, detailed information can be output by:
# aplay -l

The compiled "slmodemd" provides higher level COMM functions and also creates the modem port.
An audio card and mc97 modem cards acquire successive nardware "stations". The ALSA audio
driver will load before its dependent ALSA modem driver.  In this most common case
the audio card is functionally named hardware device:   hw:0 
The modem card will be one of:   modem:1 , modem:0 , modem:1 or hw0,1 for the ALI5451 case.
 
There are RARE instances that the ALSA audio sound driver is absent, though the modem driver is present.  In these cases the device name "modem:1" may fail but "hw:0" may be successful. It is the usually the device name dynamically assigned to the audio card.

For first usages of slmodemd try:
# slmodemd --help
to display the several command options.
# slmodemd --countrylist
will display COUNTRY_NAMEs you will need.  USA is the United States name to be used.
This list can be captured to CountryList.txt with:
# slmodemd --countrylist &> CountryList.txt

Using modem:1 as the first example, prepare the modem for dialout with:
# slmodemd --alsa -c YOUR_COUNTRY modem:1 
which should suffice for all but the ali5451 case. It has a different bridging into the audio card and there must be used:
# slmodemd --alsa -s -c YOUR_COUNTRY hw:0,1

With the proper slmodem command parameters, port and symbolic link creation should be reported:
    /dev/ttySL0 --> /dev/pts/N    
with /dev/ttySL0 a symbolic link to the true modem port /dev/pts/N , N a number
Ignore a message:
     error: mixer setup: Off-hook switch not found for card modem:1
It is harmless and is fixed in a coming ALSA update. 

IMPORTANT - slmodemd MUST be left running throughout a dialout session.
If all goes well, there can latter be tried:
# slmodemd --alsa -c YOUR_COUNTRY modem:1  &
The & just backgrounds the process, so that the command prompt is returned.
Later slmodemd can be stopped with:
# fg slmodemd
# CtrL-C
But do NOT try the & usage until everything else is perfect.
Some host systems have CONNECT problems with slmodemd backgrounded.

Files in the scripts/ folder automate the above steps, but should ONLY be used
after the manual processes are successful. For Debian derived Linux distributions (with dpkg and apt-get package management tools).  Search for a package name sl-modem-daemon. See below for some details.  A comparable SuSE/Novell package is the smartlink package

Use your Linux Distro's dialer utiilty to configure a dialout.
Some dialer utilities are a front end to "wvdial" and creat a configuration file: 
	/etc/wvdial.conf 
See the included wvdial.conf sample. Check if /etc/wvdialconf alread exists with:
# ls /etc/wvdial.conf
Utilities writing this file include Kinternet and the Redhat/Fedora "Internet Connection Wizard " (ICW).
Be carefull not to overwrite such a configuration during a wvdialconf test.
Rather, access of software to modem hardware can instead be tested with:
	wvdialconf wvtest   
DO check if a /etc/wvdial.conf is created during the configuration step:
# ls /etc/wvdial.conf 
If so a line must be added into it :
   Carrier Check = no 
A sample /etc/wvdial.conf is below.
Dialers not relying on wvdial do not require this line.
Do try alternative dialers if a dialout problem is encountered.

Testing.txt has details on follow through modem testing steps.

============ Problem solving ========================

1)  Editing /etc/wvdial.conf
For Ubuntu, there can be used:
  sudo  /etc/wvdial.conf
to use a graphical editor.  For other Linux Distros
Editing of this file with a graphical edit by a non-Root User may be blocked.  In this case:
# su - root
# wvdialconf wvtest
# chmod a+rw wvtest
Then a User can do the edit on wvtest. Then after
$ su root
# cp wvtest /etc/wvdial.conf
You can also
# cp wvtest /home/LoginName/.wvdial.rc
Then
# wvdial 
will read  the .wvdial.rc or alternatively /etc/wvdial.conf

2) The trial
# wvdialconf wvtest
stops/hangs at a /dev/ircomm port before finding /dev/ttySL0
See [http://linmodems.technion.ac.il/archive-fifth/msg04065.htm](http://linmodems.technion.ac.il/archive-fifth/msg04065.htm) for the explanation and a bypass.
An alternate route is to just edit the  wvdial.conf included in this package and try a dialout with:
# su - root
# wvdial --config wvdial.conf

3) Describe any other problems in an email to:  [email]Discuss@linmodems.org[/email]


Marv Stodolsky
2006 Jan 19

=================



Here is a slmodem compile record within folder slmodem-2.9.11-20051009/modem/
----------------
Always do a precautionary:

# make clean
rm -f slmodemd modem_test modem_main.o modem_cmdline.o modem_test.o modem.o
modem_datafile.o modem_at.o modem_timer.o modem_pack.o modem_ec.o
modem_comp.o modem_param.o modem_debug.o homolog_data.o dp_sinus.o
dp_dummy.o sysdep_common.o
rm -f *~ *.orig *.rej

Compiling with ALSA support requires prior installation of libasound2 and libasound2-dev
packages.  The former typically already installed. Includeing  ALSA support requires a
command line specification:

# cd modem
# make SUPPORT_ALSA=1
rebuild profile...
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -DSUPPORT_ALSA=1   -o modem_main.o -c modem_main.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -DSUPPORT_ALSA=1   -o modem_cmdline.o -c modem_cmdline.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -DSUPPORT_ALSA=1   -o modem.o -c modem.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -DSUPPORT_ALSA=1   -o modem_datafile.o -c modem_datafile.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -DSUPPORT_ALSA=1   -o modem_at.o -c modem_at.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -DSUPPORT_ALSA=1   -o modem_timer.o -c modem_timer.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -DSUPPORT_ALSA=1   -o modem_pack.o -c modem_pack.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -DSUPPORT_ALSA=1   -o modem_ec.o -c modem_ec.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -DSUPPORT_ALSA=1   -o modem_comp.o -c modem_comp.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -DSUPPORT_ALSA=1   -o modem_param.o -c modem_param.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -DSUPPORT_ALSA=1   -o modem_debug.o -c modem_debug.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -DSUPPORT_ALSA=1   -o homolog_data.o -c homolog_data.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -DSUPPORT_ALSA=1   -o dp_sinus.o -c dp_sinus.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -DSUPPORT_ALSA=1   -o dp_dummy.o -c dp_dummy.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -DSUPPORT_ALSA=1   -o sysdep_common.o -c sysdep_common.c
gcc -o slmodemd modem_main.o modem_cmdline.o modem.o modem_datafile.o
modem_at.o modem_timer.o modem_pack.o modem_ec.o modem_comp.o modem_param.o
modem_debug.o homolog_data.o dp_sinus.o dp_dummy.o dsplibs.o sysdep_common.o /usr/lib/libasound.so
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -DSUPPORT_ALSA=1   -o modem_test.o -c modem_test.c
gcc -o modem_test modem_test.o modem_cmdline.o modem.o modem_datafile.o
modem_at.o modem_timer.o modem_pack.o modem_ec.o modem_comp.o modem_param.o
modem_debug.o homolog_data.o dp_sinus.o dp_dummy.o dsplibs.o sysdep_common.o

# ls -lh slmodemd
-rwxr-xr-x  1 root root 1.3M Oct 10 12:54 slmodemd
is the desired product. It should be copied to /usr/sbin/slmodemd


Here are detials on the package sl-modem-daemon:
~$ apt-cache show sl-modem-daemon
Package: sl-modem-daemon
Status: install ok installed
Priority: optional
Section: non-free/misc
Installed-Size: 1004
Maintainer: Eduard Bloch <blade@debian.org>
Architecture: i386
Source: sl-modem
Version: 2.9.10+2.9.9d-6ubuntu1
Provides: slmodem
Depends: libasound2 (>> 1.0.9), libc6 (>= 2.3.4-1), debconf
Conflicts: sl-modem-modules
Conffiles:
 /etc/modutils/sl-modem-daemon.modutils c851a0c0c27a443abe5acba823278bcd
 /etc/modprobe.d/sl-modem-daemon.modutils c851a0c0c27a443abe5acba823278bcd
 /etc/hotplug/usb/slusb e5bcf1ff491513e4b1ee1a0933002c3f
 /etc/default/sl-modem-daemon d3dddfd7dd0397b9b1f49bfdf68e0005
 /etc/init.d/sl-modem-daemon 551c27912b3013a3b98138c5f88f32e4
Description: SmartLink software modem daemon
 The SmartLink modem daemon is the application part of the
 driver for recent modems produced by Smart Link Ltd.
 .
 This package replaces (along with hardware access drivers) the old
 driver generation (2.7.x) which consisted of kernel modules only.
 .
 It needs a kernel driver to access the hardware. This can be either
 recent ALSA (shipped with a newer kernel (>=2.6.4) with Alsa support
 and intel8x0m module) which is sufficient for basic operation and
 data/Internet connection, or the SmartLink kernel driver which is
 provided by separate packages which you can build using the source from
 the sl-modem-source package.

---

### Post by housam on 2008-06-01
I've used the information in the attached documents too.

---

### Post by zorrek on 2009-03-12
> **MortezaJS said:**
> Hi
I have a zoltrix modem with SmartLink chipset. i have installed the  sl-modem-source package from ubuntu repo (Hardy), and want to compile and install it by module-assistant using this command:
```

sudo module-assistant auto-install sl-modem

```
as explained at [https://help.ubuntu.com/community/DialupModemHowto/Smartlink](https://help.ubuntu.com/community/DialupModemHowto/Smartlink) but module assistant returns an error like "operation failed" :(
i have read the operation log, somewhere there is an error : "there is no rule to make the target 'clean' " or something similar to, you can test yourself :)
someone told me to install "fakeroot",and i did, but there is no difference :mad:
what's wrong?
How did you do this. apt-get install sl-modem-source fails for me
 Couldn't find package sl-modem-source. I'm running 64 bit 8.04 :(

---

### Post by MortezaJS on 2009-03-18
> **zorrek said:**
> How did you do this. apt-get install sl-modem-source fails for me
 Couldn't find package sl-modem-source. I'm running 64 bit 8.04 :(
You made me happy guy! I thought somebody have answered my unsolved question after one year :D (though I have changed my modem)
Unfortunatly it seems this driver only provides for i386 : [http://packages.ubuntu.com/hardy/sl-modem-source](http://packages.ubuntu.com/hardy/sl-modem-source)

---

### Post by hugogarro on 2012-08-08
I have an internal slamr PCI modem:

NAME="Modem: Motorola SM56 Data Fax Modem "
CLASS=0703
PCIDEV=1057:3052
SUBSYS=1057:3020
IRQ=17
IDENT=slamr

I am running Ubuntu 12.04 (64bit) I remember trying to do this a few years ago and ending buying a new USB modem. However the usb modem got busted due to bad usb port and while I get new one I need the internal one running.

So I go to [https://help.ubuntu.com/community/DialupModemHowto/Smartlink](https://help.ubuntu.com/community/DialupModemHowto/Smartlink) and start compiling the driver:

```
$ sudo module-assistant auto-install sl-modem
```And after a few seconds, compilation stops with the nice Module Assistant interactive asking me to view the log. First compilation goes through the dependancies and finds out that they are all installed, then goes through the generic script and echoes a few error messages, anyway this is the outcome from the terminal:

> ...
Done!
unpack 
The source tarball could not be found!
Package sl-modem-source not installed?
Running "m-a -f get sl-modem-source" may help.
"/usr/share/modass/packages/default.sh" build KVERS=3.2.0-23-generic KSRC=/usr/src/linux KDREV=3.2.0-23.36 kdist_image
find: «/usr/src/modules/sl*»: No such file or directory
So I do have sl-modem-source installed and running "m-a -f get" did not help. There is no "modules" directory,  instead I have /usr/src/sl-modem-2.9.11~20110321 (and a few linux headers directories)

I tried housam's guide but all the files he is asking to copy are already there.

```
$ slmodemd --alsa -c b5 modem:1
error: mixer setup: attach hw:1 error: No such file or directory
ALSA lib conf.c:4687:(snd_config_expand) Unknown parameters 1
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM modem:1
error: alsa setup: cannot open playback device 'modem:1': Invalid argument
error: cannot setup device `modem:1'
``````
$ modprobe low_level_driver
FATAL: Module low_level_driver not found.
```I think I am in the wrong path here. If someone could just enlighten me.

Thanks in advance.

uname -a
Linux zariweya 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

