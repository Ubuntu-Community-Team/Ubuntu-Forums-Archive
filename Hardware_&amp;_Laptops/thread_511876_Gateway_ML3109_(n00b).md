---
title: "Gateway ML3109 (n00b)"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by alphabetical on 2007-07-28
Hello all.

I have recently installed Ubuntu 6.06 on my new lappi, a gateway ML3109, and everything seems to work great except there is no sound and the wireless doesn't work.

I don't know the wireless chip used in this lappi or the sound card.  Here's some data

6008015R - Integrated 802.11/g WLAN (FRU)
GemTek Specifications
106971, 6008015R
Manufacturer Gemtek
Model BCM4318E 11G WMIB-158G21A20 USA
Features BroadRange technology
Form Factor Type IIIB MiniPCI
Host interface 32-bit miniPCI

Manufacturer Lite On
Model WN2300L
Chipset Realtek RTL 8185L
RF Realtek RTL 8225
Standard IEEE802.11b, IEEE802.11g, IEEE802.11i
Bus Interface MiniPCI Card,Type 3 B

Manufacturer Lite On
Model WN2300B
Standard IEEE802.11b, IEEE802.11g, IEEE802.11i
Bus Interface MiniPCI Card,Type 3 B 

HeLp?!?  :confused:

---

### Post by alphabetical on 2007-07-29
One thing is that the Wireless seems to be up...or at least in the net working utility It seems configured or about as much as my wired LAN.  It also says "the interface wlan0 is active" but when I try to connect...click wireless connection / enter internet data (essid, wep key) then it tries to connect it doesn't work  D:

Grrrr

And with the sound I have to idea...

---

### Post by mike1111 on 2007-08-07
I'm having the exact same problem!  I'd really like to get those two problems resolved because I'm absolutely done with Vista and Windows in general... or I'd like to be, once I can get Ubuntu up and running on this laptop.

If anyone has any idea... And i've tried using ndiswrapper using the windows vista driver, and that didn't work.
Sorry this is kind of a bump, but It'd b nice to use Ubuntu on this laptop.

---

### Post by csurigao on 2007-08-16
bump

---

### Post by agjones on 2007-08-16
I got the sound working by downloading the drivers from RealTek:


[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false)

Then choose 8185L.

After getting this on your computer, unzip it.  Go to Windows Wireless Drivers and choose the INF file from the download.  Reboot and it will work.


I'm still fighting to get the sound working.

---

### Post by Jerryonimo on 2007-08-23
Actually, I have a whole host of problems after upgrading to Ubuntu 7.04 Feisty:
1) Sometimes when I *log out*, the computer starts to shut down and freezes.
2) I can't switch users.
3) Occasionally when I try to switch command line screens, the computer will freeze up.
4) I can only choose "Human" themed icons for OpenOffice.org.
5) KDE crashed 20 minutes after I installed it.
6) Even though I supposedly installed ALSA, I'm not getting any sound.

I think there are some other problems, but I can't think of them right now.
You can bet I'm having a good time on this system. :D

---

### Post by PeterWalgreens on 2007-09-03
Has anyone else figured the WIfI and Sound problem out yet?

Vista is the source of the problem though, even XP has been reported to run badly on this machine....

[http://forum.notebookreview.com/showthread.php?p=2372159](http://forum.notebookreview.com/showthread.php?p=2372159)

---

### Post by oopman2002 on 2007-09-19
Similar story so far. Just bought a ML3109 Gateway and blew Vista away and installed Ubuntu 7.04. Most things work ok so far including wired network. It does not detect my internal wireless and have no sound.

---

### Post by yoblin on 2007-09-19
> **agjones said:**
> I got the sound working by downloading the drivers from RealTek:


[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false)

Then choose 8185L.

After getting this on your computer, unzip it.  Go to Windows Wireless Drivers and choose the INF file from the download.  Reboot and it will work.


I'm still fighting to get the sound working.



Yes, this works to get the wireless working, did this a couple days ago. Anyone figure out the sound? It looks like drivers are just being patched to support it, but I don't know how to integrate the patches into my ALSA driver!

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948)

---

### Post by yoblin on 2007-09-19
ok, sound is working for me on the gateway ml3109 on Ubuntu Feisty Fawn. (Being verbose for future googlers :) )

Download the files here:

[http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

you need driver library utils, not the newest version but one less (RC1)

and then download the rc1 patch and follow the install instructions:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036)

The RC2 patch didn't work for me, so install the RC1 patch with the RC1 drivers and add "options snd-hda-intel model=STAC9200" to /etc/modprobe.d/alsa-base

---

### Post by yonakatsuki on 2007-09-20
Can someone please post a short guide on how to get these working? I am having trouble figuring out how to install the wireless driver, and as for the alsa patch, I'm clueless. Yes, I'm a n00b. Please don't let me have to go back to Vista. These forums have helped me a lot for my old MX3215 notebook, which died. Help me get my favorite OS on my new one! Thank you!

---

### Post by giant22000 on 2007-09-20
Guess this seems to be common with all ML3109 users as i'm experiencing the same thing.  Tried to compile a few of the above drivers with no luck....

---

### Post by yoblin on 2007-09-20
---- EDIT -----

oh yeah, you might also need to run "sudo apt-get install build-essential" for the stuff to compile, forgot about that..

---------------

Alright, I'll try to post a more detailed explanation of what you need to do to get up and running. 

For the wireless, download this and extract it:

