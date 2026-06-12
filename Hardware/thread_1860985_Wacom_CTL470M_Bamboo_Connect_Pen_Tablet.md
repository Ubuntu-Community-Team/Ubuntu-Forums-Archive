---
title: "Wacom CTL470M Bamboo Connect Pen Tablet"
date: 2011-10-15
forum: Hardware
---

### Post by zaptec on 2011-10-15
Hi :)

I've recently bought a Wacom bamboo connect tablet; they're are very recent. And for some reason, it's not working on my ubuntu 11.10 :(

Is the tablet model is too recent for ubuntu? There is any solution for get my tablet working?



Thanks

---

### Post by Favux on 2011-10-15
Hi zaptec,

It's October again and so Wacom is releasing new BambooPT models.  And yes your model is brand new and not in the driver yet.  Fortunately Chris Bagwell is on the ball and already has figured the new models out and come up with code to support them.  He is submitting it to the kernel, so the 3.3 ? kernel will have support for them.

In the meantime you could use his patch, see:  [http://sourceforge.net/mailarchive/forum.php?thread_name=CAG1eVf398pnsDJ%2Bfm-hzUwyqJqxBCxVt5E1B%2Bi5wyb2LVj8eEg%40mail.gmail.com&forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?thread_name=CAG1eVf398pnsDJ%2Bfm-hzUwyqJqxBCxVt5E1B%2Bi5wyb2LVj8eEg%40mail.gmail.com&forum_name=linuxwacom-discuss)  Download the attachment in the third post and follow the instructions.

I need to add these models to the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Is your model the CTL-470k?  Look on the back of the tablet.  Also post the Wacom line in the output of the command *lsusb* in a terminal.

It has a stylus and two side buttons (rocker switch?) but no eraser and no touch?

---

### Post by zaptec on 2011-10-15
Thanks for the help, that work now :D

And yes, my tablet is a bamboo pen only with no eraser. It's a CTL-470

There's the lsusb wacom line

```
Bus 002 Device 005: ID 056a:00dd Wacom Co., Ltd 
```

Thank you again for the help :D

---

### Post by Favux on 2011-10-15
Good!  :)

Does the model number have a K or something?  Like CTL-470/K.

---

### Post by zaptec on 2011-10-15
Hum, on the bar code, it's CTL-470/K.

---

### Post by Favux on 2011-10-15
OK, thanks!

---

### Post by Alexomnom on 2011-10-24
Hence this Thread is about Wacom CTL-470K, I'd like to ask, if any other has the same "Prolem".
While "drawing", grapping and stuff, where I have to slide with my pen on the tablet, he sometimes "looses connection", in other words: It stops drawing/grapping (etc.). Then I have to take up my pen and touch the tablet again. 
Has someone else the same problem?

---

### Post by Favux on 2011-10-24
Hi Alexomnom,

In Natty dropping lines in Gimp was caused by Unity/Compiz.  To work around it you would log into *Classic without effects* on the log in screen.  Since Oneiric no longer has that try at the log in screen selecting (click on the gear icon) Unity 2D and logging into that.

---

### Post by Alexomnom on 2011-10-24
Going to try that...
Thanke you!

edit: Well, didn't work for me ^^... seems to be, that I just have to live with that

---

### Post by gabryzen on 2011-10-25
Trying to install the same fix, i obtain this error message:


```
insmod: error inserting 'wacom.ko': -1 Invalid module format
```

lsusb command returns:

```
Bus 006 Device 002: ID 056a:00de Wacom Co., Ltd 
```

any advice?

---

### Post by Favux on 2011-10-25
Hi gabryzen,

Welcom to Ubuntu forums!

What release of Ubuntu are you using?  In other words what is the kernel?
```
uname -r
```

---

### Post by taeksosin on 2011-10-26
If it's necessary to split off into a new thread, someone just let me know.  Have a Dell Mini 10v running Ubuntu 10.04 LTS.  Current version of kernel is 2.6.32-33-generic.  I've followed the guide in appendix 3 from [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562) .  I get the following output when I attempt to make the file.

