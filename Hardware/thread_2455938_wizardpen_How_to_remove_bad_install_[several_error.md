---
title: "wizardpen: How to remove bad install [several errors and miss match messages]"
date: 2020-12-31
forum: Hardware
---

### Post by luigiwriter2 on 2020-12-31
[Would have used the Ask Ubuntu prefix [graphics-tablet] not available here.]

I am running Ubuntu 18.04 with a USB UC-Logic WP5540U [supported as WP5540, Genius MousePen 5x4 Tablet
    VENDOR_ID=&#8221;5543&#8221;, Product ID=&#8221;0004&#8221; in the digimend driver. Definitely not supported in the wacom driver]
    I need to install it for use it on my second and larger monitor with Gimp and Krita.
    Under just the digimend basic driver, it is pressure and the two buttons are recognized, but the tablet area is limited to the small HP laptop screen. or spread over both leaving only about 4" x 2.5" tablet area for the larger monitor.  Thus my attempt to install the wizardpen.

One challenge has been finding up-to-date instructions for installing wizardpen
So far only[INDENT]Ubuntu Precise 12.04 (kernel 3.2 and X server 1.11/1.12) at
[/INDENT]
[INDENT][https://digimend.github.io/support/howto/drivers/wizardpen/](https://digimend.github.io/support/howto/drivers/wizardpen/)[/INDENT]
[INDENT=2]Which I have so screwed up that plugging in my UC-Logic WP5540U now reboots Ubuntu and a frozen login screen.
[/INDENT]
[INDENT=2][Unplug and reboot is normal.]
[/INDENT]

Another but different looking instruction set on this forum dating from[INDENT]10.4 (lucid lynx) 15th October 2010  at
[/INDENT]
[INDENT][https://ubuntuforums.org/showthread.php?t=1357711](https://ubuntuforums.org/showthread.php?t=1357711)
[/INDENT]
And the "This article needs updating to include the latest versions of Ubuntu." header noted. (last edited 2017-09-02 17:14:49 by ckimes)[INDENT][https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) [/INDENT]
[INDENT=2]Covers only Ubuntu Lucid (10.04) Maverick (10.10), and Jaunty (9.04). Which would work with 18.04 I was not sure.
[/INDENT]

I am worried that any new install attempt may be corrupted by the old install,

I have not found a description of how to uninstall from a tar.gz compile in order to prevent corruption.
The tar.gz I used is:[INDENT]wizardpen_0.8.1-0ubuntu3.tar.gz
[/INDENT]

In looking for removal instructions I found a list of [I think all but empty] debs at
[http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/pool/main/x/xserver-xorg-input-wizardpen/](http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/pool/main/x/xserver-xorg-input-wizardpen/)[INDENT]xserver-xorg-input-wizardpen_0.7.3-0jaunty5_amd64.deb
[/INDENT]
For example, when I opened it and another with "Software Install" the Download size is 0 bytes of a 19.2 KiB Deb file compaired with the 3.5 MiB tar.gz file.

Let me list the messages I culled from using Digimend's instructions with the hope you can:
1. Please advice as to whether removing first is needed.[INDENT]*  If removing is advised, point me to instructions for how, and which install instructions you would recommend
[/INDENT]
[INDENT]*  If removing is unnecessary, which instructions above, or better you know of should I follow.
[/INDENT]
[INDENT][Often, I find I am using the wrong vocabulary :( in searches. Any help there also appreciated.]
[/INDENT]

The list of Error messages I have culled out of the terminal verbosity.[INDENT]:oops: I Admit I was remiss in not looking for errors before continuing to the next step.
Also Bold is only meant as an aid when you are skimming through [If it is not an aid, let me know so I will avoid it in future.].
[/INDENT]
```
ar xvzf xserver-xorg-input-wizardpen_0.8.1-0ubuntu3.tar.gz 
```   [Produced No Errors]

README indicated packages needed to build I installed:
xutils-dev              xutils        libx11-dev              libxext-dev        build-essential        
xautomation        xinput        xserver-xorg-dev    
Plus recommended in the instructions
    autoconf         libtool        pkg-config

```
/Desktop/xserver-xorg-input-wizardpen-0.8.1$ ./autogen.sh --prefix=/usr
```
[/code]. . .
libtoolize: Consider adding 'AC_CONFIG_MACRO_DIRS([m4])' to configure.ac,
libtoolize: and rerunning libtoolize and aclocal.
libtoolize: Consider adding '-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
. . .
automake: **warning**: source file 'calibrate/wizardpen-calibrate.c' is in a subdirectory,
automake: but option 'subdir-objects' is disabled
Makefile.am:21:   while processing program 'calibrate/wizardpen-calibrate'

automake: **warning:** possible forward-incompatibility. At least a source file is in a subdirectory, but the 'subdir-objects' automake option hasn't been enabled.  For now, the corresponding output object file(s) will be placed in the top-level directory.  However, this behaviour will change in future Automake versions: they will unconditionally cause object files to be placed in the same subdirectory of the corresponding sources.
automake: You are advised to start using 'subdir-objects' option throughout your project, to avoid future incompatibilities.
. . .
/.../Desktop/xserver-xorg-input-wizardpen-0.8.1/missing: Unknown `--is-lightweight' option
Try `/.../Desktop/xserver-xorg-input-wizardpen-0.8.1/missing --help' for more information [Looked; found a code, not text, file.]
configure: **WARNING: 'missing' script is too old or missing**
. . .
checking sysfs/libsysfs.h usability... **no**
checking sysfs/libsysfs.h presence... **no**
checking for sysfs/libsysfs.h... **no**
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile[/code]
```
:~/Desktop/xserver-xorg-input-wizardpen-0.8.1$ make
```
[I][I am assuming a bunch of the following errors are because of the **'missing' script is too old or missing** above. 
Sounds like I still need to know how to UN-Make this mess.][/I]
```
. . .
wizardpen.c: In function &#8216;WizardPenAutoDevProbe&#8217;:
wizardpen.c:211:28: warning: initialization discards &#8216;const&#8217; qualifier from pointer target type [-Wdiscarded-qualifiers]
     char *wizardpen_name = xf86FindOptionValue(local->options, "Name");
                            ^~~~~~~~~~~~~~~~~~~
wizardpen.c: In function &#8216;WizardPenPreInit&#8217;:
wizardpen.c:363:7:** warning: assignment discards &#8216;const&#8217; qualifier from pointer target type** [-Wdiscarded-qualifiers]
    (local->options, "ClickPressureLevel");* [SIZE=4][Looks like it discarded most of what I may need.][/SIZE]*[INDENT][Also repeated the above text for following except for "c.xxx:7:" which increments and the option names as follows.]
[/INDENT]
.c:370:7: "debugyn"             .c:381:7: "Device"              .c:418:7: "Mode"        
.c:428:7: "TopX"                    .c:436:7: "TopY"                 .c:445:7:"BottomX"
.c:453:7:"BottomY"               .c:461:7:"TopZ"                  .c:465:7:"BottomZ"
.c:470:7:"KeepShape"        .c:476:7:"ScreenX"             .c:483:7:"ScreenY"
.c:521:7:"DebugLevel"        .c:527:7:"MouseSpeed"    .c:533:7:"MouseAccel"
.c:539:7:"ReportScreen"    .c:545:7:"Rotate90"            .c:562:7:"TPCButton"
. . .
Making all in udev
make[2]: Entering directory '/.../Desktop/xserver-xorg-input-wizardpen-0.8.1/udev'
make[2]:** Nothing to be done for 'all'.**
make[2]: Leaving directory '/.../Desktop/xserver-xorg-input-wizardpen-0.8.1/udev'
Making all in xorg
make[2]: Entering directory '/.../Desktop/xserver-xorg-input-wizardpen-0.8.1/xorg'
make[2]: **Nothing to be done for 'all'.**
. . .
calibrate/wizardpen-calibrate.c: In function &#8216;close_input&#8217;:
calibrate/wizardpen-calibrate.c:61:2: **warning: implicit declaration of function &#8216;close&#8217;; did you mean &#8216;pclose&#8217;? **[-Wimplicit-function-declaration]
  close( input->fd );
  ^~~~~
  pclose
calibrate/wizardpen-calibrate.c: In function &#8216;read_input&#8217;:
calibrate/wizardpen-calibrate.c:74:23: **warning: implicit declaration of function &#8216;read&#8217;; did you mean &#8216;fread&#8217;?** [-Wimplicit-function-declaration]
   input->read_bytes = read(
                       ^~~~
                       fread
mv -f .deps/wizardpen-calibrate.Tpo .deps/wizardpen-calibrate.Po
. . .
```
```
sudo make install
```
```
Making install in man
make[1]: Entering directory '/.../Desktop/xserver-xorg-input-wizardpen-0.8.1/man'
make[2]: Entering directory '/.../Desktop/xserver-xorg-input-wizardpen-0.8.1/man'

make[2]: **Nothing to be done for 'install-exec-am'.**

Making install in udev
make[1]: Entering directory '/.../Desktop/xserver-xorg-input-wizardpen-0.8.1/udev'
make[2]: Entering directory '/.../Desktop/xserver-xorg-input-wizardpen-0.8.1/udev'

make[2]: **Nothing to be done for 'install-exec-am'.**

Making install in xorg
make[1]: Entering directory '/.../Desktop/xserver-xorg-input-wizardpen-0.8.1/xorg'
make[2]: Entering directory '/.../Desktop/xserver-xorg-input-wizardpen-0.8.1/xorg'

make[2]: **Nothing to be done for 'install-exec-am'.**

 /bin/mkdir -p '/usr/bin'
make[2]:** Nothing to be done for 'install-data-am'.**
```

Checked Installed files

y)    the WizardPen X driver at
     /usr/lib/xorg/modules/input/wizardpen_drv.so (and wizardpen_drv.la)
y)    the WizardPen udev rules at
     /etc/udev/rules.d/67-xorg-wizardpen.rules
y)    the wizardpen .conf at
     /usr/share/X11/xorg.conf.d/70-wizardpen.conf
y)    calibration executable (alternative to xinput_calibrator) at
     /usr/bin/wizardpen-calibrate
y)    the WizardPen manual (i.e. man wizardpen in a terminal) at
     /usr/share/man/man4/wizardpen.4