[ftp://152.104.238.19/cn/wlan/RTL8185_6.1102.0702,UI_1.00.0006.zip](ftp://152.104.238.19/cn/wlan/RTL8185_6.1102.0702,UI_1.00.0006.zip)

next, install the newest ndis wrapper:

[http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=167243&release_id=537654](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=167243&release_id=537654)

Extract it to your desktop, and then open a terminal.

change to the directory you extracted the files to and run:

sudo make uninstall
make
sudo make install

next, go into the extracted realtek drivers folder and go into the windows 2000 directory. run:

sudo bash
ndiswrapper -i driver.inf     (replace driver.inf with the inf file name, I forget what it is)
ndiswrapper -l
modprobe ndiswrapper

you should then be able to go into system -> administration -> network and see your wireless card (might need to reboot). Go into it's properties and disable roaming mode. You can then select a wireless network.

To get sound working, download the driver, library and utilities from this site:

[http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

you want version 1.0.15 rc1

then go to [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036) (do a guest login)  and download:

15rc1_patch_install
patch_sigmatel.c.patch-1.0.15rc1-simple

follow the instructions in the 15rc1_patch_install file to patch the drivers and install. Note the first command won't work; that's ok.

Next, run:

sudo gedit /etc/modprobe.d/alsa-base

and add this to the end:

options snd-hda-intel model=STAC9200

reboot and it should all work. 

I'm no pro at this, and i'm going by memory here, so if someone wants to type up a clearer version you're welcome to!

---

### Post by giant22000 on 2007-09-20
Excellent post Yoblin! Cant wait to get home and try it out....

---

### Post by giant22000 on 2007-09-20
Yoblin i've followed your instructions to the "T" and cannot even get past the first step of installing ndiswrapper.  I've never had any luck with installing anything.......

---

### Post by yoblin on 2007-09-20
> **giant22000 said:**
> Yoblin i've followed your instructions to the "T" and cannot even get past the first step of installing ndiswrapper.  I've never had any luck with installing anything.......

It's possible there are some libraries I have installed that your computer doesn't, what part are you having trouble with? Are there errors coming up?

---

### Post by giant22000 on 2007-09-20
yes I am getting error messages.  The first message received when running the "make" command while installing ndiswrapper is:  ndswrapper.mod:  Permission denied

---  edit  ---

i tried running the "make" command as root and starting getting error messages after it said this:

gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20:error: stdlib.h:  No such file or directory
etc..
etc...

It gave about 100 similar error messages.  Also, i'm new to Linux so bear with me... I'm not sure what you talking about when you refer to libraries, but I bought the ML3109 yesterday and put Linux (Ubuntu 7.04) on it last night as well and then proceeded to this guide, there are no other libraries loaded that didn't come pre-loaded with Ubuntu..

---

### Post by yoblin on 2007-09-20
have you run this yet?

sudo apt-get install build-essential

that will get the libraries needed, I think..

---

### Post by giant22000 on 2007-09-20
I haven't tried that.  When I get home i'll try it and post back my results.  Thanks again Yoblin!

---

### Post by giant22000 on 2007-09-20
I tried "sudo apt-get install build-essential" command and still have error messages... any other ideas?

---

### Post by oopman2002 on 2007-09-21
I have also been trying to get the wireless and sound working on my new ML3109 with Ubuntu 7.04 and can't wait to try the stuff in this post over the weekend.

BTW - I've found several links to ML3109 drivers, most Windows but helpful info in the links.

[http://forums.extremeoverclocking.com/p2847709.html](http://forums.extremeoverclocking.com/p2847709.html)

[http://forum.notebookreview.com/showthread.php?t=155573](http://forum.notebookreview.com/showthread.php?t=155573)

Hope these are of some help. Been very happy with the 3109 and Linux. For $350 you can't beat it and it works great for college.

Lyle

---

### Post by giant22000 on 2007-09-22
Yobin I got ndiswrapper working but have another problem.  When I run the command ndiswrapper -i net8185.inf it tells me the driver is already installed.  Ok, then I proceed to run the command ndiswrapper -l and then it gives me an error message the saying "invalid driver."  Any ideas what might be causing that??

---

### Post by yoblin on 2007-09-22
> **giant22000 said:**
> Yobin I got ndiswrapper working but have another problem.  When I run the command ndiswrapper -i net8185.inf it tells me the driver is already installed.  Ok, then I proceed to run the command ndiswrapper -l and then it gives me an error message the saying "invalid driver."  Any ideas what might be causing that??

This is what I get when I run the command:

yoblin@yoblin-laptop:~$ ndiswrapper -l
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r818x)

I think it was a slightly different response before I rebooted or used it or something though. In the gui tool it always says that the hardware is not present. 

you could try installing it using the graphical tool, run "sudo ndisgtk" and use the windows 2000 drivers from the archive (those are the ones I had luck with) and reboot after installing. The graphical tool gives no feedback as to whether or not it works or not, so just reboot and go into your system -> admin -> network and see if the wireless is there and picking up networks after disabling roaming mode.

hope that helps.

---

### Post by giant22000 on 2007-09-22
Yoblin i'll give that a try and post back.  Just want to say thanks for all your help!!!

---

### Post by giant22000 on 2007-09-22
just a quick question... how do i disable roaming mode??  would the wireless network have to show up under networks or is disabling roaming mode something else you do in order for it to show up under networks?? thanks..

---

### Post by pablodavid on 2007-09-24
Gateway ML3109 issues: From the point of view of a simple minded person, willing to learn, help and share knowledge. I am new to Ubuntu and Linux (just 7 days of experience) and I am loving it!!!!

This is the way I resolved the wireless network card issue in my Ubuntu 7.04 version:

1. Make sure you have installed the program “Windows Wireless Drivers” under System/Administration. If you don’t go to Applications/Add/Remove and download it form the Ubuntu site. This is the easy part.
2. Download the Windows XP driver for the Realtek RTL8185 at: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&ProdID=35&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&ProdID=35&DownTypeID=3&GetDown=false&Downloads=true)
3. The one I used was the “Windows XP/2K/ME/98SE driver”
4. Extract it, look for the 85-PCI&Cardbus folder and open it
5. Then look for the RTL 8185 folder and open it
6. Inside this folder look for the WIN XP. Move this folder to the desktop (you have to do this or it will not work when trying to use the Windows Wireless Drivers application (don’t ask me why, it will simply NOT WORK).
7. Open the Windows Wireless Drivers application. It will ask for your password. Go to install new driver. Look for the WINXP folder you put it the Desktop. Then look for the .ini file. Hit open and the install. Reboot the laptop. It should detect the wireless card now.

This is the way I resolved the sound card problem (thanks to Yoblin):

1. Download the alsa-driver-1.0.15rc1 at [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)
2. Also download the alsa-lib-1.0.15rc1 and the alsa-utils-1.0.15rc1
3. Go to [https://bugtrack.alsa-project.org/al...ew.php?id=3036](https://bugtrack.alsa-project.org/al...ew.php?id=3036) and login as a guest
4. Download the 15rc1_patch_inatall and the patch_sigmatel.c.patch-1.0.15rc1-simple
5. Create a directory in the desktop (I called it alsa but you can use any name you want) and put all the files there.
6. Follow the directions in the 15rc1_patch_install. I agree with Yoblin, the first command is useless and will give you an error.
7. The only thing I did differently was adding sudo before every command (unless you are log in as a root user) except for the cd command
8. Remember to cd to the alsa directory (or the name of the directory you put all the files) at the terminal window or nothing will happen. (I know this might sound silly to the experts, but I am not one, and took me some time to figure this out).
9.Reboot
10.You will hear sound on you next login

---

### Post by yoblin on 2007-09-24
Glad to hear it works for someone else.

Now we can all get use out of these machines!

---

### Post by giant22000 on 2007-09-24
It's such a shame... Just as I start to get somewhere with this machine I'm going to be forced to bring it back to Best Buy.  It was such a great deal but when I got it home and started playing around with it, I discovered it has an Expresscard slot and not a standard PC Card slot.  What a disappointment... This was going to be a perfect machine for what I had planned for it!! Thanks for everybody's help!!!

---

### Post by dvenardos on 2007-09-24
> **pablodavid said:**
> 
This is the way I resolved the sound card problem (thanks to Yoblin):

1. Download the alsa-driver-1.0.15rc1 at [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)
2. Also download the alsa-lib-1.0.15rc1 and the alsa-utils-1.0.15rc1
3. Go to [https://bugtrack.alsa-project.org/al...ew.php?id=3036](https://bugtrack.alsa-project.org/al...ew.php?id=3036) and login as a guest


I am trying to get the sound working on my Gateway ML3109, but the alsa driver is now rc2 and the bugtrack url is no longer valid.
Perhaps the patch was rolled into rc2?
Can anyone give me revised instructions?

Thanks

---

### Post by yoblin on 2007-09-24
> **dvenardos said:**
> I am trying to get the sound working on my Gateway ML3109, but the alsa driver is now rc2 and the bugtrack url is no longer valid.
Perhaps the patch was rolled into rc2?
Can anyone give me revised instructions?

Thanks



sorry, copied and pasted the link and forgot that the forum adds "..." in the middle. Here's the correct link:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036)

RC2 is available but the patch was not rolled into it. I suggest using RC1 as RC2 did not work correctly when I patched it.

---

### Post by dvenardos on 2007-09-25
> **yoblin said:**
> sorry, copied and pasted the link and forgot that the forum adds "..." in the middle. Here's the correct link:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036)

RC2 is available but the patch was not rolled into it. I suggest using RC1 as RC2 did not work correctly when I patched it.

Okay, thanks I got all the files and RC1 but I am getting a compile error on:
cd alsa-lib-1.0.15rc1/
./configure && make && make install

configure:3025: checking for C compiler default output file name
configure:3052: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

Any ideas?

config.log:
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by configure, which was
generated by GNU Autoconf 2.60.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = Virgil
uname -m = i686
uname -r = 2.6.20-16-generic
uname -s = Linux
uname -v = #2 SMP Fri Aug 31 00:55:27 UTC 2007

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
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
PATH: /usr/X11R6/bin


## ----------- ##
## Core tests. ##
## ----------- ##

configure:2076: checking build system type
configure:2094: result: i686-pc-linux-gnulibc1
configure:2116: checking host system type
configure:2131: result: i686-pc-linux-gnulibc1
configure:2153: checking target system type
configure:2168: result: i686-pc-linux-gnulibc1
configure:2210: checking for a BSD-compatible install
configure:2266: result: /usr/bin/install -c
configure:2277: checking whether build environment is sane
configure:2320: result: yes
configure:2385: checking for gawk
configure:2415: result: no
configure:2385: checking for mawk
configure:2401: found /usr/bin/mawk
configure:2412: result: mawk
configure:2423: checking whether make sets $(MAKE)
configure:2444: result: yes
configure:2707: checking for gcc
configure:2723: found /usr/bin/gcc
configure:2734: result: gcc
configure:2972: checking for C compiler version
configure:2979: gcc --version >&5
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2982: $? = 0
configure:2989: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:2992: $? = 0
configure:2999: gcc -V >&5
gcc: '-V' option must have argument
configure:3002: $? = 1
configure:3025: checking for C compiler default output file name
configure:3052: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:3055: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "alsa-lib"
| #define VERSION "1.0.15rc1"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:3094: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnulibc1
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
ac_cv_env_CXXCPP_set=
ac_cv_env_CXXCPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_F77_set=
ac_cv_env_F77_value=
ac_cv_env_FFLAGS_set=
ac_cv_env_FFLAGS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=i686-pc-linux-gnulibc1
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AWK=mawk
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_make_make_set=yes
ac_cv_target=i686-pc-linux-gnulibc1

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/dvenardos/Desktop/alsa/alsa-lib-1.0.15rc1/missing --run aclocal-1.9'
ALSA_CONFIG_DIR=''
ALSA_DEPLIBS=''
ALSA_HSEARCH_R_FALSE=''
ALSA_HSEARCH_R_TRUE=''
ALSA_PLUGIN_DIR=''
AMDEPBACKSLASH=''
AMDEP_FALSE=''
AMDEP_TRUE=''
AMTAR='${SHELL} /home/dvenardos/Desktop/alsa/alsa-lib-1.0.15rc1/missing --run tar'
AR=''
AUTOCONF='${SHELL} /home/dvenardos/Desktop/alsa/alsa-lib-1.0.15rc1/missing --run autoconf'
AUTOHEADER='${SHELL} /home/dvenardos/Desktop/alsa/alsa-lib-1.0.15rc1/missing --run autoheader'
AUTOMAKE='${SHELL} /home/dvenardos/Desktop/alsa/alsa-lib-1.0.15rc1/missing --run automake-1.9'
AWK='mawk'
BUILD_ALISP_FALSE=''
BUILD_ALISP_TRUE=''
BUILD_CTL_PLUGIN_EXT_FALSE=''
BUILD_CTL_PLUGIN_EXT_TRUE=''
BUILD_CTL_PLUGIN_FALSE=''
BUILD_CTL_PLUGIN_SHM_FALSE=''
BUILD_CTL_PLUGIN_SHM_TRUE=''
BUILD_CTL_PLUGIN_TRUE=''
BUILD_HWDEP_FALSE=''
BUILD_HWDEP_TRUE=''
BUILD_INSTR_FALSE=''
BUILD_INSTR_TRUE=''
BUILD_MIXER_FALSE=''
BUILD_MIXER_TRUE=''
BUILD_MODULES_FALSE=''
BUILD_MODULES_TRUE=''
BUILD_PCM_FALSE=''
BUILD_PCM_PLUGIN_ADPCM_FALSE=''
BUILD_PCM_PLUGIN_ADPCM_TRUE=''
BUILD_PCM_PLUGIN_ALAW_FALSE=''
BUILD_PCM_PLUGIN_ALAW_TRUE=''
BUILD_PCM_PLUGIN_ASYM_FALSE=''
BUILD_PCM_PLUGIN_ASYM_TRUE=''
BUILD_PCM_PLUGIN_COPY_FALSE=''
BUILD_PCM_PLUGIN_COPY_TRUE=''
BUILD_PCM_PLUGIN_DMIX_FALSE=''
BUILD_PCM_PLUGIN_DMIX_TRUE=''
BUILD_PCM_PLUGIN_DSHARE_FALSE=''
BUILD_PCM_PLUGIN_DSHARE_TRUE=''
BUILD_PCM_PLUGIN_DSNOOP_FALSE=''
BUILD_PCM_PLUGIN_DSNOOP_TRUE=''
BUILD_PCM_PLUGIN_EMPTY_FALSE=''
BUILD_PCM_PLUGIN_EMPTY_TRUE=''
BUILD_PCM_PLUGIN_EXTPLUG_FALSE=''
BUILD_PCM_PLUGIN_EXTPLUG_TRUE=''
BUILD_PCM_PLUGIN_FALSE=''
BUILD_PCM_PLUGIN_FILE_FALSE=''
BUILD_PCM_PLUGIN_FILE_TRUE=''
BUILD_PCM_PLUGIN_HOOKS_FALSE=''
BUILD_PCM_PLUGIN_HOOKS_TRUE=''
BUILD_PCM_PLUGIN_IEC958_FALSE=''
BUILD_PCM_PLUGIN_IEC958_TRUE=''
BUILD_PCM_PLUGIN_IOPLUG_FALSE=''
BUILD_PCM_PLUGIN_IOPLUG_TRUE=''
BUILD_PCM_PLUGIN_LADSPA_FALSE=''
BUILD_PCM_PLUGIN_LADSPA_TRUE=''
BUILD_PCM_PLUGIN_LFLOAT_FALSE=''
BUILD_PCM_PLUGIN_LFLOAT_TRUE=''
BUILD_PCM_PLUGIN_LINEAR_FALSE=''
BUILD_PCM_PLUGIN_LINEAR_TRUE=''
BUILD_PCM_PLUGIN_METER_FALSE=''
BUILD_PCM_PLUGIN_METER_TRUE=''
BUILD_PCM_PLUGIN_MMAP_EMUL_FALSE=''
BUILD_PCM_PLUGIN_MMAP_EMUL_TRUE=''
BUILD_PCM_PLUGIN_MULAW_FALSE=''
BUILD_PCM_PLUGIN_MULAW_TRUE=''
BUILD_PCM_PLUGIN_MULTI_FALSE=''
BUILD_PCM_PLUGIN_MULTI_TRUE=''
BUILD_PCM_PLUGIN_NULL_FALSE=''
BUILD_PCM_PLUGIN_NULL_TRUE=''
BUILD_PCM_PLUGIN_PLUG_FALSE=''
BUILD_PCM_PLUGIN_PLUG_TRUE=''
BUILD_PCM_PLUGIN_RATE_FALSE=''
BUILD_PCM_PLUGIN_RATE_TRUE=''
BUILD_PCM_PLUGIN_ROUTE_FALSE=''
BUILD_PCM_PLUGIN_ROUTE_TRUE=''
BUILD_PCM_PLUGIN_SHARE_FALSE=''
BUILD_PCM_PLUGIN_SHARE_TRUE=''
BUILD_PCM_PLUGIN_SHM_FALSE=''
BUILD_PCM_PLUGIN_SHM_TRUE=''
BUILD_PCM_PLUGIN_SOFTVOL_FALSE=''
BUILD_PCM_PLUGIN_SOFTVOL_TRUE=''
BUILD_PCM_PLUGIN_TRUE=''
BUILD_PCM_TRUE=''
BUILD_PYTHON_FALSE=''
BUILD_PYTHON_TRUE=''
BUILD_RAWMIDI_FALSE=''
BUILD_RAWMIDI_TRUE=''
BUILD_SEQ_FALSE=''
BUILD_SEQ_TRUE=''
CC='gcc'
CCDEPMODE=''
CFLAGS=''
CPP=''
CPPFLAGS=''
CXX=''
CXXCPP=''
CXXDEPMODE=''
CXXFLAGS=''
CYGPATH_W='echo'
DEFS=''
DEPDIR=''
ECHO='echo'
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
F77=''
FFLAGS=''
GREP=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_M4_FALSE='#'
INSTALL_M4_TRUE=''
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='${SHELL} $(install_sh) -c -s'
LDFLAGS=''
LIBOBJS=''
LIBS=''
LIBTOOL=''
LIBTOOL_VERSION_INFO='2:0:0'
LN_S=''
LTLIBOBJS=''
MAKEINFO='${SHELL} /home/dvenardos/Desktop/alsa/alsa-lib-1.0.15rc1/missing --run makeinfo'
OBJEXT=''
PACKAGE='alsa-lib'
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
PYTHON_LIBS=''
RANLIB=''
SET_MAKE=''
SHELL='/bin/bash'
SND_LIB_EXTRAVER=''
SND_LIB_MAJOR=''
SND_LIB_MINOR=''
SND_LIB_SUBMINOR=''
SND_LIB_VERSION=''
STRIP=''
SYMBOLIC_FUNCTIONS_FALSE=''
SYMBOLIC_FUNCTIONS_TRUE=''
SYMBOL_PREFIX=''
VERSION='1.0.15rc1'
VERSIONED_SYMBOLS_FALSE=''
VERSIONED_SYMBOLS_TRUE=''
ac_ct_CC='gcc'
ac_ct_CXX=''
ac_ct_F77=''
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
build='i686-pc-linux-gnulibc1'
build_alias=''
build_cpu='i686'
build_os='linux-gnulibc1'
build_vendor='pc'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE}'
dvidir='${docdir}'
exec_prefix='NONE'
host='i686-pc-linux-gnulibc1'
host_alias=''
host_cpu='i686'
host_os='linux-gnulibc1'
host_vendor='pc'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
install_sh='/home/dvenardos/Desktop/alsa/alsa-lib-1.0.15rc1/install-sh'
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
target='i686-pc-linux-gnulibc1'
target_alias=''
target_cpu='i686'
target_os='linux-gnulibc1'
target_vendor='pc'

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_NAME ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define PACKAGE_STRING ""
#define PACKAGE_BUGREPORT ""
#define PACKAGE "alsa-lib"
#define VERSION "1.0.15rc1"

configure: exit 77

---

### Post by yoblin on 2007-09-25
The only libraries you need can be gotten with "sudo apt-get install build essential"

if that doesn't work then I"m not sure, someone with more knowledge of dependencies might be able to help.

---

### Post by dvenardos on 2007-09-25
> **yoblin said:**
> The only libraries you need can be gotten with "sudo apt-get install build essential"

if that doesn't work then I"m not sure, someone with more knowledge of dependencies might be able to help.

Thanks, that has it going.

My contribution would be you can cmod u + x (make it executable) on the 15rc1_patch_inatall and then sudo 15rc1_patch_inatall, instead of executing each command line by.

Ahh, just finished compiling and after rebooting the sweet sound of music for the first time on this laptop :)

Now, how do we keep updates from killing the sound?

---

### Post by yoblin on 2007-09-25
Yeah the most recent update kills the sound for me too... guess I'll have to recompile which is annoying. Anyone have any ideas how to fix that problem?

---

### Post by barrmulio on 2007-09-25
firstoff guys - thanks for the great guide

wireless is working great, but the alsa-utils is giving me an error (scroll to the bottom)
```
root@kyle:/home/felipe/Desktop/alsa/alsa-driver-1.0.15rc1# cd ../alsa-utils-1.0.15rc1
root@kyle:/home/felipe/Desktop/alsa/alsa-utils-1.0.15rc1# ./configure && make && make install
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.12... found.
checking for snd_ctl_open in -lasound... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for initscr in -lncurses... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating alsactl/Makefile
config.status: creating alsamixer/Makefile
config.status: creating amidi/Makefile
config.status: creating amixer/Makefile
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: creating alsaconf/alsaconf
config.status: creating alsaconf/Makefile
config.status: creating alsaconf/po/Makefile
config.status: WARNING:  alsaconf/po/Makefile.in seems to ignore the --datarootdir setting
config.status: creating aplay/Makefile
config.status: creating include/Makefile
config.status: creating iecset/Makefile
config.status: creating utils/Makefile
config.status: creating utils/alsa-utils.spec
config.status: creating seq/Makefile
config.status: creating seq/aconnect/Makefile
config.status: creating seq/aplaymidi/Makefile
config.status: creating seq/aseqdump/Makefile
config.status: creating seq/aseqnet/Makefile
config.status: creating speaker-test/Makefile
config.status: creating speaker-test/samples/Makefile
config.status: creating include/aconfig.h
config.status: include/aconfig.h is unchanged
config.status: executing po-directories commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
config.status: executing depfiles commands
Making all in include
make[1]: Entering directory `/home/felipe/Desktop/alsa/alsa-utils-1.0.15rc1/include'
make  all-am
make[2]: Entering directory `/home/felipe/Desktop/alsa/alsa-utils-1.0.15rc1/include'
make[2]: Leaving directory `/home/felipe/Desktop/alsa/alsa-utils-1.0.15rc1/include'
make[1]: Leaving directory `/home/felipe/Desktop/alsa/alsa-utils-1.0.15rc1/include'
Making all in alsactl
make[1]: Entering directory `/home/felipe/Desktop/alsa/alsa-utils-1.0.15rc1/alsactl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/felipe/Desktop/alsa/alsa-utils-1.0.15rc1/alsactl'
Making all in alsaconf
make[1]: Entering directory `/home/felipe/Desktop/alsa/alsa-utils-1.0.15rc1/alsaconf'
Making all in po
make[2]: Entering directory `/home/felipe/Desktop/alsa/alsa-utils-1.0.15rc1/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/home/felipe/Desktop/alsa/alsa-utils-1.0.15rc1/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/felipe/Desktop/alsa/alsa-utils-1.0.15rc1/alsaconf'
make: *** [all-recursive] Error 1

```

without this, I can't run alsaconf - thanks in advance for any help

---

### Post by dvenardos on 2007-09-25
> **barrmulio said:**
> firstoff guys - thanks for the great guide

wireless is working great, but the alsa-utils is giving me an error (scroll to the bottom)
```

make[2]: Entering directory `/home/felipe/Desktop/alsa/alsa-utils-1.0.15rc1/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory

```

without this, I can't run alsaconf - thanks in advance for any help

You are getting an error on stat (see below) did you run using sudo?

int stat(const char *path, struct stat *buf);
int fstat(int filedes, struct stat *buf);
int lstat(const char *path, struct stat *buf);
Description

These functions return information about a file. No permissions are required on the file itself, but -- in the case of stat() and lstat() -- execute (search) permission is required on all of the directories in path that lead to the file.

---

### Post by barrmulio on 2007-09-25
> **dvenardos said:**
> You are getting an error on stat (see below) did you run using sudo?

I tried running with sudo and as superuser (root).  The command above was as root

[update]
rebooted - playback is working fine, but the mic input is extremely choppy and unusable

---

### Post by dvenardos on 2007-09-25
> **barrmulio said:**
> rebooted - playback is working fine, but the mic input is extremely choppy and unusable

I don't have a mike so I can't test that. Perhaps others can test and submit a bug request if the same problem occurs.

---

### Post by yoblin on 2007-09-27
Haven't tried using the mic input, but as far as wireless I've found that sometimes the wireless doesn't connect correctly but if you suspend and unsuspend the laptop then that will knock it back into shape. Not sure why it works, but it does, and it's been helpful after figuring out that trick.

---

### Post by dvenardos on 2007-09-27
Anyone willing to file a laptop testing report for this laptop?
[https://wiki.ubuntu.com/LaptopTesting](https://wiki.ubuntu.com/LaptopTesting)

---

### Post by Muxplex on 2007-09-27
Excellent info in this thread!  

I just picked up an ML3109 yesterday, and I can't wait to load Ubuntu into it this evening.  I'm guessing that if I load and then do all the updates and then do the procedures for sound and wireless that all settings will stay as needed ...  

Anyway, one thing I find odd about this notebook is that the box it came in says the notebook has 512MB ram and a 80 GB hard drive.  Yet, the system bios and Windows properties and Ubuntu Live CD all report there is 446MB ram and a 74 GB or so  hard drive.  I know in the "old days" there could be a little bit of difference in the sizes the manufacturer stated compared to the actual sizes, but it was due to the kilo 1024 or 1000 usage thing.  The disparity here seems to be something else all together.  So, I'm wondering if all the ML3109s out there have 446MB ram as stock, and how Ubuntu will perform with only 446MB ram ...

---

### Post by yoblin on 2007-09-27
> **Muxplex said:**
> Excellent info in this thread!  

I just picked up an ML3109 yesterday, and I can't wait to load Ubuntu into it this evening.  I'm guessing that if I load and then do all the updates and then do the procedures for sound and wireless that all settings will stay as needed ...  

Anyway, one thing I find odd about this notebook is that the box it came in says the notebook has 512MB ram and a 80 GB hard drive.  Yet, the system bios and Windows properties and Ubuntu Live CD all report there is 446MB ram and a 74 GB or so  hard drive.  I know in the "old days" there could be a little bit of difference in the sizes the manufacturer stated compared to the actual sizes, but it was due to the kilo 1024 or 1000 usage thing.  The disparity here seems to be something else all together.  So, I'm wondering if all the ML3109s out there have 446MB ram as stock, and how Ubuntu will perform with only 446MB ram ...

THe hard drive difference is due to the disparity you stated. The ram difference is because of the shared ram with the video card. You can change the ram usage in the bios between 32 - 128 megs. I'm running with a gig of ram and 128 megs reserved for video, but 512 megs with 64 reserved for video worked fine with compiz-fusion as well.

---

### Post by Muxplex on 2007-09-27
Excellent!  Thanks so much for clearing that up for me :)

---

### Post by dvenardos on 2007-09-27
> **Muxplex said:**
> Excellent info in this thread!  

..., and how Ubuntu will perform with only 446MB ram ...

Ubuntu runs great with the standard ram. An even faster experience is available if you install XUbuntu, but there is no need with this laptop.

---

### Post by barrmulio on 2007-09-27
System runs great on just 512mb ram.  I have it dual booting with a clean install of Vista business (cant get quickbooks to run on wine :( ) and it's a huge difference.  

Wireless for me works just fine, tested it at starbucks, around the home (better than the acer i had, much much better than the dell d600 i have for work).  Very surprised how good and stable the signal is on this laptop.

Sound playback is now working fine.  Recording cannot be done with the mic input (tested different mics, and both are working fine on a feisty desktop i have), probably has to do with the make errors I'm getting though....

---

### Post by Muxplex on 2007-09-30
Ok, so I'm diggin' this laptop.  I installed 1GB more ram.  Got the module from Fry's for $ 29.99, after rebate. 

I've now got Ubuntu 7.04 loaded in.  I've got it seeing the wireless card, and it finds my AP but won't connect.  ( It's a Linksys BEFW11S4v4 with latest firmware ).  Ubuntu won't connect even to the AP with no security/open network.  Windows Vista connects, but "Limited"--that is to say, it associates with the AP but won't pickup a DHCP IP.  Also of note is that a static IP assigned to the laptop wireless still has a "limited" connection ... no internet and no LAN access.  I believe the problem to be that the AP/router is Wireless B and the Laptop is connecting at 54MB/s ( G ).  Is there a way for me to 'force' Ubuntu to connect at 11MB/Sec?  I know there was a way to do this in Win 2000, but can't find it in Vista or Ubuntu.  I don't want to buy a new AP/router; I've grown fond of this one.  

( Haven't messed with the Ubuntu sound issue yet ... )

p.s. the added memory makes a huge difference in performance ... :)

---

### Post by yoblin on 2007-09-30
> **Muxplex said:**
> Ok, so I'm diggin' this laptop.  I installed 1GB more ram.  Got the module from Fry's for $ 29.99, after rebate. 

I've now got Ubuntu 7.04 loaded in.  I've got it seeing the wireless card, and it finds my AP but won't connect.  ( It's a Linksys BEFW11S4v4 with latest firmware ).  Ubuntu won't connect even to the AP with no security/open network.  Windows Vista connects, but "Limited"--that is to say, it associates with the AP but won't pickup a DHCP IP.  Also of note is that a static IP assigned to the laptop wireless still has a "limited" connection ... no internet and no LAN access.  I believe the problem to be that the AP/router is Wireless B and the Laptop is connecting at 54MB/s ( G ).  Is there a way for me to 'force' Ubuntu to connect at 11MB/Sec?  I know there was a way to do this in Win 2000, but can't find it in Vista or Ubuntu.  I don't want to buy a new AP/router; I've grown fond of this one.  

( Haven't messed with the Ubuntu sound issue yet ... )

p.s. the added memory makes a huge difference in performance ... :)

I'm sure it's possible to debug the problem with Ubuntu, but I would try to get vista connecting first then Ubuntu (you're dual booting?), as the NDISWrapper is a hack of sorts. If vista can't even connect, it's hard to tell when using ubuntu if you have NDISWrapper set up correctly if there's no way to test it..  YOu might be able to disable wireless G in the bios, I'm not sure. Try enabling DHCP on the router and see if it can connect then go from there.

---

### Post by yonakatsuki on 2007-10-08
There is a small glitch I noticed. I'm wondering if it's just my laptop, or all ML3109 laptops, but when using Ubuntu, I have problems with adjusting the screen brightness with the keyboard Fn+Up/Down keys. I either get max brightness, or minimum brightness. That's it. I tried a different Linux distro, Debian, and it had no problems. I'm confused. Is it just me?

---

### Post by yoblin on 2007-10-08
> **yonakatsuki said:**
> There is a small glitch I noticed. I'm wondering if it's just my laptop, or all ML3109 laptops, but when using Ubuntu, I have problems with adjusting the screen brightness with the keyboard Fn+Up/Down keys. I either get max brightness, or minimum brightness. That's it. I tried a different Linux distro, Debian, and it had no problems. I'm confused. Is it just me?

No, mine does that too (Feisty). It wasn't a big deal to me, so I didn't worry about it, but maybe we can find a way to fix it since debian seems to work with it. I probably won't devote much time to it, but I'll let you know if I find an easy solution.

---

### Post by dvenardos on 2007-10-08
> **yonakatsuki said:**
> There is a small glitch I noticed. I'm wondering if it's just my laptop, or all ML3109 laptops, but when using Ubuntu, I have problems with adjusting the screen brightness with the keyboard Fn+Up/Down keys. I either get max brightness, or minimum brightness. That's it. I tried a different Linux distro, Debian, and it had no problems. I'm confused. Is it just me?
Mine too. The brightness key seems to be pretty flaky - it doesn't always toggle between dim and bright. Mine also automatically dims when I unplug the AC, I suppose that is a desired effect. 

How do you set the screen brightness w/o using the function button?

---

### Post by Jerryonimo on 2007-10-09
I suppose if we raise enough of a stench, then the Gutsy Gibbon guys will test us.:lolflag:
I also have an annoying problem with my sound.  I tried installing alsa, but the annoying system beep is permanent, which probably annoys other people around me.
Still, [SIZE="4"]**Ubuntu rocks!**[/SIZE]:guitar:

---

### Post by Muxplex on 2007-10-10
Yep, I'm having the same behavior with screen brightness ( Ubuntu v7.04 ).  I haven't done any looking around for the settings for AC plugged/unplugged behaviors yet; but when I'm unplugged my screen goes dim, too.

So, my sound and wireless are good to go now.  My wireless problem was with the firmware in my Linksys BEFW11S4 v4 . Although the latest few versions of firmware supposedly support WPA, it is widely reported on the net that it is problematic at best in most cases.  So, I bought a new router ( Buffalo WRT 125 that will get DD-WRT when I get time ). 

Now, my newest mystery is that I was messing around with Network settings last night and somehow my wireless card is no longer automatically found when booting into Ubuntu. I've been doing a 'sudo modprobe ndiswrapper' in a gnome-terminal to get the card up.  And, I know that I can put the modprobe statement into rc.local to 'fix it'.  But, where was the setting that first made the card come alive on boot? That is to say, I'm guessing when I installed ndiswrapper and then the windows realtek driver that the modprobe statement was automatically put somewhere--and, later was deleted or commented out when I was messing with the Network settings.  Anyone know where it originally took care of this?

---

### Post by bigoriginal on 2007-10-11
Please, please help. I bought this computer for my wife hoping to run linux on it. I have gotten the wireless working, but for some reason everytime I restart the computer the wireless is gone. I run the last 

sudo bash
ndiswrapper -i /home/amanda/Drivers/Realtek_RTL8185_Windows_6.1102.0702.2007,UI_1.00.0006/Cardbus/RTL8185/WIN2000/net8185.inf
ndiswrapper -l
modprobe ndiswrapper

commands. I added it to the rc.local but it didn't work. Is there anyway to run this as a script or anything? Also I can't get the sound to work but I'm not getting any errors and I followed all the commands and it seemed fairly early. I'm willing to format again if someone thinks they can walk me through the entire process.

Anyways thanks for any help anyone can give

---

### Post by dvenardos on 2007-10-11
Did you use the GUI installation tool ndisgtk when setting up the wireless driver? The GUI installation tool sets up everything necessary for it to load on startup. If not try installing the GUI and use it for installation.

When compiling the sound, did you download the proper version? It is no longer on the front page of the link, you have to go to the history to get the proper version.

---

### Post by bigoriginal on 2007-10-11
[http://donnieknows.com/bin/view/Main/GatewayML3109#Wireless](http://donnieknows.com/bin/view/Main/GatewayML3109#Wireless)

This is a useful page on installing ubuntu on the 3109. The author has created a script that does all the downloading and installation for the sound. Haven't tried it yet, but looks promising.

---

### Post by bigoriginal on 2007-10-11
yes, I downloaded the right version (rc1). I'm going to try the script I listed. How do i run and install with the gui? I did everything from the command line.

---

### Post by bigoriginal on 2007-10-12
Sucess. Well at least partially. So I formatted and reinstall ubuntu. I got the sound working with the script I mentioned and it worked beautifully. Downloaded all the drivers and everything automatically. As far as my wireless is concerned, I install using the gui instead of command line. Its recognizing again after I reboot, but now its not connecting. So i don't know whether this is an improvement or not. Any ideas? I'll post if I fix anything.

---

### Post by bigoriginal on 2007-10-12
K so my wireless is back in the same spot
I can get it to work but when I turn off the machine, I'm back in the same spot. 
Can anyone create me a script that I can run after I boot. 
It just needs to do the following lines

sudo bash
modprobe ndiswrapper

---

### Post by Muxplex on 2007-10-12
Just type the following into a terminal window:

  sudo gedit /etc/modules

and then go to the bottom of the file that opens and type

  ndiswrapper

and then save the file. Then, when you reboot your system will
probe for and find the wireless card.

---

### Post by Jerryonimo on 2007-10-12
> **bigoriginal said:**
> Please, please help. I bought this computer for my wife hoping to run linux on it. I have gotten the wireless working, but for some reason everytime I restart the computer the wireless is gone.
For some reason, one time when I plugged in my wireless adapter without Ndiswrapper, I was able to simply connect.
Mine is a Belkin Wireless G USB adapter.  You might want to try it.  It costs about thirty to fifty bucks.

---

### Post by dvenardos on 2007-10-19
Will the first person upgrading to 7.10 please post their results with this laptop (i.e. did the upgrade break anything).

Thanks

---

### Post by yoblin on 2007-10-19
I've run the live cd for gutsy, and the good news is that wireless now works natively, it detects all of the wireless networks in roaming mode. 

The bad news is, when I try to connect to one of the networks, it crashes and the laptop must be turned off.

The caps lock and scroll lock lights flash, anyone know what this means?

---

### Post by dvenardos on 2007-10-19
> **yoblin said:**
> I've run the live cd for gutsy, and the good news is that wireless now works natively, it detects all of the wireless networks in roaming mode. 

The bad news is, when I try to connect to one of the networks, it crashes and the laptop must be turned off.

Live CD, didn't think about trying that, that is a good way to go. 
Did you file a bug report?

---

### Post by yoblin on 2007-10-19
Haven't filed a bug report, I'm hoping I can get some more details on the problem maybe installing is what needs to be done as opposed to running the live cd, is there a difference?

---

### Post by dvenardos on 2007-10-19
> **yoblin said:**
> Haven't filed a bug report, I'm hoping I can get some more details on the problem maybe installing is what needs to be done as opposed to running the live cd, is there a difference?
It should be the same, just slower, but I am not sure about that.

You know that you can do the upgrade from within 7.04 instead of a fresh install?
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by discoandy on 2007-10-19
Wanted to update with my experience in gutsy.  Wireless works out of the box, until I try to connect to an encrypted network.  Then it freezes with the lights blinking as described before.

but connecting to my open network is great and is how I'm writing this at the moment.

The 3d effects are working well.

I can't seem to get the sound to work.  Tried that webpage that had the script to run which worked in 7.04, but doesn't work in gutsy now. 

so everything is great other than
[LIST=1]
[*]connecting to password-protected wireless access points
[*]sound
[/LIST]

---

### Post by yoblin on 2007-10-19
> **discoandy said:**
> Wanted to update with my experience in gutsy.  Wireless works out of the box, until I try to connect to an encrypted network.  Then it freezes with the lights blinking as described before.

but connecting to my open network is great and is how I'm writing this at the moment.

The 3d effects are working well.

I can't seem to get the sound to work.  Tried that webpage that had the script to run which worked in 7.04, but doesn't work in gutsy now. 

so everything is great other than
[LIST=1]
[*]connecting to password-protected wireless access points
[*]sound
[/LIST]

Thanks for the feedback. I bet we'll be able to get the sound working, just have to look a bit more into the compilation problems, but the wireless I don't really know where to start.

I filed a bug report here, add your own info to it if you wish:

[https://bugs.launchpad.net/ubuntu/+bug/154725](https://bugs.launchpad.net/ubuntu/+bug/154725)

---

### Post by yoblin on 2007-10-20
Hi everyone,

I already got an email from someone (presumably someone with more linux knowledge than myself) on the bug I posted.

It would be helpful if some people here would try to run the liveCD and post their experiences under the bug report URL I listed above, ESPECIALLY if you are running a WPA protected network. My network is WEP, and we're trying to narrow down the problem.

Plus, the more attention we call to this issue, the faster it can get fixed.

---

### Post by SaintJohnShawn on 2007-10-20
Same issue on my laptop.  Connecting to the WEP freezes the computer.

---

### Post by what4893 on 2007-10-21
I did the upgrade within 7.04 to 7.10. Something I noticed about the wireless too is that having done the upgrade my wireless keys were all stored. As soon as I gave my password for the keyring to retrieve them that's when my computer locked up. In trying to connect to a new wireless network I ran into the same exact problem with WPA encryption. The visual effects are working quite nicely. I haven't gotten every single one working yet. The fades, wobbly windows, and other basic effects work fine. Still no luck with the sound though.

---

### Post by what4893 on 2007-10-21
Well after a little tinkering just now I actually got the sound working. Now note that I did the upgrade within 7.04 so I'm not sure how this will work under other circumstances. Using the directions provided by pablodavid on page 3 of this thread with one tiny change I was able to once again get my sound working. Download all the files and follow all the directions pablodavid gives. The one change I had to make was when compiling the alsa-lib package I had to "sudo bash" before doing that. The one thing that didn't work for me though was compiling alsa-utils. Fortunately, these aren't needed to just get sound working, they include alsaconf and other such applications for adjusting volume levels. If you can't hear anything and successfully compiled both alsa-driver and alsa-lib then most likely your volume is turned down in alsa. If you didn't have any luck compiling alsa-utils as I didn't then you can go to Add/Remove Applications on the bottom of the applications menu, and search alsa mixer. The application I installed was called alsamixergui, it will appear under applications > Sound & Video > alsamixergui and in there you can adjust your volume levels. If that still doesn't fix the problem I'm afraid this is about where my linux knowledge ends. Let me know if this works for anybody else.

---

### Post by alphabetical on 2007-10-22
hey!  wow I wasn't expecting this thread to boom quite so much...

Well I followed the tut on page 3 here's what I got

ask@ask-laptop:~$ sudo tar xfj alsa-driver-1.0.15rc1.tar.gz 
tar: alsa-driver-1.0.15rc1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

could I get assistance please ??

I'm running Dapper

Oh yeh I got the wifi to work somehow a few months ago!!!  I'm not sure how but it works

---

### Post by dvenardos on 2007-10-22
> **alphabetical said:**
> 
ask@ask-laptop:~$ sudo tar xfj alsa-driver-1.0.15rc1.tar.gz 
tar: alsa-driver-1.0.15rc1.tar.gz: Cannot open: No such file or directory

The file can't be found from your home directory. You need to change into the directory where you downloaded the file. You must be able to see the file when typing "ls" at the command prompt.

---

### Post by alphabetical on 2007-10-22
By "see" like have the folder mhere the file is stored open and actually inview?  I currently have all the files I needed to DL in a desktop folder "alsa"

---

### Post by dvenardos on 2007-10-22
> **alphabetical said:**
> By "see" like have the folder mhere the file is stored open and actually inview?  I currently have all the files I needed to DL in a desktop folder "alsa"
you are telling tar to operate on the file in the current directory, so you need to:
cd desktop/alsa

---

### Post by alphabetical on 2007-10-22
> **dvenardos said:**
> you are telling tar to operate on the file in the current directory, so you need to:
cd desktop/alsa

OK I understand what I need to do know....thing is doing it :( ... I get a no such file/directory error!!! Grrrrr  I've tried many variations and locations.....but.....

Do you mind/and are willing/able to help via IM?  It may be easier...I've AIM and MSN and yahoo


**EDIT**

zomg noob  I got it!  lol


**RE-EDIT**

Running  patch alsa-driver-1.0.15rc1/alsa-kernel/pci/hda/  it's been going for 25mins already...just 

ask@ask-laptop:~/Desktop/alsa$ patch alsa-driver-1.0.15rc1/alsa-kernel/pci/hda/ 
  <--- cursor here 

Is this running right?

---

### Post by alphabetical on 2007-10-22
Left it running...it's been 2 hours...Hmmmmmmmm....

---

### Post by what4893 on 2007-10-22
alphabetical,

You entered the second part of this line from the text file right? I don't have my laptop in front of me but I remember you had to actually type in the name of the patch and the name of the alsa-driver file. Double check that you entered that correctly. I'll double check what the whole line should be a post back in a few minutes. The line you posted was only half of the line you needed to enter.

The patching should only take about 3 minutes no more than 5 minutes.

Here is the complete line to perform the patch:
patch alsa-driver-1.0.15rc1/alsa-kernel/pci/hda/patch_sigmatel.c < patch_sigmatel.c.patch-1.0.15rc1-simple

---

### Post by Muxplex on 2007-10-23
Go to the following web site:

  [http://donnieknows.com/bin/view/Main/GatewayML3109#Wireless](http://donnieknows.com/bin/view/Main/GatewayML3109#Wireless)

and look in the *Sound* section.  Donnie, from the above site, wrote
a  little script that will fix up your sound problem.

---

### Post by CrazyBoyD on 2007-10-27
I just upgraded to Gutsy from Feisty and this broke my sound and wireless networking.  I was unable to fix these using the same methods that got them working so I reinstalled using the live cd.  I got sound working no problem using the instructions from earlier in this thread, but I noticed that some people were saying they had some wireless functionality without installing ndiswrapper.  I'm not seeing any wireless networks listed at all.

---

### Post by 92sho16 on 2007-11-12
I followed the donnie knows tutorial and got the wireless to work but i have to use the modprobe code everytime i reset.

---

### Post by Muxplex on 2007-11-17
Try this;

[http://ubuntuforums.org/showpost.php?p=3520891&postcount=59](http://ubuntuforums.org/showpost.php?p=3520891&postcount=59)

---

### Post by yoblin on 2007-11-28
Hi everyone,

Since we have feisty all worked out, I decided to take the plunge and update to Gutsy from Feisty. It's been more of a pain than I expected...

Things I noticed after updating:

[INDENT]- Screen brightness hotkeys now work better (not just low/high anymore!)
- Startup seems to take a bit longer, but nothing too bad
- No software broke in the update, including crossover, but I'm guessing Vmware would need to be reinstalled (I didn't have it installed)
- Some settings got reset, I need to change my font and power preferences back manually
- Wireless seems more stable[/INDENT]

Problems SOLVED after upgrading:

[INDENT]- Need to change session: When you login, select 'gnome' as your session, rather than gnome with xgl, and make it your default
- Compiz config manager doesn't work: you have to reinstall by running:

	[INDENT]sudo apt-get remove compizconfig-settings-manager[/INDENT]
[INDENT]sudo apt-get install compizconfig-settings-manager[/INDENT]

- Indexing really kills performance on this laptop, I turned it off in the prefs
- Encrypted wireless doesn't work: you need to disable the new built-in drivers and resort to the ndiswrapper that's installed. You can do this by running:
	[INDENT]sudo gedit /etc/modprobe.d/blacklist

	then add the following to it:

	blacklist r818x
	blacklist r8180
	blacklist r8187

	Then reboot and it should work. If it still crashes, run 'sudo lsmod' and look for the driver that you need to blacklist.

	also, be sure to click 'deny' when you first login before changing the driver over, or the computer will crash.[/INDENT]
[/INDENT]

Problems UNSOLVED after upgrading:
[INDENT]
- Sound won't install like it did before
- Suspending and hibernating crashes the computer (Is this just me? I had some power manager installed before the update..)
[/INDENT]

If anyone feels like helping to fix these two remaining problems, post any helpful info! I'm working on them but not making much progress!

yoblin

--- update on suspend issue ----

looks like this is an ATI driver issue: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653)

SOLVED! See post below.

---- Update on Sound ----

SOLVED! See post below.

---

### Post by dvenardos on 2007-11-28
> **yoblin said:**
> Hi everyone,

Since we have feisty all worked out, I decided to take the plunge and update to Gutsy from Feisty. It's been more of a pain than I expected....
Unfortunately, I am relying on this laptop now (Feisty), so I can't afford to mess around with it.
Hopefully, someone else can help resolve the issues.
I am still monitoring this thread, even if I can't help out.

Best

---

### Post by lvleph on 2007-12-02
I upgraded to Gutsy and got the wireless to work using [donnieknows](http://donnieknows.com/bin/view/Main/GatewayML3109). This works in both 2.6.22-14 and 2.6.20-16 kernels. I have the sound working in the latter using donnieknows, but am still working on 2.6.22-14 kernel. I will update if I get it working.

---

### Post by yoblin on 2007-12-03
Good news! Gutsy is now 100% works on this laptop. I have figured out supspending and sound issues.

You're going to have to recompile the kernel though. Basically, I had to enable the intel sound module and switch from SLUB to SLAB. The compile-time a little under 2 hours on the laptop, and you'll probably want a wired internet connection because ndiswrapper will need fixing. If anyone has interest, I can upload my pre-compiled image file later so that this whole thing is a lot easier.

Below are the instructions to getting sound and suspend working, after you do the stuff from above. Most of the beginning stuff was grabbed from [http://blog.vaxius.net/?p=19](http://blog.vaxius.net/?p=19), with big thanks to him.

They are a little unclear because I was doing a lot of trial and error, so if anyone wants to clean them up feel free.

- yoblin


----------------------------------------


sudo -i
apt-get install linux-backports-modules-generic    # Don't know if this is necessary
apt-get install build-essential kernel-package linux-source

cd /usr/src
rm linux    # Probably not necessary?
tar xvfj linux-source-2.6.22.tar.bz2
ln -s linux-source-2.6.22 linux

apt-get install libqt3-mt-dev

cd /usr/src/linux
cp /boot/config-2.6.22-14-generic .config
make xconfig
[INDENT]	--> in 'general setup' section, select SLAB as opposed to SLUB
	--> go to sound -> advanced linux .... -> pci devices --> select 'intel hd audio' and press 'm'
	--> don't forget to hit 'save'!!![/INDENT]

make-kpkg clean
make-kpkg --append-to-version=-with-slab kernel_image --initrd binary

(wait ~2 hours)

cd ..
dpkg -i linux-image-2.6.22.9-with-slab*.deb linux-headers-2.6.22.9-with-slab*.deb
ln -s /lib/firmware/2.6.22-14-generic /lib/firmware/2.6.22.9-ubuntu1-with-slab
update-initramfs -u

reboot

sudo -i
apt-get install module-assistant dh-make debhelper debconf libstdc++5

download ati driver: [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)
go to linux x86 --> integrated/motherboard --> radeon xpress 200

cd <where you downloaded driver>

bash ati-driver-installer-*.run --buildpkg Ubuntu/gutsy
dpkg -i xorg-driver-fglrx_*.deb fglrx-kernel-source_*.deb fglrx-amdcccle_*.deb
apt-get -f install
module-assistant prepare
module-assistant update
module-assistant build fglrx
module-assistant install fglrx
depmod -a
mkdir /lib/modules/$(uname -r)/volatile
ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
aticonfig --initial
aticonfig --overlay-type=Xv

 - Make sure the following is in your /etc/X11/xorg.conf file: (gedit /etc/X11/xorg.conf)

Section "Extensions"
Option "Composite" "Disable"
EndSection

Section "ServerFlags"
Option "AIGLX" "off"
EndSection

 - Now keep fglrx from loading:

[INDENT]gedit /etc/default/linux-restricted-modules-common[/INDENT]

 - add:

[INDENT]DISABLED_MODULES="fglrx"[/INDENT]

 - set in /etc/default/acpi-support the following: (gedit /etc/default/acpi-support)

[INDENT]SAVE_VBE_STATE=false
POST_VIDEO=false
USE_DPMS=false[/INDENT]

REBOOT.

 - If you get libGL errors:
[INDENT]
sudo ln -s /usr/lib/libGLU.so.1.3.070001 /usr/lib/libGL.so.1[/INDENT]



 - If you fail to boot into gnome, like I did, boot into the 'failsafe gnome' session and simply run (in the folder you downloaded your ati driver):

[INDENT]sudo bash ati-driver-installer*.run

and go through the graphical setup, that worked for me! I restored my backed up xorg.conf before running the installer.[/INDENT]



 - If you lose wireless, like I did, just reinstall ndiswrapper:

[INDENT]	[http://sourceforge.net/project/showf...ease_id=537654](http://sourceforge.net/project/showf...ease_id=537654)

	Extract it to your desktop, and then open a terminal.

	change to the directory you extracted the files to and run:

	make
	sudo make install
	sudo modprobe ndiswrapper[/INDENT]


 - To get sound working, run donnie's script and reboot.

---

### Post by yoblin on 2007-12-04
Here's a few other issues you might encounter when upgrading to gutsy:

----

- If you get an error message when you resume from suspend, there is a typo/syntax error in line 9 of /etc/acpi/lid.sh that you need to fix:
[INDENT]
	sudo gedit /etc/acpi/lid.sh
	On line 9, change:

[INDENT]		if [ `CheckPolicy` == 0 ]; then exit; fi[/INDENT]

	to:

		[INDENT]if [ `CheckPolicy` = 0 ]; then exit; fi[/INDENT][/INDENT]

also, I think I have better luck resuming from standby when the screensaver is off..

- If ndiswrapper has trouble reloading after a suspend:

[INDENT]	add to acpi-support a line to reload ndiswrapper on resume:

[INDENT]		sudo gedit /etc/default/acpi-support
		add the following:[/INDENT]
			[INDENT]MODULES="ndiswrapper"[/INDENT][/INDENT]

- I have never gotten hibernate to work under any kernel, so I disabled it:

[INDENT]	sudo gedit /etc/default/acpi-support
	comment out the line:
[INDENT]
		# ACPI_HIBERNATE=true[/INDENT]
[/INDENT]

---

### Post by Driv3r912 on 2007-12-04
Hey everyone, any luck enabling sound on Ubuntu 7.10 for this computer?

---

### Post by dvenardos on 2007-12-04
> **Driv3r912 said:**
> Hey everyone, any luck enabling sound on Ubuntu 7.10 for this computer?Yes, see Yoblin's prior two posts above.

---

### Post by CrazyBoyD on 2007-12-04
I just attempted setting up wireless again on my 7.10 system and got ndiswrapper installed.  When I run Windows Wireless Drivers, it says net8185 Hardware present: yes, but no wireless networks would show up in network-manager.  When I go to network settings, no wireless network hardware is shown.  I installed wicd because this helped in 7.04, but again no wireless networks show up.  Under preferences->wireless interface, it just says None.  Anybody know what's going on here?

---

### Post by Driv3r912 on 2007-12-05
> **CrazyBoyD said:**
> I just attempted setting up wireless again on my 7.10 system and got ndiswrapper installed.  When I run Windows Wireless Drivers, it says net8185 Hardware present: yes, but no wireless networks would show up in network-manager.  When I go to network settings, no wireless network hardware is shown.  I installed wicd because this helped in 7.04, but again no wireless networks show up.  Under preferences->wireless interface, it just says None.  Anybody know what's going on here?

Hmm.. maybe something is wrong with the wireless card's connection itself. Make sure the card is enabled on the system (like on mine, you have to press FN + F2: Enables and disables wireless).

Also, if you are using the Gateway ML3109 (this topic's main model), you ccan see the wireless icon on the LED lights below the trackpad.

It's the first light, if it's lit, this means Wireless is enabled, if not, it's disabled.


If it's disabled: Press FN + F2, now the wireless is enabled - but still won't detect networks, so you have to restart Ubuntu 7.10.


Let us know on the results.




By the way, Yoblin :: could you upload that kernel image, it seems a bit complicated for me, and I don't want to risk my Ubuntu system. If possible, also give me the directions on how to install it, that's greatly appreciated. Thanks.

---

### Post by Driv3r912 on 2007-12-05
I edited my last post.

---

### Post by CrazyBoyD on 2007-12-05
My wireless was turned off after all.  But after turning it on and rebooting, no change.  Is there anything special that needs to be done to add it to my network configuration?

---

### Post by yoblin on 2007-12-05
> **CrazyBoyD said:**
> My wireless was turned off after all.  But after turning it on and rebooting, no change.  Is there anything special that needs to be done to add it to my network configuration?

I'm really not sure, I posted everything I had to do, try following the instructions a couple pages back. Also, try running this and see if it helps:

sudo modprobe ndiswrapper

I'm working on uploading the kernel images, btw

---

### Post by lvleph on 2007-12-06
Also, you will want to add ndiswrapper to /etc/modules file.

Oh and for those with not much room. Recompiling the Kernal takes a lot of space. I ran out of room before it finished. I had 8.7 GB partition. I will have to resize my partition.

---

### Post by Driv3r912 on 2007-12-06
How's the upload coming Yoblin?

---

### Post by CrazyBoyD on 2007-12-06
> **lvleph said:**
> Also, you will want to add ndiswrapper to /etc/modules file.

I tried this and wireless works now.  Thanks a lot.

---

### Post by yoblin on 2007-12-06
> **Driv3r912 said:**
> How's the upload coming Yoblin?


it's 250 megs, I'll upload it tonight and post link tomorrow morning. I'll use rapidshare unless someone would prefer something else.

---

### Post by Driv3r912 on 2007-12-06
> **yoblin said:**
> it's 250 megs, I'll upload it tonight and post link tomorrow morning. I'll use rapidshare unless someone would prefer something else.

Sounds good Yoblin. Thanks.

---

### Post by lvleph on 2007-12-07
Okay, so I noticed something this morning. I got to the first reboot in Yoblin's post. When I rebooted into 2.6.22-14 I had sound. Which obviously made me reluctant to even proceed further, however I did. What do you think happened that got the sound working at that point? It would be nice to figure that out, so that we could come up with a shorter version, and possibly still use SLUB.

---

### Post by yoblin on 2007-12-07
> **lvleph said:**
> Okay, so I noticed something this morning. I got to the first reboot in Yoblin's post. When I rebooted into 2.6.22-14 I had sound. Which obviously made me reluctant to even proceed further, however I did. What do you think happened that got the sound working at that point? It would be nice to figure that out, so that we could come up with a shorter version, and possibly still use SLUB.

The first reboot, as in you did the 'wait 2 hours' part? If so, then that's correct. You've recompiled your kernel with slab and the rest is just installing drivers etc..

---

### Post by yoblin on 2007-12-07
As promised, here's the pre-compiled image to save you two hours:

[http://download.yousendit.com/DFC5138D7D48E1E5](http://download.yousendit.com/DFC5138D7D48E1E5)  (image)
[http://download.yousendit.com/0548BB1E34C86D4E](http://download.yousendit.com/0548BB1E34C86D4E)  (headers)

I can upload the manual and source files too if someone needs them, but I THINK that's all you actually need...

To install them, I think you just have to place them in /etc/src/ and thencontinue from my instructions after the 'wait 2 hours' step... You might also have to edit your grub file like at the top of the page here: [http://blog.vaxius.net/?p=19](http://blog.vaxius.net/?p=19)

Let me know if that doesn't work and I'll try to figure it out, haven't ever installed a custom precompiled image myself.

---

### Post by Driv3r912 on 2007-12-07
One question Yoblin, will this fix the wireless so I can connect to an encrypted wireless point? I don't like my wireless being open.

---

### Post by yoblin on 2007-12-07
> **Driv3r912 said:**
> One question Yoblin, will this fix the wireless so I can connect to an encrypted wireless point? I don't like my wireless being open.

All you need to do to fix that problem in 7.10 is add the following to your /etc/modprobe.d/blacklist file:

blacklist r818x
blacklist r8180
blacklist r8187

Then reinstall ndiswrapper. You don't need a recompiled kernel for that.

(More complete info a couple pages back, page 9 I think..)

---

### Post by Driv3r912 on 2007-12-07
Thanks, I'll let you all know on the results later...

---

### Post by lvleph on 2007-12-07
> **yoblin said:**
> The first reboot, as in you did the 'wait 2 hours' part? If so, then that's correct. You've recompiled your kernel with slab and the rest is just installing drivers etc..

I rebooted before this > cd ..
dpkg -i linux-image-2.6.22.9-with-slab*.deb linux-headers-2.6.22.9-with-slab*.deb
ln -s /lib/firmware/2.6.22-14-generic /lib/firmware/2.6.22.9-ubuntu1-with-slab
update-initramfs -u Yes, I know that was not when I was suppose to reboot. That was accidental. I was half asleep.

So I hadn't linked to 2.6.22-9-with-slab or changed GRUB, and so when I booted, I booted to 2.6.22-14. So obviously, I didn't boot into the new kernel, right?

Am I just confused?

---

### Post by Driv3r912 on 2007-12-07
> **yoblin said:**
> As promised, here's the pre-compiled image to save you two hours:

[http://download.yousendit.com/DFC5138D7D48E1E5](http://download.yousendit.com/DFC5138D7D48E1E5)  (image)
[http://download.yousendit.com/0548BB1E34C86D4E](http://download.yousendit.com/0548BB1E34C86D4E)  (headers)

I can upload the manual and source files too if someone needs them, but I THINK that's all you actually need...

To install them, I think you just have to place them in /etc/src/ and thencontinue from my instructions after the 'wait 2 hours' step... You might also have to edit your grub file like at the top of the page here: [http://blog.vaxius.net/?p=19](http://blog.vaxius.net/?p=19)

Let me know if that doesn't work and I'll try to figure it out, haven't ever installed a custom precompiled image myself.

The /etc/src/ folder does not exist.

---

### Post by lvleph on 2007-12-07
Okay, I am up and running. I changed the enable_sound.sh, since the final release of alsa 1.0.15 had the patch already in it.
```
# get alsa-driver
if ! [ -f alsa-driver-1.0.15.tar.bz2 ]; then
    wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2
fi

# get alsa-lib
if ! [ -f alsa-lib-1.0.15.tar.bz2 ]; then
    wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2
fi

# get alsa-utils
if ! [ -f alsa-utils-1.0.15.tar.bz2 ]; then
    wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2
fi

# unpack files
if [ -d alsa-driver-1.0.15 ]; then rm -Rf alsa-driver-1.0.15; fi
tar xfj alsa-driver-1.0.15.tar.bz2 
if [ -d alsa-lib-1.0.15 ]; then rm -Rf alsa-lib-1.0.15; fi
tar xfj alsa-lib-1.0.15.tar.bz2
if [ -d  alsa-utils-1.0.15 ]; then rm -Rf alsa-utils-1.0.15; fi
tar xfj alsa-utils-1.0.15.tar.bz2 

# compile and install
cd alsa-lib-1.0.15/
./configure && make && sudo make install
cd ../alsa-utils-1.0.15/
./configure && make && sudo make install
cd ../alsa-driver-1.0.15/
./configure && make && sudo make install

# configure
sudo alsaconf
alsactl store
```

However, I do have one problem that has come up. Amarok will no longer start even after reinstallation.

> **Driv3r912 said:**
> The /etc/src/ folder does not exist.
Go ahead and make the directory.
mkdir /etc/src

EDIT: I think he meant /usr/src I could be wrong.

I know this is probably a dumb question, but I have not ever compiled a kernel before... It is okay to delete everything in the src folder correct? It is taking up 3.1G.

---

### Post by Driv3r912 on 2007-12-07
> **Driv3r912 said:**
> The /etc/src/ folder does not exist.

Nevermind, I installed the packages through Synaptic.

---

### Post by yoblin on 2007-12-07
> **Driv3r912 said:**
> The /etc/src/ folder does not exist.

sorry, meant /usr/src

my bad

I'm not sure if you can delete everything in the src folder, try renaming the larger files in there and see if the system still runs. If not just rename them back.

---

### Post by lvleph on 2007-12-07
Okay, I got an error message from amarok.
```
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amarokapp: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

---

### Post by yoblin on 2007-12-07
> **lvleph said:**
> Okay, I got an error message from amarok.
```
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amarokapp: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

have you tried running:

 sudo ln -s /usr/lib/libGLU.so.1.3.070001 /usr/lib/libGL.so.1

---

### Post by lvleph on 2007-12-07
I ended up installing libgl1-mesa-swx11-i686 from synaptic and now it works. I guess I didn't recognize the error as something you already pointed out.

---

### Post by Driv3r912 on 2007-12-07
When I go to compile Ndiswrapper, it says:


make -C driver
make[1]: Entering directory `/home/nicholas/Desktop/ndiswrapper-1.50/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.22.9-with-slab/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/nicholas/Desktop/ndiswrapper-1.50/driver'
make: *** [all] Error 2

What's wrong?

---

### Post by lvleph on 2007-12-07
if that is the sudo make install step it means that the make step didn't work correctly, so try doing that again.

Yoblin-
I renamed the /usr/src/linux-headers-2.6.22.9-with-slab and it seems to be working just fine. But I am going to do some reading before I delete anything.

Also, now all my packages are untrusted. How do I fix that?

---

### Post by Driv3r912 on 2007-12-07
no, that's at the make step.

---

### Post by lvleph on 2007-12-07
> **Driv3r912 said:**
> no, that's at the make step.

I had the same problem, but I cannot remember the solution exactly. I think I hadn't completed all the instructions, or I rebooted. I just cant remember. I am sorry.


So it seems the sound problem could have been fixed using SLUB, according to the [Master Kernel Thread](http://ubuntuforums.org/showthread.php?t=311158&highlight=delete+kernel+source).
> Q. My High Definition sound (Azalia) does not work with the new kernel!:

A. This took me a long time to figure out because I didn't have sound either. You have to enable the Intel HD (Azalia) module in Advanced Linux Sound Architecture, even if it isn't Intel.

---

### Post by lvleph on 2007-12-07
These errors ```
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```seem to be related to [this](http://ubuntuforums.org/showthread.php?p=1264009).

---

### Post by Driv3r912 on 2007-12-07
GREAT NEWS!!!

I copied the .deb files to /usr/src/ and tried installing the kernel again - and everything works great!

Thanks a lot Yoblin.


Lets hope when Ubuntu 8 comes out - it'll have all this stuff fixed out and running natively.

---

### Post by alphabetical on 2007-12-11
I'm back...Progress has been made...that is in good and bad directions.

Majorly goofed my windows install tonight...giving unbuntu another go

For sound I made it to step 11 before any errors

1     rcalsasound stop
2     tar xfj alsa-driver-1.0.15rc1.tar.bz2 
3     tar xfj alsa-lib-1.0.15rc1.tar.bz2 
4     tar xfj alsa-utils-1.0.15rc1.tar.bz2 
5     patch alsa-driver-1.0.15rc1/alsa-kernel/pci/hda/patch_sigmatel.c < patch_sigmatel.c.patch-1.0.15rc1-simple
6     cd alsa-lib-1.0.15rc1/
7     ./configure && make && make install
8     cd ../alsa-utils-1.0.15rc1/
9     ./configure && make && make install
10   cd ../alsa-driver-1.0.15rc1/
11   ./configure && make && make install
12   alsaconf 
13   alsactl store

Here's what I got 

ask@ask-laptop:~/Desktop/alsa/alsa-driver-1.0.15$ sudo ./configure && make && make install
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Hmmmm....Help a n00b?

---

### Post by lvleph on 2007-12-11
> **alphabetical said:**
> I'm back...Progress has been made...that is in good and bad directions.

Majorly goofed my windows install tonight...giving unbuntu another go

For sound I made it to step 11 before any errors

1     rcalsasound stop
2     tar xfj alsa-driver-1.0.15rc1.tar.bz2 
3     tar xfj alsa-lib-1.0.15rc1.tar.bz2 
4     tar xfj alsa-utils-1.0.15rc1.tar.bz2 
5     patch alsa-driver-1.0.15rc1/alsa-kernel/pci/hda/patch_sigmatel.c < patch_sigmatel.c.patch-1.0.15rc1-simple
6     cd alsa-lib-1.0.15rc1/
7     ./configure && make && make install
8     cd ../alsa-utils-1.0.15rc1/
9     ./configure && make && make install
10   cd ../alsa-driver-1.0.15rc1/
11   ./configure && make && make install
12   alsaconf 
13   alsactl store

Here's what I got 

ask@ask-laptop:~/Desktop/alsa/alsa-driver-1.0.15$ sudo ./configure && make && make install
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Hmmmm....Help a n00b?

You are using [Donnieknows' instructions](http://donnieknows.com/bin/view/Main/GatewayML3109), right?

You need to run
```
sudo apt-get install build-essential
```
That will have the c-compiler in it. Which version of Ubuntu are you using? If you are using Gutsy that will not get you sound, unless you have compiled a new Kernel using [Yoblin's instructions](http://ubuntuforums.org/showpost.php?p=3887733&postcount=86).

---

### Post by ..sane.. on 2007-12-11
hi guys, im new....ive been following this thread for a couple days and i also have an ml3109 gateway with Ubuntu Gutsy......wireless configured itself when installed. although i have no sound.


i am following yoblin's instructions to the "T" until i get to here:

(wait ~2 hours)

cd ..
dpkg -i linux-image-2.6.22.9-with-slab*.deb linux-headers-2.6.22.9-with-slab*.deb
ln -s /lib/firmware/2.6.22-14-generic /lib/firmware/2.6.22.9-ubuntu1-with-slab
update-initramfs -u

i have waited the two hours, put "cd" in the terminal, but i don't understand this:

dpkg -i linux-image-2.6.22.9-with-slab*.deb linux-headers-2.6.22.9-with-slab*.deb

what do i replace the "*" with? i have tried going to the files in /usr/src and typing something like this:

 dpkg -i linux-image-2.6.22.9-with-slab_2.6.22.9-with-slab-10.00.Custom_i386.deb

that is how it is named within /usr/src.
although i get an error upon pressing enter.


what am i doing wrong?




thanks
..sane..

---

### Post by lvleph on 2007-12-11
> **..sane.. said:**
> hi guys, im new....ive been following this thread for a couple days and i also have an ml3109 gateway with Ubuntu Gutsy......wireless configured itself when installed. although i have no sound.


i am following yoblin's instructions to the "T" until i get to here:

(wait ~2 hours)

cd ..
dpkg -i linux-image-2.6.22.9-with-slab*.deb linux-headers-2.6.22.9-with-slab*.deb
ln -s /lib/firmware/2.6.22-14-generic /lib/firmware/2.6.22.9-ubuntu1-with-slab
update-initramfs -u

i have waited the two hours, put "cd" in the terminal, but i don't understand this:

dpkg -i linux-image-2.6.22.9-with-slab*.deb linux-headers-2.6.22.9-with-slab*.deb

what do i replace the "*" with? i have tried going to the files in /usr/src and typing something like this:

 dpkg -i linux-image-2.6.22.9-with-slab_2.6.22.9-with-slab-10.00.Custom_i386.deb

that is how it is named within /usr/src.
although i get an error upon pressing enter.


what am i doing wrong?




thanks
..sane..

```
cd ..
```
Is what you type into the terminal to tell it to move up one directory. It stand for Change Directory, and the ".." means up one. The directory you are currently in would be considered ".". If you type ls -a you will see "." and ".." listed. These are just shortcuts that point to current directory or parent directory, respectively. If you wanted to move up two directories you might use
```
cd ../..
```

The "*" is a wild card character. This allows the terminal to find any file or folder fitting the pattern *.

---

### Post by ..sane.. on 2007-12-11
ok i kind of understand. i used the cd .. it went from this:

root@kris-laptop:~# 


to this:

root@kris-laptop:/#

then i tried putting this in:

root@kris-laptop:/# dpkg -i linux-image-2.6.22.9-with-slab*.deb linux-headers-2.6.22.9-with-slab*.deb

and got an error:


dpkg: error processing linux-image-2.6.22.9-with-slab*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing linux-headers-2.6.22.9-with-slab*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-image-2.6.22.9-with-slab*.deb
 linux-headers-2.6.22.9-with-slab*.deb



and i also tried it like this:

root@kris-laptop:/# dpkg -i linux-image-2.6.22.9-with-slab*.deb

and got this error:

dpkg: error processing linux-image-2.6.22.9-with-slab*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-image-2.6.22.9-with-slab*.deb



what do i do now?

---

### Post by lvleph on 2007-12-11
~ means you are in the home directory and / means you are in the root directory. You need to be in the /usr/src directory to run dpkg -i linux-image-2.6.22.9-with-slab*.deb linux-headers-2.6.22.9-with-slab*.deb

do this
```
cd /usr/src/
dpkg -i linux-image-2.6.22.9-with-slab*.deb linux-headers-2.6.22.9-with-slab*.deb
```

---

### Post by ..sane.. on 2007-12-11
ok got past that part....thanks!

new error:


root@kris-laptop:/usr/src# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.22.9-with-slab
find: /lib/firmware/2.6.22.9-with-slab: No such file or directory
find: /lib/firmware/2.6.22.9-with-slab: No such file or directory
find: /lib/firmware/2.6.22.9-with-slab: No such file or directory
find: /lib/firmware/2.6.22.9-with-slab: No such file or directory
find: /lib/firmware/2.6.22.9-with-slab: No such file or directory
find: /lib/firmware/2.6.22.9-with-slab: No such file or directory

what happened?



the only files in: /lib/firmware are:2.6.22.9-ubuntu1-with-slab and 2.6.22-14-generic

---

### Post by alphabetical on 2007-12-11
ask@ask-laptop:~/Desktop/alsa/alsa-driver-1.0.15$ sudo ./configure && make && make install
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/ask/Desktop/alsa/alsa-driver-1.0.15
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux)

I'm using the instructions on page 3 by PabloDavid post # 26

I'm running 6.06 dapper.  I upgraded to Gusty and would hardlock with the wireless.  I already have a dapper CD so I installed that

---

### Post by lvleph on 2007-12-12
> **alphabetical said:**
> ask@ask-laptop:~/Desktop/alsa/alsa-driver-1.0.15$ sudo ./configure && make && make install
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/ask/Desktop/alsa/alsa-driver-1.0.15
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux)

I'm using the instructions on page 3 by PabloDavid post # 26

I'm running 6.06 dapper.  I upgraded to Gusty and would hardlock with the wireless.  I already have a dapper CD so I installed that
The hardlock in Gutsy, was probably caused from not having 
```
blacklist r818x
blacklist r8187
```
in /etc/modprobe.d/blacklist

---

### Post by lvleph on 2007-12-12
Anyone having a cpu heat issue after the new kernel install?

acpi -V says 85C

---

### Post by yoblin on 2007-12-12
> **lvleph said:**
> Anyone having a cpu heat issue after the new kernel install?

acpi -V says 85C

I got 60C after a 30 minute stress test, which doesn't prove much but I don't think I am having any issues. I'll keep my eye on it in the future, and let you know.

---

### Post by lvleph on 2007-12-13
Backing up files yesterday I hit 95C! I am going back to Feisty for now, with Gutsy or maybe Hardy on my test partition. Those temps are way too high to keep operating like that. I couldn't even sit the computer on my lap for longer than a couple minutes.

---

### Post by lvleph on 2007-12-13
> **yoblin said:**
> 
sudo -i
apt-get install linux-backports-modules-generic    # Don't know if this is necessary
apt-get install build-essential kernel-package linux-source

cd /usr/src
rm linux    # Probably not necessary?
tar xvfj linux-source-2.6.22.tar.bz2
ln -s linux-source-2.6.22 linux

apt-get install libqt3-mt-dev

cd /usr/src/linux
cp /boot/config-2.6.22-14-generic .config
make xconfig
[INDENT]	--> in 'general setup' section, select SLAB as opposed to SLUB
	--> go to sound -> advanced linux .... -> pci devices --> select 'intel hd audio' and press 'm'
	--> don't forget to hit 'save'!!![/INDENT]

make-kpkg clean
make-kpkg --append-to-version=-with-slab kernel_image --initrd binary

(wait ~2 hours)

cd ..
dpkg -i linux-image-2.6.22.9-with-slab*.deb linux-headers-2.6.22.9-with-slab*.deb
ln -s /lib/firmware/2.6.22-14-generic /lib/firmware/2.6.22.9-ubuntu1-with-slab
update-initramfs -u

reboot


You know I was just looking over this and realized a step has been left out, or I don't understand something. When you run the 
```
make xconfig
``` shouldn't you then tell it to load an alternate config file? That was the whole reason why you performed ```
cp /boot/config-2.6.22-14-generic .config
```.

---

### Post by yoblin on 2007-12-13
> **lvleph said:**
> You know I was just looking over this and realized a step has been left out, or I don't understand something. When you run the 
```
make xconfig
``` shouldn't you then tell it to load an alternate config file? That was the whole reason why you performed ```
cp /boot/config-2.6.22-14-generic .config
```.

I don't *think* so... the Makefile I have in  /usr/src/linux references .config by default so by copying it over you're just setting the starting point for configuration to the current configuration you have installed

I think so at least, does this seem correct?

---

### Post by alphabetical on 2007-12-13
> **lvleph said:**
> The hardlock in Gutsy, was probably caused from not having 
```
blacklist r818x
blacklist r8187
```
in /etc/modprobe.d/blacklist

OK.  Well I'm not going to be downloading the Gutsy ISO anytime  soon...Any idea about 

ask@ask-laptop:~/Desktop/alsa/alsa-driver-1.0.15$ sudo ./configure && make && make install
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/ask/Desktop/alsa/alsa-driver-1.0.15
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux)

---

### Post by lvleph on 2007-12-13
Well, you could use the search feature to find the version.h file and then use the --with-kernel=dir option. That probably isn't much help, but it could solve the problem.
Did you try using the donnieknows script that is linked in this thread?

The command should look something like this, I believe.

```
sudo ./configure && make && make install --with-kernel=/usr/src/linux
```

Also, did you use this command before you tried to instal the alsa
```
sudo apt-get install build-essential
```

---

### Post by lvleph on 2007-12-13
> **yoblin said:**
> I don't *think* so... the Makefile I have in  /usr/src/linux references .config by default so by copying it over you're just setting the starting point for configuration to the current configuration you have installed

I think so at least, does this seem correct?

[Source to why I believe it may be necessary.](http://www.howtoforge.com/kernel_compilation_ubuntu)
[Master Kernel Thread seems to suggest doing it too.](http://ubuntuforums.org/showthread.php?t=311158&highlight=kernel)

---

### Post by lvleph on 2007-12-15
> **yoblin said:**
> I don't *think* so... the Makefile I have in  /usr/src/linux references .config by default so by copying it over you're just setting the starting point for configuration to the current configuration you have installed

I think so at least, does this seem correct?

I started with a fresh install and recompiled the kernel using this command ```
cp /boot/config-`uname -r` .config && make oldconfig
``` and now I don't have the over heating issue. In fact, I compiling something right now and running at 68C. The last time I checked on the old kernel during a file copy (lots of big files) I hit 97F. I almost shut the computer down on the spot, but instead put frozen food under my laptop. lol That was the last straw. Now things seem to be running faster, quieter, and cooler.

---

### Post by lvleph on 2007-12-15
Okay, so I ran into a problem when installing the ATI driver. I cannot get into GNOME Desktop and I followed the directions for if that hapened and I still cannot get into the desktop on the new or old kernel. What do I do to fix this?

---

### Post by yoblin on 2007-12-15
> **lvleph said:**
> Okay, so I ran into a problem when installing the ATI driver. I cannot get into GNOME Desktop and I followed the directions for if that hapened and I still cannot get into the desktop on the new or old kernel. What do I do to fix this?

Thanks for the tip on compiling above.

Can you get in using the open source drivers? If you log in (safe mode or get to another terminal through the ctrl-alt-FX keys) and restore your xorg.conf file back to the open source driver before you installed the ati driver, does that at least allow you to log in? I think the ati driver probably makes a backup before it changes the settings.

---

### Post by lvleph on 2007-12-15
> **yoblin said:**
> Thanks for the tip on compiling above.

Can you get in using the open source drivers? If you log in (safe mode or get to another terminal through the ctrl-alt-FX keys) and restore your xorg.conf file back to the open source driver before you installed the ati driver, does that at least allow you to log in? I think the ati driver probably makes a backup before it changes the settings.
I am back in. I had a typo in my xorg.conf. I left out the n in EndSection. Everything is working so well now. Nice!

---

### Post by lvleph on 2007-12-15
So I noticed a new problem. The monitor brightness function does't work very well. I have two setting; dim and really dim. Not even sure where to begin with this problem.

---

### Post by lvleph on 2007-12-18
Okay, I found a solution that does not include compiling a new kernel, but will get your sound up.
Here is what you need to do.
Open software sources
System>>administration>>software sources>>updates tab>>click Unsupport Updates>>close
Open synaptic package manager
System>>administration>>synaptic package manager
search for backports and then select linux-backports-modules-2.6.2 2.6.22-14.11
Now click apply
Once that is done restart your system.
Sound!

---

### Post by CrazyBoyD on 2007-12-21
I tried installing linux-backports-modules-2.6.2 2.6.22-14.11, but it wasn't there.  I'm guessing you installed the linux-backports-modules package, which is now at version 2.6.22.14.21.  Anyway, I rebooted and no sound.  I did the donnieknows thing and still no sound.  Did I install the wrong package, or is there a step I missed?

---

### Post by lvleph on 2007-12-21
Yeah, they updated the package. You could try one of the other packages. If none of that is working make sure that nothing is muted using
```
alsamixer
```

---

### Post by yoblin on 2007-12-22
> **lvleph said:**
> So I noticed a new problem. The monitor brightness function does't work very well. I have two setting; dim and really dim. Not even sure where to begin with this problem.

That's where mine was with feisty, but with gutsy it has things fixed.

On another note, looks like new ATI drivers are out that fix the suspend issues for some people WITHOUT recompiling:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653)

anyone with a stock gutsy kernel want to test fglrx 7.12 and see if it fixes the suspend/hibernate issues?

---

### Post by lvleph on 2007-12-22
I will test it eventually. Probably within a couple days. I started with a fresh install, because I didn't like the way things were working with the new kernel. And I ended up with so many problems it was the easiest route.

---

### Post by Aximilli on 2008-01-09
> **yoblin said:**
> ---- EDIT -----

oh yeah, you might also need to run "sudo apt-get install build-essential" for the stuff to compile, forgot about that..

---------------

Alright, I'll try to post a more detailed explanation of what you need to do to get up and running. 


I just wanted to say that I followed this guide on the sound aspect and it worked beautifully. The only thing that might be worth noting is that the last two commands of 15rc1_patch_install didn't seem to work, but I rebooted and am now blasting Metallica through my little laptop speakers, to the annoyance of my co-workers. Thanks alot Yoblin!

---

### Post by ICouldBeatSimon on 2008-01-10
OMGosh.

I've been following this post for the last few days!!  EVENTUALLY, With all your efforts (especcially Yoblins) I was able to get sound and wifi working!  Needless to say, I did a little dance when I heard the ubuntu startup music...and danced even MORE when I saw my access point giving a signal! \\:D/ My next task will be the display stuff ](*,) didn't read it thoroughly yet.

Again, thank you thank you thank you for all your hard work and research!!!

---

### Post by lvleph on 2008-01-10
The easiest way to get your display working is to use [Envy](http://albertomilone.com/nvidia_scripts1.html).

---

### Post by ICouldBeatSimon on 2008-01-10
GUESS WHAT I DID!! I wanted to post complete instructions for the wifi and sound card issues, so I started over!  I reinstalled ubuntu while connected to the internet and got 159 updates.  
I got the build-essential package.  I added

blacklist r818x
blacklist r8187

to the /etc/modprobe.d/blacklist file

I followed pablodavid's instructions for installing windows wireless drivers and used the WIN2000 .inf file.

I then added ndiswrapper to the end of /etc/modules.

I followed Donnie's sound instructions.  That didn't work, so I followed pablodavid's instructions.

I MESSED IT UP BAD. NOW NONE OF IT WILL WORK!! :( :mad:

I would GREATLY appreciate any help here!

---

### Post by lvleph on 2008-01-10
If you look at my post which is 8 posts above yours you will see how to get sound working.

---

### Post by ICouldBeatSimon on 2008-01-10
OK. I got wireless working.  Here are my settings:

sudo apt-get install build-essential

updated linux (159 updates)

got latest g++ version

sudo gedit /etc/modprobe.d/blacklist
	added
		blacklist r818x
		blacklist r8180
		blacklist r8187

installed ndiswrapper-1.48rc2
	sudo make uninstall
	make
	sudo make install

in WIN2000 folder
	ndiswrapper -i net8185.inf
	ndiswrapper -l
	modprobe ndiswrapper

sudo gedit /etc/modules
	added to end
		ndiswrapper

I also have disgtk installed, but IDK if that helps at all.

Now for sound!

Thanks for the response lvleph.  I'll try it.  The first time, however, I remember getting the sound to work w/out doing what you suggested.  But I'll do w/e works!

Oh, and thanks for the Envy link as well.  I'll get started on that as soon as I can.

---

### Post by lvleph on 2008-01-11
Well, under Gutsy the old method doesn't work anylonger. If you did it under feisty it most certainly would work.

---

### Post by Calapity on 2008-01-15
Hey Guys. I have been watching this thread since the day I got my 3109 last month. 

Last week of December I installed Kubuntu Gutsy Gibbon (7.10). Only major issue is no audio. System is currently running fulling updated

Tried running the Enable_Sound.sh script before realizing I had to recompile the kernel first. Been using linux lightly for years, but never had to recompile the kernel. Being adventurous, I figured what the hell. 

So I start to follow Yoblins steps to recompile, and am currently stuck on the step below.

Done	sudo -i
Done	apt-get install linux-backports-modules-generic # Don't know if this is necessary
Done	apt-get install build-essential kernel-package linux-source

Done	cd /usr/src
Done	rm linux # Probably not necessary?
Done	tar xvfj linux-source-2.6.22.tar.bz2
Done	ln -s linux-source-2.6.22 linux

Done	apt-get install libqt3-mt-dev

Done	cd /usr/src/linux
Done	cp /boot/config-2.6.22-14-generic .config
make xconfig



When I type in Make Xconfig I get the following error:

=
[COLOR="Red"]scripts/kconfig/qconf arch/i386/Kconfig
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

qconf: cannot connect to X server :0.0
make[1]: *** [xconfig] Error 1
make: *** [xconfig] Error 2 [/COLOR]

Any Thoughts?

Thanks!!

---

### Post by lvleph on 2008-01-15
Run the following in the terminal
```
 lspci | grep VGA
```

and post the output. If nothing comes out post the output from
```
lspci
```

---

### Post by Calapity on 2008-01-15
Lvleph,

Thanks for the quick response. Output below.

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

---

### Post by lvleph on 2008-01-16
Can you paste your /etc/X11/xorg.conf. I should have asked that in the first place. It looks like you have the address set to 0.0 when it should be 5.0.

---

### Post by Calapity on 2008-01-16
Here you go:

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RC410 [Radeon Xpress 200M]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RC410 [Radeon Xpress 200M]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

---

### Post by FrooziE on 2008-01-17
Just figured out that you need to remove the ALSA driver that comes with ubuntu before doing any of this. I followed the instructions about 5 times and nothing happened, then I removed the old ALSA driver and then followed them and presto, sound! Just a side note.

---

### Post by lvleph on 2008-01-17
> **Calapity said:**
> Here you go:

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RC410 [Radeon Xpress 200M]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RC410 [Radeon Xpress 200M]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
I don't see what is wrong, so I guess I am not going to be of much help.

---

### Post by dvenardos on 2008-02-08
Just got this working again after upgrading to Gutsy. Glad I had this thread subscribed, I hope this gets easier. The upgrade asked about replacing modified files, wonder what would have happened if I said no?

---

### Post by yoblin on 2008-03-26
Been running the 8.04 Hardy Heron beta on the laptop for a while, sound now works out of the box in addition to everything else that works in Gutsy EXCEPT scrolling and right clicking from the trackpad on the laptop.

Can someone paste their xorg.conf from Gutsy? I want to see if I can get the trackpad functionality back!

thanks

---

### Post by dvenardos on 2008-03-27
Here is my xorg.conf.
Can you tell me if you can install vmware player. Under Gutsy the processor is reported as an i386 and you can't install the player. When download and compiling it runs like a dog, because it compiles with i386 code, it is for all intents and purposes unusable under Gutsy.

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
        Option          "MaxTapTime"            "0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RC410 [Radeon Xpress 200M]"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RC410 [Radeon Xpress 200M]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by yoblin on 2008-03-27
Thanks for the xorg.conf, just copied the appropriate sections and now the trackpad works great.

Vmware player is not in the repository. I tried installing from the rpm using alien, but after installing the modules would not compile in the vmware configuration script. Seems similar to what happened in the feisty betas, vmware released a new version pretty quickly that would compile after the official release IIRC.

---

### Post by dvenardos on 2008-07-03
Anyone else have a problem with Hardy Heron returning from suspend it just looks up when you wake it up?
If I switch to a terminal I can see the messages:
kinit: trying to resume from ...
kinit: no resume image, doing normal boot.

Everything else seems to work fine, but losing suspend is very inconvenient.

---

### Post by yoblin on 2008-07-03
> **dvenardos said:**
> Anyone else have a problem with Hardy Heron returning from suspend it just looks up when you wake it up?
If I switch to a terminal I can see the messages:
kinit: trying to resume from ...
kinit: no resume image, doing normal boot.

Everything else seems to work fine, but losing suspend is very inconvenient.

sorry, no ideas.. I'm running Hardy but I went back to the open source ATI drivers without Compiz because it's so much less work!

---

### Post by dvenardos on 2008-07-03
> **yoblin said:**
> sorry, no ideas.. I'm running Hardy but I went back to the open source ATI drivers without Compiz because it's so much less work!
I was running the open source driver w/o Compiz also. I just tried installing the proprietary drivers and same result. It looks it is not locked up however, it just takes about a minute to resume. Guess I will do some searching not saving resume image.

---

### Post by Driv3r912 on 2008-07-22
I hate to bring back an old thread everyone. But, now that I am running Ubuntu 8.04 flawlessly with emerald and compiz, I have a minor problem.

I noticed that when I had the ATI Accelerated graphics Driver enabled, on boot, sometimes after the Usplash the screen will sit blank. The only real way to bypass it was to move the mouse right after the usplash on startup, or restart multiple times which isn't good. So, now that I disabled the driver, everything works great.


The main reason I bring this back is because, does anyone now how to enable at least normal desktop effects from the appearance screen? And, if someone else knows about that ATI Accelerated Graphics Driver and the blank screen on startup issue, please come back as well.

 

Thanks,
Driv3r912

---

### Post by dvenardos on 2008-07-22
> **Driv3r912 said:**
> The main reason I bring this back is because, does anyone now how to enable at least normal desktop effects from the appearance screen?
I believe the desktop effects are only available when running Compiz Fusion which is only available with the ATI proprietary driver.

Did you run an upgrade or new install? I have still not been able to get sleep working properly.

---

### Post by Driv3r912 on 2008-07-23
new install partitioned with windows xp pro.

Are you running Ubuntu 7.10?




I was running the ATI Proprietary Driver, but as I described above, it crashes the system when I boot up. I have to move the mouse around when it's booting to get the logon screen up.


Sleep is working on my system right now. Ubuntu 8.04 sound works out of the box. You just need to get ndiswrapper and the RTL Driver and then set (with 8.04 anyway).

---

### Post by dvenardos on 2008-07-23
> **Driv3r912 said:**
> Are you running Ubuntu 7.10?
Distribution upgrade from 7.10 to 8.04. Everything works except for sleep.

---