```

teacher@SittingBull:~/Desktop/wacom$ make -C /lib/modules/$(uname -r)/build SUBDIRS=$(pwd) modules
make: Entering directory `/usr/src/linux-headers-2.6.32-33-generic'
  CC [M]  /home/teacher/Desktop/wacom/wacom_wac.o
/home/teacher/Desktop/wacom/wacom_wac.c:17:28: error: linux/input/mt.h: No such file or directory
/home/teacher/Desktop/wacom/wacom_wac.c: In function ‘wacom_tpc_mt_touch’:
/home/teacher/Desktop/wacom/wacom_wac.c:693: error: implicit declaration of function ‘input_mt_slot’
/home/teacher/Desktop/wacom/wacom_wac.c:694: error: implicit declaration of function ‘input_mt_report_slot_state’
/home/teacher/Desktop/wacom/wacom_wac.c:708: error: implicit declaration of function ‘input_mt_report_pointer_emulation’
/home/teacher/Desktop/wacom/wacom_wac.c: In function ‘wacom_setup_input_capabilities’:
/home/teacher/Desktop/wacom/wacom_wac.c:1129: error: implicit declaration of function ‘input_abs_set_res’
/home/teacher/Desktop/wacom/wacom_wac.c:1238: error: implicit declaration of function ‘input_mt_init_slots’
/home/teacher/Desktop/wacom/wacom_wac.c:1240: error: ‘MT_TOOL_MAX’ undeclared (first use in this function)
/home/teacher/Desktop/wacom/wacom_wac.c:1240: error: (Each undeclared identifier is reported only once
/home/teacher/Desktop/wacom/wacom_wac.c:1240: error: for each function it appears in.)
make[1]: *** [/home/teacher/Desktop/wacom/wacom_wac.o] Error 1
make: *** [_module_/home/teacher/Desktop/wacom] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic'
teacher@SittingBull:~/Desktop/wacom$ 

```I'm a linux newb, completely at a loss to figure out exactly what it's saying.  Near as I can tell, I'm missing lunix/input/mt.h, but I'd figured that'd be covered by running the updates/upgrades and what not.  Anyone have any recommendations?

---

### Post by Favux on 2011-10-26
Hi taeksosin,

You're fine on this thread.  You have that right, the mt.h (multi-touch header) is missing.  Lucid's (10.04) 2.6.32 kernel doesn't have it.  As far as I know Natty's 2.6.38 kernel is the first to have it.  Maybe it appears in .37 or something but I know Maverick's 2.6.35 doesn't have it either.

If you have a Pen/Connect (the DD, *lsusb* in a terminal) then all you need is the stylus working.  We can probably do that by patching input-wacom.  If you have one of the other models with touch, you won't be able to get touch working without 2.6.38 or higher.

---

### Post by taeksosin on 2011-10-26
Favux,

You're right on the money with the Bamboo type.  It's the Bamboo Connect CTL 470/k, and all I care about is pen functionality.  How would I go about patching input-wacom?

Just a wee bit of background, I have 30 some odd units in a school computer lab that this is for.  Infecting 450ish K-8 kids per year with opensource as best as I can, and GIMP + Bamboo I think is going to be a winning combination.

---

### Post by Favux on 2011-10-26
Nice project.  Sounds like a good way to expose the students to OSS.  :)

The line #'s in the following assume your cloning input-wacom (appendix 2) but it should work with input-wacom-0.11.1 also.  Either way once you have the uncompressed input-wacom source code folder you're set.  In the wacom_wac.c file in the 2.6.30 folder in the input-wacom folder add:
```
static const struct wacom_features wacom_features_0xDD =
        { "Wacom Bamboo Connect", WACOM_PKGLEN_BBFUN,     14720,  9200, 1023, 63, BAMBOO_PT };
```
between:
```
static const struct wacom_features wacom_features_0xDB =
	{ "Wacom Bamboo 2FG 6x8 SE", WACOM_PKGLEN_BBFUN,  21648, 13700, 1023, 63, BAMBOO_PT };
static const struct wacom_features wacom_features_0x20 =
	{ "Wacom Intuos 4x5",     WACOM_PKGLEN_INTUOS,    12700, 10600, 1023, 31, INTUOS };
