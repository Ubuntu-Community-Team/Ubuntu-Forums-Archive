---
title: "the usb soundcard doesn't work"
date: 2009-02-17
forum: Hardware
---

### Post by KanineN on 2009-02-17
Hello! I have just purchased a usb soundcard because I don't have any internal soundcard on this computer. I plugged it in but it didn't work. The problem is that it's not a brand soundcard or anything. 


It just says "usb 2.0 audio adapter w/Microphone Jack. I could take a picture but I don't think it would help. It was a cd in the box but that is only for windows installation. The usb is on because a red lamp is flashing.

---

### Post by kostkon on 2009-02-17
First of all, could you please tell what version of Ubuntu do you have? Also, connect the card and then open a terminal and give
```
aplay -l
```
and post the output here.

---

### Post by KanineN on 2009-02-17
I have ubuntu 8.10. This is what I get of the command aplay -l 

```
**** List of PLAYBACK hardware devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
   Subordinate Units: 4 / 4
   Subordinate unit no. 0: subdevice # 0
   Subordinate unit no. 1: subdevice # 1
   Subordinate unit no. 2: subdevice # 2
   Subordinate unit no. 3: subdevice # 3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
   Subordinate units: 1 / 1
   Subordinate unit no. 0: subdevice # 0
card 1: default [C-Media USB Headphone Set], device 0: USB Audio [USB Audio]
   Subordinate units: 1 / 1
   Subordinate unit no. 0: subdevice # 0
```

It can be some type-o but that is just that I have a swedish version and have translated it with google translate.

---

### Post by kostkon on 2009-02-17
OK. It seems that you also have a internal sound card of some sort, or maybe its a dial-up modem. Anyway, your USB sound card seems to be recognised fine.