--------------------------------------------------------------------            
Finally the[INDENT]**Xorg.0.log**
[/INDENT]
which is supposed to exist at[INDENT]/var/log.
[/INDENT]
after touching the pen to the tablet
**has never materialized **even when the tablet was not freezing the computer. :confused:

---

### Post by ajgreeny on 2020-12-31
It looks as if there's a snap package and an old PPA for precise for wizardpen which I think is the one you mention.
[https://launchpad.net/~wizardpen-devs/+snaps](https://launchpad.net/~wizardpen-devs/+snaps)
[https://launchpad.net/~doctormo/+archive/ubuntu/xorg-wizardpen/+index?field.series_filter=natty](https://launchpad.net/~doctormo/+archive/ubuntu/xorg-wizardpen/+index?field.series_filter=natty)

I have no knowledge of either and the PPA may be far too old to be of any use but I have given you the URL just in case it's of any use.

Please in future use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**
I have not edited your post and added code tags as it is far too long and difficult to deal with. Code tags would have made it a great deal more readable.

---

### Post by luigiwriter2 on 2020-12-31
Thanks for your quick reply. Re-edited. Easy to add the tags after the first. [/code] copy and paste, remove [/] in the one at the beginning. Not bad for a BASIC spaghetti code and IBM card Fortran4 survivor.
Thanks for the links am investigating
Fuzzy brain seems to think I can use "apt-get uninstall or purge <app-name>" to clean up if I can get the app-name part right? Your thoughts? 
Or does apt get a reference list from a compile process? Again may be calling things by the wrong names.

---

### Post by luigiwriter2 on 2021-01-04
hi, ajgreeny, 
Well, It has been reading until my eyeballs fell out.

I still have wizardpen installed although Ubuntu 18.04 recognizes the UC-LOGIC Tablet WP5540U through "xinput" but not as a Wacom Tablet. 
There is some semi-good news for non-wacom supported pen tablets at the x-input level. I say semi-good because it is a clunkey fix at the moment.

So just so the world knows.

PTXConf or the Pen tablet and Touch screen Xinput Configuration tool
Install instructions at:
[http://wenhsinjen.github.io/ptxconf/](http://wenhsinjen.github.io/ptxconf/)
 [https://github.com/wenhsinjen/ptxconf](https://github.com/wenhsinjen/ptxconf)
I am "watching" the latter in hopes of a new version. 

Unfortunately the latest install "ptxconf.py" is still dependent on Python 2.7 reached the end of its life on January 1st, 2020, and has to be invoked from terminal each session. Meaning the last compatible Ubuntu is 18.04. 
[https://github.com/wenhsinjen/ptxconf/issues/9](https://github.com/wenhsinjen/ptxconf/issues/9)
is[SIZE=3][FONT=century gothic] Save settings across sessions? Output or store generated settings?              #9[/FONT][/SIZE]
What I have to do each session is 
1. With Touch pad pen, touch the pad. 
2. [Ctrl]+[Alt]+[T]
3. cd ptxconf
4. ./ptxconf.py
5. Select the Monitor
6. Select the tablet
7. click [apply]
Then open Kirta, GIMP or whatever.

Basicly Wizardpen and DIGImend projects have gone moreabund since most tablets work with the later distros because of x-config improvements.

However, no one has really cracked the newer two monitor challange at the Debian level. 
Basically Ubuntu 18.04 makes them into one monitor, which leaves about a 4" high by 2" wide part of the "Non-Wacom" UC-LOGIC tablets to draw in a full screen Kirta on a 32" 1920x1080 monitor.

The hardest part of researching this was very few posters understand there is a big difference in how to handle Wacom or DIGImend [UC-logic] problems and which distro [ie Arch Luinix vs Ubuntu] is automatically using which set of drivers [Solutions for one rarely work for both, from the 60 sets of posts, documents, and wicki I have read.]

Hope this saves anyone else that 100 or so pages of eye bleeryness.
And as Walter Cronkite used to say "And that's the way it Is." ;)

---