```
At about line #1342 so it looks like:
```
static const struct wacom_features wacom_features_0xDB =
	{ "Wacom Bamboo 2FG 6x8 SE", WACOM_PKGLEN_BBFUN,  21648, 13700, 1023, 63, BAMBOO_PT };
static const struct wacom_features wacom_features_0xDD =
        { "Wacom Bamboo Connect", WACOM_PKGLEN_BBFUN,     14720,  9200, 1023, 63, BAMBOO_PT };
static const struct wacom_features wacom_features_0x20 =
	{ "Wacom Intuos 4x5",     WACOM_PKGLEN_INTUOS,    12700, 10600, 1023, 31, INTUOS };
```
And add:
```
	{ USB_DEVICE_WACOM(0xDD) },
```
between:
```
	{ USB_DEVICE_WACOM(0xDB) },
	{ USB_DEVICE_WACOM(0x41) },
```
At about line #1512 so it looks like:
```
	{ USB_DEVICE_WACOM(0xDB) },
	{ USB_DEVICE_WACOM(0xDD) },
	{ USB_DEVICE_WACOM(0x41) },
```
Then go on to compile as instructed.

To avoid patching xf86-input-wacom's wcmUSB.c if you have the Lucid default xf86-input-wacom-0.10.5 go ahead and update that as in part II.

---

### Post by taeksosin on 2011-10-31
Sorry about the delay on trying this, hadn't had time to play with it.  Getting an error when I attempt to compile after following the steps in Appendix 2.  I made the changes to the necessary file, get the following when I go and try to run autogen.sh.  It LOOKS like it has an issue with the second bit of code you had me add in, is there something additional I need to change?  Output from autogen.sh below.

```

teacher@SittingBull:~/Desktop/input-wacom$ cp 2.6.30/wacom.ko /lib/modules/2.6.32-34-generic/kernel/drivers/input/tablet
cp: cannot stat `2.6.30/wacom.ko': No such file or directory
teacher@SittingBull:~/Desktop/input-wacom$ ./autogen.sh --prefix=/usrautoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --install --copy
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
autoreconf: Leaving directory `.'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for gawk... (cached) gawk
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/2.6.32-34-generic/build
checking kernel version... 2.6.32-34-generic

configure: creating ./config.status
config.status: creating Makefile
config.status: creating 2.6.30/Makefile
config.status: creating 2.6.36/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
make  all-recursive
make[1]: Entering directory `/home/teacher/Desktop/input-wacom'
Making all in 2.6.30
make[2]: Entering directory `/home/teacher/Desktop/input-wacom/2.6.30'
    Building linuxwacom drivers for 2.6 kernel.
make -C /lib/modules/2.6.32-34-generic/build M=/home/teacher/Desktop/input-wacom/2.6.30
make[3]: Entering directory `/usr/src/linux-headers-2.6.32-34-generic'
  CC [M]  /home/teacher/Desktop/input-wacom/2.6.30/wacom_wac.o
/home/teacher/Desktop/input-wacom/2.6.30/wacom_wac.c:1343: error: 'WACOM_PKGLEN_BBPEN' undeclared here (not in a function)
make[4]: *** [/home/teacher/Desktop/input-wacom/2.6.30/wacom_wac.o] Error 1
make[3]: *** [_module_/home/teacher/Desktop/input-wacom/2.6.30] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.32-34-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/teacher/Desktop/input-wacom/2.6.30'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/teacher/Desktop/input-wacom'
make: *** [all] Error 2

----------------------------------------
  BUILD ENVIRONMENT:
       linux kernel - yes 2.6.30
      kernel source - yes /lib/modules/2.6.32-34-generic/build

Your wacom.ko is available under 
    /home/teacher/Desktop/input-wacom/2.6.30
If you have an USB device, you can copy the driver by:
    cp 2.6.30/wacom.ko /lib/modules/2.6.32-34-generic/kernel/drivers/input/tablet
If you have a serial device, please copy the driver by:
    cp 2.6.30/wacom_w8001.ko /lib/modules/2.6.32-34-generic/kernel/drivers/input/touchscreen

NOTE: The kernel drivers included in this package are only
tested with the X Wacom driver built from xf86-input-wacom.
 If you are running an X server version older than 1.7, 
please use the drivers provided by linuxwacom package.

teacher@SittingBull:~/Desktop/input-wacom$ 

```