The thing you need to do is to install the *PulseAudio Device Chooser* utility (it will have a menu entry in *Applications &#8594; Sound & Video*). Run it, left-click on its icon in your system tray and select *Volume Control*.

From there you will be able to send the audio stream of one application from one device to another in real time. In the *Playback* tab you should see the audio streams of your running applications (the ones that produce audio only, of course). Right-click on one and select *Move Stream...* to move its audio to the device you want.

In the *Input Devices* and *Output Devices* tabs you can set the default input and output device to be used by your applications. Right-click on the device you want and enable the *Default* option.

For example, you can set your USB card as the default output device and all your applications will send their audio there by default.

For this to work, you should set your sound playbacks in *System &#8594; Preferences &#8594; Sound* to *Autodetect* (and if you want your inputs to *PulseAudio*), in case you have changed them.

You can set *PulseAudio Device Chooser* to start every time you login from its preferences.

Hope that helps...

---

### Post by KanineN on 2009-02-17
When I try to install pulseaudio i get this message when i do the ./configure command

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.

```

And this is the config.log 

```
/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1756: checking for a BSD-compatible install
configure:1812: result: /usr/bin/install -c
configure:1823: checking whether build environment is sane
configure:1866: result: yes
configure:1931: checking for gawk
configure:1947: found /usr/bin/gawk
configure:1958: result: gawk
configure:1969: checking whether make sets $(MAKE)
configure:1990: result: yes
configure:2243: checking for g++
configure:2273: result: no
configure:2243: checking for c++
configure:2273: result: no
configure:2243: checking for gpp
configure:2273: result: no
configure:2243: checking for aCC
configure:2273: result: no
configure:2243: checking for CC
configure:2273: result: no
configure:2243: checking for cxx
configure:2273: result: no
configure:2243: checking for cc++
configure:2273: result: no
configure:2243: checking for cl.exe
configure:2273: result: no
configure:2243: checking for FCC
configure:2273: result: no
configure:2243: checking for KCC
configure:2273: result: no
configure:2243: checking for RCC
configure:2273: result: no
configure:2243: checking for xlC_r
configure:2273: result: no
configure:2243: checking for xlC
configure:2273: result: no
configure:2301: checking for C++ compiler version
configure:2308: g++ --version >&5
./configure: line 2309: g++: command not found
configure:2311: $? = 127
configure:2318: g++ -v >&5
./configure: line 2319: g++: command not found
configure:2321: $? = 127
configure:2328: g++ -V >&5
./configure: line 2329: g++: command not found
configure:2331: $? = 127
configure:2354: checking for C++ compiler default output file name
configure:2381: g++    conftest.cpp  >&5
./configure: line 2382: g++: command not found
configure:2384: $? = 127
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "padevchooser"
| #define PACKAGE_TARNAME "padevchooser"
| #define PACKAGE_VERSION "0.9.3"
| #define PACKAGE_STRING "padevchooser 0.9.3"
| #define PACKAGE_BUGREPORT "mzcnqripubbfre (at) 0pointer (dot) de"
| #define PACKAGE "padevchooser"
| #define VERSION "0.9.3"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2423: error: C++ compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_GUILIBS_CFLAGS_set=
ac_cv_env_GUILIBS_CFLAGS_value=
ac_cv_env_GUILIBS_LIBS_set=
ac_cv_env_GUILIBS_LIBS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_PKG_CONFIG_set=
ac_cv_env_PKG_CONFIG_value=
ac_cv_env_PULSE_CFLAGS_set=
ac_cv_env_PULSE_CFLAGS_value=
ac_cv_env_PULSE_LIBS_set=
ac_cv_env_PULSE_LIBS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AWK=gawk
ac_cv_prog_make_make_set=yes

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/pedro/Skrivbord/padevchooser-0.9.3/missing --run aclocal-1.9'
AMDEPBACKSLASH=''
AMDEP_FALSE=''
AMDEP_TRUE=''
AMTAR='${SHELL} /home/pedro/Skrivbord/padevchooser-0.9.3/missing --run tar'
AUTOCONF='${SHELL} /home/pedro/Skrivbord/padevchooser-0.9.3/missing --run autoconf'
AUTOHEADER='${SHELL} /home/pedro/Skrivbord/padevchooser-0.9.3/missing --run autoheader'
AUTOMAKE='${SHELL} /home/pedro/Skrivbord/padevchooser-0.9.3/missing --run automake-1.9'
AWK='gawk'
CC=''
CCDEPMODE=''
CFLAGS=''
CPP=''
CPPFLAGS=''
CXX='g++'
CXXDEPMODE=''
CXXFLAGS=''
CYGPATH_W='echo'
DEFS=''
DEPDIR=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
GREP=''
GUILIBS_CFLAGS=''
GUILIBS_LIBS=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='${SHELL} $(install_sh) -c -s'
LDFLAGS=''
LIBOBJS=''
LIBS=''
LN_S=''
LTLIBOBJS=''
MAKEINFO='${SHELL} /home/pedro/Skrivbord/padevchooser-0.9.3/missing --run makeinfo'
OBJEXT=''
PACKAGE='padevchooser'
PACKAGE_BUGREPORT='mzcnqripubbfre (at) 0pointer (dot) de'
PACKAGE_NAME='padevchooser'
PACKAGE_STRING='padevchooser 0.9.3'
PACKAGE_TARNAME='padevchooser'
PACKAGE_URL='http://0pointer.de/lennart/projects/padevchooser/'
PACKAGE_VERSION='0.9.3'
PATH_SEPARATOR=':'
PKG_CONFIG=''
PULSE_CFLAGS=''
PULSE_LIBS=''
SET_MAKE=''
SHELL='/bin/bash'
STRIP=''
USE_LYNX_FALSE=''
USE_LYNX_TRUE=''
VERSION='0.9.3'
ac_ct_CC=''
ac_ct_CXX=''
am__fastdepCC_FALSE=''
am__fastdepCC_TRUE=''
am__fastdepCXX_FALSE=''
am__fastdepCXX_TRUE=''
am__include=''
am__leading_dot='.'
am__quote=''
am__tar='${AMTAR} chof - "$$tardir"'
am__untar='${AMTAR} xf -'
bindir='${exec_prefix}/bin'
build_alias=''
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
exec_prefix='NONE'
have_lynx=''
host_alias=''
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
install_sh='/home/pedro/Skrivbord/padevchooser-0.9.3/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
mkdir_p='mkdir -p --'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='NONE'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_NAME "padevchooser"
#define PACKAGE_TARNAME "padevchooser"
#define PACKAGE_VERSION "0.9.3"
#define PACKAGE_STRING "padevchooser 0.9.3"
#define PACKAGE_BUGREPORT "mzcnqripubbfre (at) 0pointer (dot) de"
#define PACKAGE "padevchooser"
#define VERSION "0.9.3"

configure: exit 77
```

---

### Post by kostkon on 2009-02-17
What? I don't understand why you tried to compile *PulseAudio*! You don't need to compile anything, even more *PulseAudio*, which is already installed and running in your system!

The thing you need to do is to open *Synaptic* (*System &#8594; Administration &#8594; Synaptic Package Manager*), search for the *PulseAudio Device Chooser*, mark this package for installation and click *Apply* to install it.

Then go to *Applications &#8594; Sound & Video* to find its menu entry and click to run it.

And, please, please, check [this very useful guide on how to install software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware")... It is *very* helpful...

Hope that helps.

Come back to tell how everything went...

---

### Post by KanineN on 2009-02-17
hmm, thats strange. If a install.sh file doesn't exist I always compile it...


Back to the problem, I can hear it buzzing in the earphones but I dont get any sound when I turn on a music file. I have done as you said, put the USB audio as default but it still doesn't work.

---

### Post by KanineN on 2009-02-18
It's working now! I did as you said and made so the playback is playing in the usb audio! But is there anyway so I can make so it always playbacks in usb audio? First I did it with mplayer and when I started spotify it didn't work until I redirected it to usb-audio.. 

EDIT: I played a file in youtube and did as you said, redirecting the sound to the usb but then I was curious wondering what happened if I choosed terminate stream, so I did and now I can choose firefox from the list so now I can hear anything on youtube.

---

### Post by kostkon on 2009-02-18
> **KanineN said:**
> It's working now! I did as you said and made so the playback is playing in the usb audio! But is there anyway so I can make so it always playbacks in usb audio? First I did it with mplayer and when I started spotify it didn't work until I redirected it to usb-audio.. 

EDIT: I played a file in youtube and did as you said, redirecting the sound to the usb but then I was curious wondering what happened if I choosed terminate stream, so I did and now I can choose firefox from the list so now I can hear anything on youtube.
Good news

I don't why setting the card as the default does not work for you. But, the good thing is that *PulseAudio* remembers your choice.

Thus, if you send the audio stream of an application to your USB card, the next time you run this application again, *PulseAudio* will send its audio to your card again.

You could test it and if you like report here if it works as expected.

---