---

### Post by thrischan on 2011-11-13
Hi Favux,

Thank you very much for your help, I have learned much from your posts. However I have the exact same problem as taeksosin. I have a CTL-470/K an I am in 2.6.32 for reasons out of my control. I undertand the mt.h is designed for a more advanced kernerl but this tablet is very simplistic and doesn't have touch functions or anything fancy, just need the stylus working. 

I tried changing the lines of the wacom_wac.c as you suggested. I did it in input-wacom-0.11.1 AND in the version from git in appendix #2 and got the same error  when configuring :

> /home/teacher/Desktop/input-wacom/2.6.30/wacom_wac.c:1343: error: 'WACOM_PKGLEN_BBPEN' undeclared here (not in a function)

I went to the file wacom_wac.h and added the line "#define WACOM_PKGLEN_BBPEN	10" to define BBPEN just on top of the stylus ang it finally compiled.I copied de wacom.ko and everything else you mentioned in the appendix.

After trying all this , the tablet doesn't want to work.

Any thoughts? Am I doing something wrong with this patch?

Thanks in advance Favux...

---

### Post by Favux on 2011-11-13
Hi taeksosin and thrischan,

Sorry my mistake.  I used the wrong variable.  It should have been WACOM_PKGLEN_BBFUN and not the more recent WACOM_PKGLEN_BBPEN.  I'll fix the instructions in post #15.

---

### Post by thrischan on 2011-11-13
Hi Favux,

Thank you for you quick response. I fixed the file but still, the CTL-470/K is not working. 

I also tried PART II to manually compile xf86-input-wacom-0.11.x and nothing. 

My Xorg information is the following, ( I updated Xorg from a untable repository for no reason other than just than trying to solve this problem  ) so I don't know if the problem could be this : 

> X.Org X Server 1.11.1.902 (1.11.2 RC 2)
Release Date: 2011-10-28
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.1.0-rc4-amd64 x86_64 Debian
Current Operating System: Linux cvargas 2.6.32-5-amd64 #1 SMP Mon Oct 3 03:59:20 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-5-amd64 root=UUID=1436e4a5-f2d0-447c-bc43-aa9c2bc9b49a ro quiet
Build Date: 02 November 2011  10:15:50AM
xorg-server 2:1.11.1.902-1 (Cyril Brulebois <kibi@debian.org>) 
Current version of pixman: 0.21.8

Should I install a fresh copy of my system to get rid of this unstable Xorg that is spread all over my system? and try again? Or is there something I am not aware of?

Thanks in advance!

---

### Post by Favux on 2011-11-13
Hi thrischan,

So this time it compiled without an error?

My inclination is to blame the problem on your new Xorg.  But before you nuke it what configuration file are you using?  I imagine instead of 10-wacom.conf in /usr/lib/X11/xorg.conf.d for that X server you would need a 50-wacom.conf located in /usr/share/X11/xorg.conf.d.  Is that what you have?

---

### Post by thrischan on 2011-11-13
Hi Favux ,

Oops! too late I already re-install the computer :-/

Here it is what i did exactly :

1-Re-installed debian squeeze in a minimal installation.
2-Installed desktop from the stable official repository ( apt-get install xserver-xorg-core xorg xdm xfce4 )

At this stage this is my current Xorg version

> X.Org X Server 1.7.7
Release Date: 2010-05-04
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.37-trunk-amd64 x86_64 Debian
Current Operating System: Linux cvargas 2.6.32-5-amd64 #1 SMP Mon Oct 3 03:59:20 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-5-amd64 root=UUID=2c552b66-d8a0-4001-ba4b-7c4fa620f4b9 ro quiet
Build Date: 18 February 2011  08:27:24PM
xorg-server 2:1.7.7-13 (Cyril Brulebois <kibi@debian.org>) 
Current version of pixman: 0.16.4

3- I installed my utilities packages (chrome, mousepad, squeeze) + xorg realated packges ( build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libxinerama-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev)

4- Followed "PART 2" to intall util-macros-1.8.0.tar.bz2 and xf86-input-wacom/xf86-input-wacom-0.11.1.tar.bz2 ( dind't use git )

>  Important : After reboot, the ctl-470/K is not working at this stage. I plugged my old ctl-460/k and it is not working either.

5 - Patched wacom_wac.c with the new version of the patch you suggested in post #15 right here.


6 - Went back to appendix 2 to install the driver ( I could't follow the tutorial exactly, there are 2 things I did  differently : (1) I dont have acces to git in this pc so i downloaded it form another computer and bring it here and (2) I downloaded the linux headers "linux-headers-2.6.32-5-amd64" since thats my kerner when I hit uname-r )

At this stage my ctl-470/k is not working but my old ctl460/k works perfectly. 

A don't think this has to to with my linux-headers cause the old tablet is working perfectly. Any thought? 

This ctl-470 is tough :-)

---

### Post by Favux on 2011-11-13
Shoot.

Given that your ctl460/k works then the xf86-input-wacom install should be good.  Although I admit to never having seen an amd64 header before.  What Chris did a little while back was remove the need to add a new BambooPT model to the xf86-input-wacom's wcmUSB.c file.  Provided the right stuff is coming in from the kernel it is suppose to be automatically recognized.  I forget which version, but certainly by 0.11.1.  I'm sort of wondering what would happen if we tried that since adding the model to wcmUSB.c shouldn't break anything.  The old models are still in there after all.

Does the new model show up in?
```
xinput list
```
How about?
```
xsetwacom list
```

So the problem would seem to be in the kernel.  Does the new protocol the third generation BambooPT's use differ so much that even stylus is affected, unlike the second generation?

Let's see what the Xorg.0.log in /var/log is seeing with the new tablet plugged in.  We also want to figure out what event it is on so you can run evtest on its stylus.

---

### Post by thrischan on 2011-11-13
Hi Favux, 

It seems both tablets are being detected , here are the results :

xinput list with ctl-470/k returns the following

```
Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Genius Optical Mouse                      id=10   [slave  pointer  (2)]
&#9116;   &#8627; HID 04f3:0103                             id=12   [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation          id=13   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Connect Pen stylus           id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Connect Pen eraser           id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Connect Pen stylus           id=14   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Connect Pen eraser           id=15   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; HID 04f3:0103
```

xinput list with ctl-460/k returns the following

```
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Genius Optical Mouse                      id=10   [slave  pointer  (2)]
&#9116;   &#8627; HID 04f3:0103                             id=12   [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation          id=13   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Pen 4x5 Finger touch         id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Pen 4x5 Finger pad           id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Pen 4x5 Pen stylus           id=14   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Pen 4x5 Pen eraser           id=15   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; HID 04f3:0103
```

xsetwacom list with ctl-470/k

```
Wacom Bamboo Connect Pen stylus         id: 8   type: STYLUS    
Wacom Bamboo Connect Pen eraser         id: 9   type: ERASER    
Wacom Bamboo Connect Pen stylus         id: 14  type: STYLUS    
Wacom Bamboo Connect Pen eraser         id: 15  type: ERASER 
``` 

xsetwacom list with ctl-460/k

```
Wacom Bamboo Pen 4x5 Finger touch       id: 8   type: TOUCH     
Wacom Bamboo Pen 4x5 Finger pad         id: 9   type: PAD       
Wacom Bamboo Pen 4x5 Pen stylus         id: 14  type: STYLUS    
Wacom Bamboo Pen 4x5 Pen eraser         id: 15  type: ERASER   

```

I guess it would be better for you if I attach the .log to this post since I don't know what to look for.

Thanks in advance.

---

### Post by Favux on 2011-11-13
Wow!  That Xorg.0.log is a serious mess.  It's trying to put the stylus on both event7 and event8 and then when it encounters the eraser it correctly notices there isn't one, throws up a bunch of warnings and uninstalls the wacom X module.  Which it shouldn't do.  Looks like it finally goes through on the last try which is why we see it in xinput and xsetwacom list.  Were you plugging and unplugging the 470 or was it plugged in the whole time?

It does complain about the tablet being unknown:
```
(--) Wacom Bamboo Connect Pen stylus: Wacom Unknown USB tablet maxX=14720 maxY=9200 maxZ=1023 resX=1016 resY=1016  tilt=enabled
```
I'm not sure if that's to be expected with Chris' change or not because it is relatively new.

Given that we see it in xinput and xsetwacom list I would think the stylus should work.  So maybe because it sets up on both events?

What to do?

Why don't we try changing the 50-wacom.conf to:
```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WALTOP|WACOM"
	MatchDevicePath "/dev/input/event7"
	Driver "wacom"
EndSection

```
And see what happens?  If that doesn't work try event8.  If evdev sets up on the unclaimed event that might block the stylus anyway, but still.

---

### Post by thrischan on 2011-11-13
Hi Favux,

Yes, I was plugin/unplugin because I was testing hehe. At the end I was kind  of impatient with this issue so I thought it was easier to take another plan :Since I have to stay in debian 6 squeeze, I decided to update the kernel.

[https://ticketing.nforce.com/index.php?/Knowledgebase/Article/View/27/0/upgrading-the-kernel-to-2638-in-debian-6-squeeze](https://ticketing.nforce.com/index.php?/Knowledgebase/Article/View/27/0/upgrading-the-kernel-to-2638-in-debian-6-squeeze)

After that followed intructions from Chris Bagwell in this post 

[http://sourceforge.net/mailarchive/forum.php?thread_name=CAG1eVf398pnsDJ%2Bfm-hzUwyqJqxBCxVt5E1B%2Bi5wyb2LVj8eEg%40mail.gmail.com&forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?thread_name=CAG1eVf398pnsDJ%2Bfm-hzUwyqJqxBCxVt5E1B%2Bi5wyb2LVj8eEg%40mail.gmail.com&forum_name=linuxwacom-discuss)

And everything is working perfectly :-) 

Now I'm in debian squeeze with a ctl-470/k, using kernel 2.6.38 though.

Sorry about not being able to test event8 but I already got rid of that installation. Anything else you need regarding the ctl-470/k feel free to ask me, I will be more than happy to help. I really appreciate what you guys are doing here for all of us.

---

### Post by fragos on 2011-12-07
Just purchased a Bamboo Connect 470/K to replace my Graphire4. I'm running 11.10. I ./configure, make and sudo make install xf86-input-wacom-0.12.0. My Graphire4 still works but although lsusb sees my Bamboo Connect, xinput list doesn't. Perhaps there's something more I need to do. Suggestions please.

---

### Post by Favux on 2011-12-07
Hi fragos,

You need input-wacom-0.12.0, which just came out.  That has your new model in it.  See part I. on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by fragos on 2011-12-07
> **Favux said:**
> Hi fragos,

You need input-wacom-0.12.0, which just came out.  That has your new model in it.  See part I. on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

Thank you very much Favux -- worked like a charm.

---

### Post by dbozhinovski on 2011-12-08
Hi!

A long time user of Ubuntu, but a lurker on the forums so far. I've bought one of these too (Wacom Bamboo ctl-470/k) and successfully installed it with the patched driver. However, as another poster mentioned before, when drawing (regardless of program used), the line randomly breaks. 

It isn't much of an issue with scalar graphics, but can be a royal frustration with vector graphics (namely, in InkScape). I've googled for a while now, but no solution has come up yet. Any ideas on how to solve this, aside from the turning off effects/hardware accelerated desktop? (I've tried that already - no luck). 

Thanks, and in case this isn't the right thread to ask this in - I apologize and will move it to the proper location as instructed.

---

### Post by fragos on 2011-12-08
I've experienced the same with an older Graphire4 since I installed 11.04. Problem persisted with 11.10. I upgraded my tablet to the latest Bamboo Connect and the problem is still there. Not that we can believe all we read on the web but I did read where someone claimed this was an issue relating to Unity and Compiz. I tried with Unity 2D which doesn't use Compiz and the problem is still there when drawing in GIMP. When using the stylus to position the cursor there are no visible problems but that doesn't mean that the cursor location isn't jumping to the edge and returning without a visual trail to follow. It would appear this is a software problem but for which package to report the bug is a mystery.

---

### Post by Favux on 2011-12-08
Hi dbozhinovski and fragos,

Welcome to Ubuntu forums dbozhinovski!

You're seeing bugs presumambly introduced by Ubuntu in their version of the X stack.  At a guess it's from their multi-touch stuff.  For at least Gimp in Oneiric (where the problem is the worst) you can turn off the history-buffer and make Gimp usable again:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154)  The Gimp PPA with Alexia's patch linked to in the bug report is here:  [https://launchpad.net/~grumbel/+archive/gimp](https://launchpad.net/~grumbel/+archive/gimp)

Peter Hutterer (Red Hat Xorg developer) has been working on the multi-touch stuff for X over the last month or two.  Since he is also the lead developer on xf86-input-wacom, his version probably won't have the bugs the Ubuntu one does.  So if/when Ubuntu switches over to the new X server (in time for Precise?) hopefully this will finally be fixed.

---

### Post by dbozhinovski on 2011-12-08
Thank you for the detailed answer, Favux. 

I realize it will eventually be fixed, but it is a bit frustrating to have to switch to a Windows PC each time I have something graphics related to work on :) 

Precise feels a bit too far away, hoping for a patch of some sort in the meantime. :)

---

### Post by lene2 on 2012-03-20
I'd like to pick up the problem with the xf86-input-wacom driver registering on multiple or wrong event devices and the evdev catchall messing with it.

I have a lucid install and a CTL-470/K. I've done the following:
1. Compiled and installed a patched (instructions at [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562), Appendix 2) wacom kernel module. Result: tablet is detected as visible in dmesg
2. Compiled and installed xf86-input-wacom 0.14.0
3. Compiled and installed util-macros 1.8.0 (see [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562), section II b)

At this point I have my tablet showing up in xinput list and xsetwacom list but drawing on it has no effect on the mouse pointer. According to Favux's post from November 13th I've selected event8 for testing in 10-wacom.conf, but it doesn't help:

```

ection "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event8"
    Driver "wacom"
EndSection
...

```The same happens if I select input9 (the other option found in Xorg.0.log) there.

xsetwacom list
```

Wacom Bamboo Connect Pen stylus     id: 11    type: STYLUS    
Wacom Bamboo Connect Pen eraser     id: 18    type: ERASER

```xinput list (with specific input device selected in 10-wacom.conf)
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Connect Pen stylus             id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Connect Pen                    id=12    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=15    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=17    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Connect Pen eraser             id=18    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Logitech USB Receiver                       id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=16    [slave  keyboard (3)]

```Notably, this differs from what I get without selecting a specific input device. If I don't select input[89] I get the same as in the post from November 13th from thrishan (ie 2 stylus and 2 erasers). I cannot capture any events from the tablet with xev. Does anyone have further experience in debugging this? I'll attach my current Xorg.0.log for reference.

---

### Post by Favux on 2012-03-20
Hi lene2,

Welcome to Ubuntu forums!

Thanks for testing.  Chris has submitted a patch to input-wacom for this and has tested it.  Instead of the manual changes to input-wacom's 2.6.30 folder try applying this patch.  After downloading and extracting the patch change directory into input-wacom and run:
```
patch -p1 < path-to-patch/input-wacom-Backport-2nd-and-3rd-gen-Bamboo-support-to-2.6.30.patch
```
Hopefully I have the strip (-p) correct.

Then please post your results on linuxwacom-discuss:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)

I contacted Chris re you so he'll be expecting your post.

---

### Post by lene2 on 2012-03-22
This patch did the trick. Thanks. I'll also post to linuxwacom-discuss.

---

### Post by Favux on 2012-03-22
Hi lene2,

Good, I'm glad your Connect Pen is now working on Lucid.  :)

Thank you for testing the patch and posting on linuxwacom-discuss.

---

### Post by tsbertalan on 2012-04-21
> **fragos said:**
> Just purchased a Bamboo Connect 470/K to replace my Graphire4. I'm running 11.10. I ./configure, make and sudo make install xf86-input-wacom-0.12.0. My Graphire4 still works but although lsusb sees my Bamboo Connect, xinput list doesn't. Perhaps there's something more I need to do. Suggestions please.

I also had my CTL 470/K showing up in lsusb (lsusb | grep acom gives "Bus 006 Device 002: ID 056a:00dd Wacom Co., Ltd"), but not in xinput list. I tried ./configure and cp'ing the wacom.ko files from the input-wacom-0.12.0 and input-wacom-0.12.1, both with and without Chris Bagwell's patches.

BUT, I'm on 10.10 Maverick, with the 2.6.35 kernel, so my situation might be different from fragos's.

I've also tried installing the xserver-xorg-input-wacom and wacom-dkms packages, at least one of which came from ppa:irie/wacom. At this point, I've probably just messed something up. But I can still reliably get a "Wacom" entry to show up in lsusb, pretty much whatever I do.

---

### Post by fragos on 2012-04-21
> **tsbertalan said:**
> I also had my CTL 470/K showing up in lsusb (lsusb | grep acom gives "Bus 006 Device 002: ID 056a:00dd Wacom Co., Ltd"), but not in xinput list. I tried ./configure and cp'ing the wacom.ko files from the input-wacom-0.12.0 and input-wacom-0.12.1, both with and without Chris Bagwell's patches.

BUT, I'm on 10.10 Maverick, with the 2.6.35 kernel, so my situation might be different from fragos's.

I've also tried installing the xserver-xorg-input-wacom and wacom-dkms packages, at least one of which came from ppa:irie/wacom. At this point, I've probably just messed something up. But I can still reliably get a "Wacom" entry to show up in lsusb, pretty much whatever I do.

I'd recommend installing Ubuntu 12.04 and all you'll need to do is install the dkms driver. There are problems you haven't seen yet when drawing with the stylus that are fix in the 12.04 generation.

---

### Post by Favux on 2012-04-21
Hi tsbertalan,

Welcome to Ubuntu forums!

If you are using Maverick (10.10) then you need to use Chris' new backport patches for third generation BambooPTs to input-wacom for Lucid and Maverick.  The patch is attached to the bottom of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  See appendix 2 near the bottom of the HOW TO.

First remove any DKMS install you have through Synaptic Package Manager.  The dkms wacom.ko is likely to overwrite any new wacom.ko you compile otherwise.

---

### Post by tsbertalan on 2012-04-21
Holy crap, it worked! After removing wacom-dkms (specifically through Synaptic, as instructed, although I suspect apt-get or aptitude would have also worked), I did:

```

tar -xvf input-wacom-0.12.1.tar.bz2
cd input-wacom-0.12.1/
patch -p1 < /home/tsbertalan/Desktop/input-wacom-Backport-2nd-and-3rd-gen-Bamboo-support-to-2.6.30.patch
./configure --enable-wacom --prefix=/usr
sudo         cp 2.6.30/wacom.ko /lib/modules/2.6.35-32-generic/kernel/drivers/input/tablet
sudo reboot

```

Where the "cp" line was taken from the output of the "./configure" line. I tried using the git clone version, but the patch didn't seem very happy there.

Fragos, I probably will upgrade to 12.04 after reading doing a little more reading about it--I was intending to skip the 11.x stuff and go straight for this LTS release, but didn't realize it's coming would coincide so perfectly with the end of the semester, when I'd actually have time to iron out all the inevitable problems.

I guess the next thing to play around with is easystroke, so I can avoid switching to my mouse just to use the scroll wheel.

Thanks, guys. I guess it pays to stop lurking and speak up with a question every once in a while!

---

### Post by Favux on 2012-04-21
Great!

Yeah, whatever removes the dkms.  I just know for sure that Synaptics does.  The idea is to avoid having to manually remove it because the PPA's never include those instructions which irks me no end.  If it is called wacom-dkms it would be something like:
```
sudo dkms remove -m wacom-dkms -v <version> --all

sudo rm -r /usr/src/wacom-dkms-<version>
```
You could get version by looking into the the package's dkms.conf I suppose.

Heck and posting can even be fun!  :)

---

### Post by tsbertalan on 2012-04-21
Alright, thanks. I'll try that if a kernel upgrade breaks support. In the mean time, it seems to be working OK (see attachment from working with [this tutorial]("http://emptyeasel.com/2008/09/26/painting-with-a-wacom-tablet-in-gimp/").)

---

### Post by Favux on 2012-04-21
Sure.  Good to see you're jumping right in.  :)

---

