---
title: "HOW TO Set Up a Wacom Serial Tablet in Ubuntu"
date: 2011-06-11
forum: Hardware
---

### Post by Favux on 2011-06-11
**Lucid, Maverick, Natty, Oneiric, & Precise**.

Last updated:  June 6, 2012

**[COLOR="Blue"][SIZE="4"]Good News![/SIZE][/COLOR]**
**[COLOR="Blue"][SIZE="3"]A wacom_serial.ko has been written by [tokenrove]("http://ubuntuforums.org/showpost.php?p=11015139&postcount=43").[/SIZE][/COLOR]  Together with a patched inputattach the protocol IV serial tablets are supported.  Protocol IV devices include the Digitizer II (UD series), PenPartner, Graphire, and Cintiq series of Wacom serial tablets.**  This serio-based driver is still feature incomplete and does not yet support pad buttons, tilt, suppression, or the Graphire relative wheel.  This is a link to **the newest driver and inputattach patch:**  [wacom_serial-120327-1.tar.bz2]("http://cipht.net/releases/wacom_serial-120327-1.tar.bz2")  See [post #349]("http://ubuntuforums.org/showpost.php?p=11798248&postcount=349").  **Instructions are on tokenrove's page "A kernel driver for legacy Wacom serial tablets" here:**  [http://cipht.net/2011/07/02/wacom_serial-initial-release.html](http://cipht.net/2011/07/02/wacom_serial-initial-release.html)  Those of you with the appropriate model should **consider helping tokenrove with testing**, as he has requested, in order to shake out any bugs and add the feature support in.  The **[COLOR="Blue"][SIZE="3"]PenPartners[/SIZE] now work[/COLOR]** thanks to **bserem**, see [post #314]("http://ubuntuforums.org/showpost.php?p=11730826&postcount=314").  **[COLOR="Blue"][SIZE="3"]Graphire[/SIZE] tablets now work[/COLOR]** thanks to the response of [Graiden]("http://ubuntuforums.org/showpost.php?p=11938399&postcount=416") and [jellysheep]("http://ubuntuforums.org/showpost.php?p=11941245&postcount=422") to the urgent call for Graphire testers.  The eraser just needs to be re-enabled and the mouse scroll wheel confirmed.
**[COLOR="Blue"][SIZE="3"]Feedback on the new version of wacom_serial.ko appreciated.[/SIZE][/COLOR]  If your tablet didn't work with it before please try it now**
**[COLOR="Blue"][SIZE="3"]Update (6-6-12):[/SIZE]  we are very close to having all of the wacom_serial.ko driver features functional and tested![/COLOR]**  The next steps will be submission to the kernel and input-wacom.  :)  **Thank you testers!**

**[COLOR="Blue"][SIZE="3"]  [Roaldfre]("http://ubuntuforums.org/showpost.php?p=11035835&postcount=78") has also written a wacom_serial5.ko.[/SIZE][/COLOR]  Protocol V devices include the Intuos and Intuos2 models.**  The code is here:  **[https://github.com/RoaldFre/wacom_serial5](https://github.com/RoaldFre/wacom_serial5)**
**[COLOR="Blue"][SIZE="3"]Update (1-16-12):[/SIZE]  with the addition of the 4D mouse support roaldfre now has all of the wacom_serial5.ko driver features functional and tested![/COLOR]**  The next steps will be submission to the kernel and input-wacom.  :)  **Thank you testers!**

***Thank you tokenrove and roaldfre.  This is awesome!***


**[SIZE="3"]Sources[/SIZE]**
"A kernel driver for legacy Wacom serial tablets" by tokenrove:  [http://cipht.net/2011/07/02/wacom_serial-initial-release.html](http://cipht.net/2011/07/02/wacom_serial-initial-release.html)
"Serial Protocol IV" by tokenrove:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Serial_Protocol_IV](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Serial_Protocol_IV)
"Driver for old serial Wacom protocol V tablets (Intuos and Intuos2)" by roaldfre:  [https://github.com/RoaldFre/wacom_serial5](https://github.com/RoaldFre/wacom_serial5)
Linux Console Project (for inputattach) by esr, jsimmons, skitt, vojtech:  [http://sourceforge.net/projects/linuxconsole/](http://sourceforge.net/projects/linuxconsole/)

"Wacom Hacking" by John Tsiombikas:  [http://codelab.wordpress.com/2010/02/21/wacom-hacking/](http://codelab.wordpress.com/2010/02/21/wacom-hacking/) - the original xf86-input-wacom serial patch.
"Problems with Wacom Intuos2 serial and Xserver 1.7 (ubuntu lucid)" by Sebastian Berthold:  [http://sourceforge.net/mailarchive/forum.php?thread_name=4BEB198B.9030809%40sleif.de&forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?thread_name=4BEB198B.9030809%40sleif.de&forum_name=linuxwacom-discuss) - first serial patch and second serial patch set on linuxwacom-discuss.
Sources for regenerating the xf86-input-wacom build scripts, WWWWolf at:  [http://codelab.wordpress.com/2010/02/21/wacom-hacking/](http://codelab.wordpress.com/2010/02/21/wacom-hacking/)  and:  [http://forums.opensuse.org/english/get-technical-help-here/hardware/444426-wacom-graphics-tablet.html](http://forums.opensuse.org/english/get-technical-help-here/hardware/444426-wacom-graphics-tablet.html)
"dixScreenOrigins has been removed from server" by Gaetan Nadon:  [http://sourceforge.net/mailarchive/forum.php?thread_name=201006170748.14485.rob%40janerob.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=201006170748.14485.rob%40janerob.com&forum_name=linuxwacom-devel) - patch to build on X server 1.9.

"Wacom Graphire I serial and Lucid" thread:  [http://ubuntuforums.org/showthread.php?t=1480915](http://ubuntuforums.org/showthread.php?t=1480915)
"Wacom Artpad II serial and Lucid" thread:  [http://ubuntuforums.org/showthread.php?t=1593973]("http://ubuntuforums.org/showthread.php?t=1593973")
"Configuring A Wacom Tablet In Lucid Lynx" thread:  [http://ubuntuforums.org/showthread.php?t=1462026&page=3](http://ubuntuforums.org/showthread.php?t=1462026&page=3) -  setting up a serial Wacom ArtzII tablet using a Keyspan serial->USB adapter, posts #24 to #34 with HOW TO at #34.  Kernel patch for the Keyspan serial-to-USB driver, adds a dummy TIOCGSERIAL ioctl, on [post #30]("http://ubuntuforums.org/showpost.php?p=10292776&postcount=30").
"Wacom DigitizerII 12x18 UD1218R Problems with Maverick Server" thread:  [http://ubuntuforums.org/showthread.php?t=1649439](http://ubuntuforums.org/showthread.php?t=1649439)

The [**Linux Wacom Tablet Project**]("http://sourceforge.net/projects/linuxwacom/") sourceforge site.
The Linux Wacom Project's  [**mediawiki main page**]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page").
The Linux Wacom Project's mediawiki [**linuxwacom HOWTO's**]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:Linuxwacom").
The Linux Wacom Project's mediawiki [**xf86-input-wacom HOWTO's**]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO").
The Linux Wacom Project's mediawiki [**DeveloperPages**]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:DeveloperPages").

Previous versions of wacom_serial.ko:
original version:  [http://cipht.net/releases/wacom_serial-110702-0.tar.gz](http://cipht.net/releases/wacom_serial-110702-0.tar.gz)
first version to support the PenPartner:  [http://cipht.net/releases/wacom_serial-120301-1.tar.bz2](http://cipht.net/releases/wacom_serial-120301-1.tar.bz2)


[SIZE="3"]**Ubuntu Release Specific Notes[/SIZE]**
**Precise Pangolin** (12.04):  The default xf86-input-wacom is 0.14.0.  Tokenrove's and roaldfre's new wacom_serial.ko serial tablet drivers also work for Precise, provided you make the appropriate edit to wacom_serial.c noted below.

**Oneiric Ocelot** (11.10):  The default xf86-input-wacom is 0.11.0.  Tokenrove's and roaldfre's new wacom_serial.ko serial tablet drivers also work for Oneiric.

**Natty Narwhal** (11.04):  The default xf86-input-wacom is 0.10.11.  Tokenrove's and roaldfre's new wacom_serial.ko serial tablet drivers are basically for Natty (kernel 2.6.38 or better).  The new serial drivers use inputattach to present the incoming raw data from the wacom_serial.ko's to xf86-input-wacom, which treats the incoming data as usb packets.  As part of the set up you need to add a 70-serial-wacom.rules file to your local udev rules (in /etc/udev/rules.d).  Tokenrove has supplied a test version for protocol 4 tablets that does build on Lucid and Maverick but describes it as "crippled".

**Maverick Meerkat** (10.10):  The default xf86-input-wacom is 0.10.8.  In order for 0.10.6 xf86-input-wacom to build on Maverick's 1.9 Xserver you need to apply a third patch:  "0003-dixScreenOrigins has been removed from server".  Patch sets that apply to xf86-input-wacom-0.10.7 and 0.10.8 are being tested in post #2.

**Lucid Lynx** (10.04):  The default xf86-input-wacom is 0.10.5.  You apply the version 3 0.10.6 patch set to the xf86-input-wacom-0.10.6 source code following the instructions below in part I.  Then after regenerating the build scripts you can compile and install as you normally would.  Patch sets that apply to xf86-input-wacom-0.10.7 and 0.10.8 are being tested in post #2.


**[SIZE="3"]Summary[/SIZE]**
Wacom serial tablet support was dropped from xf86-input-wacom due to a lack of developer resources.  The Wacom X driver was switched to Xorg's xf86-input-wacom beginning with Xserver 1.7.  This means that starting with Lucid there has been no official Wacom driver support for the UD series, PenPartner, and the Graphire, Intuos, and Cintiq series of serial tablets.  However serial ISDv4 devices (tablet PCs) have been and continue to be supported.

Tokenrove and roaldfre are developing new wacom_serial.ko's as the way forward for Wacom serial tablet support with xf86-input-wacom.  This is your chance to test and contribute to Linux kernel development!

A patch set for serial tablets by John Tsiombikas & Sebastian Berthold, using the old linuxwacom serial driver, was partially developed and works for enabling serial tablets when applied to xf86-input-wacom-0.10.6.  It does not apply cleanly to versions later than 0.10.6.  It was not included in the xf86-input-wacom driver because it needed further work.  Unfortunately development stopped after the second patch set was submitted on 5-24-10.  Which places the patch set about 20 commits into the 0.10.6+ git tree.  Sebastian had a serial Wacom Intuos2 GD-1218-R, and of course his patch set worked for it.  A number of serial tablet owners have successfully applied this patch set and gotten their tablets working in Lucid and Maverick.

This HOW TO shows you how to enable your serial tablet in Oneiric, Natty, Maverick, and Lucid.  The wacom_serial.ko drivers are new and being tested; and remember the old linuxwacom serial driver patch set is not finished driver worthy code, so be prepared for some glitches.

The HOW TO essentially consists of **two parts**.  The first deals with the **new kernel serial drivers for Natty and Oneiric** and the second uses the **linuxwacom serial driver for Lucid and Maverick**.  Currently for Lucid and Maverick the **[v3]xf86-input-wacom-0.10.6_serial-patches** is considered "validated" as it appears to be the most completely functional so far.  See post #2 for test patch set instructions for xf86-input-wacom-0.10.7 and 0.10.8.


**[SIZE="5"]New serial tablet drivers[/SIZE] - [SIZE="3"]for Natty and Oneiric[/SIZE]**
Once testing has firmed up the feature set and ironed out any bugs the new serial tablet drivers will be submitted to the Linux kernel for inclusion.

[SIZE="3"]***Testers reporting success***[/SIZE]
First ***wacom_serial.ko*** tester on Maverick was [**dreh**]("http://ubuntuforums.org/showpost.php?p=11041307&postcount=98") for a Wacom Digitizer II UD-1218-R.
First ***wacom_serial5.ko*** tester on Natty was [**firstattempt**]("http://ubuntuforums.org/showpost.php?p=11134517&postcount=133") for a Wacom Intuos GD-0405-R.  Second was [**alexcrow**]("http://ubuntuforums.org/showpost.php?p=11240634&postcount=163") for a Intuos2 A4 0912-R.  Third was **[luminol]("http://ubuntuforums.org/showpost.php?p=11379989&postcount=249")** for a Intuos2 XD-0912-R.
First ***wacom_serial.ko*** tester on Oneiric was **[mpGoodwin]("http://ubuntuforums.org/showpost.php?p=11377763&postcount=244")** for a Wacom Artpad. Second was [**dreh**]("http://ubuntuforums.org/showpost.php?p=11388036&postcount=255") for a Wacom Digitizer II UD-1218-R.
First ***wacom_serial5.ko*** tester on Oneiric was **[thorwil]("http://ubuntuforums.org/showpost.php?p=11375144&postcount=227")** for a Wacom Intuos2 GD-1212-R.

**[SIZE="3"]I. Prepare your system to build the kernel module and install Xorg's xf86-input-wacom-0.11.x tar[/SIZE]**
**Note**:  The following instructions assume you are downloading packages, extracting them, and compiling them on your Desktop.  If you use another directory change the directory paths in the commands accordingly.

Copy and paste each line into a terminal (Applications > Accesories > Terminal) and hit enter after each line (except the ones in parenthesis).  Careful, some lines extend past the right side of the "box".  Get all of them.
```
cd ./Desktop

sudo apt-get update

*(For **Mint** use **libX11-dev** instead of libx11-dev in the following command)*
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev

sudo apt-get upgrade

```


**[SIZE="3"]II. Build the serial kernel module/driver and the patched inputattach[/SIZE]**
The following is based on tokenrove's protocol 4 wacom_serial.ko package or roaldfre's protocol 5 wacom_serial5.ko package and their instructions in the above links.  Compiling and installing either of the serial_wacom.ko's is shown as well as patching and compiling inputattach.  Then if you have Lucid or Maverick update your xf86-input-wacom as below in appendix 1 at the bottom of the HOW TO.   Tokenrove has supplied a udev rule for wacom_serial.ko, see appendix 2 below.

**[COLOR="Blue"]For the 3.2 kernel (Precise) and protocol 4 (wacom_serial.ko) tablets[/COLOR]** you need to edit the wacom_serial.c source code in the wacom_serial folder after you unpack it.  This is necessary to prevent placing your tablet on the recently added tsc40.ko kernel module which now claims 0x3d as its serio protocol.  For wacom_serial5 (Intuos and Intuos2) you can ignore all of this unless you also use a protocol IV tablet.

In wacom_serial.c change line #49 from:
```
#define SERIO_WACOM_IV 0x3d
```
to:
```
#define SERIO_WACOM_IV 0x3e
```
i.e. the **d** to **e** before compiling.  You want it to look like:
```
/* XXX To be removed before (widespread) release. */
#ifndef SERIO_WACOM_IV
#define SERIO_WACOM_IV 0x3e
#endif
```
Also for wacom_serial you'll need to edit the serio-ids.h file changing line #129 to:
```
# define SERIO_WACOM_IV		0x3e
```
again changing **d** to **e**.  When you run the *make all* command both the compiled inputattach.ko along with wacom_serial.ko will now no longer conflict with tsc40.ko.

In the unlikely event you also had an Intuos tablet (protocol V) you would need to change it's current 0x3e to 0x3f since we're now giving 0x3e to the protocol IV tablets.  With 0x3e now claimed by wacom_serial.ko in you would in the wacom_serial5.c source code change line #46 to:
```
#define SERIO_WACOM_V 0x3f
```
i.e. the **e** to **f** before compiling.  You want it to look like:
```

/* XXX To be removed before (widespread) release. */
#ifndef SERIO_WACOM_V
#define SERIO_WACOM_V 0x3f
#endif

```
Similarly for wacom_serial5 edit the inputattach.patch in the folder, line #'s 72 and 75 so they read:
```

# define SERIO_WACOM_IV		0x3e
*and*
# define SERIO_WACOM_V		0x3f

```
Since 0x3d is the last one in serio.h in the 3.4 kernel rc we should be safe using 0x3e and 0x3f for the wacom_serial.ko's.

**a) Download and compile the protocol 4 wacom_serial.ko - by tokenrove** 
Rather than use the download link in [post #314]("http://ubuntuforums.org/showpost.php?p=11730826&postcount=314") we'll just grab tokenrove's new wacom_serial.ko tar directly:
```
wget http://cipht.net/releases/wacom_serial-120327-1.tar.bz2

tar xjvf wacom_serial-120327-1.tar.bz2

cd wacom_serial

make all

sudo cp inputattach /usr/bin

sudo cp wacom_serial.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet

sudo depmod -a

cd ..
```

**Note** for **tokenrove's protocol 4 serial_wacom.ko** in **Lucid or Maverick** use:  [http://cipht.net/releases/wacom_serial-for-2.6.35-testing.tar.gz](http://cipht.net/releases/wacom_serial-for-2.6.35-testing.tar.gz)  This a backport version for testers on earlier kernel versions.  A new input API dependency in later kernels was removed so wacom_serial.ko will build.  This amounts to all 4 lines beginning with *input_abs_set_res* being deleted.  But this version is accompanied by the warning "THIS VERSION HAS BEEN CRIPPLED TO ALLOW TESTING ON KERNEL 2.6.35.  PLEASE DO NOT USE IT UNLESS YOU MUST."  If you chose to use this version for Lucid or Maverick see appendix 1 below.  **Roaldfre** has **not done** this **for wacom_serial5** so it will not build in Lucid or Maverick.

**[SIZE="3"]OR[/SIZE]**

**a) Download and compile the protocol 5 wacom_serial5.ko (Intuos and Intuos2 tablets) - by roaldfre** 
You can either clone the wacom_serial5 git repository as below or use the download button on roaldfre's site for a tar or zip package.  Note if you use the download button a 7 digit identifier representing the last commit is appended to wacom_serial5 along with RoaldFre's name as a prefix.  I suggest you rename the extracted folder to wacom_serial5 or change the commands below to reflect the current name of the folder.
```
(install git if you haven't before)
sudo apt-get install git-core

git clone https://github.com/RoaldFre/wacom_serial5.git

cd wacom_serial5

make all

sudo cp wacom_serial5.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet

sudo depmod -a

cd ..
```
To view the manual on git cloning enter *man git clone* in a terminal.  It will explain more about the cloning process and how to use it, for example how to clone into a specified directory.

**b) Download and compile inputattach for the Intuos (protocol 5) tablets**
**Note:**  You can skip this step with tokenrove's recent wacom_serial tars, including the most recent wacom_serial-120327-1.tar, because he includes a pre-patched inputattach.c in the package and the *make all* command compiles the inputattach.ko along with the wacom_serial.ko.
Tokenrove's instructions won't work for the Intuos tablets in Ubuntu because Lucid, Maverick, and Natty are using an older version in the ***joystick-20051019*** package.  So the patch doesn't apply to it.  Instead get a newer version by downloading the ***linuxconsoletools-1.4.2*** package at the **Linux Console Project**:  [http://sourceforge.net/projects/linuxconsole/](http://sourceforge.net/projects/linuxconsole/).  Oneiric switches over to the newer inputattach from Linux Console.  Then follow these instructions:
```
sudo apt-get install libsdl1.2-dev

cd linuxconsoletools-1.4.2

*(if you have an Intuos tablet)*
patch -p1 < ~/Desktop/wacom_serial5/inputattach.patch

make

sudo PREFIX=/usr make install

cd ..
```
Eventually patches to add support for the new wacom_serial.ko's for Wacom serial tablets will be submitted at the Linux Console site.


**[SIZE="3"]Using inputattach with the new kernel module[/SIZE]**
Then following tokenrove's instructions with your tablet connected, turn it on, and run the command for starting inputattach.  Which would be either:
```

sudo inputattach --wacom_iv /dev/ttyS0
or
sudo inputattach --wacom_v /dev/ttyS0

```
To auto-start inputattach add the appropriate command (without sudo) to near the bottom of rc.local in /etc like so:
```

# By default this script does nothing.

inputattach --wacom_iv /dev/ttyS0
or
inputattach --wacom_v /dev/ttyS0

exit 0

```
Using:
```
gksudo gedit /etc/rc.local
```
Because the newly compiled wacom_serial.ko was copied into the appropriate /lib/modules directory for your kernel there is no need to manually load the module/driver with *sudo insmod ./wacom_serial5.ko*.  Either way of starting inputattach will also load the module.

**[SIZE="3"]Troubleshooting[/SIZE]**
On some systems adding the above inputattach command to rc.local doesn't work, perhaps because either inputattach or loading the wacom_serial.ko is a little slow and causes a bit of a hang.  You can deal with that by adding a trailing ampersand like so:
```
inputattach --wacom_iv /dev/ttyS0 &
```
This way the command is run in the "background".
* thanks to [mpGoodwin]("http://ubuntuforums.org/showpost.php?p=11409497&postcount=261") for pointing this out.

The Wacom serial tablets are usually on /dev/ttyS0 (or /dev/ttyUSB0 if using a serial-to-usb convertor).  If that doesn't work or you are not sure use:
```
sudo dmesg | grep ttyS
or
sudo dmesg | grep ttyUSB
```
to determine the port in use.

Something else that can cause problems is having two inputattach binaries installed.  The inputattach binary should be in /usr/bin.  If you also have another located in /usr/local/bin that will cause problems.  Right click on the binaries and check in Properties for the date (they were compiled).  You want to remove the duplicate in /usr/local/bin while also making sure the inputattach in /usr/bin is the one you compiled for your tablet.
* thanks to [bruis]("http://ubuntuforums.org/showpost.php?p=11893636&postcount=412") for pointing this out.


**[SIZE="3"]Tablet configuration[/SIZE]** is done through the 50-wacom.conf in /usr/share/X11/xorg.conf.d.  Since that is a distribution file users are encouraged to place their settings in a [52-wacom-options]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d") file.  Alternatively, because xf86-input-wacom doesn't have wacomcpl (Wacom Control Panel), you can set up a [script of xsetwacom commands]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration") to run when the system starts like wacomcpl's .xinitrc.  Both linked pages are on the xf86-input-wacom mediawiki HOWTO page linked above in Sources.   Also see *man wacom* & *man xsetwacom* entered in a terminal for more information on configuration options or parameters.


**[SIZE="5"]Old serial tablet driver[/SIZE] - [SIZE="3"]for Lucid & Maverick[/SIZE]**

[SIZE="3"]***Testers reporting success***[/SIZE] - probably need at least a protocol IV and a protocol V tablet reporting success to consider a patch set "validated".
First ***[v2]xf86-input-wacom-0.10.6_serial-patches*** tester on Maverick was [**Gizmoatwork**]("http://ubuntuforums.org/showpost.php?p=11034138&postcount=75") for an Intuos2 GD-0608-R.
First ***[v3]xf86-input-wacom-0.10.6_serial-patches*** tester on Lucid was [**timonoko**]("http://ubuntuforums.org/showpost.php?p=10994021&postcount=13") for the Graphire ET-0405-R.  Second on Maverick was [**Gizmoatwork**]("http://ubuntuforums.org/showpost.php?p=11041798&postcount=100") for an Intuos2 GD-0608-R.


**[SIZE="3"]I. Download Xorg's xf86-input-wacom-0.10.6 tar, patch it, and compile for Lucid or Maverick[/SIZE]** (the X driver)

**a) Download on your Desktop and, after installing the needed build libraries, unpack the xf86-input-wacom tar**
Open a terminal and enter (copy and paste) the following commands:
```

cd ./Desktop

wget http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.10.6.tar.bz2

sudo apt-get update

*(For **Mint** use **libX11-dev** instead of libx11-dev in the following command)*
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev

sudo apt-get upgrade

tar xjvf xf86-input-wacom-0.10.6.tar.bz2

```

**b) Apply the patches**
Download the patch set ***[v3]xf86-input-wacom-0.10.6_serial-patches*** attached below and extract it (right click).  Copy the patches into the now uncompressed source code folder xf86-input-wacom-0.10.6.  Then after changing directory into the xf86-input-wacom-0.10.6 folder apply the patches with the following commands.
```

cd xf86-input-wacom-0.10.6

patch -p1 < 0001-rename-wcmICDV4Speed-to-wcmSerialSpeed.patch

patch -p1 < 0002-reenable-support-for-legacy-serial-tablets.patch

*(apply the following only in Maverick, not needed for Lucid)*
patch -p1 < 0003-dixScreenOrigins-has-been-removed-from-server.patch

```
The original patch set from Sebastian Berthold, [v2]xf86-input-wacom-0.10.6_serial-patches, has been replaced with [v3].  Removed an unnecessary change in the first patch so it doesn't need to be fixed with the second patch.  It is interesting to note that the first patch *rename-wcmICDV4Speed-to-wcmSerialSpeed* would have been accepted at the time of original submission in May 2010 by the LWP into xf86-input-wacom-0.10.6+ if the change had been made then.  The original [v2] patch set is still attached.
* thanks to [thorwil]("http://ubuntuforums.org/showpost.php?p=10094864&postcount=618") for pointing out the third patch (to get 0.10.6 to build on 2.6.35).

**c) Regenerate the xf86-input-wacom build scripts**
The second patch adds the two new files wcmSerial.h and wcmSerial.c and also lists them in Makefile.am.  But since the original auto-generated build scripts were generated without them we need to update them (aclocal.m4, etc.).  So to regenerate the build scripts run in the terminal the following command:
```
aclocal && automake && autoconf
```
*thanks to [timonoko]("http://ubuntuforums.org/showpost.php?p=10994021&postcount=13") for pointing this out

**d) Compile the patched xf86-input-wacom source code**
```

./configure --prefix=/usr

make

sudo make install

```
Now reboot.


**[SIZE="3"]II. The xorg.conf[/SIZE]**
Currently the xorg.conf is used to configure serial tablets.  The following example xorg.conf assumes your xorg.conf is either empty or not there and needs to be created.  If you have a Wacom tablet mouse (cursor), you need to add a cursor section and add a cursor line to "ServerLayout" as shown.  Otherwise the cursor section and line are not needed and shouldn't be added.
```

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"         "/dev/ttyS0"
    Option        "Type"           "stylus"
    Option        "ForceDevice"    "Serial"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"         "/dev/ttyS0"
    Option        "Type"           "eraser"
    Option        "ForceDevice"    "Serial"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"         "/dev/ttyS0"
    Option        "Type"           "cursor"
    Option        "ForceDevice"    "Serial"
EndSection

Section "ServerLayout"
    Identifier    "X.org Configured"
    InputDevice   "stylus"
    InputDevice   "eraser"
    InputDevice   "cursor"
EndSection

```
If your xorg.conf is present with entries, say because you have a Nvidia video card/chipset and you are using the proprietary Nvidia video driver, then you would add the relevant Wacom "InputDevice" sections and to the "ServerLayout" the accompanying InputDevice line for each Wacom section.  Ask if you have questions, and be sure to post your current xorg.conf.
* thanks to timonoko for confirming "Serial" works in the "ForceDevice" option and that the all capitalized "SERIAL" isn't necessary

As always before changing a X configuration file make a **back up**.  In this case your current working xorg.conf if you have one.  In a terminal enter:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
To **restore** it from the command line if X is broken, and your graphical Desktop won't start, use:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
You can get to the command line by selecting the *recovery mode* option when you boot.

To **edit** it enter in a terminal:
```
gksudo gedit /etc/X11/xorg.conf
```
You may actually need the above command to create an xorg.conf.

The Wacom serial tablets are usually on /dev/ttyS0 (or /dev/ttyUSB0 if using a serial-to-usb convertor).  If that doesn't work or you are not sure use:
```
sudo dmesg | grep ttyS
or
sudo dmesg | grep ttyUSB
```
to determine the port in use.

**TO DO List**
1) Show dev(ice) line examples for serial to usb conversion cable?
2) Add section with information on use of serial to usb conversion cable?


**Appendix 1:  Install Xorg's xf86-input-wacom-0.11.x tar for wacom_serial.ko.  This is optional with Natty, required for Lucid or Maverick.** (the X driver)
The new wacom_serial.ko won't work with older versions of xf86-input-wacom.  Natty's default 0.10.11 or better are OK.  If you are using the wacom_serial.ko in Lucid or Maverick despite the warning let's try to standardize on xf86-input-wacom-0.11.x since it is planned that 0.11.x will be a "stable" branch for a while with bug fixes back ported into it.

**a) First** for **Lucid only** update to xorg-macros v. 1.8 (you only need to do this once).  You do not need to update xorg-macros in Maverick, it already has v. 1.8.
```

wget http://xorg.freedesktop.org/releases/individual/util/util-macros-1.8.0.tar.bz2

sudo cp /usr/share/aclocal/xorg-macros.m4 /usr/share/aclocal/xorg-macros.m4.bak

tar xjvf util-macros-1.8.0.tar.bz2

cd util-macros-1.8.0

./configure --prefix=/usr

make

sudo make install

cd ..
```

**b) Now compile the **xf86-input-wacom-0.11.1 tar (download, compile, and install xf86-input-wacom):
```

wget http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.11.1.tar.bz2

tar xjvf xf86-input-wacom-0.11.1.tar.bz2

cd xf86-input-wacom-0.11.1

./configure --prefix=/usr

make

sudo make install
```
Now reboot.

**Appendix 2:  70-serial-wacom.rules for wacom_serial.ko**
There is a typo in tokenrove's protocol 4 rule and it should read **ENV{PRODUCT}=='13/3d/*'** not ENV{PRODUCT}='13/3d/*', so:
```
ACTION=="add|change", SUBSYSTEM=="pnp", ENV{PRODUCT}=='13/3d/*', ENV{NAME}=="Wacom protocol IV serial tablet", SYMLINK="input/wacom", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"
```
There is not yet a rule for roaldfre's protocol 5.  Perhaps something like the following would do:
```
ACTION=="add|change", SUBSYSTEM=="pnp", ATTRS{id}=="PNP0501", ENV{NAME}=="Wacom protocol V serial tablet", SYMLINK="input/wacom", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"
```
To create and/or edit the 70-serial-wacom.rules use:
```
gksudo gedit /etc/udev/rules.d/70-serial-wacom.rules
```
Then add the appropriate rule to the file.


tags:  Wacom serial tablet, UD, PenPartner, Graphire, Intuos, Cintiq

---

### Post by Favux on 2011-06-11
Last updated: July 20, 2011

**[SIZE="5"]Project:  Get Serial patches to build on xf86-input-wacom-0.10.7[/SIZE]**

[SIZE="3"]***Testers reporting success***[/SIZE] - probably need at least a protocol IV and a protocol V tablet reporting success to consider a patch set "validated".
First ***[v1]xf86-input-wacom-0.10.7_serial-patches*** tester on Maverick was [**dreh**]("http://ubuntuforums.org/showpost.php?p=10996008&postcount=21") for a Wacom Digitizer II UD-1218-R.  Second was [**Gizmoatwork**]("http://ubuntuforums.org/showpost.php?p=11041798&postcount=100") for an Intuos2 GD-0608-R.
First ***[v2]xf86-input-wacom-0.10.7_serial-patches*** tester on Maverick was [**dreh**]("http://ubuntuforums.org/showpost.php?p=10999689&postcount=32") for a Wacom Digitizer II UD-1218-R.
First ***[v3]xf86-input-wacom-0.10.7_serial-patches*** tester on Maverick was [**dreh**]("http://ubuntuforums.org/showpost.php?p=11019832&postcount=47") for a Wacom Digitizer II UD-1218-R.  Second was [**Gizmoatwork**]("http://ubuntuforums.org/showpost.php?p=11033045&postcount=65") for an Intuos2 GD-0608-R.


**[SIZE="3"]I. Download Xorg's xf86-input-wacom-0.10.7 tar, apply the 0.10.7 test patches, and compile for Lucid or Maverick[/SIZE]** (the X driver)
**[COLOR="Blue"]The 0.10.7 patch sets apply to xf86-input-wacom-0.10.7 and all 3 versions are confirmed to "work" in that you can draw with the stylus.[/COLOR]**  The monolithic second patch was split into 6 patches.  A fair amount of code clean up has been accomplished by [v3] which we're now testing.

However there appear to be problems with pressure according to dreh and Gizmoatwork.  Gizmoatwork also reports non-functioning stylus side buttons for his protocol 5 Intuos2.  Both problems appear as soon as the change to 0.10.7 is made and apparently affect all 3 versions of the 0.10.7 patch sets.

**a) Download on your Desktop and, after installing the needed build libraries, unpack the xf86-input-wacom tar**
Open a terminal and enter (copy and paste) the following commands:
```

cd ./Desktop

wget http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.10.7.tar.bz2

sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev

sudo apt-get upgrade

tar xjvf xf86-input-wacom-0.10.7.tar.bz2

```

**b) Apply the patches**
Download the patch set ***[v3]xf86-input-wacom-0.10.7_serial-patches*** attached above and extract it (right click).  Copy the patches into the now uncompressed source code folder xf86-input-wacom-0.10.7.  Then after changing directory into the xf86-input-wacom-0.10.7 folder apply the patches with the following commands.
```

cd xf86-input-wacom-0.10.7

patch -p1 < 0001-rename-wcmICDV4Speed-to-wcmSerialSpeed.patch

patch -p1 < 0002-xf86WacomDefs.h-Legacy-serial-device.patch

patch -p1 < 0003-xf86Wacom.c-Legacy-serial-device-detection.patch

patch -p1 < 0004-wcmSerial.h-Add-to-driver.patch

patch -p1 < 0005-wcmSerial.c-Add-to-driver.patch

patch -p1 < 0006-Makefile.am-New-wcmSerial-files.patch

patch -p1 < 0007-wacom.man-Add-Serial-to-ForceDevice-option.patch

(apply the following only in Maverick, not needed for Lucid)
patch -p1 < 0008-dixScreenOrigins-has-been-removed-from-server.patch

```
* thanks to [thorwil]("http://ubuntuforums.org/showpost.php?p=10094864&postcount=618") for pointing out the "dixScreenOrigins-has-been-removed-from-server.patch" (to get 0.10.7 to build on 2.6.35).

**c) Regenerate the xf86-input-wacom build scripts**
The patch set adds the two new files wcmSerial.h and wcmSerial.c and the sixth patch also lists them in Makefile.am.  But since the original auto-generated build scripts were generated without them we need to update them (aclocal.m4, etc.) otherwise the following error will likely be thrown in /var/log/Xorg.0.log:
> I) LoadModule: “wacom”
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
dlopen: /usr/lib/xorg/modules/input/wacom_drv.so: undefined symbol: gWacomSerialDevice
(EE) Failed to load /usr/lib/xorg/modules/input/
So to regenerate the build scripts run in the terminal the following command:
```
aclocal && automake && autoconf
```
*thanks to [timonoko]("http://ubuntuforums.org/showpost.php?p=10994021&postcount=13") for pointing this out

**d) Compile the patched xf86-input-wacom source code**
```

./configure --prefix=/usr

make

sudo make install

```
Now reboot.

**TO DO List**
**Done** - 1) Get patch set to apply against 0.10.7
**Done** - 2) Simplify the second monolithic patch by breaking it up into separate patches.
**Done** - 3) Get patch set with above changes tested. - by dreh (protocol 4) & Gizmoatwork (protocol 5)
**Started** - 4) Clean up the patch set code a little.
5) Find and fix pressure and stylus side button problems.


**[SIZE="3"]II. Serial snippet in the xorg.conf.d wacom.conf[/SIZE]**
Hopefully we'll be able to replace the xorg.conf with a serial snippet.  Something like the following:
```

Section "InputClass"
    Identifier "Wacom legacy serial class"
#    MatchProduct "???"
    Driver "wacom"
    Option "ForceDevice" "Serial"
EndSection

```
At a guess we could probably use for the match:
```

    MatchProduct "PNP0501"
or
    MatchPnPID "PNP0501"

```
While technically not correct, since it is a generic Plug n Play kernel module, "PNP0501" worked for us using a .fdi file with HAL.  Likely not a problem unless there is a second unidentified serial device on the system.  And you would know if you have another serial device connected.  Some of the later serial tablets may have had an early form of a Plug n Play identifier, but I don't see any PnP identifiers in the code.  If so we'll need to add them in.  To check and develop information we'll need, enter this command in a terminal,:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
```
assuming the tablet is on ttyS0, and post the output please.

To edit the wacom.conf in Lucid use:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
```
In Maverick use:
```
gksudo gedit /usr/share/X11/xorg.conf.d/50-wacom.conf
```

It may be we need to make a new udev rule to get this to work.  So let's try:
```
ACTION!="add|change", SUBSYSTEM=="tty|pnp", SUBSYSTEMS=="pnp", ATTRS{id}=="PNP0501", ENV{ID_MODEL}="Legacy Serial Wacom Tablet $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Legacy Serial Wacom Tablet $attr{id}", SYMLINK="input/wacom"
```
in /etc/udev/rules.d, and call it 70-serial-wacom.rules.  Use:
```
gksudo gedit /etc/udev/rules.d/70-serial-wacom.rules
```
From:  [http://sourceforge.net/mailarchive/forum.php?thread_name=20110721001013.GA8525%40barra.bne.redhat.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=20110721001013.GA8525%40barra.bne.redhat.com&forum_name=linuxwacom-devel)

**TO DO List**
**Started** - 1) Try to develop a Serial Tablet snippet for the wacom.conf rather than use a xorg.conf. - several candidates tested by dreh, no luck yet
**Started** - 2) Need output of *udevadm info* command above and *xinput list* from working serial tablet for additional match line. - now have udevadm info from timonoko, dreh, & Gizmoatwork.  Timonoko's shows only ttyS0 while dreh & Gizmoatwork's are identical and both also have "PNP0501".  Serial snippet may not work for all serial tablets if not all Wacom serial tablets have "PNP0501".  So at least some serial tablets may require a xorg.conf.  **Would help to have a few more**.  Timonoko & Gizmoatwork's xinput lists shows the expected "device names" stylus, eraser, and cursor from the xorg.conf identifiers.  Maybe need full udevadm info's to check for anything possibly not currently included?



**[SIZE="5"]Project:  Get Serial patches to build on xf86-input-wacom-0.10.8[/SIZE]**

[SIZE="3"]***Testers reporting success***[/SIZE]


**[SIZE="3"]The show stopper commits on the xf86-input-wacom-0.10.7+ tree[/SIZE]**
The six patches/commits we likely need to wade through were all made on 6-22-10 and are:
1) "Split model probing, DEVICE_INIT and DEVICE_OPEN into separate functions.":  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=b5c27a694278641a0507e8d8cf883f02bdf69a49](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=b5c27a694278641a0507e8d8cf883f02bdf69a49)

2) "Remove serial class detection into the serial code.":  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=4e363076599b038ad032805f2a3023dd9f46826b](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=4e363076599b038ad032805f2a3023dd9f46826b)

3) Then "Factor out device class detection." from wcmConfig.c:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=aa382e6c8818e97538b2dad5d9b121a9cb533ed7](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=aa382e6c8818e97538b2dad5d9b121a9cb533ed7)

4) Then "Purge ForceDevice option - unneeded." involving 4 files:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=3ecabe9bd95b666fdd2a913ef1623751263e221d](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=3ecabe9bd95b666fdd2a913ef1623751263e221d)
Ouch!  This one hurts.

5) Then "Move class-specific option parsing into the device classes." involving a bunch of files:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=69d53ac51115af9f34a48451e13b717e48c06079](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=69d53ac51115af9f34a48451e13b717e48c06079)

6) Then "Move baud rate into ISDV4-specific backend." involving 4 files:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=cc4aa77eddbbe02ab7c9263dfd75ecf45f89fb96](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=cc4aa77eddbbe02ab7c9263dfd75ecf45f89fb96)
I think I can, with a lot of luck, muddle through to here.  But I'll probably have to keep wcmSerialSpeed in xf86WacomDefs.h and wcmCommon.c along with speed in wcmCommon.c.  I don't think the serial tablets will allow getting the baud rate from the serial tablet equivalent of wcmISDV4Data that the patch changes to.  But I could be wrong.


Then "Only execute GetRanges() once for ISDV4 devices." to wcmISDV4.c:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=19e0951239f9a24c60469bf1bf7f872358bd4e78](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=19e0951239f9a24c60469bf1bf7f872358bd4e78)
Only important because "ISDV4 tablets don't seem to like multiple query commands in a row, the reply for those are garbage. Hence, put a barrier in to prevent this. Since the isdv4data is shared between all devices off the same port, this simply skips the work of the isdv4GetRanges() and returns early with success."  So this may mean determining whether a serial device is an ISDV4 device (tablet PC) or a serial tablet may be trickier than I think, since we can't send out an extra query.


**[SIZE="3"]Compiling and testing the patches on a xf86-input-wacom-0.10.7+ snapshot[/SIZE]** (the X driver)

Let's see if we can get past the first 3 commits.  Apply the patch set **[aa382e6]xf86-input-wacom-0.10.7+_serial-patches** attached below to the commit's snapshot xf86-input-wacom-aa382e6.  If you're using the serial patch set you are already really a tester and I'm hoping some of you will test the 10.7+ patch sets and supply feedback.

**a) Download on your Desktop and, after installing the needed build libraries, unpack the xf86-input-wacom tar**
First down load the attached xf86-input-wacom-aa382e6.tar.gz onto your Desktop.  Open a terminal and enter (copy and paste) the following commands:
```

cd ./Desktop

sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev

sudo apt-get upgrade

tar zxvf xf86-input-wacom-aa382e6.tar.gz

```
**Note**:  Haven't figured out how to download the xf86-input-wacom snapshot from the command line.  Can get it directly from the git repository by clicking on *snapshot* in the browser.  The following wget command:
```
wget http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=snapshot;h=b5c27a694278641a0507e8d8cf883f02bdf69a49;sf=tgz
```
doesn't work.  If anyone knows how please let me know because I'd rather do that than keep attaching the snapshots.


**b) Apply the patches**
Download the patch set ***[aa382e6]xf86-input-wacom-0.10.7+_serial-patches*** attached below and extract it (right click).  Copy the patches into the now uncompressed source code folder xf86-input-wacom-aa382e6.  Then after changing directory into the xf86-input-wacom-0.10.7 folder apply the patches with the following commands.
```

cd xf86-input-wacom-aa382e6

patch -p1 < 0001-rename-wcmICDV4Speed-to-wcmSerialSpeed.patch

patch -p1 < 0002-xf86WacomDefs.h-Legacy-serial-device.patch

patch -p1 < 0003-wcmConfig.c-Legacy-serial-device-detection.patch

patch -p1 < 0004-wcmSerial.h-Add-to-driver.patch

patch -p1 < 0005-wcmSerial.c-Add-to-driver.patch

patch -p1 < 0006-Makefile.am-New-wcmSerial-files.patch

patch -p1 < 0007-wacom.man-Add-Serial-to-ForceDevice-option.patch

(apply the following only in Maverick, not needed for Lucid)
patch -p1 < 0008-dixScreenOrigins-has-been-removed-from-server.patch

```

**c) Compile the patched xf86-input-wacom source code**
```

./autogen.sh --prefix=/usr

make

sudo make install

```
Now reboot.

The first commit's snapshot xf86-input-wacom-b5c27a6 and the patch set for it ***[b5c27a6]xf86-input-wacom-0.10.7+_serial-patches*** are also attached below.

**TO DO List**
1) Get patch set to apply against 0.10.8


**_Appendix 1_:  Tablet Initialization**
Several folks have reported after using the original patches ([v2]xf86-input-wacom-0.10.6_serial-patches) their tablet would not respond unless they started wacdump first.  Wacdump can only be run briefly otherwise it will seg fault.  After that their tablet works fine.  So a few actually have set up wacdump in a script called from a Launcher or even to startup automatically on a reboot.  I'm not sure how many people are affected by this and if the percentage changes between Lucid and Maverick.

Wacdump usage is described in the [Viewing Wacom Data (wacdump)]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Linuxwacom_HOWTO#Viewing_Wacom_Data_.28wacdump.29") section of the Linuxwacom HOWTO.  Prebuilt wacdump binaries are available in the linuxwacom package, although they were removed in the last few released versions.  I think the most recent version that has the prebuilt wacdumps is [linuxwacom-0.8.8-10]("http://sourceforge.net/projects/linuxwacom/files/linuxwacom/").  They are located in the unpacked linuxwacom-0.8.8-10 source code folder in /prebuilt either /32 or /64.

This would seem to indicate a problem with the line discipline from the tty.  Presumably what wacdump does is set it correctly.  Since the tablets initialized without any problems with linuxwacom-0.8.4 we may be able to figure out what the problem is, i.e what change was introduced.  Assuming it is in the wacom driver code and not a general system thing.  It would be nice to fix this problem, especially if it fairly common.

While using the wacdump binary you may encounter the following error:
> ./wacdump: error while loading shared libraries: libtinfo.so.5: cannot open shared object file: No such file or directory
This is because Ubuntu is not one of the distributions that splits libtinfo out of the ncurses library.  Since wacdump is expecting to find libtinfo simply create a libtinfo linked file pointing to libncurses.  Create it in /lib if you have a 32-bit install or /lib64 if a 64-bit install.  For example:
```

cd /lib64
sudo ln -s libncurses.so.5.7 libtinfo.so.5

```

**_Appendix 2_:  Working with the patches**
With the xf86-input-wacom-0.10.7 patch set you can work on each individual patch separately.  The exception being the second patch "0002-xf86WacomDefs.h-Legacy-serial-device.patch".  Because it shares xf86WacomDefs.h with the first patch "0001-rename-wcmICDV4Speed-to-wcmSerialSpeed.patch" you have to apply and commit the first patch before working on the second one.

The first step is to install git (which you only need to do once) and then download xf86-input-wacom:
```

cd Desktop

sudo apt-get install git-core

git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom

```
Next change directory into the xf86-input-wacom folder.  There is no need to create a git branch, instead just *checkout* the tag *xf86-input-wacom-0.10.7* and work with a 'detached HEAD'.
```

cd xf86-input-wacom

git checkout xf86-input-wacom-0.10.7

```
Copy the patch(es) you want to work with into the xf86-input-wacom folder and apply the one you want to work with first.  After your changes add it, commit it, and create the patch.  Let's go through an example:
```

patch -p1 < 0001-rename-wcmICDV4Speed-to-wcmSerialSpeed.patch

**[make your changes]**

git add src/wcmCommon.c src/wcmConfig.c src/wcmISDV4.c src/wcmValidateDevice.c src/xf86WacomDefs.h

git commit -s
(when the nano editor pops up just copy the subject and commit message from the previous version of the patch, e.g.:
[I]rename wcmICDV4Speed to wcmSerialSpeed

Allows sharing between ISDV4 tablet PCs and re-introduced legacy serial tablets.

Signed-off-by: Sebastian Berthold <sb@sleif.de>
Signed-off-by: Favux[/I]
and add your changes to the body of the message)

git format-patch HEAD~1

```
Returning to the master branch:
```
git checkout master
```
You can update xf86-input-wacom when in the master branch by running:
```
git pull
```

---

### Post by firstattempt on 2011-06-14
Hi and thank you very much for your help 
I'm trying to get my Wacom Intuos GD-0405-R to work under ubuntu Natty (kernel 2.6.38.8) but, following advices provided here, i'm stuck at the "make" step
It appears i can't compile xf86-input-wacom-0.10.6 (nor 10.4 or 10.7) with or without the patches (i've checked that latest (11.1) do compile ok)
```
CC     xf86Wacom.lo
In file included from xf86Wacom.c:47:0:
xf86Wacom.h:96:38: error: expected &#8216;)&#8217; before &#8216;local
```is the pattern of errors i've got for output

I'm guessing i have problems with some mismatching libraries or kernel or karma
("configure" output is good, i've tried others procedures/patches - xf86-input-wacom_git-20100511.patch - mentioned on others places)
Didn't found something specific to Natty so far ...

Maybe are you aware of something which can make my relationship with my tablet less unbalanced 'coz it seems like i love her much more than she loves me, can't be just because i'm into narwhal nursing now  :-({|=

OOOps > Linuxwacom will not build on kernel 2.6.38 i guess it's related to this !

---

### Post by Favux on 2011-06-14
Hi firstattempt,

Welcome to the serial tablet thread!

Right now my main goal is to make it easier for serial tablets to set up in Lucid, since it will be around for two more years.  The fact that thanks to thorwil and Gaetan Nadon they will build on Maverick's 1.9 X server is a great bonus.

Sorry, but xf86-input-wacom 0.10.6 or 0.10.7 won't build on Natty's 1.10 X server.  To do that we'd need to get the patches to apply to a very recent version of xf86-input-wacom.  Probably 0.10.11 (Natty's default version) and later.

So first we probably need to get the patches to build on xf86-input-wacom-0.10.8.  Since there was a big code reorganization, especially including the ISDv4 serial stuff, I expect that will be challenging.  I haven't even looked at that yet.  It may not be doable by me.  After that is accomplished it probably wouldn't be too hard to move up the chain of releases to a current xf86-input-wacom.  I don't think there were too many more significant code changes for serial stuff after 0.10.8.

In short to get your Wacom Intuos GD-0405-R to love you you'll need to use either Lucid or Maverick.  :)

---

### Post by firstattempt on 2011-06-14
Sure you made a good point   :D  sounds like a Oneiric challenge though

Thanks again

---

### Post by tokenrove on 2011-06-21
Hi,

I was wondering if anyone else had started working on this, yet -- that is, porting the old serial code to the newer versions of xf86-input-wacom?

I started working on it this morning (against 0.10.10), and can't guarantee how long I'm going to take to do it, but I'd like to avoid duplicating work if someone is already doing this.  My goal is to get the patch into a state where it can be accepted into the xf86-input-wacom codebase so that these ridiculous efforts every few versions can stop.

Cheers.

---

### Post by Favux on 2011-06-21
Hi tokenrove,

Welcome to Ubuntu forums!

> I was wondering if anyone else had started working on this, yet -- that is, porting the old serial code to the newer versions of xf86-input-wacom?

I started working on it this morning (against 0.10.10), and can't guarantee how long I'm going to take to do it, but I'd like to avoid duplicating work if someone is already doing this.
That's great!  Something that is really needed.

While I have no way to know for sure, as far as I'm aware, you are the only one currently working on the serial code.  As mentioned I have some more style cleanup of the wcmSerial.c and .h code as per Peter's in line comments if you are interested.

---

### Post by dreh on 2011-06-22
Hi Favux et al,
these are great news. I'm not updating to natty cause of my old Wacom tablet. I would love to see some improvement here --> How can I help? My new Lenovo workstation will arrive this week (thumbs cross)  and I'm willing to install natty (64bit) instead of maverick on it if there is a possible way to test bleeding edge Wacom drivers for my UD serial tablet.
Thank you Favux for being active in this field!
Johannes alias Dreh

---

### Post by tokenrove on 2011-06-22
> **Favux said:**
> While I have no way to know for sure, as far as I'm aware, you are the only one currently working on the serial code.  As mentioned I have some more style cleanup of the wcmSerial.c and .h code as per Peter's in line comments if you are interested.

Okay, I will continue to work on it.  As I said, it's not a high priority for me (although I want my old UD tablet to work on my current machine), so it may take some time, but I think it would be a travesty to lose support for these great devices which are still so functional.

I was wondering -- do you think that getting older Wacom tablets added to the input/serio code in the kernel (so you can "inputattach -wacom-ud /dev/ttyS0" for example) would be the right way to approach cleaning up detection?

Cheers.

---

### Post by Favux on 2011-06-22
Hi Johannes,

> I'm not updating to natty cause of my old Wacom tablet. I would love to see some improvement here --> How can I help?
Thank you for the offer!  Right now it would be most helpful to test the current patch sets in Lucid and Maverick so we know which of them are currently working and can iron out any glitches in them or the instructions.  I have a second patch set for 0.10.7 ready to go if the first one is verified.  And once someone tests "Serial" instead of "SERIAL" in the ForceDevice option.

Knowing details on your model and the baudrate it uses etc. would be helpful.  It is possible some of the glitches reported are model specific, and that would help figure that out.

Hopefully we can make the Serial HOW TO useful for setting up serial tablets in the interim.


Once tokenrove has some code I'm sure he will want testers, including testers in Natty.

---

### Post by Favux on 2011-06-22
Hi tokenrove,

> I was wondering -- do you think that getting older Wacom tablets added to the input/serio code in the kernel (so you can "inputattach -wacom-ud /dev/ttyS0" for example) would be the right way to approach cleaning up detection?
That would make sense to me actually.  But it's Peter Hutterer's opinion that matters.  So it is good you asked on devel.

By the way they have already implemented inputattach for wacom_w8001.ko touchscreens in input-wacom:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Input-wacom)  on the Developer pages:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:DeveloperPages](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:DeveloperPages)

So you may have a chunk of the work done for you already.

---

### Post by Favux on 2011-06-27
Hi everyone,

I finally looked at getting the patch set to apply to xf86-input-wacom-0.10.8.  It looks like there are 6 show stopper commits in a row all on 6-22-10.

I think it may be possible to muddle through to the sixth one, with a lot of luck.  But with the 6th commit, "Move baud rate into ISDV4-specific backend." - [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=cc4aa77eddbbe02ab7c9263dfd75ecf45f89fb96](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=cc4aa77eddbbe02ab7c9263dfd75ecf45f89fb96), I'll probably have to keep wcmSerialSpeed in xf86WacomDefs.h and wcmCommon.c along with speed in wcmCommon.c.  I don't think the serial tablets will allow getting the baud rate from the serial tablet equivalent of wcmISDV4Data that the commit changes to.  But I'm not sure.  So if anyone sees a way chime in.

If that breaks ISDV4 devices, i.e. serial tablet PCs, that would be a big problem.  It would be good, if we ever get to that point, for someone to test a serial tablet PC with that hypothetical future patch set.

So even if after 0.10.8 it is smooth sailing to 0.11.1 that would likely be a problem for submission of the patch set.  Not to mention the error messages need to be fixed and the requested look up tables, etc.  Of course tokenrove may by then have code that obviates those problems.

But for now I've gotten way ahead of things.  Hopefully folks will start using the patch sets and supply feed back sometime soon.

---

### Post by timonoko on 2011-06-29
I got these lines in my /var/log/Xorg.0.log:

I) LoadModule: &#8220;wacom&#8221;
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
dlopen: /usr/lib/xorg/modules/input/wacom_drv.so: undefined symbol: gWacomSerialDevice
(EE) Failed to load /usr/lib/xorg/modules/input/


Then I tried "aclocal && automake && autoconf" before ".configure" and "make" and "make install".

Now the pen is working perfectly, even the pressure sensitivity is 100% OK.

I have Lucid and ET-0405-R tablet.

---

### Post by Favux on 2011-06-29
Hi timonoko,

Welcome to Ubuntu forums!

Outstanding!  Thank you for the feedback.  :)

I am assuming you used the [v3]xf86-input-wacom-0.10.6_serial-patches for xf86-input-wacom-0.10.6 on Lucid.  Am I correct?  With the *aclocal && automake && autoconf* commands.

Would you mind, while the tablet is working, running the commands *xinput list* and *udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)* and posting the outputs?

Also it may help if you supply any specifications on your Graphire ET-0405-R you have.  Stylus has how many side buttons?  Eraser?  Wacom mouse?  Tablet active area in mm or inches?  Baud rate?  Etc.

Are you planning on testing the 0.10.7 patch set?

---

### Post by timonoko on 2011-06-29
I made everything just like this HOWTO said. I found this aclocal-stuff by Googling "gWacomSerialDevice".

$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; stylus                                      id=6    [slave  pointer  (2)]
&#9116;   &#8627; eraser                                      id=7    [slave  pointer  (2)]
&#9116;   &#8627; cursor                                      id=8    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=15    [slave  pointer  (2)]
&#9116;   &#8627; EL USB Keyboard                             id=12    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Power Button                                id=10    [slave  keyboard (3)]
    &#8627; Sirius USB2.0 Camera                        id=13    [slave  keyboard (3)]
    &#8627; Sirius USB2.0 Camera                        id=14    [slave  keyboard (3)]
    &#8627; EL USB Keyboard                             id=11    [slave  keyboard (3)]

~$ udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pnp0/00:08/tty/ttyS0':
    KERNEL=="ttyS0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pnp0/00:08':
    KERNELS=="00:08"
    SUBSYSTEMS=="pnp"
    DRIVERS=="serial"

  looking at parent device '/devices/pnp0':
    KERNELS=="pnp0"
    SUBSYSTEMS==""
    DRIVERS==""

ET-0405-R has stylus and mouse. Stylus has eraser and two buttons. Tablet area is 12 mm wide.

The sensitivity curve feels better than it was in Jaunty. The Gimp ink flows more smoothly, just like in Windows and Photoshop.

---

### Post by Favux on 2011-06-29
Thanks for the outputs and specifications.  I really appreciate it.

> The sensitivity curve feels better than it was in Jaunty. The Gimp ink flows more smoothly, just like in Windows and Photoshop.

Sweet.

I'm not sure about a serial snippit in wacom.conf with just ttyS* to match to, so we might need to stay with the xorg.conf.

Would you be willing to try "Serial" instead of "SERIAL" on the ForceDevice option lines in xorg.conf and see if it still works?

> I made everything just like this HOWTO said. I found this aclocal-stuff by Googling "gWacomSerialDevice".
That was nice work.  Thanks for the tip.  I just started looking at that and trying to figure out why you need to run those extra commands.  I think your the first person to report that.  Is it possible, by any chance, that you didn't get all of the dependency line like autoconf?  It extends way to the right of the box and some folks accidently cut it off when they copy and paste.
> sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev


---

### Post by timonoko on 2011-06-29
> **Favux said:**
> 
Would you be willing to try "Serial" instead of "SERIAL" on the ForceDevice option lines in xorg.conf and see if it still works?

Changed one of  them, works OK.

> 
Is it possible, by any chance, that you didn't get all of the dependency line like autoconf?  It extends way to the right of the box and some folks accidently cut it off when they copy and paste.I pasted the stuff into a file and applied chmod+x and run it. And the file is OK. 

-- I realize now however that this might cause errors, because pasting stuff directly onto command line uses same set of environmental variables. :-)

---

### Post by Favux on 2011-06-29
> Changed one of them, works OK.
Good!  Could you please change all of them to "Serial" and see if the tablet still works.  I'm trying to figure out if the code is case specific, i.e. requires "SERIAL" for version 2 of the 0.10.7 patch.  If it is we would need a small change to a line in the code.  If not we're good to go.
```
I pasted the stuff into a file and applied chmod+x and run it. And the file is OK.

-- I realize now however that this might cause errors, because pasting stuff directly onto command line uses same set of environmental variables. 
```
Alright, that could be it.  I did find another report on Ubuntu forums about that error.  I thought that was because he was using a serial-to-usb converter and had some other issues.  I'm assuming you found the fix here:  [http://forums.opensuse.org/english/get-technical-help-here/hardware/444426-wacom-graphics-tablet.html](http://forums.opensuse.org/english/get-technical-help-here/hardware/444426-wacom-graphics-tablet.html)

Hopefully we don't need the fix.  But if we do have to generate a new aclocal.m4 because we've added new files and whatnot no big deal.  I can just add:
```
aclocal && automake && autoconf
```
to the instructions.

---

### Post by timonoko on 2011-06-29
>   Could you please change all of them to "Serial" and see if the tablet still works.  I'm trying to figure out if the code is case specific, i.e. requires "SERIAL" for version 2 of the 0.10.7 patch.  If it is we would need a small change to a line in the code.  If not we're good to go.
Changed all. Works OK.

> I'm assuming you found the fix here:  [http://forums.opensuse.org/english/get-technical-help-here/hardware/444426-wacom-graphics-tablet.html](http://forums.opensuse.org/english/get-technical-help-here/hardware/444426-wacom-graphics-tablet.html)
I think it was here:[ http://codelab.wordpress.com/2010/02/21/wacom-hacking/]("http://codelab.wordpress.com/2010/02/21/wacom-hacking/")

---

### Post by Favux on 2011-06-29
> Changed all. Works OK.
Great!  Ready to bring out version 2 of the 0.10.7 patch set then.  As soon as someone tests version 1.
```
I think it was here: http://codelab.wordpress.com/2010/02/21/wacom-hacking/
```
Sure enough according to WWWWolf:
> I was boundlessly confused by the missing gWacomSerialDevice symbol. Then I realised that that source file in question wasn’t even compiled. And that’s completely expected – the reference was added to Makefile.am but it’s not in the auto-generated build scripts. You need to re-run autotools to update the files.
That makes sense.  I'll update the instructions to include re-generating the build scripts then.  Thank you very much!

---

### Post by dreh on 2011-06-29
Hello Favux et al,
my new workstation arrived today. I installed Ubuntu 10.10 (64 bit server. I used your 'A Call for Testers' - Guide and it works.

I used the 10.7 V1 Patch. Interestingly I don't have to wacdump to get the tablet initialized it works after login --> this is a major improvement for me.  

```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)

  looking at device '/devices/pnp0/00:08/tty/ttyS0':
    KERNEL=="ttyS0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pnp0/00:08':
    KERNELS=="00:08"
    SUBSYSTEMS=="pnp"
    DRIVERS=="serial"
    ATTRS{id}=="PNP0501"

  looking at parent device '/devices/pnp0':
    KERNELS=="pnp0"
    SUBSYSTEMS==""
    DRIVERS==""

```
I used the serial snipped but that didn't work. hardcoding in xorg.conf did the job.
Thank you for this guide. Is there anything else I can test and poste to improve the quality of the driver ?
Johannes alias Dreh

---

### Post by Favux on 2011-06-29
Hi Johannes,

Absolutely Outstanding!  :D

Great timing.  Glad your new IBM workstation arrived today.  So now we have a confirmation for v3 of the 0.10.6 patch set in Lucid and version 1 of the 0.10.7 patch set in Maverick!
> Interestingly I don't have to wacdump to get the tablet initialized it works after login --> this is a major improvement for me. 
Super.  I'm actually wondering if rather than setting the line discipline wacdump was getting around the error caused by not regenerating the build script.  It will be interesting to see what sort of feedback we get on that.

Right now I count it a victory that we are able to use 0.10.7.  That's two versions newer than the default Lucid version (with all the bug fixes and improvements that brings) and only one behind the Maverick default.
> Is there anything else I can test and post to improve the quality of the driver ?
Definitely.  I should have v2 of the 0.10.7 patch set out in a little bit for testing.  More code clean up and fixing of *man wacom*.  After that there's maybe a couple of more easy fixes we could work on for v3.  And we could also work on the serial snippet.  Thank you for the udevadm info.

After that it would be trying to get the patch set to apply to 0.10.8 if I'm feeling brave (maybe foolish is a better description).  I think rather than just jumping to the 0.10.8 tar it would be better to test several snap shots along the 0.10.7+ tree.  So you would need to compile several versions of 0.10.7+ for testing.  Would you be game for that?

---

### Post by dreh on 2011-06-29
Sure! I have lots to do the next days but I'm gonna find some time in between.

---

### Post by Favux on 2011-06-29
Alright Johannes and anyone else interested,

I have version 2 of the 0.10.7 patch set posted on the HOW TO.  Looking forward to hearing your test results.  :)


Also while *MatchDevicePath "/dev/ttyS*"* didn't work in a serial tablet snippet for you could you test:
```
Section "InputClass"
    Identifier "Wacom legacy serial class"
#    MatchProduct "???"
    MatchDevicePath "/dev/ttyS0"
    Driver "wacom"
    Option "ForceDevice" "Serial"
EndSection
```
and see if it works for you?  Maybe using a wild card match (*) doesn't work for serial ports even though it does for usb ports.  If it does then, since your *udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)* showed "PNP0501", please try:
```
Section "InputClass"
    Identifier "Wacom legacy serial class"
    MatchProduct "PNP0501"
    MatchDevicePath "/dev/ttyS0"
    Driver "wacom"
    Option "ForceDevice" "Serial"
EndSection
```
Don't know if MatchProduct is the correct one to use.  The documentation is always so out of date.  I'll try to see if there's something else like MatchId.  If we can get something similar to this working we'd have a snippet that works for at least some serial tablets and shouldn't interfere with ISDV4 serial devices.

And other testers remember you need to comment out (#) your Wacom sections in xorg.conf and the Wacom lines in "ServerLayout" to test the wacom.conf.  Part III. in the HOW TO describes how to edit the wacom.conf.

Alright I think I found it - MatchPnPID.  So if MatchProduct above doesn't work try:
```
Section "InputClass"
    Identifier "Wacom legacy serial class"
    MatchPnPID "PNP0501"
    MatchDevicePath "/dev/ttyS0"
    Driver "wacom"
    Option "ForceDevice" "Serial"
EndSection
```
And if that works try changing ttyS0 back to a wildcard match ttyS*:
```
Section "InputClass"
    Identifier "Wacom legacy serial class"
    MatchPnPID "PNP0501"
    MatchDevicePath "/dev/ttyS0"
    Driver "wacom"
    Option "ForceDevice" "Serial"
EndSection
```
It would be great if the wild card match works.  Our candidate serial tablet snippet would be more versatile, although I think most if not all use the S0 port.

---

### Post by dreh on 2011-06-30
> **Favux said:**
> Alright Johannes and anyone else interested,

I have version 2 of the 0.10.7 patch set posted on the HOW TO.  Looking forward to hearing your test results.  :)

Hi Favux,
unfortunately I get compiler errors.

```
make
make  all-recursive
make[1]: Entering directory `/home/johannes/Desktop/xf86-input-wacom-0.10.7'
Making all in conf
make[2]: Entering directory `/home/johannes/Desktop/xf86-input-wacom-0.10.7/conf'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/johannes/Desktop/xf86-input-wacom-0.10.7/conf'
Making all in src
make[2]: Entering directory `/home/johannes/Desktop/xf86-input-wacom-0.10.7/src'
  CC     xf86Wacom.lo
  CC     wcmCommon.lo
  CC     wcmConfig.lo
  CC     wcmISDV4.lo
  CC     wcmSerial.lo
wcmSerial.c: In function ‘serialGetResolution’:
wcmSerial.c:1041: error: ‘header’ undeclared (first use in this function)
wcmSerial.c:1041: error: (Each undeclared identifier is reported only once
wcmSerial.c:1041: error: for each function it appears in.)
make[2]: *** [wcmSerial.lo] Error 1
make[2]: Leaving directory `/home/johannes/Desktop/xf86-input-wacom-0.10.7/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/johannes/Desktop/xf86-input-wacom-0.10.7'
make: *** [all] Error 2
```

Probably this is a minor issue but my coding skills are very under developed. To counter check I recompiled V1 and it still compiles.
Snippet testing is next ...

---

### Post by Favux on 2011-06-30
Hmmm.  It compiled fine for me in Maverick.  Let me check again.  Maybe I put the wrong patch in or made a inadvertent change.  You're sure you applied all 8 patches?

Looking forward to the report on the snippet.

---

### Post by Favux on 2011-06-30
Ahh.  I built it a few days ago without regenerating the build scripts, then there are no errors.

But if I do regenerate them (aclocal && automake && autoconf) then I get the same error in /src:
```
  CC     xf86Wacom.lo
  CC     wcmCommon.lo
  CC     wcmConfig.lo
  CC     wcmISDV4.lo
  CC     wcmSerial.lo
wcmSerial.c: In function ‘serialGetResolution’:
wcmSerial.c:1041: error: ‘header’ undeclared (first use in this function)
wcmSerial.c:1041: error: (Each undeclared identifier is reported only once
wcmSerial.c:1041: error: for each function it appears in.)
make[2]: *** [wcmSerial.lo] Error 1

```

I'll take down v2 of the 0.10.7 patches off the HOW TO then.  So delete your copy or rename it so you don't confuse it with the hopefully fixed new version 2.  If I can figure out the problem.

---

### Post by dreh on 2011-06-30
Hi Favux,
tried compiling again with same results. 

Do I need to reference the snippet in the "serverlayout"-section of xorg.conf? Is this quote true in Ubuntu?
> Note: The InputClass section automatically enables the AutoServerLayout option, you do not need to specify it.
If yes, I can't get the driver running with all given options:

```
MatchPnPID "PNP0501"

```
```
MatchProduct "PNP0501"

```

---

### Post by Favux on 2011-06-30
Not sure what you mean.  There is no "ServerLayout" in xorg.conf.d.  The 50-wacom.conf where you should be placing the snippet is at /usr/share/X11/xorg.conf.d in Maverick.  Stick it between the serial (ISDV4) and Ntrig snippets.  You should have your xorg.conf Wacom stuff commented out while testing a wacom.conf file in xorg.conf.d and there is no need to reference a .conf file snippet in the xorg.conf "ServerLayout".  See also part III a) of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

I'm surprised at least ttyS0 doesn't work.

I'm not going to start working on fixing v2 for a little bit.  Need to take a short break and do some other stuff.  I don't think it'll be too hard, cross fingers.  Maybe something this evening.


Edit:  Oops.  I went ahead and found where it broke and I didn't even mean to.  Just couldn't leave it alone.  Now use the easy fix or try something else?  :)

Edit 2:  OK, fixed it.  Or at least it compiles without error.  I'll post the fixed v2 as soon as a make a new patch to replace the one with the error.  We'll see if the tablet still works.  ;)

---

### Post by dreh on 2011-06-30
Sry I'm not a native english speaker - maybe I'm expressing myself a bit confusing :D
My xorg.conf looks like this (without all the NVIDIA stuff)

```
#Section "InputDevice"
#    Driver        "wacom"
#    Identifier    "stylus"
#    Option        "Device"         "/dev/ttyS0"
#    Option        "Type"           "stylus"
#    Option        "ForceDevice"    "Serial"
#EndSection

#Section "InputDevice"
#    Driver        "wacom"
#    Identifier    "eraser"
#    Option        "Device"         "/dev/ttyS0"
#    Option        "Type"           "eraser"
#    Option        "ForceDevice"    "Serial"
#EndSection

#Section "InputDevice"
#    Driver        "wacom"
#    Identifier    "cursor"
#    Option        "Device"         "/dev/ttyS0"
#    Option        "Type"           "cursor"
#    Option        "ForceDevice"    "Serial"
#EndSection
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
#       InputDevice   "stylus"
#    InputDevice   "eraser"
#    InputDevice   "cursor"
EndSection

```

and the /usr/share/X11/xorg.conf.d/50-wacom.conf looks like this:

```
Section "InputClass"
        Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
        MatchProduct "Wacom|WALTOP|WACOM"
        MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class"
        MatchProduct "Serial Wacom Tablet"
        Driver "wacom"
        Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
        Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
    Identifier "Wacom legacy serial class"
    MatchProduct "PNP0501"
    #MatchPnPID "PNP0501"
    MatchDevicePath "/dev/ttyS0"
    Driver "wacom"
    Option "ForceDevice" "Serial"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001|N-Trig Pen"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        Option "Button2" "3"
EndSection

```

The xorg.conf.d/50-wacom.conf wont start up the tablet in any variation. maybe my Digitizer II just isn't compatibel with udev at all. To cross check if I did something else wrong I uncommented the wacom lines in xorg.conf and 'BOOM' it works again after xorg restart.

Ok I have to go to bed. I'm tired like hell. Tomorrow morning I can test the repaired driver (v2) if it's available.
dreh alias johannes

---

### Post by Favux on 2011-06-30
Thanks for all your work.  I figured I just misunderstood you.  Deutsch?

Looks like you are doing everything correctly which probably means I am the one doing something wrong.

The fact that even *MatchDevicePath "/dev/ttyS0"* alone doesn't work is probably a big fat clue if I can figure it out.  :confused:

I have v2 back up for you to test.  Compiles without the error anyway.

Sleep well.  Tomorrow then.

---

### Post by dreh on 2011-06-30
hehe and
compiled --> installed --> (v2 repaired) works!
Im off to bed.
J.

---

### Post by Favux on 2011-06-30
Outstanding!  :D  Thank you for testing it.

lol  You couldn't leave it alone either.


Regarding the snippet.  Have you tried?
```
Section "InputClass"
    Identifier "Wacom legacy serial class"
    MatchPnPID "PNP0501"
    Driver "wacom"
    Option "ForceDevice" "Serial"
EndSection
```

---

### Post by dreh on 2011-07-01
> **Favux said:**
> Outstanding!  :D  Thank you for testing it.

lol  You couldn't leave it alone either.


Regarding the snippet.  Have you tried?
```
Section "InputClass"
    Identifier "Wacom legacy serial class"
    MatchPnPID "PNP0501"
    Driver "wacom"
    Option "ForceDevice" "Serial"
EndSection
```

morning,
i tried the above snippet (again) and couldn't get it run. 

Unfortunately we maybe introduced a bug: In Gimp when I draw with the tablet the pressure curve works like intended till you force the pen quite hard on the tablet (I would say it's max pressure). If I do that the stroke stops drawing until I loosen it a bit again than it continuous. So Max pressure = 0 ClickForce. Is there a possibility to calibrate this with xsetwacom or Gimp preferences? I'll try another painting program.
I'll update more on this ... Probably it would be good to test 10.6 and 10.7 v1 if the bug is here, too.
J.

Edit: Same behavior in Inkscape

---

### Post by Favux on 2011-07-01
> i tried the above snippet (again) and couldn't get it run.

Shoot.  I would really like a snippet for v3.  I guess the last thing to try is:
```
Section "InputClass"
    Identifier "Wacom legacy serial class"
    MatchProduct "PNP0501"
    Driver "wacom"
    Option "ForceDevice" "Serial"
EndSection
```
because I can't imagine MatchVendor would work.  What I'm thinking is MatchDevicePath only works on the input subsystem.  In other words the path has to be /dev/input/something which is why /dev/ttyS0 isn't working.  The documentation (what little there is) doesn't say that, but it is the only thing that makes sense.

For a lark you could try MatchDevice "/dev/ttyS0" as the only match.  I thought I read that one somewhere but I can't find it now.  The only new match I'm sure they added was MatchDriver for Xserver 1.10.  If you try MatchDevice be sure to back up your current working 50-wacom.conf so you can restore it if MatchDevice breaks X.  I guess I'll have to try and find the .fdi we were using in HAL.  But I don't think there is a direct translation from that match to a xorg.conf.d Match.

> Unfortunately we maybe introduced a bug: In Gimp when I draw with the tablet the pressure curve works like intended till you force the pen quite hard on the tablet (I would say it's max pressure). If I do that the stroke stops drawing until I loosen it a bit again than it continuous. So Max pressure = 0 ClickForce.
What Mode is your tablet in, Relative or Absolute?  The pressure fix for 0.10.7 was:
> In relative mode, subtract the old pressure value from the new one.

Otherwise the pressure builds up to the maximum and stays there, even when the pen is lifted off the tablet. Same goes for tilt, wheel and rotation/throttle
Sure you can adjust ClickForce.  The default is 27.  At some point they normalized all pressure levels to 0 - 2047 regardless of what the hardware reports.  So I think you could increase ClickForce all the way to 2047 if you wanted.
```
xsetwacom set "stylus" ClickForce "54"
```

The bug could be from the serial code but it is at least as likely to be in the driver code.  The 0.10.x series was not suppose to be for general user use.  That is the code cleanup and feature subtract and add series tree.  0.11.0, which just came out, was suppose to be the first version for general user testing.  Because it is suppose to be nearly feature complete and more bug free.  In other words more stable code.

So definitely:
> Probably it would be good to test 10.6 and 10.7 v1 if the bug is here, too.
Maybe timonoko or someone else could tell us if they are seeing it with 0.10.6?  Or in Lucid in case it is a Maverick thing.


Edit:  Oh, and did I guess correctly?  Your Digitizer II is a UD-0608-A?

---

### Post by tokenrove on 2011-07-01
> **Favux said:**
> 
So even if after 0.10.8 it is smooth sailing to 0.11.1 that would likely be a problem for submission of the patch set.  Not to mention the error messages need to be fixed and the requested look up tables, etc.  Of course tokenrove may by then have code that obviates those problems.


I think the old approach of having all the serial code in the xorg driver is probably not the right direction.  I now have a working input driver for protocol 4 Wacom serial tablets -- at least it works nicely on my Digitizer II; I still need to do some debugging and put protocol documentation up on the xf86-input-wacom wiki, but it's a good step.  It works just fine with the existing wcmUSB code on the X side.

This brings me to a question (obviously I'll ask the linuxwacom-devel list, too, but I wanted to get a general feel here first) -- are many people using serial Intuos or Intuos 2 tablets?  I don't have any protocol 5 devices and I think things would be cleaner if the drivers were separate.

---

### Post by Favux on 2011-07-01
Hi tokenrove,

> **tokenrove]I think the old approach of having all the serial code in the xorg driver is probably not the right direction.[/QUOTE]
Sure, but while we're waiting for you to come up with the code I thought I'd see what we could do with what we have.  Actually making some progress.
[QUOTE=tokenrove]I now have a working input driver for protocol 4 Wacom serial tablets -- at least it works nicely on my Digitizer II said:**
> 
That is great!  Real progress and fast too.
[QUOTE=tokenrove]This brings me to a question (obviously I'll ask the linuxwacom-devel list, too, but I wanted to get a general feel here first) -- are many people using serial Intuos or Intuos 2 tablets? I don't have any protocol 5 devices and I think things would be cleaner if the drivers were separate.
Don't forget the Citiq's.  Although having support for better than half the serial models is obviously better than no support.

---

### Post by tokenrove on 2011-07-01
> **Favux said:**
> That is great!  Real progress and fast too.

Thanks.  I would have liked to have gotten to it sooner but some other things got in the way.  Anyway, I expect by the end of the evening I should be at the limits of what I can do with my tablet alone and will need others to test.  (Already, my itch is scratched, since I can finally use my tablet in the gimp properly.)


> **Favux said:**
> Don't forget the Citiq's.  Although having support for better than half the serial models is obviously better than no support.

According to the old serial code, the Cintiqs were protocol 4.  Only the Intuos 1 and 2 are protocol 5, according to that code.  I don't know if it's just that that code worked with the Cintiqs in some sort of backwards compatibility mode.

Anyway, I'm going to ask about that on the mailing list.  I'd just like to know how much interest there is in having an Intuos driver and whether I should put together an implementation or if someone actually owning such a device is interested in doing it.

Cheers.

---

### Post by Favux on 2011-07-02
Hi Johannes,

I looked at the code a little and I see the pressure levels set in the model specific section of wcmSerial.c like the usb tablet pressure levels are specified for each model in the usb kernel driver wacom.ko's wacom_wac.c file.  Then in the parse function section I see that the model specific pressure levels are used to help parse the incoming serial data packets.  But I haven't seen anything that would actually manipulate pressure so I don't think the problem is in the serial patches.  Just another reason to try and get the serial patches to build on 0.10.8 I guess.


**Johannes and others interested in testing,**

I have a release candidate for the version 3 patches.  Because these patches are more likely to break things than anything previous I'll attach the 3 changed patches here.  Just replace the corresponding v2 patch with the v3 patch.  But keep the v2 patches!  Then go ahead and compile as usual.  Good luck!

---

### Post by Favux on 2011-07-03
I went over everything and the snippet I posted in #33 should work:
```
Section "InputClass"
    Identifier "Wacom legacy serial class"
    MatchPnPID "PNP0501"
    Driver "wacom"
    Option "ForceDevice" "Serial"
EndSection
```
Try changing "Serial" to "SERIAL" to check if it is case specific in xorg.conf.d.  The line we were using in the wacom.fdi with HAL was:
> <match key="@info.parent: pnp.id" contains_outof="PNP0501;WACf;FUJ02e5;FUJ02e7">
So you can see why I thought MatchProduct might work.  But I found the commit for MatchPnPID and it explains why we need to use it instead:  [http://cgit.freedesktop.org/xorg/xserver/commit/?id=645679c1523eee7028f3244cee57936b93326a2a](http://cgit.freedesktop.org/xorg/xserver/commit/?id=645679c1523eee7028f3244cee57936b93326a2a)

So as long as the command:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
```
has the following section in the output:
>   looking at parent device '/devices/pnp0/00:08':
    KERNELS=="00:08"
    SUBSYSTEMS=="pnp"
    DRIVERS=="serial"
    ATTRS{id}=="PNP0501"
the snippet should work.  As you can see it is the Plug n Play (pnp) subsystem and the Plug n Play ID or ATTRS{id} is "PNP0501".  So if it isn't working check and see if "PNP0501" has disappeared from that section.  It shouldn't do that though, which is what is making me wonder about SERIAL.

---

### Post by alexcrow on 2011-07-04
As far as Natty/Intuos2 goes, I have an Intuos2 serial which I love dearly. I upgraded to Natty assuming it would work as it has done since Lucid for me, but just found out it's broken. So yes, I would be very interested, but sadly I am about as good at kernel development as a dead slug would be at repairing an F1 car.

Looking forward to any other Intuos2 users posting on this though!

Alex

---

### Post by Favux on 2011-07-04
Hi Alex,

Welcome to Ubuntu forums!

[QUOTE=alexcrow]I have an Intuos2 serial which I love dearly. I upgraded to Natty assuming it would work as it has done since Lucid for me, but just found out it's broken.[/QUOTE]
Maybe you could consider installing a small Lucid or Maverick partition and helping out with the updated serial driver patchsets?  We could use an Intuos2/protcol V tablet testing them.  The legacy driver is feature complete and supports protocol V.  Don't know how far we'll get with it but I know we'll get further with help.  If we can get it running on 0.10.8 I think there is only a big variable renaming between 0.10.8 and Natty's 0.10.11.

And then when tokenrove or whoever comes out with a modern protocol V driver for Natty you could help test that.

---

### Post by tokenrove on 2011-07-05
> **alexcrow said:**
> As far as Natty/Intuos2 goes, I have an Intuos2 serial which I love dearly. I upgraded to Natty assuming it would work as it has done since Lucid for me, but just found out it's broken. So yes, I would be very interested, but sadly I am about as good at kernel development as a dead slug would be at repairing an F1 car.

I don't mind giving it a shot, keeping in mind that since I can't test it at all locally, we'd be doing a lot of back and forth with people like you testing incremental, tiny changes.

Let me get any kinks that come up sorted out of the protocol IV driver this week, and then I'll see about doing a protocol V driver.

Thanks Favux for updating the post to link to my driver.  Any feedback from users with protocol IV devices would be appreciated, as I would like to improve it quickly to the point where the current painful situation for serial users can be resolved.

Cheers.

---

### Post by dreh on 2011-07-06
> **tokenrove said:**
> 
Any feedback from users with protocol IV devices would be appreciated, as I would like to improve it quickly to the point where the current painful situation for serial users can be resolved.
Cheers.

Hi Favux, tokenrove,
sry for beeing silent. I shrinked my LVM and miscalculated the GB size - had to reinstall Ubuntu from scratch. I'm gonna test the new serial driver and the v3rc1 patch today.
j.

---

### Post by Favux on 2011-07-06
Hi Johannes,

Welcome back!  Yes, working on partitions always has me biting my fingernails.  :)
> I'm gonna test the new serial driver and the v3rc1 patch today.
Great!  I can't work on the second 0.10.8 commit until I get feedback on rc1v3 since it affects files changed in rc1v3.  And tokenrove will appreciate feedback on his new driver too.

---

### Post by dreh on 2011-07-06
> **tokenrove said:**
> Any feedback from users with protocol IV devices would be appreciated, as I would like to improve it quickly to the point where the current painful situation for serial users can be resolved.
Cheers.

Hello tokenrove,
my compile fails with:
```

bash:>sudo make all
HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function &#8216;conf_askvalue&#8217;:
scripts/kconfig/conf.c:105: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function &#8216;conf_choice&#8217;:
scripts/kconfig/conf.c:307: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-30-server'
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-30-server'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  UPD     include/generated/utsrelease.h
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-30-server'
make: *** [all] Error 2
```
You need more infos? Are there some dependencies missing?

Linux ali 2.6.35-30-server #54-Ubuntu SMP Tue Jun 7 20:13:05 UTC 2011 x86_64 GNU/Linux - Wacom Ud-1218 R Serial Tablet
Johannes

---

### Post by dreh on 2011-07-06
> **Favux said:**
> 
**Johannes and others interested in testing,**

I have a release candidate for the version 3 patches.  Because these patches are more likely to break things than anything previous I'll attach the 3 changed patches here.  Just replace the corresponding v2 patch with the v3 patch.  But keep the v2 patches!  Then go ahead and compile as usual.  Good luck!

Congrats code works!
J.

---

### Post by Favux on 2011-07-06
Wow, that is excellent!  :D

Alright, I'll post the official v3 patch set in a little bit.  Please test that when you get a chance.  I decided I should fix a typo I spotted, shouldn't break anything but...

We've now addressed 20 of the 40 comments, which I feel is pretty good.  I think we'll call v3 the last of the 0.10.7 patch sets, at least for now.  Unless we have to fix something or maybe get a wacom.conf serial snippet working.

On to 0.10.8!

---

### Post by tokenrove on 2011-07-06
> **dreh said:**
> Hello tokenrove,
my compile fails with:
```

bash:>sudo make all

```
You need more infos? Are there some dependencies missing?


Thanks for trying it.  This looks like you are building in the kernel directory.  What you actually want to do is just build the module (run make all, without sudo, in the wacom_serial directory).  You won't need sudo until you insmod the module.

Edit: in fact, it seems that this occurs when PWD isn't defined in the environment.  Could you change the occurances of M=$(PWD) to M=$(shell pwd) in Makefile and try again?


Hope this helps, and let me know how it goes.

---

### Post by dreh on 2011-07-07
Sure your welcome! It failed again. Sorry I can't debug myself my coding skills are so poor. 

> **tokenrove said:**
> Could you change the occurances of M=$(PWD) to M=$(shell pwd) in Makefile and try again?

This is what I did:
1. changed code
2. make clean
3. make all

```
make all
make -C /lib/modules/2.6.35-30-server/build M=/home/johannes/Desktop/wacom/tokenrove/wacom_serial modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-30-server'
  CC [M]  /home/johannes/Desktop/wacom/tokenrove/wacom_serial/wacom_serial.o
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/johannes/Desktop/wacom/tokenrove/wacom_serial/wacom_serial.c:31:
include/linux/mmzone.h:18: fatal error: generated/bounds.h: No such file or directory
compilation terminated.
make[2]: *** [/home/johannes/Desktop/wacom/tokenrove/wacom_serial/wacom_serial.o] Error 1
make[1]: *** [_module_/home/johannes/Desktop/wacom/tokenrove/wacom_serial] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-30-server'
make: *** [all] Error 2
```

What am I missing?
J.

---

### Post by tokenrove on 2011-07-07
> **dreh said:**
> 
What am I missing?


Looks better.  Could you make sure linux-headers-2.6.35-30, linux-headers-2.6.35-30-generic, and build-essential are installed?

Cheers.

---

### Post by dreh on 2011-07-08
> **tokenrove said:**
> Looks better.  Could you make sure linux-headers-2.6.35-30, linux-headers-2.6.35-30-generic, and build-essential are installed?

Cheers.

hello tokenrove,
the packages are already installed unfortunately it still won't compile.
Johannes

---

### Post by tokenrove on 2011-07-09
> **dreh said:**
> 
the packages are already installed unfortunately it still won't compile.


Make sure you are not running it as root, either as root or with "sudo".  I just built in on my wife's Ubuntu machine (with the same kernel), and when run with sudo, I get the same error; when run as a normal user, it gets past the point you indicated.

Unfortunately, I discovered that the code currently depends on a feature of the input API added in a later kernel version.  So I will create a backport for testers on earlier kernel versions.  Quite sorry about that.

If you still have the patience, give this version a shot:
  [http://cipht.net/releases/wacom_serial-for-2.6.35-testing.tar.gz](http://cipht.net/releases/wacom_serial-for-2.6.35-testing.tar.gz)

If the previous errors persist, please let me know what shell you are using.  When I get the chance this weekend, I will try to make sure that everything works with my tablet on my wife's machine.

---

### Post by dreh on 2011-07-09
> **tokenrove said:**
> Make sure you are not running it as root, either as root or with "sudo".  I just built in on my wife's Ubuntu machine (with the same kernel), and when run with sudo, I get the same error; when run as a normal user, it gets past the point you indicated.

Unfortunately, I discovered that the code currently depends on a feature of the input API added in a later kernel version.  So I will create a backport for testers on earlier kernel versions.  Quite sorry about that.

If you still have the patience, give this version a shot:
  [http://cipht.net/releases/wacom_serial-for-2.6.35-testing.tar.gz](http://cipht.net/releases/wacom_serial-for-2.6.35-testing.tar.gz)

If the previous errors persist, please let me know what shell you are using.  When I get the chance this weekend, I will try to make sure that everything works with my tablet on my wife's machine.
Hi tokenrove,
thanks for all the effort you put into this. Unfortuantely an error persists:
```
make all
make -C /lib/modules/2.6.35-30-server/build M=/home/johannes/Downloads/wacom_serial modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-30-server'
  CC [M]  /home/johannes/Downloads/wacom_serial/wacom_serial.o
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /home/johannes/Downloads/wacom_serial/wacom_serial.c:34:
include/linux/mmzone.h:18: fatal error: generated/bounds.h: No such file or directory
compilation terminated.
make[2]: *** [/home/johannes/Downloads/wacom_serial/wacom_serial.o] Error 1
make[1]: *** [_module_/home/johannes/Downloads/wacom_serial] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-30-server'
make: *** [all] Error 2

```
Schönen Gruß
J.
P.S. no root/sudo involved

---

### Post by Gizmoatwork on 2011-07-09
Hi everybody. I'm quite new to linux, but I love it. I'm using Linux Mint 10 (Julia) 64 bits.

Kernel : 2.6.35-22

I'd love my Intuos 2 Serial tablet to work.
As I'm not coder, I don't know how to compile things :oops:

Could you please tell me where to start and what to do ?

---

### Post by Favux on 2011-07-09
Hi Gizmoatwork,

The 2.6.35 kernel makes Julia or Mint 10 the equivalent of Maverick.  If the X server is 1.9 it basically is Maverick.  Run *Xorg -version* in a terminal and check or post the output.

---

### Post by Gizmoatwork on 2011-07-09
So my X Version is 11, and my xorg-server is 1.9.0.

Does it make any sense ?
If it does, what should I do next ?

---

### Post by Favux on 2011-07-09
OK, you basically have Ubuntu 10.10 or Maverick and the instructions in part I. and II. of the HOW TO should work for you.  Read/skim though them a couple of times and they'll start making a little sense.  Just follow them a step at a time and copy & paste the commands into a terminal, rather than typing them in.  Be careful, some of the commands extend past the right edge of the box they are in.  Be sure to get it all.  Ask if you get stuck.

Since you have an Intuos2 it is a protocol V tablet and tokenrove doesn't yet have a driver for it.  So you need to use the old serial driver which is in the patch sets.  Like the HOW TO says we're testing/using version 3 for xf86-input-wacom-0.10.7 right now.

---

### Post by Gizmoatwork on 2011-07-09
Thank you very much for your help.

So.
I run all the commands in section I. Everything went fine.

Then.
I added the lines of section II at the end of my xorg.conf file (after having done a backup).

And then.
I'm stuck !

I tried to reboot, but nothing happens... :(

---

### Post by Favux on 2011-07-09
Sounds like compiling the driver went well.

What exactly happens when you restart?  Hopefully you made the backup to your xorg.conf I instructed you to do.

What video card/chipset do you have?  In other words ATI, Intel, Nvidia?

Was there an xorg.conf already there or when you used the edit command did the file appear blank?

---

### Post by Gizmoatwork on 2011-07-09
> **Favux said:**
> What exactly happens when you restart?  


My desktop starts as usual. If I launch The Gimp, my Wacom doesn't work.

> **Favux said:**
> 
What video card/chipset do you have? 
It's an ATI Radeon 9550.

> **Favux said:**
> 
Was there an xorg.conf already there or when you used the edit command did the file appear blank?

Yes, I already had xorg.conf file. It was not blank.

---

### Post by Favux on 2011-07-09
Whew, I thought you broke X and couldn't start your Desktop!

What is the output of *xinput list* in a terminal?

Could you show me your current xorg.conf in /etc/X11?  Let's see if we need to change some things.  Does your Intuos2 have a Wacom tablet mouse?

---

### Post by Gizmoatwork on 2011-07-09
Here is what xinput list gives me :
```
Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)    id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; STV06xx                                     id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]

```And my xorg.conf :

```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "0-DFP4"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "75"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "fglrx"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP4" "0-DFP4"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"         "/dev/ttyS0"
    Option        "Type"           "stylus"
    Option        "ForceDevice"    "Serial"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"         "/dev/ttyS0"
    Option        "Type"           "eraser"
    Option        "ForceDevice"    "Serial"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"         "/dev/ttyS0"
    Option        "Type"           "cursor"
    Option        "ForceDevice"    "Serial"
EndSection

Section "ServerLayout"
    Identifier    "X.org Configured"
    InputDevice   "stylus"
    InputDevice   "eraser"
    InputDevice   "cursor"
EndSection

```

I don't have a Wacom mouse, just a regular stylus.

---

### Post by Favux on 2011-07-09
Since stylus and eraser aren't showing up in *xinput list* the tablet isn't on the wacom X driver.  That could be because you had two "ServerLayouts" see if this xorg.conf works better.  Remember you can restore your back up xorg.conf from the command line you can get to using the recovery mode option.
```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
    InputDevice   "stylus"
    InputDevice   "eraser"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "0-DFP4"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "75"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "fglrx"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP4" "0-DFP4"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"         "/dev/ttyS0"
    Option        "Type"           "stylus"
    Option        "ForceDevice"    "Serial"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"         "/dev/ttyS0"
    Option        "Type"           "eraser"
    Option        "ForceDevice"    "Serial"
EndSection
```
Basically we've added the stylus and eraser line the "ServerLayout" section your proprietary ATI driver "fglrx" gave you and the stylus and eraser sections.

---

### Post by Gizmoatwork on 2011-07-10
Oh My God !
[SIZE=4][B][COLOR=Red][COLOR=Purple]It works ![/COLOR]
[/COLOR][/B][/SIZE]It's years now that I want my good old serial Intuos2 to work under Linux. You've made it possible.

Thanks :D

There are still a few strange things :

1 - The buttons on my stylus don't work

2 - The tablet is pressure-sensitive and it works, but if I press too hard, it reacts as if I don't press at all. Is there a threshold ?

---

### Post by Favux on 2011-07-10
Outstanding!  You have the first protocol V tablet to report success.  :D

What model is your Intuos2?

[QUOTE=Gizmoatwork]1 - The buttons on my stylus don't work[/QUOTE]
We should be able to fix that.  How many side buttons does the stylus have?
[QUOTE=Gizmoatwork]2 - The tablet is pressure-sensitive and it works, but if I press too hard, it reacts as if I don't press at all. Is there a threshold ? [/QUOTE]
Dreh also reports the same thing.  There is a threshold called ClickForce we can play with.  This may be a bug in the driver, not the serial part we are adding.  That's one of the reasons to try to move up to xf86-input-wacom-0.10.8 like we are trying to do in post #2.  There is another pressure fix in 0.10.8 that may help.

Let's try some diagnostics.  Please post the output in a terminal of:
```
xinput list
```
I'm assuming there will be a "stylus" and "eraser" line.  If so also run:
```
xinput list-props "stylus"
```
and post that output.

---

### Post by Gizmoatwork on 2011-07-10
Well, I'm very happy to report success !

My model is GD-0608-R

My stylus has 2 clickable zones, but on the same button. Check this image, it'll make more sense :

[IMG]http://i16.media.anitec.ca/10063486.jpg[/IMG]

```
xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; stylus                                      id=6    [slave  pointer  (2)]
&#9116;   &#8627; eraser                                      id=7    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)    id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; STV06xx                                     id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

``````
xinput list-props "stylus"
Device 'stylus':
    Device Enabled (142):    1
    Coordinate Transformation Matrix (144):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (259):    0
    Device Accel Constant Deceleration (260):    1.000000
    Device Accel Adaptive Deceleration (261):    1.000000
    Device Accel Velocity Scaling (262):    10.000000
    Wacom Tablet Area (269):    0, 0, 20320, 16240
    Wacom Rotation (270):    0
    Wacom Pressurecurve (271):    0, 0, 100, 100
    Wacom Serial IDs (272):    32, 0, 2, 0
    Wacom TwinView Resolution (273):    0, 0, 0, 0
    Wacom Display Options (274):    -1, 0, 1
    Wacom Screen Area (275):    0, 0, 1280, 1024
    Wacom Proximity Threshold (276):    0
    Wacom Capacity (277):    -1
    Wacom Pressure Threshold (278):    27
    Wacom Sample and Suppress (279):    2, 4
    Wacom Enable Touch (280):    0
    Wacom Hover Click (281):    0
    Wacom Enable Touch Gesture (282):    0
    Wacom Touch Gesture Parameters (283):    50, 20, 250
    Wacom Tool Type (284):    "STYLUS" (258)
    Wacom Button Actions (285):    "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)

```

---

### Post by Favux on 2011-07-10
Alright, so far nothing is jumping out at me.

OK, two side buttons on a rocker switch.  Try entering these xsetwacom set commands in a terminal and see if the buttons work:
```
xsetwacom set "stylus" Button2 "3"
xsetwacom set "stylus" Button3 "2"
```

For more diagnostics let us see if the Xorg.0.log is complaining about something.  It is located in /var/log.  Since it is big you'll want to compress it by right clicking on it and using Create Archive.  Then attach it to your next post with Manage Attachments below.

Also it would be helpful to have the output of:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
```
Thanks!

---

### Post by Gizmoatwork on 2011-07-10
```
xsetwacom set "stylus" Button2 "3"
xsetwacom set "stylus" Button3 "2"
```No success. Nothing has changed.

```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)

looking at device '/devices/pnp0/00:08/tty/ttyS0':
    KERNEL=="ttyS0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pnp0/00:08':
    KERNELS=="00:08"
    SUBSYSTEMS=="pnp"
    DRIVERS=="serial"
    ATTRS{id}=="PNP0501"

  looking at parent device '/devices/pnp0':
    KERNELS=="pnp0"
    SUBSYSTEMS==""
    DRIVERS==""


```

---

### Post by Favux on 2011-07-10
If your running the two xsetwacom commands on one line don't.  Each should be run as a separate line.  Let me look at the Xorg.0.log.

Also try running:
```
xsetwacom get "stylus" all
```
and posting that output.


Wow!  That's the first serial tablet Xorg.0.log I've seen in a long time.  And the first one I've seen from xf86-input-wacom.  So I'm going to post the relevant Wacom stuff.  Thanks Gizmoatwork!
```

[    24.704] (II) LoadModule: "wacom"
[    24.757] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    24.771] (II) Module wacom: vendor="X.Org Foundation"
[    24.771] 	compiled for 1.9.0, module version = 0.10.7
[    24.771] 	Module class: X.Org XInput Driver
[    24.771] 	ABI class: X.Org XInput driver, version 11.0
.....
[    25.289] (**) Option "Device" "/dev/ttyS0"
[    25.290] (**) stylus: always reports core events
[    25.290] (II) XINPUT: Adding extended input device "stylus" (type: STYLUS)
[    25.290] (**) Option "StopBits" "1"
[    25.290] (**) Option "DataBits" "8"
[    25.290] (**) Option "Parity" "None"
[    25.290] (**) Option "Vmin" "1"
[    25.290] (**) Option "Vtime" "10"
[    25.290] (**) Option "FlowControl" "Xoff"
[    25.290] (**) stylus: forcing legacy tablet protocol
[    25.291] , 0x24, 0x23, 0x24, 0x23, 0x24, 0x53, 0x50, 0xd, 0x23, 0xd(==) Wacom tablet model : GD-0608-R00,V1.2-7
[    27.271] , 0x43, 0xd(--) stylus: using pressure threshold of 27 for button 1
[    28.302] (--) stylus: Wacom Serial Intuos tablet speed=38400 maxX=20320 maxY=16240 maxZ=1023 resX=2540 resY=2540  tilt=enabled
[    28.302] , 0x54, 0xd, 0x54, 0x31, 0xd, 0x49, 0x44, 0x31, 0xd, 0x49, 0x54, 0x30, 0xd, 0x53, 0x54, 0xd(--) stylus: top X=0 top Y=0 bottom X=20320 bottom Y=16240 resol X=2540 resol Y=2540
[    28.303] (**) Option "Device" "/dev/ttyS0"
[    28.303] (**) eraser: always reports core events
[    28.303] (II) XINPUT: Adding extended input device "eraser" (type: ERASER)
[    28.303] , 0x54, 0x31, 0xd, 0x49, 0x44, 0x31, 0xd, 0x49, 0x54, 0x30, 0xd, 0x53, 0x54, 0xd(--) eraser: top X=0 top Y=0 bottom X=20320 bottom Y=16240 resol X=2540 resol Y=2540

```
So the Xorg.0.log looks clean and without complaints.

---

### Post by Gizmoatwork on 2011-07-10
Yes, I typed the xsetwacom on 2 separate lines.

```
xsetwacom get "stylus" all
```
It replies with :

```
1
1
1
1
1
```And so on for many lines.

---

### Post by Favux on 2011-07-10
Interesting.  So what are we to make of that?  That the new xsetwacom re-written for xf86-input-wacom doesn't work with the serial tablet stuff or is it just the button stuff?

Let's check that by trying the button commands as options in the xorg.conf instead.  Remember to back up your current working xorg.conf.  Since this version has the wacom stuff maybe change the extension name to say *.bak2*?

Try adding these two side button options in the stylus section:
```
Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"         "/dev/ttyS0"
    Option        "Type"           "stylus"
    Option        "ForceDevice"    "Serial"
    Option        "Button2"        "3"
    Option        "Button3"        "2"
EndSection
```
Then reboot of course.

---

### Post by Gizmoatwork on 2011-07-10
Just did what you've proposed.
No luck.  :(
No change.

---

### Post by Favux on 2011-07-10
Shoot.  :(

Before we get too far into this is there a chance your **rocker switch is broken**?  In other words do the side buttons work elsewhere, say in Windows?

I might have broken the stylus buttons with some of the changes I've made.  Let's hope so because then we should be able to fix them.  Most likely going from the 0.10.7 version 2 to version 3 patch set would be my guess.  So you would have to compile with the v2 patch set and install and see if the side switch buttons now work.

But we would probably want to confirm that the stylus buttons worked with either version 2 (the original patch set) or version 3 of the xf86-input-wacom-0.10.6 patches.  Because they may have been broken all along, at least for protocol V serial tablets like the Intuos2.

That's probably what you should check into next if you have the time and are willing to compile the driver again.  The instructions for 0.10.6 are in appendix 1.  So maybe start with v2 or v3 of 0.10.6 and if one of them works try v2 of the 0.10.7 patch set.

---

### Post by Gizmoatwork on 2011-07-10
[FONT=Verdana][SIZE=4][COLOR=Purple]**YES !**[/COLOR][/SIZE][/FONT]

So, as you suggested, I compiled xf86-input-wacom-0.10.6 with [v2] patches.
And now, I have the pressure which works great. :)

And : One of the 2 rocker buttons which works too. :) :)

So the only remaining bit is the 2nd rocker button which doesn't work. But to be honest, it's not a big issue, because I don't use it much while drawing.

Let me know if you want me to test something.

---

### Post by Favux on 2011-07-10
Excellent!  Nice work!  :D  Thank you.

I would very much like you to move up the chain to help me find where it gets broken.  That will help tell me if I broke it.  If I did it I can probably fix it.

I'm assuming v3 for 0.10.6 will work since v2 does.  My guess is so will v1 of the 0.10.7 patch set.  If it breaks, both stylus side button and pressure, then that would likely mean the problem is with xf86-input-0.10.7.  I'm hoping v2 will also work and I broke the side button with v3.   That's assuming the pressure problem was introduced by xf86-input-0.10.7 and not the serial patch set for it, which v1 will tell us.

---

### Post by roaldfre on 2011-07-11
Hi guys!

I ordered an old Intuos1 tablet form eBay that arrived today. I thought it was a USB tablet, but it turned out to be serial >_<.

I have a (tiny) bit of experience in writing linux kernel drivers. I would like to implement protocol V for those Intuos 1 and 2 tablets based on the wacom_serial driver from tokenrove.

Does anybody have any pointers to the protocol specs for those tablets?

---

### Post by roaldfre on 2011-07-11
Ok, I managed to get mouse movement that correlated somehow to where I put the pen on the tablet. Did not change anything to the parsing of the protocol yet (still haven't found decent specs for it).

[Edit]
Implemented a part of protocol V by copying from old wcmSerial code. Mouse movement and pressure work :-). Still lots of debug messages, slowing things down somewhat.
Code at [https://github.com/RoaldFre/wacom_serial5]("https://github.com/RoaldFre/wacom_serial")

---

### Post by tokenrove on 2011-07-11
> **dreh said:**
> Hi tokenrove,
thanks for all the effort you put into this. Unfortuantely an error persists:


Very curious.  Could you send me the output of the following commands:

```

ls -l /lib/modules/2.6.35-30*/build
find /lib/modules/2.6.35-30*/build/include -name bounds.h
dpkg -l | grep linux-headers

```

Sorry it's taken so long to sort this out!

Cheers.

---

### Post by tokenrove on 2011-07-11
> **roaldfre said:**
> Ok, I managed to get mouse movement that correlated somehow to where I put the pen on the tablet. Did not change anything to the parsing of the protocol yet (still haven't found decent specs for it).

[Edit]
Implemented a part of protocol V by copying from old wcmSerial code. Mouse movement and pressure work :-). Still lots of debug messages, slowing things down somewhat.
Code at [https://github.com/RoaldFre/wacom_serial](https://github.com/RoaldFre/wacom_serial)

Awesome.  The various versions of the linuxwacom serial driver are really the only reference I've found for the protocols.  I'm going to write up a description of them on the linuxwacom.sf.net wiki sometime this week when I get another chance to work on it, but I'm thrilled that I don't have to write the Intuos driver blind.

Good luck.

---

### Post by roaldfre on 2011-07-11
I implemented switching the device ID from stylus to eraser to mouse. However, the GIMP doesn't seem to pick this up.

Is there any dumping utility to dump the data/state that the wacom driver sends to X? I've tried wacdump from the linuxwacom module, but that only seems to work with its own kernel module, I think.

Or, less generally: Any way of confirming that the devices get switched correctly (eg, the correct setting in GIMP, or another tool to show this)

---

### Post by Favux on 2011-07-11
Hi roaldfre,

Welcome to Ubuntuforums!

Thanks for tackling the protocol V's!

Wacdump isn't supported by xf86-input-wacom.  You use evtest instead:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:DeveloperPages](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:DeveloperPages)

---

### Post by dreh on 2011-07-11
Hello Tokenrove
> **tokenrove said:**
> Very curious.  Could you send me the output of the following commands:

```
**ls -l /lib/modules/2.6.35-30*/build**
lrwxrwxrwx 1 root root 40 2011-07-05 14:47 /lib/modules/2.6.35-30-generic/build -> /usr/src/linux-headers-2.6.35-30-generic
lrwxrwxrwx 1 root root 39 2011-07-05 16:00 /lib/modules/2.6.35-30-server/build -> /usr/src/linux-headers-2.6.35-30-server
```
```
**find /lib/modules/2.6.35-30*/build/include -name bounds.h**
/lib/modules/2.6.35-30-generic/build/include/generated/bounds.h
```
```

[B]dpkg -l | grep linux-headers
[/B]ii  linux-headers-2.6.35-22                   2.6.35-22.35                                      Header files related to Linux kernel version 2.6.35
ii  linux-headers-2.6.35-22-server            2.6.35-22.35                                      Linux kernel headers for version 2.6.35 on x86_64
ii  linux-headers-2.6.35-30                   2.6.35-30.54                                      Header files related to Linux kernel version 2.6.35
ii  linux-headers-2.6.35-30-generic           2.6.35-30.54                                      Linux kernel headers for version 2.6.35 on x86/x86_64
ii  linux-headers-2.6.35-30-server            2.6.35-30.54                                      Linux kernel headers for version 2.6.35 on x86_64
ii  linux-headers-generic                     2.6.35.30.38                                      Generic Linux kernel headers
ii  linux-headers-server                      2.6.35.30.38                                      Linux kernel headers on Server Equipment.

```
Hope this helps :D
J.

---

### Post by roaldfre on 2011-07-11
Ok, got device switching to work. Added tilt as well.
Still very much WIP. Progress can be tracked here: [http://github.com/RoaldFre/wacom_serial5/commits/]("http://github.com/RoaldFre/wacom_serial/commits/")

---

### Post by brentn on 2011-07-11
Is it possible to compile this on Natty??  I actually have Linux Mint LXDE version 11 (equivalent of Natty), and am having trouble with the make command.

Can I downgrade something to make this compile, or should I install version 10 (equivalent of Maverick) to get this to work

---

### Post by tokenrove on 2011-07-11
Ahoy,

> **dreh said:**
> Hope this helps :D

It does... but I remain confused.  Try this command:

```

dpkg -L linux-headers-2.6.35-30-server | grep bounds.h

```

It should print:

```

/usr/src/linux-headers-2.6.35-30-server/include/generated/bounds.h

```

but I imagine it doesn't, or if it does, then an "ls" of that file should show no such file or directory.  I think there is something wrong with the installation of your kernel headers.

Perhaps you could remove and reinstall the linux-headers-2.6.35-30-server package?  Do you have any idea how this could have become corrupted?  (Unless there's something I'm missing -- very possible -- but this package contains the file in question on the machine I am checking on my side.)

I can't even find a file list of this specific version of the package online, but the earlier version (*-22) contains the file in question.

Hopefully one step closer.  Cheers.

---

### Post by Favux on 2011-07-12
Hi brentn,

It should just compile after you change directory into the unpacked serial_wacom folder and enter *make all*.  What is the problem you are having with make all?  What are the error messages?

You shouldn't need to downgrade your release.

---

### Post by roaldfre on 2011-07-12
> **brentn said:**
> Is it possible to compile this on Natty??  I actually have Linux Mint LXDE version 11 (equivalent of Natty), and am having trouble with the make command.

Can I downgrade something to make this compile, or should I install version 10 (equivalent of Maverick) to get this to work

If you follow tokenrove's guide, you should be able to make it compile. Make sure you have all the necessary headers.

Note that my verion only supports protocol V as of now (and only tested on an Intuos1), for protocol IV you need tokenrove's version.

For what it's worth, I'm running Gentoo on a 2.6.39.2 kernel (also worked with a 2.6.37 iirc), xorg-server 1.10.2, xf86-input-wacom 0.11.0.

@tokenrove: what do you think would be more appropriate? Supporting both protocols in the same driver, or separate drivers? I'm leaning towards the first option, as pretty much the only thing that needs to be changed is the packet parser. It may get more messy if I try to implement protocolV-specific things, though (eg, there are two channels, apparently, etc)

---

### Post by dreh on 2011-07-12
Hello tokenrove
> **tokenrove said:**
> Ahoy,
Perhaps you could remove and reinstall the linux-headers-2.6.35-30-server package?
That did the trick. What I did next:
downloaded Joystick sources and tried to patch inputattach. It failed. Maverick doesnt come with joystick-1.4.1 it comes with joystick-20051019 and the patch didn't work automagically. So I softlinked it and it now fails on some parts. I patched the few lines by hand adding: 

```
{ "--w8001",           "-w8001",       "Wacom W8001",
        B38400, CS8,
        SERIO_W8001,            0x00,   0x00,   0,      NULL },
{ "--wacom_iv",                "-wacom_iv",    "Wacom protocol 4 tablet",
       B9600, CS8,
       SERIO_WACOM_IV,         0x00,   0x00,   0,      NULL },

```
(Hopefully I didn't make a mistake).
I went on with the guide on your site. I commented my xorg.conf setup and rebooted.

I loaded the ko file and inputattach gives me a non functioning tablet although messages say everything is ok.
```
**xinput list**
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Digital Media Pro Keyboard	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Laser Mouse                	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 4 serial tablet eraser   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 4 serial tablet cursor   	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 4 serial tablet stylus   	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft® Digital Media Pro Keyboard	id=8	[slave  keyboard (3)]
```
```
[B]less /var/log/kern.log
[/B]Jul 12 11:04:48 ali kernel: [  633.004960] serio: Serial port ttyS0
Jul 12 11:04:48 ali kernel: [  633.044124] input (null): Wacom tablet: Digitizer II, version 1.4
Jul 12 11:04:48 ali kernel: [  633.044128] input (null): Max pressure: 255.
Jul 12 11:04:48 ali kernel: [  633.084018] input (null): Configuration string: ~RE233C920,000,00,1270,1270
Jul 12 11:04:48 ali kernel: [  633.114025] input: Wacom protocol 4 serial tablet as /devices/serio2/input/input5
```
```
**less /var/log/messages**
Jul 12 11:04:48 ali kernel: [  633.004960] serio: Serial port ttyS0
Jul 12 11:04:48 ali kernel: [  633.044124] input (null): Wacom tablet: Digitizer II, version 1.4
Jul 12 11:04:48 ali kernel: [  633.114025] input: Wacom protocol 4 serial tablet as /devices/serio2/input/input5

```
step by step :D

---

### Post by tokenrove on 2011-07-12
> **dreh said:**
> 
I loaded the ko file and inputattach gives me a non functioning tablet although messages say everything is ok.


Awesome, that's great.  Now, let's get it working.  What version of xserver-xorg-wacom-input is installed?  I noticed when I tested it on my linux/ppc machine that an older version of the X driver recognized the device but didn't actually receive any events from it.  As soon as I updated the X-side wacom input driver, it worked.  The version I've tested with successfully here (on Debian) is  0.10.10+20110203-1+b1.  If you could also include in your message the lines from /var/log/Xorg.0.log that appear after you run inputattach, that would be helpful, too.  It should say a bunch of stuff like:

```


[146373.335] (**) Wacom protocol 4 serial tablet: Applying InputClass "Wacom class"
[146373.358] (II) LoadModule: "wacom"
[146373.516] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[146373.785] (II) Module wacom: vendor="X.Org Foundation"
[146373.785]    compiled for 1.10.2, module version = 0.11.99
[146373.785]    Module class: X.Org XInput Driver
[146373.785]    ABI class: X.Org XInput driver, version 12.2
[146373.785] (II) Using input driver 'wacom' for 'Wacom protocol 4 serial tablet'
[146373.785] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[146373.786] (**) Wacom protocol 4 serial tablet: always reports core events
[146373.786] (**) Option "Device" "/dev/input/event12"
[146373.817] (II) Wacom protocol 4 serial tablet: type not specified, assuming 'stylus'.
[146373.817] (II) Wacom protocol 4 serial tablet: other types will be automatically added.
[146373.817] (--) Wacom protocol 4 serial tablet stylus: using pressure threshold of 27 for 
button 1
[146373.817] (--) Wacom protocol 4 serial tablet stylus: Wacom Unknown USB tablet maxX=10240
 maxY=7680 maxZ=255 resX=1270000 resY=1270000  tilt=enabled

```

Cheers.

---

### Post by tokenrove on 2011-07-12
> **roaldfre said:**
> @tokenrove: what do you think would be more appropriate? Supporting both protocols in the same driver, or separate drivers? I'm leaning towards the first option, as pretty much the only thing that needs to be changed is the packet parser. It may get more messy if I try to implement protocolV-specific things, though (eg, there are two channels, apparently, etc)

My suspicion is that it is only going to get messier as you support multiple channels.  Let's not make the same mistakes as the old driver, which clearly evolved piece by piece.  Of course, maybe you'll figure out some really elegant way of supporting it all in the same driver; I am eager to be proven wrong.

I'll try to write up what I know about Protocol 4 on the linuxwacom wiki.  Maybe you can do the same for protocol 5?

Keep in mind that my plan for the driver I wrote is to actually remove the untested parts if no one comes forward to try them out.  I'd rather a simple and clear driver that is well-tested than something that's going to be a maintenance nightmare because I tried to shoehorn in everything from the old code.

Cheers.

---

### Post by roaldfre on 2011-07-12
Very good points!

I'm going to remove all protocol 4 related code from my version of your driver and clean things up.
At the moment it's still in a rather untidy "hack" state, but it should suffice already to give people preliminary functionality of their protocol 5 wacom tablets (all features of my intuos1 work now: stylus/eraser movement, pressure and tilt; mouse movement and buttons).

Now, if I am not mistaken, the only tablets with protocol 5 are the Intuos and the Intuos2, correct? So that means I'll drop all support for other tablets. I'd also need someone with an Intuos2 to test that part of the code.

It is indeed more tidy to keep them separated, and the overlapping pieces of code are not *that* unwieldy to keep in-sync between our versions, I guess. (I do have some experience with projects that have different branches that heavily rely on the same code. They all started diverging too much in that shared code and it now is an incredible mess to get them back together at the same level -- that's what I *really* want to avoid with this driver.)

---

### Post by Favux on 2011-07-12
Hi tokenrove and roaldfre,

Since the wacom_serial.ko is going to be split into a protocol IV and V version, have you thought up the new names yet?  Say something on the order of?:

wacom_serial4.ko

wacom_serial5.ko

---

### Post by roaldfre on 2011-07-12
Yup, I have already changed the name of my part of the driver to wacom_serial5. Will rename the actual module as well (forgot).

---

### Post by dreh on 2011-07-12
> **tokenrove said:**
>  If you could also include in your message the lines from /var/log/Xorg.0.log that appear after you run inputattach, that would be helpful, too.  It should say a bunch of stuff like:

Xorg.0.log gives this while I inputattach
```
[ 19480.964] (II) config/udev: Adding input device Wacom protocol 4 serial tablet (/dev/input/mouse1)
[ 19480.964] (II) No input driver/identifier specified (ignoring)
[ 19480.964] (II) config/udev: Adding input device Wacom protocol 4 serial tablet (/dev/input/event5)
[ 19480.964] (**) Wacom protocol 4 serial tablet: Applying InputClass "evdev tablet catchall"
[ 19480.964] (**) Wacom protocol 4 serial tablet: Applying InputClass "Wacom class"
[ 19480.964] (II) LoadModule: "wacom"
[ 19480.964] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[ 19480.965] (II) Module wacom: vendor="X.Org Foundation"
[ 19480.965]    compiled for 1.9.0, module version = 0.10.7
[ 19480.965]    Module class: X.Org XInput Driver
[ 19480.965]    ABI class: X.Org XInput driver, version 11.0
[ 19480.965] (**) Option "Device" "/dev/input/event5"
[ 19481.040] (II) Wacom protocol 4 serial tablet: type not specified, assuming 'stylus'.
[ 19481.040] (II) Wacom protocol 4 serial tablet: other types will be automatically added.
[ 19481.040] (**) Wacom protocol 4 serial tablet stylus: always reports core events
[ 19481.040] (II) Wacom protocol 4 serial tablet stylus: hotplugging dependent devices.
[ 19481.040] (**) Wacom protocol 4 serial tablet eraser: Applying InputClass "evdev tablet catchall"
[ 19481.040] (**) Wacom protocol 4 serial tablet eraser: Applying InputClass "Wacom class"
[ 19481.040] (**) Option "Device" "/dev/input/event5"
[ 19481.120] (**) Wacom protocol 4 serial tablet eraser: always reports core events
[ 19481.190] (II) XINPUT: Adding extended input device "Wacom protocol 4 serial tablet eraser" (type: ERASER)
[ 19481.382] (--) Wacom protocol 4 serial tablet eraser: using pressure threshold of 27 for button 1
[ 19481.382] (--) Wacom protocol 4 serial tablet eraser: Wacom Unknown USB tablet speed=38400 maxX=22860 maxY=15240 maxZ=255 resX=1016 resY=1016  tilt=enabled
[ 19481.383] (--) Wacom protocol 4 serial tablet eraser: top X=0 top Y=0 bottom X=22860 bottom Y=15240 resol X=1016 resol Y=1016
[ 19481.383] (**) Wacom protocol 4 serial tablet cursor: Applying InputClass "evdev tablet catchall"
[ 19481.383] (**) Wacom protocol 4 serial tablet cursor: Applying InputClass "Wacom class"
[ 19481.383] (**) Option "Device" "/dev/input/event5"
[ 19481.422] (**) Wacom protocol 4 serial tablet cursor: always reports core events
[ 19481.462] (II) XINPUT: Adding extended input device "Wacom protocol 4 serial tablet cursor" (type: CURSOR)
[ 19481.462] (--) Wacom protocol 4 serial tablet cursor: top X=0 top Y=0 bottom X=22860 bottom Y=15240 resol X=1016 resol Y=1016
[ 19481.463] (II) Wacom protocol 4 serial tablet stylus: hotplugging completed.
[ 19481.582] (II) XINPUT: Adding extended input device "Wacom protocol 4 serial tablet stylus" (type: STYLUS)
[ 19481.582] (--) Wacom protocol 4 serial tablet stylus: top X=0 top Y=0 bottom X=22860 bottom Y=15240 resol X=1016 resol Y=1016
```

Xserver Version X.Org X Server 1.9.0. This looks very promising to me. but still no reaction when using the pen
J.

---

### Post by Favux on 2011-07-12
Hi Johannes,

You still have version 0.10.7 from using the patch sets.  Try installing the xf86-input-wacom-0.11.1 tar.  See the instructions in part II. b) of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by bobfunk67 on 2011-07-12
Hello Favux. Recently I found this forum about configuring wacom serial tablets. At this time I have my old Wacom UD-1212 serial tablet in the wardrobe, and use in my photographic studio an intuos3 A4 usb and a bamboo usb, but I prefer to try using the bigger UD-1212 than the smaller Bamboo.
As I am not a coder (I'm photographer) and there are more than 10 pages of information in this thread, where are exactly the steps to try work on ubuntu 10.10 with this tablet ?
   Thanks, Roberto

---

### Post by dreh on 2011-07-12
> **Favux said:**
> Hi Johannes,

You still have version 0.10.7 from using the patch sets.  Try installing the xf86-input-wacom-0.11.1 tar.  See the instructions in part II. b) of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

This did the trick! Tokenroves driver works with my tablet. One nit the eraser doesn't work as expected but maybe I have to get familiar with the _new_ xsetwacom parameters.

Please help me to understand this driver will be possible to use in natty/oneiric with unity? Where could we be in some time - the 2 new serial wacom files will go upstream?

The next days I'm quite busy again but I can maybe find some time in between for testing Favux patches again to see where things broke with the ClickForce/Threshold bug and I can test 10.8 if this is still of interest.
Johannes

---

### Post by Favux on 2011-07-12
Hi Roberto,

Welcome to Ubuntu forums!

There are now two basic ways to go.  You can either use the old serial driver updated for xf86-input-wacom, which is what the HOW TO is about i.e. it shows you how to install the patch sets to add the old driver to xf86-input-wacom.  So you use appendix 1 or part I, depending on whether you want a 0.10.6 or a 0.10.7 patch set along with the xorg.conf in part II.

However we now have new serial driver, which in the case of your UD-1212 is tokenrove's new wacom_serial.ko which is for the protocol IV tablets.  Instructions are linked up near the top of the HOW TO.  We don't quite have instructions written up on how to do that in Maverick yet.  But that's what Johannes a.k.a. dreh just finished doing over the last couple of pages.

The two new drivers will be submitted upstream to the Linux Wacom Project for inclusion.  Peter Hutterer has already given tentative approval for the way takenrove and roaldfre are doing things.  So with luck they may even be available for Oneiric.


Hi Johannes,

Great!  Definitely talk about the eraser with tokenrove in more detail.  That's the kind of thing he wants feedback on.

And sure, when your not testing for tokenrove we could also work on the patch set.  That won't hurt anything and will be fun besides.  So I'd like that.  :)

In addition to the pressure problem which Gizmoatwork is also seeing in the 0.10.7 patches are you seeing the loss of the stylus side buttons like he reports?

---

### Post by Gizmoatwork on 2011-07-12
> **Favux said:**
> Excellent!  Nice work!  :D  Thank you.

I would very much like you to move up the chain to help me find where it gets broken.  That will help tell me if I broke it.  If I did it I can probably fix it.

I'm assuming v3 for 0.10.6 will work since v2 does.  My guess is so will v1 of the 0.10.7 patch set.  If it breaks, both stylus side button and pressure, then that would likely mean the problem is with xf86-input-0.10.7.  I'm hoping v2 will also work and I broke the side button with v3.   That's assuming the pressure problem was introduced by xf86-input-0.10.7 and not the serial patch set for it, which v1 will tell us.

Ok, so 0.10.6 with [v3] patches works similar than [v2] patches (pressure OK, one fonctionnal side button.
The problem seems to come from 0.10.7 which I tested with [v1] patches (pressure broken, no side button working).

Let me know If I can be of any further help.

---

### Post by Favux on 2011-07-12
Super, thanks Gizmoatwork!  That's the information I was waiting for.  :)

So I think we're almost ready to call v3 the "official" 0.10.6 patch set and take down the original or v2 patch set.


OK, I really didn't change anything for 0.10.7 v1 other than break the second giant 0.10.6 patch into 6 patches.

That means there are two issues starting with 0.10.7:
1) Pressure is wonky.
2) Stylus side buttons don't work.

Now we need to figure out if the pressure problem is a general 0.10.7 bug or something to do with the patch.  Ironically one of the reasons to go to 0.10.7 is it had a pressure bug fix.  But pressure works better with the buggy xf86-input-wacom-0.10.6!  Interesting to note 0.10.8 also has a bug fix for pressure.

The stylus side buttons seem more likely a problem with not updating something in the patch set.  I'll try to go back through the 0.10.6+ commits and see if I can figure out what I missed.  Hopefully it's something simple like a variable renaming.


Edit:  Hmmm.  Cripes.  Is it the "Change WacomModel->name check to WacomModel->tablet_type" commit that's breaking things?:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=cda653b2690f5ed99ca48fcaf33c24539b5529e3](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=cda653b2690f5ed99ca48fcaf33c24539b5529e3)  I sure hope not because that looks like a bear.

---

### Post by tokenrove on 2011-07-12
> **roaldfre said:**
> It is indeed more tidy to keep them separated, and the overlapping pieces of code are not *that* unwieldy to keep in-sync between our versions, I guess. (I do have some experience with projects that have different branches that heavily rely on the same code. They all started diverging too much in that shared code and it now is an incredible mess to get them back together at the same level -- that's what I *really* want to avoid with this driver.)

I think the common code is unlikely to change much.  In fact, your driver should end up cleaner than mine since so much of the model switching can be eliminated, and much of the configuration requesting.  Are you running inputattach at a faster baud rate than 9600?  AFAICT from the old code, the Intuos should be able to go at 19200, at least.  (BTW, that's one thing to sort out -- I still need to add the proper reset sequence to inputattach, which I suspect will help Penpartner support on the protocol IV side)

Renaming the modules is a good idea.  My plan was to do some revisions to mine after I got a few people testing things, and then once things are stabilized, aim to get it into the mainline kernel.  On that note, you should keep an eye on the linuxwacom-devel mailing list if you don't already; some of the messages there when I announced my driver prefigure some changes I need to make to how I'm sending events.  I unfortunately haven't had a lot of time to work on it -- but on the plus side, I've been using my own tablet every day with no problems.

Cheers.

---

### Post by tokenrove on 2011-07-12
> **dreh said:**
> This did the trick! Tokenroves driver works with my tablet. One nit the eraser doesn't work as expected but maybe I have to get familiar with the _new_ xsetwacom parameters.

Please help me to understand this driver will be possible to use in natty/oneiric with unity? Where could we be in some time - the 2 new serial wacom files will go upstream?

Great, I'm very glad to hear it's working, at least in the most basic form.  Any discrepencies you discover, just describe them to me as best as possible and I will try to track them down.  The eraser has worked well for me, but I only use it a little.  Unfortunately, I know almost nothing about xsetwacom, too.

By the way, do you know if your tablet is supposed to have tilt support?  I know how to implement it, I just haven't bothered as I don't think my own tablet handles it.  (Then again, the old driver appears to have had tilt-in-protocol-IV support cut out many years ago, so I wouldn't have known.)

I don't know about release schedules of various things, but my own plan is to give a generous period for testing to shake out any problems with the driver, then attempt to get it into the kernel upstream (and likewise the patch for inputattach).

Cheers.

---

### Post by Favux on 2011-07-12
Hi tokenrove,

In case you missed it inputattach is now in Linux Console as of April this year:  [http://sourceforge.net/projects/linuxconsole/](http://sourceforge.net/projects/linuxconsole/)

---

### Post by dreh on 2011-07-13
Hello tokenrove, hello favux and everyone else,
I'm excited the serial wacom issue has so much activity. Thanks for all the work and information you provide. I'm overall impressed of community based-"engineering" and open source.

Now to work:
> **tokenrove said:**
> Any discrepencies you discover, just describe them to me as best as possible and I will try to track them down.
First. I initialize my tablet with the command sudo inputattach --wacom_iv /dev/ttyS0 - this command stays running or in other words the shell hangs (sending the command to background with "&" don't function). If I Ctrl-C or mouseklick-close the shell my tablet stops working. Is this behavior intended? 
Second. the eraser won't work as a mousepointer (before it did). There's is no reaction to it other than in Gimp where the eraser is when in range of the tablet "unfocus" the paint tool. When you paint with i.e. brush you have a dotted circle (with cirlce tooltip) this vanishes if you get the eraser in range but still you can't "paint the erase color" or "mouse" over your screen.

> **tokenrove said:**
> 
By the way, do you know if your tablet is supposed to have tilt support?  I know how to implement it, I just haven't bothered as 
Sry I can't provide any infos on this one - I had never tilt support (or not enabled).

Also sorry for my holperiges (bumpy) english. 
Johannes

---

### Post by roaldfre on 2011-07-13
> **tokenrove said:**
> I think the common code is unlikely to change much.  In fact, your driver should end up cleaner than mine since so much of the model switching can be eliminated, and much of the configuration requesting.  Are you running inputattach at a faster baud rate than 9600?  AFAICT from the old code, the Intuos should be able to go at 19200, at least.  (BTW, that's one thing to sort out -- I still need to add the proper reset sequence to inputattach, which I suspect will help Penpartner support on the protocol IV side)

Renaming the modules is a good idea.  My plan was to do some revisions to mine after I got a few people testing things, and then once things are stabilized, aim to get it into the mainline kernel.  On that note, you should keep an eye on the linuxwacom-devel mailing list if you don't already; some of the messages there when I announced my driver prefigure some changes I need to make to how I'm sending events.  I unfortunately haven't had a lot of time to work on it -- but on the plus side, I've been using my own tablet every day with no problems.

Cheers.

Hmm, I'll try running it at 19200 baud now. I'll also have a look at the mailing list.

My code can indeed be simplified considerably, as it seems I only need to support Intuos 1 and 2 (I found something about a serial Cintiq tablet being protocol 5 too? Only found a reference to it here: [http://www.mail-archive.com/linuxwacom-devel@lists.sourceforge.net/msg03166.html](http://www.mail-archive.com/linuxwacom-devel@lists.sourceforge.net/msg03166.html) - can anyone confirm that this needs to be included in my driver? I can't seem to find it in the old code that deals with protocol 5)

Regarding inputattach, are you planning to keep this as a dependency, or do you eventually want to move the initialization to the driver itself (could get messy again)? [Edit: nvm, should have read mailing list first ;-)]

---

### Post by roaldfre on 2011-07-13
19200 baud working now for protocol 5 (as of [http://github.com/RoaldFre/wacom_serial5/commit/0a397cf505510bdbbc75ff26eedbde311be31d61](http://github.com/RoaldFre/wacom_serial5/commit/0a397cf505510bdbbc75ff26eedbde311be31d61)). Had to put some extra initialization code in inputattach.

I also renamed my repository from wacom_serial to wacom_serial5. New link for those who want to try it out: [http://github.com/RoaldFre/wacom_serial5](http://github.com/RoaldFre/wacom_serial5)
__(@Favux: can the first post be edited to reflect this change?)

---

### Post by Favux on 2011-07-13
Hi roaldfre,

Link changed to reflect new repository name.

Yeah, I got confused about the Cintiqs.  The newer usb ones are protocol 5 but apparently the original serial Cintiqs are protocol 4 i.e. no tool serial numbers.

---

### Post by bobfunk67 on 2011-07-13
Hi tokenrove, As Favux told me I'm try to install your custom developed wacom driver with your instructions on a system. As we have some computers to use I have no problem to make a fresh ubuntu install to begin with the process. What release is the recommended? 9.10 10.04 10.10, or another distribution.
   Thanks, Roberto

---

### Post by roaldfre on 2011-07-13
I just added support for both channels. However, I'm not quite sure what the effect of this should be? Obviously, I only have one mouse pointer. How can I test if both channels work properly? What should I expect?

---

### Post by tokenrove on 2011-07-19
> **bobfunk67 said:**
> Hi tokenrove, As Favux told me I'm try to install your custom developed wacom driver with your instructions on a system. As we have some computers to use I have no problem to make a fresh ubuntu install to begin with the process. What release is the recommended? 9.10 10.04 10.10, or another distribution.


Sorry for the late response.  For some reason I stopped getting notifications from the forum in my email.

In general, I recommend the latest versions you can use, as it was developed on Debian with kernel 2.6.39 and xf86-input-wacom 0.10.10, and there are problems with versions earlier than that.

Which serial tablet do you have?  I now have people testing the Digitizer II and Penpartner (which doesn't work out of the box with the current driver); it would be great if I could find Graphire or Cintiq users, otherwise I am soon going to strip out the code for those tablets and try to focus on making a new release of the driver with some issues corrected for the Digitizer II and Penpartner.

Cheers.

---

### Post by tokenrove on 2011-07-19
> **dreh said:**
> 
First. I initialize my tablet with the command sudo inputattach --wacom_iv /dev/ttyS0 - this command stays running or in other words the shell hangs (sending the command to background with "&" don't function). If I Ctrl-C or mouseklick-close the shell my tablet stops working. Is this behavior intended? 


You can run inputattach with the additional option --daemon which will prevent this.

> **dreh said:**
> 
Second. the eraser won't work as a mousepointer (before it did). There's is no reaction to it other than in Gimp where the eraser is when in range of the tablet "unfocus" the paint tool. When you paint with i.e. brush you have a dotted circle (with cirlce tooltip) this vanishes if you get the eraser in range but still you can't "paint the erase color" or "mouse" over your screen.


Okay, the first issues is that it doesn't send core events.  I think you can change that with xinput/xsetwacom options.

When you use the eraser in GIMP, can you select (with the eraser) the eraser tool from the toolbar and erase with it?

Unfortunately I have not been at home with my tablet the last few days and can't check, but I seem to recall the behavior I was having was that the eraser was treated as a separate tool by the gimp and seemed to work as long as I selected a tool for it.

When I am back, I will do a double check over this.  In the meantime, you could try 'xsetpointer -l', find the exact name of the eraser device, then 'xsetpointer +c "Wacom ... whatever name"' to enable sending core events.  Also check in the gimp "Input Devices" dialog -- try changing the eraser's mode from DISABLED to SCREEN and see what happens.

> **dreh said:**
> 
Also sorry for my holperiges (bumpy) english. 


Not a problem.  Sorry for the delay in my response.  I stopped getting notifications for some reason.

I'm planning to do another bunch of work on the driver this coming weekend if I'm at home, including adding the support for Digitizer II features that I know are missing.

Cheers.

---

### Post by Favux on 2011-07-20
Hi tokenrove and roaldfre,

They're changing the ISDV4 rules to:
```
ACTION!="add|change", GOTO="wacom_end"

# Match all serial wacom tablets with a serial ID starting with WACf
# Notes: We assign NAME though we shouldn't, but currently the server requires it
#        We assign the lot to subsystem pnp too because server reads NAME from
#        the parent device. Once all that's fixed, as simple SUBSYSTEM="tty"
#        will do and the ENV{NAME} can be removed.
SUBSYSTEM=="tty|pnp", SUBSYSTEMS=="pnp", ATTRS{id}=="WACf*", ENV{ID_MODEL}="Serial Wacom Tablet $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Serial Wacom Tablet $attr{id}"
SUBSYSTEM=="tty|pnp", SUBSYSTEMS=="pnp", ATTRS{id}=="FUJ*", ENV{ID_MODEL}="Serial Wacom Tablet $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Serial Wacom Tablet $attr{id}"

LABEL="wacom_end"
```
They tell me what I should be using is something like this:
```
SUBSYSTEM=="tty|pnp", SUBSYSTEMS=="pnp", ATTRS{id}=="PNP0501", ENV{ID_MODEL}="Legacy Serial Wacom Tablet $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Legacy Serial Wacom Tablet $attr{id}", SYMLINK="input/wacom"
```
So I imagine you'd want something close to:
```
SUBSYSTEM=="input", SUBSYSTEMS=="pnp", ENV{PRODUCT}='13/3d/*', ENV{ID_MODEL}="Legacy Serial Wacom Tablet $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Legacy Serial Wacom Tablet $attr{id}", SYMLINK="input/wacom"
```
Except I don't know about *ENV{PRODUCT}='13/3d/*'*.  I haven't seen the udevadm info from a wacom_serial.ko so I don't know where you're getting that from.

See:  [http://sourceforge.net/mailarchive/forum.php?thread_name=CAG1eVf1wS%2BPDgK7rjpvK9X_wjL%2BCxCQoi5%3DfOmm%3D3u_2ePtbCQ%40mail.gmail.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=CAG1eVf1wS%2BPDgK7rjpvK9X_wjL%2BCxCQoi5%3DfOmm%3D3u_2ePtbCQ%40mail.gmail.com&forum_name=linuxwacom-devel)  Lennart's replies haven't shown up in the archive yet.

Edit:  Redo due to an oops.

---

### Post by luminol on 2011-07-28
Running Lucid 10.04.3 and an Intuous GD-1212-R with a ch341-uart USB<->serial converter.

I followed the setup instructions for Lucid and am making progress. wacdump shows everything working fine, albeit a little laggy but xinput list doesn't show the device.

My xorg.conf is:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 22 11:44:23 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice   "stylus"
    InputDevice   "eraser"
    InputDevice   "cursor"

EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"         "/dev/ttyUSB0"
    Option        "Type"           "stylus"
    Option        "ForceDevice"    "Serial"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"         "/dev/ttyUSB0"
    Option        "Type"           "eraser"
    Option        "ForceDevice"    "Serial"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"         "/dev/ttyUSB0"
    Option        "Type"           "cursor"
    Option        "ForceDevice"    "Serial"
EndSection


Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Anything else to try or check?

---

### Post by Favux on 2011-07-28
Hi again luminol,

OK, you've established with wacdump that the tablet is on /dev/ttyUSB0.  So that's good.

What does *xsetwacom -V* show?  What is the output of?
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyUSB0)
```
And we should look at your Xorg.0.log in /var/log and see what it is showing.  Go ahead and compress and attach it to your next post.

Is the ch341 kernel driver/module auto-loading?
```
lsmod | grep ch341
```
What does it show in dmesg?
```
dmesg | grep ch341
```

The xorg.conf looks good.  The Nvidia installer configures the mouse and keyboard in xorg.conf which you don't need.  So you can remove those entries if you want to and let them be configured the way that is intended:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Thu Apr 22 11:44:23 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice   "stylus"
    InputDevice   "eraser"
    InputDevice   "cursor"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"         "/dev/ttyUSB0"
    Option        "Type"           "stylus"
    Option        "ForceDevice"    "Serial"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"         "/dev/ttyUSB0"
    Option        "Type"           "eraser"
    Option        "ForceDevice"    "Serial"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"         "/dev/ttyUSB0"
    Option        "Type"           "cursor"
    Option        "ForceDevice"    "Serial"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by luminol on 2011-07-29
> Hi again luminol,

OK, you've established with wacdump that the tablet is on /dev/ttyUSB0.  So that's good.

What does *xsetwacom -V* show?

0.10.6

> What is the output of?
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyUSB0)
```

It is:

```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyUSB0)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:13.4/usb6/6-2/6-2:1.0/ttyUSB0/tty/ttyUSB0':
    KERNEL=="ttyUSB0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:13.4/usb6/6-2/6-2:1.0/ttyUSB0':
    KERNELS=="ttyUSB0"
    SUBSYSTEMS=="usb-serial"
    DRIVERS=="ch341-uart"
    ATTRS{port_number}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:13.4/usb6/6-2/6-2:1.0':
    KERNELS=="6-2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="ch341"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="03"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="01"
    ATTRS{bInterfaceProtocol}=="02"
    ATTRS{modalias}=="usb:v1A86p7523d0254dcFFdsc00dp00icFFisc01ip02"
    ATTRS{supports_autosuspend}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:13.4/usb6/6-2':
    KERNELS=="6-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}==" 96mA"
    ATTRS{urbnum}=="96"
    ATTRS{idVendor}=="1a86"
    ATTRS{idProduct}=="7523"
    ATTRS{bcdDevice}=="0254"
    ATTRS{bDeviceClass}=="ff"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="6"
    ATTRS{devnum}=="2"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{product}=="USB2.0-Ser!"

  looking at parent device '/devices/pci0000:00/0000:00:13.4/usb6':
    KERNELS=="usb6"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="47"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0001"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="6"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.32-33-generic ohci_hcd"
    ATTRS{product}=="OHCI Host Controller"
    ATTRS{serial}=="0000:00:13.4"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:13.4':
    KERNELS=="0000:00:13.4"
    SUBSYSTEMS=="pci"
    DRIVERS=="ohci_hcd"
    ATTRS{vendor}=="0x1002"
    ATTRS{device}=="0x438b"
    ATTRS{subsystem_vendor}=="0x105b"
    ATTRS{subsystem_device}=="0x0e0a"
    ATTRS{class}=="0x0c0310"
    ATTRS{irq}=="18"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00001002d0000438Bsv0000105Bsd00000E0Abc0Csc03i10"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
```

> And we should look at your Xorg.0.log in /var/log and see what it is showing.  Go ahead and compress and attach it to your next post.

Done and done.

> Is the ch341 kernel driver/module auto-loading?
```
lsmod | grep ch341
```

Looks to be:
```
lsmod | grep ch341
ch341                   8216  0 
usbserial              33694  1 ch341

```

> What does it show in dmesg?
```
dmesg | grep ch341
```

Looks good:
```
dmesg | grep ch341
[   11.199706] USB Serial support registered for ch341-uart
[   11.199736] ch341 6-2:1.0: ch341-uart converter detected
[   11.222185] usb 6-2: ch341-uart converter now attached to ttyUSB0
[   11.222213] usbcore: registered new interface driver ch341
```

> The xorg.conf looks good.  The Nvidia installer configures the mouse and keyboard in xorg.conf which you don't need.  So you can remove those entries if you want to and let them be configured the way that is intended:

Will do. I hopelessly borked my first attempt, so I reinstalled.

---

### Post by Favux on 2011-07-29
> I hopelessly borked my first attempt, so I reinstalled. 
I'm cringing.  I hope I didn't cause that.

The Xorg.0.log seems to be telling the tale:
```
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.10.6
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
......
(**) Option "Device" "/dev/ttyUSB0"
(EE) stylus: wcmDeviceTypeKeys unable to ioctl USB key bits.
(**) stylus: always reports core events
(II) XINPUT: Adding extended input device "stylus" (type: STYLUS)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(EE) stylus: usbDetect: can not ioctl version
(EE) stylus: wcmOpen found undetectable  /dev/ttyUSB0 
(EE) Couldn't init device "stylus"
(II) UnloadModule: "wacom"
(**) Option "Device" "/dev/ttyUSB0"
(EE) eraser: wcmDeviceTypeKeys unable to ioctl USB key bits.
(**) eraser: always reports core events
(II) XINPUT: Adding extended input device "eraser" (type: ERASER)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(EE) eraser: usbDetect: can not ioctl version
(EE) eraser: wcmOpen found undetectable  /dev/ttyUSB0 
(EE) Couldn't init device "eraser"
(II) UnloadModule: "wacom"
(**) Option "Device" "/dev/ttyUSB0"
(EE) cursor: wcmDeviceTypeKeys unable to ioctl USB key bits.
(**) cursor: always reports core events
(II) XINPUT: Adding extended input device "cursor" (type: CURSOR)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(EE) cursor: usbDetect: can not ioctl version
(EE) cursor: wcmOpen found undetectable  /dev/ttyUSB0 
(EE) Couldn't init device "cursor"
(II) UnloadModule: "wacom"

```
The error:
> (EE) stylus: usbDetect: can not ioctl version
is the same one smws ran into with his keyspan serial to usb converter.  It's linked in Sources:  [http://ubuntuforums.org/showthread.php?t=1462026&page=3](http://ubuntuforums.org/showthread.php?t=1462026&page=3)  If that's the problem, where we have to modify the kernel driver for your ch341 that could be a little tough.  His programmer brother actually did that for him.  We might need tokenrove or roaldfre to help.  At least we've got a template and also some keywords to google with.

Let's try a long shot and assume it's actually a permissions problem.  If so let's try editing /etc/group.  First check in the group file if there is a line like *dialout: x:20:*.  Is it followed by your user name?  In other words does it look like?
```
dialout:x:20:yourusername
```
If not add your user name by editing the file:
```
gksudo gedit /etc/group
```
and then reboot.

---

### Post by luminol on 2011-07-29
> **Favux said:**
> I'm cringing.  I hope I didn't cause that.

No problems. I back up /var/cache/apt/archives/ with AptOnCD and /home is on a separate partition for just such an emergency. 

> [/QThe Xorg.0.log seems to be telling the tale:
```
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.10.6
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
......
(**) Option "Device" "/dev/ttyUSB0"
(EE) stylus: wcmDeviceTypeKeys unable to ioctl USB key bits.
(**) stylus: always reports core events
(II) XINPUT: Adding extended input device "stylus" (type: STYLUS)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(EE) stylus: usbDetect: can not ioctl version
(EE) stylus: wcmOpen found undetectable  /dev/ttyUSB0 
(EE) Couldn't init device "stylus"
(II) UnloadModule: "wacom"
(**) Option "Device" "/dev/ttyUSB0"
(EE) eraser: wcmDeviceTypeKeys unable to ioctl USB key bits.
(**) eraser: always reports core events
(II) XINPUT: Adding extended input device "eraser" (type: ERASER)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(EE) eraser: usbDetect: can not ioctl version
(EE) eraser: wcmOpen found undetectable  /dev/ttyUSB0 
(EE) Couldn't init device "eraser"
(II) UnloadModule: "wacom"
(**) Option "Device" "/dev/ttyUSB0"
(EE) cursor: wcmDeviceTypeKeys unable to ioctl USB key bits.
(**) cursor: always reports core events
(II) XINPUT: Adding extended input device "cursor" (type: CURSOR)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(EE) cursor: usbDetect: can not ioctl version
(EE) cursor: wcmOpen found undetectable  /dev/ttyUSB0 
(EE) Couldn't init device "cursor"
(II) UnloadModule: "wacom"

```
The error:

is the same one smws ran into with his keyspan serial to usb converter.  It's linked in Sources:  [http://ubuntuforums.org/showthread.php?t=1462026&page=3](http://ubuntuforums.org/showthread.php?t=1462026&page=3)  If that's the problem, where we have to modify the kernel driver for your ch341 that could be a little tough.  His programmer brother actually did that for him.  We might need tokenrove or roaldfre to help.  At least we've got a template and also some keywords to google with.

It would be great if it were as simple as search-and-replacing the keyspan patch to point to "ch341" where applicable, but IANAP.

> Let's try a long shot and assume it's actually a permissions problem.  If so let's try editing /etc/group.  First check in the group file if there is a line like *dialout: x:20:*.  Is it followed by your user name?  In other words does it look like?
```
dialout:x:20:yourusername
```
If not add your user name by editing the file:
```
gksudo gedit /etc/group
```
and then reboot.

Thanks, but no luck, it's already correct in /etc/group.

---

### Post by Favux on 2011-07-29
Sure, why would it be easy?  :)

Yep, I'm doubting the search and replace simplicity somehow.

Alright we need to look at the source code for your Lucid kernel and see what we've got.  We can also look at the source code for PL2303 and the Keyspan.  Between the two of them guiding us on the ch341 we might have a chance.  Otherwise we'll have to plead for help.  Besides it would seem tokenrove and roaldfre are going to be getting questions about this anyway.  That stupid TCIOCGSERIAL ioctl has turned out to be a major pain.

To work with the kernel source code see appendix 1 on the [linuxwacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949").  And from the two patches the directory they should be in is linux-source-2.6.32/drivers/usb/serial.

---

### Post by Favux on 2011-07-29
Wow, if we get lucky it may not be all that hard.  Looks like we only need to do exactly what the pl2303-ioctl patch does.  Open a terminal and run the following commands:
```
cd Desktop

apt-get source linux-image-`uname -r`

```
Navigate to linux-2.6.32/drivers/usb/serial with Nautilus and right click on ch341.c and open in gedit.  So at line # 549 in ch341.c change this function:
```
/*static int ch341_ioctl(struct usb_serial_port *port, struct file *file,*/
static int ch341_ioctl(struct tty_struct *tty, struct file *file,
			unsigned int cmd, unsigned long arg)
{
	struct usb_serial_port *port = tty->driver_data;
	dbg("%s (%d) cmd = 0x%04x", __func__, port->number, cmd);

	switch (cmd) {
	case TIOCMIWAIT:
		dbg("%s (%d) TIOCMIWAIT", __func__,  port->number);
		return wait_modem_info(port, arg);

	default:
		dbg("%s not supported = 0x%04x", __func__, cmd);
		break;
	}

	return -ENOIOCTLCMD;
}
```
to read as follows:
```
/*static int ch341_ioctl(struct usb_serial_port *port, struct file *file,*/
static int ch341_ioctl(struct tty_struct *tty, struct file *file,
			unsigned int cmd, unsigned long arg)
{
+	struct serial_struct ser;
	struct usb_serial_port *port = tty->driver_data;
	dbg("%s (%d) cmd = 0x%04x", __func__, port->number, cmd);

	switch (cmd) {
+	case TIOCGSERIAL:
+		memset(&ser, 0, sizeof ser);
+		ser.type = PORT_16654;	/* ? */
+		ser.line = port->serial->minor;
+		ser.port = port->number;
+		ser.baud_base = 460800;
+
+		if(copy_to_user((void __user*)arg, &ser, sizeof ser)) {
+			return -EFAULT;
+		}
+		return 0;
+
	case TIOCMIWAIT:
		dbg("%s (%d) TIOCMIWAIT", __func__,  port->number);
		return wait_modem_info(port, arg);

	default:
		dbg("%s not supported = 0x%04x", __func__, cmd);
		break;
	}

	return -ENOIOCTLCMD;
}
```
The +'s are just to show you which lines to add.  Remove them before you compile, but make sure the indentations stay the same.  That's important.  Or you can use the attached patch after removing the .txt extention.

Then compile it and copy the newly compiled ch341.ko into place:
```
cd linux-2.6.32/drivers/usb/serial

make -C/lib/modules/`uname -r`/build M=`pwd` modules

sudo cp ch341.ko /lib/modules/`uname -r`/kernel/drivers/usb/serial/

sudo depmod -a
```
Then reboot.

---

### Post by x200 on 2011-08-01
Hi favux,

first of all thanks for all the support for tablet users - I have been using my tablet PC (Lenovo x200 tablet) under ubuntu 9.10 happily and successfully now for quite some time.

Nevertheless, when updating to Lucid, and then to Maverick, I was not able to get the tablet to work. At least, when rebooting, the tablet seems to be recognized by X correctly, /var/log/Xorg.0.log gives:

(...)
[    35.073] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
[    35.073] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    35.073] (II) LoadModule: "wacom"
[    35.073] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    35.255] (II) Module wacom: vendor="X.Org Foundation"
[    35.255]    compiled for 1.9.0, module version = 0.11.99
[    35.255]    Module class: X.Org XInput Driver
[    35.255]    ABI class: X.Org XInput driver, version 11.0
[    35.255] (**) Serial Wacom Tablet: always reports core events
[    35.255] (**) Option "Device" "/dev/ttyS0"
[    35.255] (**) Option "StopBits" "1"
[    35.255] (**) Option "DataBits" "8"
[    35.255] (**) Option "Parity" "None"
[    35.255] (**) Option "Vmin" "1"
[    35.255] (**) Option "Vtime" "10"
[    35.255] (**) Option "FlowControl" "Xoff"
[    35.255] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    35.255] (II) Serial Wacom Tablet: other types will be automatically added.
[    35.768] (II) Serial Wacom Tablet stylus: serial tablet id 0x93.
[    35.768] (--) Serial Wacom Tablet stylus: using pressure threshold of 27 for button 1
[    35.768] (--) Serial Wacom Tablet stylus: Wacom General ISDV4 tablet maxX=26312 maxY=16520 maxZ=255 resX=100000 resY=100000  tilt=disabled
[    35.768] (II) Serial Wacom Tablet stylus: hotplugging dependent devices.
[    35.768] (II) Serial Wacom Tablet stylus: hotplugging completed.
[    35.768] (II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS)
[    35.768] (**) Option "BaudRate" "38400"
[    35.780] (**) Serial Wacom Tablet eraser: Applying InputClass "Wacom serial class"
[    35.780] (**) Serial Wacom Tablet eraser: always reports core events
[    35.780] (**) Option "Device" "/dev/ttyS0"
[    35.781] (**) Option "BaudRate" "38400"
[    35.781] (**) Option "StopBits" "1"
[    35.781] (**) Option "DataBits" "8"
[    35.781] (**) Option "Parity" "None"
[    35.781] (**) Option "Vmin" "1"
[    35.781] (**) Option "Vtime" "10"
[    35.781] (**) Option "FlowControl" "Xoff"
[    35.781] (--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet maxX=26312 maxY=16520 maxZ=255 resX=100000 resY=100000  tilt=disabled
[    35.781] (II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
[    35.781] (**) Serial Wacom Tablet touch: Applying InputClass "Wacom serial class"
[    35.781] (**) Serial Wacom Tablet touch: always reports core events
[    35.781] (**) Option "Device" "/dev/ttyS0"
[    35.781] (**) Option "BaudRate" "38400"
[    35.782] (**) Option "StopBits" "1"
[    35.782] (**) Option "DataBits" "8"
[    35.782] (**) Option "Parity" "None"
[    35.782] (**) Option "Vmin" "1"
[    35.782] (**) Option "Vtime" "10"
[    35.782] (**) Option "FlowControl" "Xoff"
[    35.782] (--) Serial Wacom Tablet touch: Wacom General ISDV4 tablet maxX=26312 maxY=16520 maxZ=255 resX=100000 resY=100000  tilt=disabled
[    35.782] (II) XINPUT: Adding extended input device "Serial Wacom Tablet touch" (type: TOUCH)
(...)

and stylus, touch, and eraser are listed using xinput list and xsetwacom list.

Nevertheless: when trying to use the tablet (e.g. moving the stylus over the tablet), /var/log/Xorg.0.log successively is filled with warnings like
(...)
[   137.764] (WW) Serial Wacom Tablet touch: bad data at 1 v=f0 l=9
[   137.812] (WW) Serial Wacom Tablet touch: bad data at 1 v=80 l=9
[   137.812] (WW) Serial Wacom Tablet touch: bad data at 1 v=cc l=9
[   138.036] (WW) Serial Wacom Tablet touch: bad data at 1 v=f2 l=9
[   138.060] (WW) Serial Wacom Tablet touch: bad data at 1 v=f0 l=9
[   138.136] (WW) Serial Wacom Tablet touch: bad data at 1 v=f0 l=9
[   138.148] (WW) Serial Wacom Tablet touch: bad data at 1 v=f4 l=9
[   138.172] (WW) Serial Wacom Tablet touch: bad data at 3 v=f1 l=9
(etc...)

If in addition I restart X, the tablet is not recognized anymore, and Xorg.0.log gives:

(...)
[   289.397] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
[   289.397] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[   289.397] (II) LoadModule: "wacom"
[   289.398] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[   289.398] (II) Module wacom: vendor="X.Org Foundation"
[   289.398]    compiled for 1.9.0, module version = 0.11.99
[   289.398]    Module class: X.Org XInput Driver
[   289.398]    ABI class: X.Org XInput driver, version 11.0
[   289.398] (**) Serial Wacom Tablet: always reports core events
[   289.398] (**) Option "Device" "/dev/ttyS0"
[   289.398] (**) Option "StopBits" "1"
[   289.398] (**) Option "DataBits" "8"
[   289.398] (**) Option "Parity" "None"
[   289.398] (**) Option "Vmin" "1"
[   289.398] (**) Option "Vtime" "10"
[   289.398] (**) Option "FlowControl" "Xoff"
[   289.398] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[   289.398] (II) Serial Wacom Tablet: other types will be automatically added.
[   292.652] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[   292.652] (WW) Serial Wacom Tablet stylus: Query failed with 38400 baud. Trying 19200.
[   295.906] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[   299.597] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[   299.597] (II) Serial Wacom Tablet stylus: serial tablet id 0x93.
[   299.597] (II) UnloadModule: "wacom"
(...)

This behaviour I observed both using the default xf86-input-wacom-0.10.8 as well as after updating to xf86-input-wacom-0.11.99

The X configuration for the tablet is included in /usr/share/X11/xorg.conf.d/50-wacom.conf
as suggested in Sec. 3)a under 

[http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1) 

(it consistently gave errors, when using /etc/X11/xorg.conf as suggested under Sec. 3)b in the same howto.

I would be grateful for any hints on the problem.

Best regards,

Ralf/x200

---

### Post by Favux on 2011-08-01
Hi Ralf,

Welcome to Ubuntu forums!

The only issue I'm aware of for the X200t/X201t in Maverick is a pressure issue for the stylus.  I think one of the most recent commits might have finally addressed the problem.  By the way I'm not sure where you're getting version 0.11.99 of xf86-input-wacom from.  That was like an rc release before 0.11.0 came out.

So my guess is that there is something wrong with your install.  Let's try reinstalling xf86-input-wacom first.  Clone the git repository so you get the latest version i.e. 0.11.1+.  See part II. c) on the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Be sure to install git-core in a) if you haven't already.

If you are using xsetwacom commands having two executables can mess things up.  Check in /usr/local/bin for a xsetwacom binary (it should be in /usr/bin). This may mean you forgot the '--prefix=/usr' flag on the xf86-input-wacom configure line. Delete the one in the wrong location, i.e. /usr/local/bin.

Out of curiosity do you have a setserial executable in /usr/bin?

---

### Post by x200 on 2011-08-01
Hi favux,

thanks for your feedback. Concerning your questions:

> version 0.11.99 of xf86-input-wacom

I get/got this from doing the clone described in part II.c) of the Bamboo P&T HOW TO you cited. 

> xsetwacom having two executables:

I only find /usr/bin/xsetwacom, no xsetwacom under /usr/local/bin

> setserial in /usr/bin

No, I don't have this, but 
$ which setserial gives: /bin/setserial

To obtain version 0.11.1 I then followed part II.b. /var/log/Xorg.0.log then again shows errors similar to those I saw when trying to get the tablet running in Lucid:

(...)
[    32.985] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
[    32.985] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    32.985] (II) LoadModule: "wacom"
[    32.986] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    33.005] (II) Module wacom: vendor="X.Org Foundation"
[    33.005]    compiled for 1.9.0, module version = 0.11.1
[    33.005]    Module class: X.Org XInput Driver
[    33.005]    ABI class: X.Org XInput driver, version 11.0
[    33.005] (**) Serial Wacom Tablet: always reports core events
[    33.005] (**) Option "Device" "/dev/ttyS0"
[    33.005] (**) Option "StopBits" "1"
[    33.005] (**) Option "DataBits" "8"
[    33.005] (**) Option "Parity" "None"
[    33.005] (**) Option "Vmin" "1"
[    33.005] (**) Option "Vtime" "10"
[    33.005] (**) Option "FlowControl" "Xoff"
[    33.005] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    33.005] (II) Serial Wacom Tablet: other types will be automatically added.
[    36.259] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[    36.259] (WW) Serial Wacom Tablet stylus: Query failed with 38400 baud. Trying 19200.
[    39.513] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[    42.767] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[    42.767] (II) Serial Wacom Tablet stylus: serial tablet id 0x93.
[    42.767] (II) UnloadModule: "wacom"
[    42.767] (EE) PreInit returned NULL for "Serial Wacom Tablet"
(...)

Tomorrow I will play around with higher version of xf86-input-wacom.

I also read something about udev rules files (e.g. under [https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/522318]("https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/522318")), but using or disabling the suggested /etc/udev/rules.d/65-xorg-wacom.rules does not seem to make a difference, and /lib/udev/rules.d/69-xserver-xorg-input-wacom.rules seems to cover this, anyway (just playing around). Do you know where to find the default  
/lib/udev/rules.d/69-xserver-xorg-input-wacom.rules? - I could not find this, and thought about making sure that I do have the right rules file.

Best regards,

Ralf.

---

### Post by Favux on 2011-08-01
> $ which setserial gives: /bin/setserial

OK, it's in /bin.  I'm guessing setserial is automatically installed when a serial port is detected.  I'd go to Synaptic Package Manager and reinstall it in case your version is corrupted.
> > version 0.11.99 of xf86-input-wacom  
I get/got this from doing the clone described in part II.c) of the Bamboo P&T HOW TO you cited. 
Ah, I checked this.  Sorry I read 0.11.99 as 0.10.99.  I guess Peter put a new tag on it that I don't see in the repo., but that is what you get cloning the current git repository now.  I guess that indicates a new rc.  Wow, does that mean 1.0 is coming soon?
> Do you know where to find the default
/lib/udev/rules.d/69-xserver-xorg-input-wacom.rules?
Ron at Debian stopped maintaining it about a year ago.  So I suppose the "official" version is at:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Fixed_device_files_with_udev](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Fixed_device_files_with_udev)  Which reminds me I need to add the two new tablets and the new tablet PC.  But those are usb rules.  It seems like the distros have gone their own way and there never was a standard for serial tablets.

However Peter just posted new serial ISDV4 rules on linuxwacom-devel.  Some udev guru came through and pointed out the ones in Fedora had some errors.  And I posted them in post #113 on this thread (previous page).

Can't find my notes on Ubuntu's version but I do have an applicable one from Jaunty I think:
```
# Symlinks for old-style tty devices
SUBSYSTEMS=="pnp", SUBSYSTEM=="tty", ATTRS{id}=="WACf00[45678]*", SYMLINK+="input/wacom"
```
which was in the Ubuntu wacom.rules.

---

### Post by x200 on 2011-08-02
Hi favux,

> **Favux said:**
> OK, it's in /bin.  I'm guessing setserial is automatically installed when a serial port is detected.  I'd go to Synaptic Package Manager and reinstall it in case your version is corrupted.

I reinstalled setserial, but to no apparent effect (/var/log/Xorg.0.log and behaviour w.r.t. tablet did not change).

> **Favux said:**
> Ah, I checked this.  Sorry I read 0.11.99 as 0.10.99.  I guess Peter put a new tag on it that I don't see in the repo., but that is what you get cloning the current git repository now.  I guess that indicates a new rc.  Wow, does that mean 1.0 is coming soon?

Ok, I will keep using 0.11.99 for now.

> **Favux said:**
> However Peter just posted new serial ISDV4 rules on linuxwacom-devel.  Some udev guru came through and pointed out the ones in Fedora had some errors.  And I posted them in post #113 on this thread (previous page).

My knowledge of udev is poor.  Where would be the correct location for these udev rules? I suppose /{etc,lib}/udev/rules.d/ ?

I checked the following: I replaced my /etc/udev/rules.d/10-wacom.rules with the first part in #113, and I added the line 

> **Favux said:**
> ```
# Symlinks for old-style tty devices
SUBSYSTEMS=="pnp", SUBSYSTEM=="tty", ATTRS{id}=="WACf00[45678]*", SYMLINK+="input/wacom"
```


into

/lib/udev/rules.d/69-xserver-xorg-input-wacom.rules

(see attachments).

In effect I still get this strange behaviour that the tablet is
 - recognized but not functioning after reboot (see attached   
   Xorg.0.log.after-reboot.txt)
 - and not recognized after restarting X only (see attached
   Xorg.0.log.after-Xserver-restart.txt)

In the former case (after reboot), at least I do not get error messages any more when I (try to) use the tablet (mühsam ernährt sich das Eichhörnchen...).

For completeness (?) I also attached my /usr/share/X11/xorg.conf.d/50-wacom.conf

Also, I checked using the 60-wacom.rules for single tablets given in the [link on udev]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Fixed_device_files_with_udev") you provided, i.e. replaced it for the above /lib/udev/rules.d/69-xserver-xorg-input-wacom.rules. After reboot the tablet is recognized correctly, but when I move the stylus over the screen I again get sequences of error messages similar to those described in my first message #121.

I would be very grateful for further hints.

Would it be a good idea to move ahead to Natty? 

Best regards,

Ralf.

---

### Post by Favux on 2011-08-03
Hi Ralf,

> Where would be the correct location for these udev rules? I suppose /{etc,lib}/udev/rules.d/ ?
Custom or local rules are suppose to be in /etc/udev/rules.d as oppose to the distribution's rules in /lib/udev/rules.d.  I agree with tokenrove, call it 70-serial-wacom.rules, so it runs after the 69 wacom.rules.  What you did in the 69 rules is OK but I figured the better place to add the legacy serial rule would be just below the ISDV4 serial rules in 70-serial-wacom.rules.  I would not use 10 (10-wacom.rules).  You were correct not to embed it in the usb script because the usb tablets with touch export two kernel devices, the stylus and touch.  That's what all that is in 69.  Whereas the serial tablet PCs multiplex touch and the stylus.

The 50-wacom.conf is good and should be picking up your X200t.  I believe the baud rate is suppose to be 38400 and I'm not sure why you're having the problem with the time out.  Since the problem reading the port doesn't seem to be setserial I sort of wonder about a hardware problem.  You could try adding it explicitly to the wacom.conf after the driver line.  I guess both serial snippets since I'm not sure which one is matching your tablet.
```
Option "BaudRate"  "38400"
```

At this point I'm wondering if your hardware (maybe the stylus) has gone bad.  And it coincidently happened during your upgrades.  Do you have a windows partition to test the stylus on?  Or access to another stylus?

---

### Post by Favux on 2011-08-03
Oops!  What was I thinking?  The X200t came out after Jaunty didn't it?  So we don't even know if:
```
UBSYSTEMS=="pnp", SUBSYSTEM=="tty", ATTRS{id}=="WACf00[45678]*", SYMLINK+="input/wacom"
```
matches your digitizer's identifier.  To find out what it is enter:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
```
Anyway you'd be better off using the new ISDV4 udev rules in post #113 because we know they'll match.  Just place them in 70-serial-wacom.rules.

---

### Post by x200 on 2011-08-03
Hi favux,

unfortunately, I still can not report any progress. Curiously, I still see the tablet recognized but not operating after reboot, and after Xserver restart (re-login) the tablet is not recognized anymore. The hardware is ok though. Details:

> **Favux said:**
> Custom or local rules are suppose to be in /etc/udev/rules.d as oppose to the distribution's rules in /lib/udev/rules.d.  I agree with tokenrove, call it 70-serial-wacom.rules, so it runs after the 69 wacom.rules
  

I cleaned this up. I shifted the new ISDV4 rules to a new file /etc/udev/rules.d/70-serial-wacom.rules, resp. deleted 10-wacom.rules. The behaviour after reboot remains the same (tablet recognized but not operating, logs as those sent in msg. #125). 

> **Favux said:**
> What you did in the 69 rules is OK but I figured the better place to add the legacy serial rule would be just below the ISDV4 serial rules in 70-serial-wacom.rules.  


When adding the rule you suggested after the ISDV4 rules in 70-serial-wacom.rules, the behaviour is not different.

> **Favux said:**
> 
The 50-wacom.conf is good and should be picking up your X200t.  I believe the baud rate is suppose to be 38400 and I'm not sure why you're having the problem with the time out.  Since the problem reading the port doesn't seem to be setserial I sort of wonder about a hardware problem.  You could try adding it explicitly to the wacom.conf after the driver line.  I guess both serial snippets since I'm not sure which one is matching your tablet.
```
Option "BaudRate"  "38400"
```


I do not observe any effect adding this line as you suggested in 50-wacom.conf

> **Favux said:**
> 
At this point I'm wondering if your hardware (maybe the stylus) has gone bad.

I checked this - stylus & touch are fully functioning under windows, so the hardware seems fine.

> **Favux said:**
> Oops!  What was I thinking?  The X200t came out after Jaunty didn't it?  So we don't even know if:
```
UBSYSTEMS=="pnp", SUBSYSTEM=="tty", ATTRS{id}=="WACf00[45678]*", SYMLINK+="input/wacom"
```
matches your digitizer's identifier.  To find out what it is enter:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
```


This gives:

  looking at device '/devices/pnp0/00:0a/tty/ttyS0':
    KERNEL=="ttyS0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pnp0/00:0a':
    KERNELS=="00:0a"
    SUBSYSTEMS=="pnp"
    DRIVERS=="serial"
    ATTRS{id}=="WACf008"

  looking at parent device '/devices/pnp0':
    KERNELS=="pnp0"
    SUBSYSTEMS==""
    DRIVERS==""

---

### Post by Favux on 2011-08-03
With "WACf008" as the identifier the old rule should have matched.  Hmm.
> When adding the rule you suggested after the ISDV4 rules in 70-serial-wacom.rules, the behaviour is not different.
Not sure what you mean.  What is the current contents of your 70-serial-wacom.rules?

OK, it is not the hardware.  That is good to know.

---

### Post by x200 on 2011-08-03
> **Favux said:**
> Not sure what you mean.  What is the current contents of your 70-serial-wacom.rules?


```
$ cat /etc/udev/rules.d/70-serial-wacom.rules
ACTION!="add|change", GOTO="wacom_end"

# Match all serial wacom tablets with a serial ID starting with WACf
# Notes: We assign NAME though we shouldn't, but currently the server requires it
#        We assign the lot to subsystem pnp too because server reads NAME from
#        the parent device. Once all that's fixed, as simple SUBSYSTEM="tty"
#        will do and the ENV{NAME} can be removed.
SUBSYSTEM=="tty|pnp", SUBSYSTEMS=="pnp", ATTRS{id}=="WACf*", ENV{ID_MODEL}="Serial Wacom Tablet $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Serial Wacom Tablet $attr{id}"

SUBSYSTEM=="tty|pnp", SUBSYSTEMS=="pnp", ATTRS{id}=="FUJ*", ENV{ID_MODEL}="Serial Wacom Tablet $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Serial Wacom Tablet $attr{id}"

# Version suggested by favux, msg. #124 in http://ubuntuforums.org/showthread.php?t=1780154&page=13
# SUBSYSTEMS=="pnp", SUBSYSTEM=="tty", ATTRS{id}=="WACf00[45678]*", SYMLINK+="input/wacom"

LABEL="wacom_end"

```

When using the last line (the rule you provided) in addition, nothing changes. (Using the line only, the tablet is not recognized.)

---

### Post by Favux on 2011-08-03
Thanks.  Well you want to use the new rules Peter just came up with.  Not an old Ubuntu Jaunty(?) rule.

I was hoping the problem you were having was due to the old rules that lennart pointed out had problems.  Things have been a little flaky for serial tablet PCs since Lucid and I sort of was hoping that was the issue, or part of it.  The new rules in 70 should be overriding the old rules in 69 but maybe you should comment those out just in case?

The old serial ISDV4 rules in 69-xserver-xorg-input-wacom.rules for Lucid, Maverick, and Natty are at the top before the script starts:
```
# Catch the serial tablets and tell X that's what they are
ACTION=="add|change", SUBSYSTEM=="pnp", ATTR{id}=="WACf*", ENV{NAME}="Serial Wacom Tablet"
ACTION=="add|change", SUBSYSTEM=="pnp", ATTR{id}=="FUJ*", ENV{NAME}="Serial Wacom Tablet"
ACTION=="add|change", SUBSYSTEMS=="pnp", ATTRS{id}=="WACf*", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"
ACTION=="add|change", SUBSYSTEMS=="pnp", ATTRS{id}=="FUJ*", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"

```
This is where I figured tokenrove or roaldfre would want to add their new rule in Natty or I could add the legacy serial tablet rule for Lucid and Maverick.  Although actually Ubuntu should do that and we should be in /etc as you're now doing.

If that doesn't do anything, and it doesn't seem likely, I'm stumped.  My guess is something got messed up in the upgrade chain.  Of course the only way to test that would be to do a fresh install of Maverick.

You might want to try and post the problem to linuxwacom-discuss:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)  Folks who know more than I do hang out there and tend to be helpful.

---

### Post by x200 on 2011-08-03
I tried putting the rules into 69-xserver-xorg-input-wacom.rules before on Lucid also. Repeating it on Maverick did not help either, as you expected.

I will try a new installation of Maverick, and if this also does not help, I will follow your suggestion and contact linuxwacom-discuss. In any case, I will post any further findings here. For now, many thanks for your help!

Best regards,

Ralf.

---

### Post by firstattempt on 2011-08-09
[SIZE=1]THANKS EVERYONE for your Work  :-)
New[/SIZE][SIZE=1][COLOR=Black] [SIZE=1]wacom_serial5.ko for Protocol V devices on my[/SIZE]  [/COLOR]Intuos GD-0405-R Works :-)
Natty Narwhal and kernel 2.6.38.10
Not yet deeply tested, but i needed to thumbs up :-D
Ok in Gimp

Let me know if you need some feedback (output of some cryptic commands)[/SIZE] [SIZE=1]

The script i need to create for autolaunch is related to the "insmod ./wacom_serial5.ko" and/or "input attach" instructions, right ? did i miss some ?[/SIZE] [SIZE=1]

Thanks again[/SIZE]   \\:D/=D>:D

---

### Post by Favux on 2011-08-09
Hi again firstattempt,

Excellent!  :)

Yes please test some more.  I'm sure roaldfre will want to discuss things with you, so keep an eye on this thread for his response.
> Let me know if you need some feedback (output of some cryptic commands)

What is the output of:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
```
in a terminal?  If I have the input path correct.  Also let's take a peek at the following terminal commands:
```

xinput list

xsetwacom list

dmesg | grep [Ww]acom

dmesg | grep serial

ls -l /dev/input/by-path

```
Please post the outputs.  Thanks.

> The script i need to create for autolaunch is related to the "insmod ./wacom_serial5.ko" and/or "input attach" instructions, right ? did i miss some ?

I would think it is the inputattach command.  The wacom_serial5.ko should autoload.  If not it is easy to fix.  What is the output of?:
```
lsmod | grep serial
```
or if that returns nothing just *lsmod*.

What command are you using for inputattach?

By the way was using the Linux Console download OK.  Or would you prefer a separate inputattach only?

---

### Post by firstattempt on 2011-08-09
hi  :)
> was using the Linux Console download OK.  Or would you prefer a separate inputattach only?Not sure about what you are talking about ? i used the linuxconsoletools-1.4.1 and patched via "patch -p1 < ~/Desktop/path-to-roaldfre's-wacom_serial5-folder/inputattach.patch"

i'm using 
***sudo inputattach --wacom_v /dev/ttyS0***
*changed "wacom_iv" to "wacom_v" here*

***lsmod | grep serial*** gives :
wacom_serial5          16870  0 

***udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)***
  looking at device '/devices/pnp0/00:0f/tty/ttyS0':
    KERNEL=="ttyS0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pnp0/00:0f':
    KERNELS=="00:0f"
    SUBSYSTEMS=="pnp"
    DRIVERS=="serial"
    ATTRS{id}=="PNP0501"

  looking at parent device '/devices/pnp0':
    KERNELS=="pnp0"
    SUBSYSTEMS==""
    DRIVERS==""

***xinput list***
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImExPS/2 Logitech Wheel Mouse               id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 5 serial tablet stylus       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 5 serial tablet eraser       id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 5 serial tablet cursor       id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 5 serial tablet pad          id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard 
```***xsetwacom list***
Wacom protocol 5 serial tablet stylus    id: 10    type: STYLUS    
Wacom protocol 5 serial tablet eraser    id: 11    type: ERASER    
Wacom protocol 5 serial tablet cursor    id: 12    type: CURSOR    
Wacom protocol 5 serial tablet pad    id: 13    type: PAD  

***dmesg | grep [Ww]acom***
[ 3432.128042] input (null): Wacom tablet: Intuos, version 1.2
[ 3432.140181] input: Wacom protocol 5 serial tablet as /devices/pnp0/00:0f/tty/ttyS0/serio3/input/input4
[ 9143.332032] input (null): Wacom tablet: Intuos, version 1.2
[ 9143.344181] input: Wacom protocol 5 serial tablet as /devices/pnp0/00:0f/tty/ttyS0/serio4/input/input5

***dmesg | grep serial***
[ 3432.140181] input: Wacom protocol 5 serial tablet as /devices/pnp0/00:0f/tty/ttyS0/serio3/input/input4
[ 9143.344181] input: Wacom protocol 5 serial tablet as /devices/pnp0/00:0f/tty/ttyS0/serio4/input/input5

***ls -l /dev/input/by-path***
total 0
lrwxrwxrwx 1 root root 9 2011-08-09 15:46 platform-i8042-serio-0-event-kbd -> ../event2
lrwxrwxrwx 1 root root 9 2011-08-09 15:46 platform-i8042-serio-1-event-mouse -> ../event3
lrwxrwxrwx 1 root root 9 2011-08-09 15:46 platform-i8042-serio-1-mouse -> ../mouse0

Hope it could be of some help :)

(stylus, eraser and pressure sensitivity works in Gimp)

---

### Post by Favux on 2011-08-09
Thank you firstattempt for providing that baseline!  That definitely helps.
> stylus, eraser and pressure sensitivity works in Gimp
Great!

At some point I'd like to look into variations of the rule in 70-serial-wacom.rules but I think I should wait until roaldfre asks his questions.
> i used the linuxconsoletools-1.4.1 and patched via "patch -p1 < ~/Desktop/path-to-roaldfre's-wacom_serial5-folder/inputattach.patch"
Basically I was just asking whether you would want to compile intputattach by itself rather than it and the other joy stick stuff in Linux Console.

Oh and just to be sure, you are using the default 50-wacom.conf in xorg.conf.d and not a xorg.conf, correct?

---

### Post by firstattempt on 2011-08-09
humm, i guess in a perfect world compiling intputattach by itself would be the way to go but honestly downloading and compiling linuxconsoletools wasn't a big deal, at all ! a few seconds ... you may have other priorities ... :P
Making myself comfortable with the instructions to build that "driver"  was way more challenging, but that could be me :lol::lol::lol:

Yes i didn't touch to xorg.conf so 50-wacom.conf was used
Thanks for pointing it out to me :D I was about to dig into xsetwacom and such

---

### Post by Favux on 2011-08-09
All right.  Well I wouldn't do it today, I was just thinking it might simplify it for some folks.  Input-wacom has a stand alone inputattach.  I was thinking a pre-patched stand alone inputattach would make things easier for some folks.  For sure if you have suggestions on how to improve the instructions let me know.

Here's some stuff on using xsetwacom to configure or you could use 52-wacom-options.  But I'd go with xsetwacom since I doubt you're hot plugging.  Or does "hot plugging" work for you?  Can you turn the tablet off and on and it still works in other words?:
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

---

### Post by firstattempt on 2011-08-09
Hot plugging ! i didn't even thought it would be an option ...
just tried and well :D cursor went crazy for a few seconds as soon as i get the pen close to the tablet (not even touching) then freeze, freezing mouse as well for a few seconds and going back to normal ... BUT
when back to normal, killing the inputattach process and restarting it makes the tablet fully functional again
(btw i need to start inputattach *and* issue insmod command for the tablet to work at session start up)

Instructions were pretty good ! i was referring at those lonely moments when striding along some new territories :) 
Maybe adding some ways to find the path to the device for the serial port to which the tablet is attached, i think i was lucky on that one : ***/dev/ttyS0*** (i have only one serial port - a serial board - so i made a wild guess that ttyS0 should be fine :rolleyes:)

Thanks for the links !

---

### Post by Favux on 2011-08-09
Thanks for being brave and trying the hot plug experiment.  Sounds like you had fun.  :)  Alright so no hot plug because inputattach has to be restarted.
> btw i need to start inputattach and issue insmod command for the tablet to work at session start up
A way to automatically start inputattach would be nice.  We'll see what roaldfre or tokenrove has to say on auto-starting it.  Without the sudo that would be easy.

Let's see if we can fix the insmod since that shouldn't be necessary.  I assume before you issue insmod that:
```
lsmod | grep serial
```
doesn't show wacom_serial5.ko.  First with it running try to rebuild the module dependencies and see if it will auto-load then:
```
sudo depmod -a
```
Try a reboot and see if it is there with the *lsmod*.  If not try the following.

Some kernel modules won't load on some systems for whatever reason.  You can force it to load by adding it to the list in modules in /etc.  So just add *wacom_serial5* to the bottom of the list:
```
gksudo gedit /etc/modules
```
Save, close and reboot.
> Maybe adding some ways to find the path to the device for the serial port to which the tablet is attached
Alright, let me think about that one.  And let me know if anything else comes to mind.

Edit:  Could you run:
```
sudo dmesg | grep ttyS
```
and check if that tells you what serial port is active?  If so it seems like a good way to get it for inputattach.  Run it before you start inputattach, but I don't think it'll matter either way.

---

### Post by firstattempt on 2011-08-10
without running inputattach :
***sudo dmesg | grep ttyS***
[    0.310550] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.691032] 00:0f: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

no luck autoloading wacom_serial5 so far !? i've tried all options (i may know)
sudo depmod -a alone doesn't work ...
/etc/modules : i've tried with correct path to wacom_serial5 and just "wacom_serial5"

i've also tried with wacom_serial5.ko copied in "/lib/modules/2.6.38-10-generic/kernel/drivers/tty/serial"
yes no wacom_serial5.ko before issuing insmod

Even more Fun :)

found this : [http://www.murraytwins.com/blog/?p=103](http://www.murraytwins.com/blog/?p=103)
something to do with 70-serial-wacom.rules [FONT=Verdana]? provided one is :[/FONT]
ACTION=="add|change", SUBSYSTEM=="pnp", ENV{PRODUCT}='13/3d/*', ENV{NAME}=="Wacom protocol IV serial tablet",SYMLINK+="input/wacom",ENV{ID_INPUT}="1",ENV{ID_INPUT_TABLET}="1"

---

### Post by Favux on 2011-08-10
Good, it looks like we can use dmesg then to find the port.

For the modules list "wacom_serial5.ko" should work.  You shouldn't need the path.  It should be in your /lib/modules/kernel in use/drivers/input somewhere.  You can try *locate wacom_serial5.ko* to find the directory.  Is "/lib/modules/2.6.38-10-generic/kernel/drivers/tty/serial" where it was installed?

OK, I see.  He used a rule with a RUN+ command included to match the port and then modprobe wacom_w8001.  Then he did the same thing for inputattach.  Sure we could try that if you want to.  We could also wait for roaldfre.  Whatever you want.

---

### Post by nego0 on 2011-08-10
Hi 
I'v got a wacom model: CTE-43(sapphire)
And have no idea how to install the driver
```
desmania@desmania-MS-7100:~$ lsusb
Bus 002 Device 003: ID 056a:0013 Wacom Co., Ltd Graphire 3 4x5
```
Some help please:P

Thank you

---

### Post by Favux on 2011-08-10
Hi nego0,

You're on the wrong thread. Could you please start one of your own in Hardware and Laptops, and reply there?  I'll find you.

You mean a CTE-430, correct?  Anyway since it is a usb Wacom tablet that has been out of few years I'm surprised it isn't working out of the box in Natty (11.04).  Check in Synaptic Package Manager or Software Center that the package xserver-xorg-input-wacom is installed.  It should have been by default.  If not install it and reboot.

---

### Post by roaldfre on 2011-08-10
Hi firstattempt, it's awesome to hear that the driver is working for you too! :)

It's  been a bit of a low priority project for me lately. It's in a state  that is usable enough for me. Not all tools have been implemented yet  (those that I can't debug).
It's also not a full implementation of  protocol V according to the specs of xf86-input-wacom. I had some bugs  when doing it correctly that I'll probably need to dig into the code of  xf86-input-wacom to see what's going wrong. Either way, X doesn't really  know how to handle two independent pointers at the same time, so it's  not really that useful anyway.

If you have additional tools (apart from the standard pen and a lens cursor), I'd be happy to support them in the driver so you can test them! :-)


Regarding hotplugging:

> Hot plugging ! i didn't even thought it would be an option ...
 just tried and well :grin:  cursor went crazy for a few seconds as soon as i get the pen close to  the tablet (not even touching) then freeze, freezing mouse as well for a  few seconds and going back to normal ... BUT
 when back to normal, killing the inputattach process and restarting it makes the tablet fully functional again
 (btw i need to start inputattach *and* issue insmod command for the tablet to work at session start up)Abnormal behaviour is to be expected. When turning the tablet back on,  it is internally in it's base baudrate. It needs to be sent a command  (at that lower base baudrate) to switch to the faster rate. However, the  driver did not notice that the tablet was gone, and is still polling it  at the fast rate.
You will probably receive a lot of "Received unknown protocol V packet type!" messages in your dmesg (run 'dmesg' in terminal and look at last lines).

I'm not too familiar with hotplugging serial devices (is that even possible?). Maybe tokenrove knows more of that?


Regarding loading the module automatically:

There isn't an "official" way of permanently installing the driver, yet. In fact, I've only been using it by manually insmodding the module.
However, I just dropped the wacom_serial5.ko in /lib/modules/$(uname -r)/kernel/drivers/ (it will get placed in a proper subdirectory, in case the driver make it to the official linux tree, eventually; but it's not much of an issue).
After you copied that over, you should run "sudo depmod -a". The module should now autoload if you run the inputattach command (at least, it does so here).

---

### Post by firstattempt on 2011-08-10
wacom_serial5.ko insn't installed ! just build from the sources and that's all, if i'm correct
i copied it into "/lib/modules/2.6.38-10-generic/kernel/drivers/tty/serial" in the hope (wild guess based on some googling) to make the system take it into account at boot time ...
(a search for the file gives the places where either i copied it or the original one built from source)

Thank you very much Favux, but i don't want to put some pressure on you, i'm not in any urge with this 
If you think that strategic considerations, number benefit and exchange of experiences/point of views could be the best route, it will be fine with me :)

Haha, too late :D
Hello roaldfre and Thanks :)
unfortunately no additional tools, only the pen, here
trying now with *wacom_serial5.ko in* "/lib/modules/2.6.38-10-generic/kernel/drivers/" followed by "sudo depmod -a"

---

### Post by firstattempt on 2011-08-10
OK wacom_serial5.ko placed in "/lib/modules/$(uname -r)/kernel/drivers/" auto loads  ... after issuing the inputattach command ! :D
not at boot time ! An opportunity for clarification in the instructions to build the driver ? ;)

Now for the auto inputattach ... i've tried that rule _appended_ in 70-serial-wacom.rules :
ACTION=="add|change", SUBSYSTEM=="tty",KERNEL=="ttyS0",ATTRS{id}=="PNP0501",RUN+=”inputattach --daemon --wacom_v /dev/ttyS0"

with no luck, looks like the problem lies with the sudo part of the original command, obviously it's not possible to use that here

---

### Post by Favux on 2011-08-10
> OK wacom_serial5.ko placed in "/lib/modules/$(uname -r)/kernel/drivers/" auto loads ... after issuing the inputattach command !
not at boot time !
Nice.  I can add that to the HOW TO.  Input-wacom puts wacom_w8001.ko in /lib/modules/`uname -r`/kernel/drivers/input/touchscreen/, so not a lot of help there.  I would think either /lib/modules/`uname -r`/kernel/drivers/input/serio/ or /lib/modules/`uname -r`/kernel/drivers/input/tablet/.

For inputattach try adding the path.  So *locate inputattach*.  It should be in /usr/bin if you used the PREFIX=/usr like I suggested.  So:
```
ACTION=="add|change", SUBSYSTEM=="tty", KERNEL=="ttyS0" ,ATTRS{id}=="PNP0501", RUN+=&#8221;/usr/bin/inputattach --daemon --wacom_v /dev/ttyS0"

```
Again I think maybe we could work on the rule a bit.

---

### Post by firstattempt on 2011-08-10
yes it's /usr/bin/inputattach but no doesn't work here :(

here is the output of : ***udevadm test /sys/class/tty/ttyS0/***
run_command: calling: test
udevadm_test: version 167
This program is for debugging only, it does not run any program,
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

parse_file: reading '/lib/udev/rules.d/40-fuse-utils.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-gnupg.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-hplip.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-ia64.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-libgphoto2-2.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-libsane.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-ppc.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-usb-media-players.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-usb_modeswitch.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-xserver-xorg-video-intel.rules' as rules file
parse_file: reading '/lib/udev/rules.d/42-qemu-usb.rules' as rules file
parse_file: reading '/lib/udev/rules.d/45-fuse.rules' as rules file
parse_file: reading '/lib/udev/rules.d/45-libmtp8.rules' as rules file
parse_file: reading '/lib/udev/rules.d/50-firmware.rules' as rules file
parse_file: reading '/lib/udev/rules.d/50-udev-default.rules' as rules file
parse_file: reading '/lib/udev/rules.d/55-dm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/56-hpmud_support.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-cdrom_id.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-ffado.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-floppy.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-alsa.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-input.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-serial.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage-dm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage-tape.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-v4l.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-gnome-bluetooth-rfkill.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-mobile-action.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-persistent-storage-edd.rules' as rules file
parse_file: reading '/lib/udev/rules.d/64-xorg-xkb.rules' as rules file
parse_file: reading '/lib/udev/rules.d/66-xorg-synaptics.rules' as rules file
parse_file: reading '/lib/udev/rules.d/69-xorg-vmmouse.rules' as rules file
parse_file: reading '/lib/udev/rules.d/69-xserver-xorg-input-wacom.rules' as rules file
parse_file: reading '/lib/udev/rules.d/70-acl.rules' as rules file
parse_file: reading '/lib/udev/rules.d/70-hid2hci.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-cd.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-net.rules' as rules file
parse_file: reading '/lib/udev/rules.d/70-printers.rules' as rules file
[COLOR=Navy]parse_file: reading '/etc/udev/rules.d/70-serial-wacom.rules' as rules file[/COLOR]
parse_file: reading '/lib/udev/rules.d/75-cd-aliases-generator.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-net-description.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-persistent-net-generator.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-probe_mtd.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-tty-description.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-ericsson-mbm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-longcheer-port-types.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-pcmcia-device-blacklist.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-platform-serial-whitelist.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-qdl-device-blacklist.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-simtech-port-types.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-usb-device-blacklist.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-x22x-port-types.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-zte-port-types.rules' as rules file
parse_file: reading '/lib/udev/rules.d/78-graphics-card.rules' as rules file
parse_file: reading '/lib/udev/rules.d/78-sound-card.rules' as rules file
parse_file: reading '/lib/udev/rules.d/80-drivers.rules' as rules file
parse_file: reading '/lib/udev/rules.d/80-mm-candidate.rules' as rules file
parse_file: reading '/lib/udev/rules.d/80-udisks.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-brltty.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-hdparm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-hplj10xx.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-keyboard-configuration.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-pcmcia.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-regulatory.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-usbmuxd.rules' as rules file
parse_file: reading '/lib/udev/rules.d/90-alsa-restore.rules' as rules file
parse_file: reading '/lib/udev/rules.d/90-alsa-ucm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/90-hal.rules' as rules file
parse_file: reading '/lib/udev/rules.d/90-libgpod.rules' as rules file
parse_file: reading '/lib/udev/rules.d/90-pulseaudio.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-keyboard-force-release.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-keymap.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-udev-late.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-battery-recall-dell.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-battery-recall-fujitsu.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-battery-recall-gateway.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-battery-recall-ibm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-battery-recall-lenovo.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-battery-recall-toshiba.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-csr.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-hid.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-wup.rules' as rules file
parse_file: reading '/lib/udev/rules.d/97-bluetooth-serial.rules' as rules file
parse_file: reading '/lib/udev/rules.d/97-bluetooth.rules' as rules file
parse_file: reading '/dev/.udev/rules.d/root.rules' as rules file
udev_rules_new: rules use 243804 bytes tokens (20317 * 12 bytes), 41120 bytes buffer
udev_rules_new: temporary index used 69980 bytes (3499 * 20 bytes)
udev_device_new_from_syspath: device 0x20c8d0d0 has devpath '/devices/pnp0/00:0f/tty/ttyS0'
udev_device_new_from_syspath: device 0x20c9dfe8 has devpath '/devices/pnp0/00:0f/tty/ttyS0'
udev_device_read_db: device 0x20c9dfe8 filled with db file data
udev_device_new_from_syspath: device 0x20c9e1c0 has devpath '/devices/pnp0/00:0f'
udev_device_new_from_syspath: device 0x20c9e418 has devpath '/devices/pnp0'
udev_rules_apply_to_event: GROUP 20 /lib/udev/rules.d/50-udev-default.rules:11
udev_rules_apply_to_event: RUN 'socket:@/org/freedesktop/hal/udev_event' /lib/udev/rules.d/90-hal.rules:2
udev_event_execute_rules: no node name set, will use kernel supplied name 'ttyS0'
udev_node_add: creating device node '/dev/ttyS0', devnum=4:64, mode=0660, uid=0, gid=20
udev_node_mknod: preserve file '/dev/ttyS0', because it has correct dev_t
udev_node_mknod: preserve permissions /dev/ttyS0, 020660, uid=0, gid=20
node_symlink: preserve already existing symlink '/dev/char/4:64' to '../ttyS0'
udev_device_update_db: unable to create temporary db file '/dev/.udev/data/c4:64.tmp': Permission denied
udevadm_test: UDEV_LOG=6
udevadm_test: DEVPATH=/devices/pnp0/00:0f/tty/ttyS0
udevadm_test: MAJOR=4
udevadm_test: MINOR=64
udevadm_test: DEVNAME=/dev/ttyS0
udevadm_test: ACTION=add
udevadm_test: SUBSYSTEM=tty
udevadm_test: ID_MM_CANDIDATE=1
udevadm_test: run: 'socket:@/org/freedesktop/hal/udev_event'

---

### Post by Favux on 2011-08-10
Thanks for running test.  Sure enough it looks like a permission thing.  Did he add inputattach to the appropriate group and just not bother to tell us?  That's a little strange.

---

### Post by tokenrove on 2011-08-11
> **firstattempt said:**
> 
ACTION=="add|change", SUBSYSTEM=="pnp", ENV{PRODUCT}='13/3d/*', ENV{NAME}=="Wacom protocol IV serial tablet",SYMLINK+="input/wacom",ENV{ID_INPUT}="1",ENV{ID_INPUT_TABLET}="1"

I wanted to note that this udev rule is clearly wrong; it's assigning PRODUCT when it should be matching against it.  I don't know if it has anything to do with your problem (I haven't been following this discussion), but if you are using this rule with one of the new serial drivers, make sure it reads
```

ENV{PRODUCT}=='13/3d/*',

```
Also, this will only match the Wacom protocol IV driver I wrote; roaldfre's driver uses the USB vendor and product ids.

Hope this helps.

---

### Post by firstattempt on 2011-08-11
Hello tokenrove and Thanks :)

70-serial-wacom.rules with ***ENV{PRODUCT}='13/3d/*'*** !!! 
Just checked, i confirm that's the one in the archive coming from : [https://github.com/RoaldFre/wacom_serial5](https://github.com/RoaldFre/wacom_serial5) and it's the same as the one in wacom_serial-110702-0.tar.gz

so i have tried to comment the line with that rule, which isn't supposed to work anyway, and no problem ! apparently we don't need it :shock:

still no progress in the inputattach autoload department though

---

### Post by Favux on 2011-08-11
Hi firstattempt,

> so i have tried to comment the line with that rule, which isn't supposed to work anyway, and no problem ! apparently we don't need it
The kernel is exporting "Wacom protocol 4 tablet" for tokenrove and "Wacom protocol 5 tablet" for roaldfre.  See their respective inputtattach.patch.  For e.g. roaldfre's code in the patch is:
```
+{ "--wacom_iv",		"-wacom_iv",	"Wacom protocol 4 tablet",
+	B9600, CS8,
+	SERIO_WACOM_IV,		0x00,	0x00,	0,	NULL },
+{ "--wacom_v",		"-wacom_v",	"Wacom protocol 5 tablet",
+	B9600, CS8,
+	SERIO_WACOM_V,		0x00,	0x00,	0,	wacom_v_init },
```
That's why your *xinput list* shows:
```
&#9116;   &#8627; Wacom protocol 5 serial tablet stylus       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 5 serial tablet eraser       id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 5 serial tablet cursor       id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 5 serial tablet pad          id=13    [slave  pointer  (2)]
```
Then xf86-input-wacom is appending the type on the name exported by the kernel (inputattach), i.e. stylus, eraser, cursor, and pad.

So the keyword being used by the match line of 50-wacom.conf in the usb snippet is "Wacom":
```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM|WALTOP|Hanwang"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection
```
What we need to avoid is the keyword "Serial Wacom Tablet".  Because one of the ISDV4 serial tablet snippets is using that:
```
Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection
```
I believe that is coming from the serial wacom.rule currently used in Fedora which had been changed to this going forward:
```
ACTION!="add|change", GOTO="wacom_end"

# Match all serial wacom tablets with a serial ID starting with WACf
# Notes: We assign NAME though we shouldn't, but currently the server requires it
#        We assign the lot to subsystem pnp too because server reads NAME from
#        the parent device. Once all that's fixed, a simple SUBSYSTEM="tty"
#        will do and the ENV{NAME} can be removed.
SUBSYSTEM=="tty|pnp", SUBSYSTEMS=="pnp", ATTRS{id}=="WACf*", ENV{ID_MODEL}="Serial Wacom Tablet $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Serial Wacom Tablet $attr{id}"
SUBSYSTEM=="tty|pnp", SUBSYSTEMS=="pnp", ATTRS{id}=="FUJ*", ENV{ID_MODEL}="Serial Wacom Tablet $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Serial Wacom Tablet $attr{id}"

LABEL="wacom_end"
```

---

### Post by Favux on 2011-08-11
Hi tokenrove,

That clears it up a little.  It is a typo and that is suppose to be a match.  So the rule should look like:
```
ACTION=="add|change", SUBSYSTEM=="pnp", ENV{PRODUCT}=='13/3d/*', ENV{NAME}=="Wacom protocol IV serial tablet", SYMLINK="input/wacom",ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"
```
Correct?  I changed the symlink += to = because I don't foresee a use case where a user would be attaching two of the same type of serial tablets.

I think it is OK to move the symlink to the end so we could then integrate it into the current serial rules like so:
```
ACTION!="add|change", GOTO="wacom_end"

# Match all serial wacom tablets with a serial ID starting with WACf
# Notes: We assign NAME though we shouldn't, but currently the server requires it
#        We assign the lot to subsystem pnp too because server reads NAME from
#        the parent device. Once all that's fixed, a simple SUBSYSTEM="tty"
#        will do and the ENV{NAME} can be removed.
SUBSYSTEM=="tty|pnp", SUBSYSTEMS=="pnp", ATTRS{id}=="WACf*", ENV{ID_MODEL}="Serial Wacom Tablet $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Serial Wacom Tablet $attr{id}"
SUBSYSTEM=="tty|pnp", SUBSYSTEMS=="pnp", ATTRS{id}=="FUJ*", ENV{ID_MODEL}="Serial Wacom Tablet $attr{id}", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", ENV{NAME}="Serial Wacom Tablet $attr{id}"

# Legacy serial tablet rules
SUBSYSTEM=="pnp", ENV{PRODUCT}=='13/3d/*', ENV{NAME}=="Wacom protocol IV serial tablet", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", SYMLINK="input/wacom"

LABEL="wacom_end"
```
Does that look reasonable?

And we need a new rule for roaldfre's protocol 5.

By the way I still don't quite see where 13/3d/* is coming from.  Do you mind explaining that a little and maybe posting an attributes walk?  Say:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
```

---

### Post by roaldfre on 2011-08-11
> **firstattempt said:**
> Hello tokenrove and Thanks :)

70-serial-wacom.rules with ***ENV{PRODUCT}='13/3d/*'*** !!! 
Just checked, i confirm that's the one in the archive coming from : [https://github.com/RoaldFre/wacom_serial5](https://github.com/RoaldFre/wacom_serial5) and it's the same as the one in wacom_serial-110702-0.tar.gz

so i have tried to comment the line with that rule, which isn't supposed to work anyway, and no problem ! apparently we don't need it :shock:

still no progress in the inputattach autoload department though

Ah, yes, I personally don't use those udev rules. That file is still the original from tokenrove. I never changed it.
If you find something that works, I can update it in the repository. Otherwise I'd probably remove it from the repo for now.

---

### Post by Favux on 2011-08-11
Hi firstattempt,

How about for now putting it in a Launcher?  For example:

Name:  Start inputattach
Command:  gksudo inputattach --daemon --wacom_v /dev/ttyS0

I don't think you should need the full path /usr/bin/inputattach.  Then if you drag it into Unity's launcher it's always available and a single click brings up a request for your Password.  After you enter it you're done.  Not perfect but livable for the moment?


firstattempt and roaldfre,

Does this work?
```
ACTION=="add|change", SUBSYSTEM=="pnp", ATTRS{id}=="PNP0501", ENV{NAME}=="Wacom protocol V serial tablet", SYMLINK="input/wacom", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"
```

---

### Post by firstattempt on 2011-08-11
hi Favux,
Yep basically what i was doing except i have "sudo inputattach --daemon --wacom_v /dev/ttyS0", nothing happen with gksudo here (isn't that command only for gui application ?)
That's what i was doing anyway back in old Windows days : launching/stoping the wacom service with a script when needed, i didn't like to let my tablet always plugged and unnecessarily overheating ...
i will try that rule but looks like roaldfre confirmed the obsolete status of it, but i surely miss something here

with your new rule
***udevadm test /sys/class/tty/ttyS0/*** gives exactly the same output as before (the one i posted here) before and after issuing ***udevadm trigger --sysname-match=ttyS0***
didn't tried a reboot because i don't know a way to have some feedback about what's going on 
ok after trying a reboot, looking at udev.log didn't show something specific, unless
```
KERNEL[1313097798.246557] add      /devices/pnp0/00:0f/tty/ttyS0 (tty)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pnp0/00:0f/tty/ttyS0
SUBSYSTEM=tty
DEVNAME=ttyS0
SEQNUM=1541
MAJOR=4
MINOR=64

UDEV  [1313097798.676582] add      /devices/pnp0/00:0f/tty/ttyS0 (tty)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pnp0/00:0f/tty/ttyS0
SUBSYSTEM=tty
DEVNAME=/dev/ttyS0
SEQNUM=1541
ID_MM_CANDIDATE=1
MAJOR=4
MINOR=64
```

---

### Post by Favux on 2011-08-11
Well good point, I was thinking more of the aspect that gksudo would give a nice pop up window to enter the password into.  It works for me if I use it along with an executable script, which is command line.  I have a notification in it so I know it has run.

Wow, nice.  But I'm not sure what to make of udev.log other than the ttyS0 port was added.  And I don't know what to make of the fact that test was the same.  Hmmm.

> i will try that rule but looks like roaldfre confirmed the obsolete status of it, but i surely miss something here
I'm a little confused about it myself.  Certainly udev rules are doing a lot of configuration.  But they don't seem necessary for Wacom tablets since they use the name exported from the kernel to find a keyword to match in the 50-wacom.conf in xorg.conf.d.  And that's where the configuration happens.  So the only real reason for the 69-wacom.rules in Ubuntu is to provide symlinks in case you are using a xorg.conf.  And of course there really isn't any real reason to use xorg.conf anymore.

But I have the impression that some other distros, maybe Fedora and Debian, in certain situations do need udev rules for at least some Wacom tablets.  Perhaps just due to a difference in their udev setup.

Anyway I think it is still consider best practice to provide a udev rule for a new device driver.  Although I suppose you could skip the symlink.

---

### Post by Favux on 2011-08-13
Hi firstattempt,

Let's try doing what input-wacom talks about for inputattach with W8001.  The README suggests using rc.local "so the device will be mapped to a /dev/input/event# before X driver starts."

So add the line:
```
inputattach --wacom_v /dev/ttyS0
```
to rc.local like this:
```
# By default this script does nothing.

inputattach --wacom_v /dev/ttyS0

exit 0
```
Using:
```
gksudo gedit /etc/rc.local
```
of course.

Worth a shot.

---

### Post by firstattempt on 2011-08-13
Bingo ! :)
Congratulations, [COLOR=Black]straight in the bull's-eye[/COLOR] :shock:
# Now the script does load inputattach at boot time.
Thanks Favux

---

### Post by Favux on 2011-08-13
Great!  :D

Now I think we have a pretty complete HOW TO for the wacom_serial.ko's if I add that to it.  I'd appreciate it when you get a chance if you looked it over for mistakes or any suggestions you might have.

Still debating on whether I should move the rules to an appendix or just trash them.  Same about building xf86-input-wacom.  Maybe that should just be a link?

---

### Post by firstattempt on 2011-08-14
Hi Favux,
But of course, if i can contribute in any way 

In case of roaldfre's driver i think it's better to follow your instuctions than the tokenrove's one because of the insmod**,** linuxconsoletools and udev rule bits (don't follow wacom_serial5 Readme)
[B]
a) Download and compile the protocol 5 wacom_serial5.ko (Intuos and Intuos2 tablets) - by roaldfre
[/B]- git is not mandatory here, we can follow roaldfre's link and download (via the "button" on right side) the driver from there
- if using git, maybe make sure people are aware one can "control" where in the computer the repository is going to be downloaded (so one can "cd" appropriately later)  :
```
git clone https://github.com/RoaldFre/wacom_serial5.git /path/to/wacomserial5Folder
```where "wacomserial5Folder" is a folder the git command will create and download the driver into
[I]hum, this could be only confusing perhaps better to point "git --help clone" if finer granularity is needed

[/I][B]b) Download and compile inputattach
[/B]"(or if you have an Intuos tablet, be sure to add in the snapshot # to wacom_serial5 if using a snapshot)" i found it a bit confusing did you mean something like "in case of wacom_serial5 : patch -p1 < ~/Desktop/wacom_serial5/inputattach.patch"

For the "inputattach --wacom_iv /dev/ttyS0" perhaps a reminder that this command will automagically do what "sudo insmod ./wacom_serial5.ko" is supposed to do (in case someone wonders after reading tokenrove's instructions )

would be nice to point out that tablet configuration is done via "/usr/share/X11/xorg.conf.d/50-wacom.conf" file or better via "xsetwacom" commands script

cheers

---

### Post by alexcrow on 2011-09-11
All, 

I have posted the below to RoaldFre's Github issues, reposting here in case anyone else has noticed this:

I have a serial Intuos2 A4 on Natty. I compiled and installed the module and patched inputattach as detailed here: [http://ubuntuforums.org/showthread.php?t=1780154](http://ubuntuforums.org/showthread.php?t=1780154).

The tablet is connected to a BrianBoxes serial adapter (legacy-free PC) and it works in XP (and worked in older Ubuntus).

However on running inputattach dmesg shows the following, repeatedly with in increasing number after serio in the last line.

[  126.738363] serio: Serial port ttyS5
[  126.758349] input (null): Model string: ~#XD-0912-R00,V1.2-6
[  126.758353] input (null): Wacom tablet: Intuos2, version 1.2
[  127.756586] input (null): Timed out waiting for tablet to respond with configuration string.
[  127.756599] wacom_serial5: probe of serio17 failed with error -5

I hope you can help.

Thanks

Alex

---

### Post by firstattempt on 2011-09-11
Hi Alexcrow,

First i'm in no way educated enough to give you an adequate answer to your current problem but 
looking at [RoaldFre]("https://github.com/RoaldFre")'s "wacom_serial5.c" code
```


    /* My Intuos tablet won't respond to a configuration request, so it 
     * seems
     * TODO: Intuos2 does work? Or remove alltogether (seems to be 
     * removed altogether in older code) */
    if (wacom->dev->id.version != MODEL_INTUOS) {
        err = wacom_send(serio, REQUEST_CONFIGURATION_STRING);
        if (err)
            return err;


        u = wait_for_completion_timeout(&wacom->cmd_done, HZ);
        if (u == 0) {
            dev_info(&wacom->dev->dev, "Timed out waiting for "
                    "tablet to respond with "
                    "configuration string.\n");
            return -EIO;
        }
    }


    init_completion(&wacom->cmd_done);

```it appears that [RoaldFre]("https://github.com/RoaldFre") didn't had an opportunity to test that "feature" on Intuos2 and suggested on comment above to remove it
so maybe try to comment those lines - 680/698 - in the code and recompile ...
```

cd wacom_serial5  
make all  
sudo cp wacom_serial5.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet  sudo depmod -a

```Again just a wild guess ...

---

### Post by alexcrow on 2011-09-11
Just shows why one should always look at the code. Obviously I didn't ;-)

Cheers

Alex

---

### Post by firstattempt on 2011-09-11
Yeah i noticed too ! it's all in code :D:D

---

### Post by Favux on 2011-09-11
Hi alexcrow,

Good looks like firstattempt and you have it working.  :)

Do you have the XD-0912P?

Also if you still have the puck/Wacom tablet mouse roaldfre would like feedback on how that is working.

---

### Post by alexcrow on 2011-09-11
I'm not sure, dmesg gave me this:

[  164.407151] serio: Serial port ttyS5
[  164.426325] input (null): Model string: ~#XD-0912-R00,V1.2-6
[  164.426329] input (null): Wacom tablet: Intuos2, version 1.2
[  164.446187] input (null): Coordinates string: ~C30480,24060
[  164.446319] input: Wacom protocol 5 serial tablet as /devices/pci0000:00/0000:00:1e.0/0000:08:00.0/tty/ttyS5/serio2/input/input6
[  172.393140] serio: Serial port ttyS5
[  172.413096] input (null): Model string: ~#XD-0912-R00,V1.2-6
[  172.413099] input (null): Wacom tablet: Intuos2, version 1.2
[  172.432984] input (null): Coordinates string: ~C30480,24060
[  172.433028] input: Wacom protocol 5 serial tablet as /devices/pci0000:00/0000:00:1e.0/0000:08:00.0/tty/ttyS5/serio3/input/input7

I think I ended up with two because I was trying to get my airbrush to work. Perhaps it's a bit early for that. But I can tell you that my Cursor - on the underside is written:

XC-100-00
S/N: 2HP006942

works ok apart from the scroll wheel.

I used to use the following in xorg.conf, but as you can see the natty upgrade commented it all out. If anyone can suggest how to get the airbrush working again if possible I would be most grateful.

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#       Identifier     "stylus"
#       Driver         "wacom"
#       Option         "Type" "stylus"
#       Option         "Device" "/dev/ttyS1"
##      Option     "Serial" "42144138"
#       Option         "Mode" "Absolute"
#       Option         "Vendor" "WACOM"
#       Option         "Threshold" "5"
#       Option         "Twinview" "rightof"
#       Option     "MMonitor" "off"
#       Option         "BottomY" "22061"
#       Option         "BottomX" "30480"
#       #Option    "KeepShape" "on"
#       Option         "TopY" "0"
#       Option         "TopX" "0"
#       Option         "PressCurve" "25,0,100,75"
#EndSection
#Section "InputDevice"
#       Identifier     "airbrush"
#       Driver         "wacom"
#       Option         "Type" "stylus"
#       Option         "Device" "/dev/ttyS1"
#       Option         "Serial" "56623267"
#       Option         "Mode" "Absolute"
#       Option         "Vendor" "WACOM"
#       Option         "Threshold" "5"
#       Option         "Twinview" "rightof"
#       Option         "MMonitor" "off"
#       Option         "BottomY" "22061"
#       Option         "BottomX" "30480"
#       #Option         "KeepShape" "on"
#       Option         "TopY" "0"
#       Option         "TopX" "0"
#       Option         "PressCurve" "25,0,100,75"
#EndSection
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#       Identifier     "eraser"
#       Driver         "wacom"
#       Option         "Type" "eraser"
#       Option         "Device" "/dev/ttyS1"
#       Option         "Mode" "Absolute"
#       Option         "Vendor" "WACOM"
#       Option         "Threshold" "5"
#       Option         "BottomY" "22061"
#       Option         "BottomX" "30480"
#       Option         "TopY" "0"
#       Option         "TopX" "0"
#       Option         "PressCurve" "25,0,100,75"
#       Option         "Twinview" "rightof"
#       Option     "MMonitor" "off"
#       #Option    "KeepShape" "on"
#       #Option "ScreenNo" "1"
#EndSection
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#       Identifier     "cursor"
#       Driver         "wacom"
#       Option         "Type" "cursor"
#       Option         "Device" "/dev/ttyS1"
#       Option         "Mode" "Relative"
#       Option         "Vendor" "WACOM"
#       #Option            "Twinview" "rightof"
#EndSection

Thanks

Alex

---

### Post by Favux on 2011-09-11
Alright, we'll go with Wacom Intuos2 A4 0912-R.

Perfect because in addition to the puck roaldfre needs feedback on the airbrush.  Right now the airbrush doesn't work?  And that's with it separately on the tablet, not with the stylus or mouse there?

So there are two things to work on:  puck scrollwheel and the airbrush.

By the way once the airbrush works you should be able to configure it and the stylus separately due to the new input tool serial # capability Alexia Death (Gimp developer) and Peter Hutterer have added to xf86-input-wacom.  See the Linux Wacom Project mediawiki HOW TO pages for configuration:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

Especially:
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d)

---

### Post by roaldfre on 2011-09-11
Just a quick update, here. I've fixed (removed) that config request in the repository.

The scrollwheel and airbrush are indeed not implemented yet, but it shouldn't be too hard to get them working as well. I'll have a look at it tomorrow. ;-)

[Edit] Just for the record. You airbrush is not working at all (you don't see the cursor moving when it comes in proximity, can't tap, etc); or it's just the wheel that does not work? The latter is normal, the former is a bit of a bigger issue.

---

### Post by alexcrow on 2011-09-11
> **roaldfre said:**
> Just a quick update, here. I've fixed (removed) that config request in the repository.

The scrollwheel and airbrush are indeed not implemented yet, but it shouldn't be too hard to get them working as well. I'll have a look at it tomorrow. ;-)

[Edit] Just for the record. You airbrush is not working at all (you don't see the cursor moving when it comes in proximity, can't tap, etc); or it's just the wheel that does not work? The latter is normal, the former is a bit of a bigger issue.

Hi Favux & [roaldfre]("http://ubuntuforums.org/member.php?u=1337839"),

Thanks for the reply.

The drawing tip of the airbrush does not work. The scroll wheel on both the puck and the airbrush do nothing. The eraser on the airbrush seems to be able to move the cursor at least, just as the one on the stylus pen does.

I have always been testing with one tool on the tablet at all times.

I will remove the extra stuff I've put in /usr/share/X11/xorg.conf.d/50-wacom.conf to try to get these things working as it may be confusing the issue - going back to what was there when I started.

Cheers

Alex

---

### Post by roaldfre on 2011-09-11
Ok, I couldn't resist already trying to take a stab at it. It's possible that the scroll wheel of the mouse puck works now (and *maybe* even the wheel on the airbrush).

relevant commit: [http://github.com/RoaldFre/wacom_serial5/commit/1972304f6cf6b7bfbf58c8d7edcbf5106ef2aa01](http://github.com/RoaldFre/wacom_serial5/commit/1972304f6cf6b7bfbf58c8d7edcbf5106ef2aa01)

---

### Post by alexcrow on 2011-09-12
> **roaldfre said:**
> Ok, I couldn't resist already trying to take a stab at it. It's possible that the scroll wheel of the mouse puck works now (and *maybe* even the wheel on the airbrush).

relevant commit: [http://github.com/RoaldFre/wacom_serial5/commit/1972304f6cf6b7bfbf58c8d7edcbf5106ef2aa01](http://github.com/RoaldFre/wacom_serial5/commit/1972304f6cf6b7bfbf58c8d7edcbf5106ef2aa01)

Thanks roaldfre,

I won't be able to test this until after work. I will tell you how it goes.

Cheers

Alex

---

### Post by alexcrow on 2011-09-12
> **alexcrow said:**
> Thanks roaldfre,

I won't be able to test this until after work. I will tell you how it goes.

Cheers

Alex

OK, 

The mouse scrollwheel works now, however the airbrush tool behaves as before, ie the only response is from the eraser end of it, the stylus end and the wheel does nothing.

Getting there though. Is there no-one else with an Intuos2 serial out there? Alexia maybe?

Cheers

Alex

---

### Post by Favux on 2011-09-12
> The mouse scrollwheel works now
Cool, roaldfre's got the cursor working now.
> Is there no-one else with an Intuos2 serial out there?
Don't worry you're not alone.  There are plenty of folks with Wacom serial tablets.  Just remember for the last year and a half (Lucid(10.04)/X server 1.7/xf86-input-wacom came out) everyone has been told their serial tablet will no longer work.  Or they found out for themselves the hard way.

Going to take a while for the word to spread that that is no longer true and linux is serial tablet friendly again.

---

### Post by roaldfre on 2011-09-12
Can you try running the wacom_serial5.c from [http://pastebin.com/Pt5QzQg8](http://pastebin.com/Pt5QzQg8) and seeing what dmesg says when you bring the airbrush into proximity.

It should dump some data from every packet it receives.

You can monitor the output better by doing a "sudo tail -f /var/log/messages" in a terminal. This gives you 'real time' output, so you can directly see how the driver reacts to the tool.

Bringing the pen or an eraser in and out of proximity should show you what the output should be like. First an ID packet, then a bunch of pen packets, then an out of proximity packet. It prints the header of every received packet as well.

Please paste the relevant section of the dmesg when doing this test with the airbrush here (or upload to something like pastebin.com if its too big).

One thing I just thought of, you can try resetting the tablet (by killing and starting inputattach again) and bringing the different tools in proximity in different 'orders'.
For example, reset and bring the airbrush in prox as the very first tool. See what happens.
Then, reset and bring pen in prox first, then airbrush (then pen again -- still working?).
Reset and reverse the order: first airbrush, then pen (then airbrush again -- working now?).
See if something different happens in the dmesg.

---

### Post by alexcrow on 2011-09-13
> **roaldfre said:**
> Can you try running the wacom_serial5.c from [http://pastebin.com/Pt5QzQg8](http://pastebin.com/Pt5QzQg8) and seeing what dmesg says when you bring the airbrush into proximity.

It should dump some data from every packet it receives.

You can monitor the output better by doing a "sudo tail -f /var/log/messages" in a terminal. This gives you 'real time' output, so you can directly see how the driver reacts to the tool.

Bringing the pen or an eraser in and out of proximity should show you what the output should be like. First an ID packet, then a bunch of pen packets, then an out of proximity packet. It prints the header of every received packet as well.

Please paste the relevant section of the dmesg when doing this test with the airbrush here (or upload to something like pastebin.com if its too big).

One thing I just thought of, you can try resetting the tablet (by killing and starting inputattach again) and bringing the different tools in proximity in different 'orders'.
For example, reset and bring the airbrush in prox as the very first tool. See what happens.
Then, reset and bring pen in prox first, then airbrush (then pen again -- still working?).
Reset and reverse the order: first airbrush, then pen (then airbrush again -- working now?).
See if something different happens in the dmesg.

All I have had time for tonight is compiling and installing your code and bringing the airbrush tip (the stylus end) in, moving it around, and out 2 or 3 times.

BTW, the cursor did not react to the airbrush even though it was the first tool on the tablet after a reboot with the newly compiled module.

/var/log/messages didn't show anything, I have to pipe dmesg to grep to get this.

Hope the attachment works OK!

Alex

---

### Post by roaldfre on 2011-09-13
That all looks perfectly fine to me. Normally, the events should get sent to the xf86-input-wacom driver.

Can you try running evtest and see if it detects the events? You should be able to install it with the command
```
$ sudo apt-get install evtest
```

Then switch to a tty (ctrl-alt-f2, for instance) and run
```
$ sudo evtest > evtest_dump.txt
```

Then select the number of the wacom device on the prompt.

Bring the airbrush in and out of proximity, hit ctrl-c and upload the evtest_dump.txt file somewhere.

---

### Post by alexcrow on 2011-09-16
> **roaldfre said:**
> That all looks perfectly fine to me. Normally, the events should get sent to the xf86-input-wacom driver.

Can you try running evtest and see if it detects the events? You should be able to install it with the command
```
$ sudo apt-get install evtest
```Then switch to a tty (ctrl-alt-f2, for instance) and run
```
$ sudo evtest > evtest_dump.txt
```Then select the number of the wacom device on the prompt.

Bring the airbrush in and out of proximity, hit ctrl-c and upload the evtest_dump.txt file somewhere.

Here you go, one with just the airbrush tip in and out, the other with in, wheel movements, out, and in with the eraser tip and out again.

Many thanks, sorry for the delay.

ALex

---

### Post by roaldfre on 2011-09-17
Just had a look at those files. Looks like the driver isn't properly sending a BNT_TOOL_AIRBRUSH command. I'll have a look at the data dump you posted earlier and see if I can trace what's happening and figure out why it's not working.

As an aside, I just remembered I hard coded the identifier to be a large Intuos1 model (the one I have). If I can't find any obvious reason for why it's not reporting the BTN_TOOL event, I can try changing that hard coded value and see if that works. (To get that fixed properly, xf86-input-wacom would need to be patched as well.)

[Edit]
Damn, it's probably fixed by now. Just forgot to declare the untested tools (like the airbrush). I've just declared them all now. Commit: [http://github.com/RoaldFre/wacom_serial5/commit/8667efb3aa830e21e4d5b3d03e49eb816307d35c](http://github.com/RoaldFre/wacom_serial5/commit/8667efb3aa830e21e4d5b3d03e49eb816307d35c)

---

### Post by alexcrow on 2011-09-17
> **roaldfre said:**
> Just had a look at those files. Looks like the driver isn't properly sending a BNT_TOOL_AIRBRUSH command. I'll have a look at the data dump you posted earlier and see if I can trace what's happening and figure out why it's not working.

As an aside, I just remembered I hard coded the identifier to be a large Intuos1 model (the one I have). If I can't find any obvious reason for why it's not reporting the BTN_TOOL event, I can try changing that hard coded value and see if that works. (To get that fixed properly, xf86-input-wacom would need to be patched as well.)


OK, thanks very much.

If you are in the UK, I could always pack up the Intuos2 and send it to you!

Cheers

Alex

---

### Post by roaldfre on 2011-09-17
Looks like I was a bit too late in editing that previous post. Just so you don't miss it, check git(hub) for the latest version. Hopefully the airbrush should get recognised, now.

If it works, you can also try to test if the eraser from the airbrush gets recognised as being different from the eraser from the normal pen stylus.

---

### Post by alexcrow on 2011-09-17
> **roaldfre said:**
> Looks like I was a bit too late in editing that previous post. Just so you don't miss it, check git(hub) for the latest version. Hopefully the airbrush should get recognised, now.

If it works, you can also try to test if the eraser from the airbrush gets recognised as being different from the eraser from the normal pen stylus.

OK, will test today or tomorrow.

Cheers

Alex

---

### Post by alexcrow on 2011-09-17
> **alexcrow said:**
> OK, will test today or tomorrow.

Cheers

Alex

Rebuilt from fresh git - for now I can say that the airbrush tip is recognised in that I can use it like the pen. How would I look for the different IDs for the tip and the eraser? evtest?

Cheers

Alex

---

### Post by Favux on 2011-09-17
Sweet, sounds like protocol 5 is close to complete now!

Since its protocol 5 I think if your xf86-input-wacom is recent enough (>0.11.0; *xsetwacom -V*) you should be able to use:
```
xsetwacom get ToolSerialPrevious
```
See *man xsetwacom* and *man wacom*.

---

### Post by alexcrow on 2011-09-18
> **Favux said:**
> Sweet, sounds like protocol 5 is close to complete now!

Since its protocol 5 I think if your xf86-input-wacom is recent enough (>0.11.0; *xsetwacom -V*) you should be able to use:
```
xsetwacom get ToolSerialPrevious
```See *man xsetwacom* and *man wacom*.

Hi, I used this ppa for newer xsever-xorg-input-wacom:

[https://launchpad.net/~irie/+archive/wacom](https://launchpad.net/~irie/+archive/wacom)

I get this:

user@beast:~$ xsetwacom get "Wacom protocol 5 serial tablet stylus" ToolSerialPrevious
0
user@beast:~$ 
user@beast:~$ xsetwacom get "Wacom protocol 5 serial tablet eraser" ToolSerialPrevious
0
user@beast:~

regardless of which tool was previously in proximity.

Cheers

Alex

---

### Post by alexcrow on 2011-09-18
> **alexcrow said:**
> Hi, I used this ppa for newer xsever-xorg-input-wacom:

[https://launchpad.net/~irie/+archive/wacom]("https://launchpad.net/%7Eirie/+archive/wacom")

I get this:

user@beast:~$ xsetwacom get "Wacom protocol 5 serial tablet stylus" ToolSerialPrevious
0
user@beast:~$ 
user@beast:~$ xsetwacom get "Wacom protocol 5 serial tablet eraser" ToolSerialPrevious
0
user@beast:~

regardless of which tool was previously in proximity.

Cheers

Alex


Actually, restarting X fixed the above. I put this:

```
Section "InputClass"
        Identifier "Wacom protocol 5 serial tablet"
        MatchProduct "Wacom protocol 5 serial tablet"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        Option "ToolSerials" "56623267,airbrush,Airbrush"
        Option "Threshold" "15"
        Option "KeepShape" "on"
EndSection

Section "InputClass"
        Identifier "Wacom protocol 5 serial tablet eraser"
        MatchDriver "wacom"
        MatchProduct "tablet eraser"

        # Apply custom Options to this device below.
        Option "PressCurve" "25,0,100,75"
EndSection

Section "InputClass"
        Identifier "Wacom protocol 5 serial tablet stylus"
        MatchDriver "wacom"
        MatchProduct "tablet stylus"
#       Option     "Serial" "42144138"
#
        # Apply custom Options to this device below.
        Option "PressCurve" "25,0,100,75"
EndSection

Section "InputClass"
        Identifier "Wacom protocol 5 serial tablet Airbrush stylus"
        MatchDriver "wacom"
        MatchProduct "Airbrush stylus"
#       Option       "Serial" "56623267"
#
        # Apply custom Options to this device below.
        Option "PressCurve" "25,0,100,75"
EndSection

Section "InputClass"
        Identifier "Wacom protocol 5 serial tablet Airbrush eraser"
        MatchDriver "wacom"
        MatchProduct "Airbrush eraser"
#       Option       "Serial" "56623267"
#
        # Apply custom Options to this device below.
        Option "PressCurve" "25,0,100,75"
EndSection
```

in 50-wacom.conf and now in Gimp the airbrush is now recognised as a separate tool. The wheel on it still seems to do nothing, that could however be an axis setup issue.

I think we are very close to having at least Intuos2 serial tablets fully working again!

Cheers

Alex

---

### Post by Favux on 2011-09-18
That looks recent enough to me (9-4-11).  Not sure why Irie hasn't updated to input-wacom-0.11.1 although that isn't relevant to you.  If you wanted you could clone the git repository.  See [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") part I. or the [LinuxWacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949").  Doubt that would help though.

That looks like the correct command syntax to me.  Using the ID # might be a little more convenient.  It appears to be returning the same "serial number" you would see with a protocol 4 input tool.  In other words that's what I get when I try ToolSerialPrevious with my BambooPT stylus and eraser. With my other input tool (touch) I see it return 1.  A protocol 5 input tool serial number is something like 8 digits long.

So my guess is you are getting a protocol 4 return and aren't seeing a protocol 5 serial number for some reason.  Does *xinput list* give another entry (device name and ID #) for the airbrush?  Could you post your current one?


Edit:  Great!  :D

Your second post renders the above irrelevant.  Now I'm wondering how we would translate the 50-wacom.conf settings into a 52-wacom-options.conf for Xserver 1.10 and up?  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d)  Can we treat the airbrush as a dependent device or is it a parent device like the stylus?

---

### Post by alexcrow on 2011-09-18
> **Favux said:**
> Sweet, sounds like protocol 5 is close to complete now!

Since its protocol 5 I think if your xf86-input-wacom is recent enough (>0.11.0; *xsetwacom -V*) you should be able to use:
```
xsetwacom get ToolSerialPrevious
```See *man xsetwacom* and *man wacom*.

One more thing - a bit odd, I've just noticed the wheel on the puck is inverted. I don't think it was like that before...

---

### Post by alexcrow on 2011-09-18
> **Favux said:**
> 
Edit:  Great!  :D

Your second post renders the above irrelevant.  Now I'm wondering how we would translate the 50-wacom.conf settings into a 52-wacom-options.conf for Xserver 1.10 and up?  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d)  Can we treat the airbrush as a dependent device or is it a parent device like the stylus?

I think what I've posted is already a "dependent device" config. The filename is just a semantic issue from what I see, you could split out all but the first section into 52-blah, or have I got the whole thing wrong? I've just seen creating a new file as a recommendation to prevent the distro upgrades from clobbering your config.

If you notice in all but the first section I key first off the "driver" match rather than the Product. I based it on this:

[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d#Example_Dependent_Device_Static_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d#Example_Dependent_Device_Static_Configuration)

However, like you, I really don't know what counts as a parent in this case, except the above seems to indicate the eraser is also a dependent of stylus. Aargh!

This is so much more confusing that the old way of doing it. The documentation is frankly very bad, even if you did have a USB tablet! Eg this paragraph:

*"Identify each input tool's device name with [xsetwacom list]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom"). We use the MatchDriver tag here to simplify device selection. This  way, we rely on the distribution-wide match tags to apply the right  driver to our device and then only match on those devices that have the  wacom driver applied to them.  However because the xf86-input-wacom  driver appends the input tool type after the server has made the  MatchProduct match we can not use the same match method for the parent  device (stylus).  Instead stylus (tablet wide) options must be applied  to the appropriate snippet in the 50-wacom.conf file or a match similar  to that used in the 52-wacom-options.conf file as shown below. "*

Really is no help at all. Does the example that follows all go in the 50- file or the 52-file, or should it be split between the two?

xinput --list output is:

user@beast:~$ xinput --list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                     id=8    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                     id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 5 serial tablet stylus     id=10   [slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 5 serial tablet eraser     id=12   [slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 5 serial tablet cursor     id=13   [slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 5 serial tablet pad        id=14   [slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 5 serial tablet Airbrush stylus    id=15   [slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 5 serial tablet Airbrush eraser    id=16   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=11   [slave  keyboard (3)]


Cheers

Alex

---

### Post by Favux on 2011-09-18
lol  Are you really critiquing Peter Hutterer's timeless prose?  That's his edit of my stuff to make it clearer.  ;)  Actually it's mostly me.  Seems pellucid to me!  Jeez, gripe, gripe.

What happened is I discovered that X server 1.10 didn't allow configuring the parent device as we thought it would.  It did allow configuring the dependent devices though, finally.  So we had to redo my original stuff for 1.10 since it was wrong.  Oh well.

What follows is a 52-wacom-options.conf but the stylus snippet is a restatement of the 50-wacom.conf usb snipped with stylus options added because the stylus is the parent device of the tablet.


Edit:  How could such an obvious improvement be considered confusing anyway!  ;)

Thanks for the xinput list.  Can't tell for sure whether airbrush is being seen as a parent or dependent.  We're seeing *Wacom protocol 5 serial tablet Airbrush* then with stylus or eraser appended.  So is *Wacom protocol 5 serial tablet Airbrush* the device name and a parent or is Airbrush appended to the parent *Wacom protocol 5 serial tablet*?  Just going to have to test it looks like.  My guess is it is a dependent.  I think only something like the BambooPT which has the kernel exporting the stylus and touch as separate devices can have two parents.  But I'm not 100% sure what tokenrove and roaldfre have done with the wacom_serial.ko.

---

### Post by roaldfre on 2011-09-18
For what it's worth, wacom_serial{4,5}.ko should be identical to a USB Intuos{1,2} tablet after its events have been processed by the xf86-input-wacom driver. We tell xf86-input-wacom that we are USB Intuos tablets.

[Edit] Inverted scroll wheel is now fixed. Looks like xf86-input-wacom inverts the value it gets from USB Intuos tablets, so I now invert it myself when I send it.

---

### Post by alexcrow on 2011-09-18
> **Favux said:**
> lol  Are you really critiquing Peter Hutterer's timeless prose?  That's his edit of my stuff to make it clearer.  ;)  Actually it's mostly me.  Seems pellucid to me!  Jeez, gripe, gripe.

What happened is I discovered that X server 1.10 didn't allow configuring the parent device as we thought it would.  It did allow configuring the dependent devices though, finally.  So we had to redo my original stuff for 1.10 since it was wrong.  Oh well.

What follows is a 52-wacom-options.conf but the stylus snippet is a restatement of the 50-wacom.conf usb snipped with stylus options added because the stylus is the parent device of the tablet.


Edit:  How could such an obvious improvement be considered confusing anyway!  ;)

Thanks for the xinput list.  Can't tell for sure whether airbrush is being seen as a parent or dependent.  We're seeing *Wacom protocol 5 serial tablet Airbrush* then with stylus or eraser appended.  So is *Wacom protocol 5 serial tablet Airbrush* the device name and a parent or is Airbrush appended to the parent *Wacom protocol 5 serial tablet*?  Just going to have to test it looks like.  My guess is it is a dependent.  I think only something like the BambooPT which has the kernel exporting the stylus and touch as separate devices can have two parents.  But I'm not 100% sure what tokenrove and roaldfre have done with the wacom_serial.ko.

OK, Apologies are warranted then - I am not a developer, but in my day job I'm a sysadmin, network and systems architect, and I did find it difficult to understand. However it seems my guess about the 52-wacom.conf file snippets being a reiteration of the declaration in the lower numbered file were correct. Do entries in higher-numbers files overrride those in lower?

Cheers

Alex

---

### Post by Favux on 2011-09-18
Thanks roaldfre.  Scroll wheel has been a pain.  They and the touch strips got inverted at some point.  I thought that had been straightened out.

OK, then from what roaldfre says we have one parent.  So then once we declare the ToolSerials option with something like:
```
        Option "ToolSerials" "42144138,pen;56623267,airbrush"
```
can we use the Serial option to treat the stylus and Airbrush as dependent devices?  If that syntax is correct.  Hmmm, what happens if we try...


Edit:  Just caught your post.  No apology needed.  If you have a better way to say it let me know and I'll fix it.  Yes whatever runs last controls.  Lower numbers run first.  And /etc/X11/xorg.conf.d runs after /usr/share/X11/xorg.conf.d.  This is all my fault anyway.  I pointed out to Peter we were not being good citizens by changing the distro supplied configuration files.

---

### Post by Favux on 2011-09-18
Does the stylus eraser have the same serial number as the stylus?  Does the Airbrush eraser have the same serial number as the Airbrush?

---

### Post by roaldfre on 2011-09-18
That is probably the case. The serial is related to the actual physical tool itself, afaik (at least with my standard pen).

---

### Post by alexcrow on 2011-09-18
> **Favux said:**
> Does the stylus eraser have the same serial number as the stylus?  Does the Airbrush eraser have the same serial number as the Airbrush?

Yes - that is what I saw when swapping the tools and flipping them. The ToolSerial only changed when I swapped the tools. However, I can only speak for my own tools of course. I don't have an "artpen", if indeed that exists for Intuos2, for example.

For all I know, there might be tools that look like this, with a different ID for every prong:

[http://donstuff.files.wordpress.com/2008/10/swissarmymouse.jpg](http://donstuff.files.wordpress.com/2008/10/swissarmymouse.jpg)

Cheers!

Alex

---

### Post by alexcrow on 2011-09-18
> **Favux said:**
> .  If you have a better way to say it let me know and I'll fix it.  Yes whatever runs last controls.  Lower numbers run first.  And /etc/X11/xorg.conf.d runs after /usr/share/X11/xorg.conf.d.  This is all my fault anyway.  I pointed out to Peter we were not being good citizens by changing the distro supplied configuration files.

Thanks,

At the moment I am not capable of thinking out a complete sensible summary of what is happening or how it should be described (eg determination of parent/child devices). I think that when the code is bedded down and I get a chance to test with all the various tools then we can change the documentation.

But perhaps an early start would be to state that "InputClass sections in [/etc/X11/xorg.conf.d|/usr/share/X11/xorg.conf.d] are evaluated in numerical order, with those in /etc/X11/xorg.conf.d being evaluated after all of the sections in /usr/share/X11/xorg.conf.d. Files that are read later may override previously declared options or add new options. We suggest leaving 50-wacom.conf as your distro supplies it to avoid losing your settings when you update or upgrade". This might help to demystify that part of it at least.

BTW, for getting the list of options, it is suggested to use "man wacom". This man page, at least in Natty, seems out of date, ie no mention at all of InputClass.

I know, whinge whinge!

Cheers

Alex

---

### Post by Favux on 2011-09-18
Shoot, I wonder what happened to my Swiss Army knife!  Loved that stupid thing.  :)

OK, given that here is a first pass for a 52-wacom-options.conf for the Intuos2 at /etc/X11/xorg.conf.d.  Assuming of course the 50-wacom.conf at /usr/share/X11/xorg.conf.d is the unchanged distro/xf86-input-wacom supplied version.
```
Section "InputClass"
	Identifier "Wacom Intuos2 options"
	MatchProduct "Wacom"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"

	# Apply custom Options to this device below.
        Option "ToolSerials" "42144138,pen,Stylus;56623267,airbrush,Airbrush"
        Option "Threshold" "15"
        Option "KeepShape" "on"
EndSection

Section "InputClass"
        Identifier "Wacom Intuos2 stylus options"
        MatchDriver "wacom"
        MatchProduct "Stylus stylus"

	# Apply custom Options to this device below.
        Option "PressCurve" "25,0,100,75"
EndSection

Section "InputClass"
        Identifier "Wacom Intuos2 eraser options"
        MatchDriver "wacom"
        MatchProduct "Stylus eraser"

        # Apply custom Options to this device below.
        Option "PressCurve" "25,0,100,75"
EndSection

Section "InputClass"
        Identifier "Wacom Intuos2 Airbrush options"
        MatchDriver "wacom"
        MatchProduct "Airbrush stylus"

        # Apply custom Options to this device below.
        Option "PressCurve" "25,0,100,75"
EndSection

Section "InputClass"
        Identifier "Wacom Intuos2 Airbrush eraser options"
        MatchDriver "wacom"
        MatchProduct "Airbrush eraser"

        # Apply custom Options to this device below.
        Option "PressCurve" "25,0,100,75"
EndSection

Section "InputClass"
        Identifier "Wacom Intuos2 cursor options"
        MatchDriver "wacom"
        MatchProduct "cursor"

        # Apply custom Options to this device below.
EndSection
```
Be prepared to deal with X breakage!

If I have the syntax right then the *device names* in xinput list should read:
```

Wacom protocol 5 serial tablet Stylus stylus
Wacom protocol 5 serial tablet Stylus eraser
Wacom protocol 5 serial tablet cursor
Wacom protocol 5 serial tablet pad
Wacom protocol 5 serial tablet Airbrush stylus
Wacom protocol 5 serial tablet Airbrush eraser

```

Good point!  So man wacom probably needs an update, have to think about that.  Installing a newer xf86-input-wacom automatically brings along the updated man wacom and man xsetwacom for that version.

Edit:  Still haven't figured out what the Serial option is for.  To assign a different serial number?  Or to assign one if ToolSerialPrevious doesn't return one?

---

### Post by alexcrow on 2011-09-19
> **Favux said:**
> 
Edit:  Still haven't figured out what the Serial option is for.  To assign a different serial number?  Or to assign one if ToolSerialPrevious doesn't return one?

The Option "Serial" "whatever" was required, at least in my case, in /etc/X11/xorg.conf to match the tool to a new tool name back in the day. I had to insert it to make sure I could actually have different options on my airbrush, and again, I think, for apps to see it as a new tool, not just the pen stylus again. I get the feeling it is now irrelevant.

Still no response from my airbrush wheel though, but I think that's not far off.

Cheers

Alex

---

### Post by Favux on 2011-09-19
[QUOTE=alexcrow]The Option "Serial" "whatever" was required, at least in my case, in /etc/X11/xorg.conf to match the tool to a new tool name back in the day.[/QUOTE]
That's right!  Dimly remember doing that a few times now.  Tried to help a Cintiq user translate that into a .fdi come to think of it.  Don't remember if we succeeded but doubt it.  So it might be an xorg.conf only option.  And you're right, essentially deprecated because you'd want to use ToolSerials I would think.

---

### Post by alexcrow on 2011-09-21
> **Favux said:**
> Good point!  So man wacom probably needs an update, have to think about that.  Installing a newer xf86-input-wacom automatically brings along the updated man wacom and man xsetwacom for that version.



Hi,

To clarify, the man from the PPA I used still has all the old Xorg.conf options listed (which is fine) but doesn't have any mentions of, for instance "InputClass", only the Xorg.conf "InputDevice". There is also nothing on matching rules at all.

Cheers

Alex

---

### Post by Favux on 2011-09-21
Thanks, but I'm not sure what if anything they'd let me put in.  That's what I have to think about.  I'm reasonably sure they consider it covered by the *SEE ALSO man xorg.conf* at the bottom.

Man xorg.conf has a INPUTCLASS SECTION in its nightmarishly long self.  That has "InputClass" and matching.  I do notice that *man xorg.conf.d* doesn't work though.  I think that's a bug.  It's probably suppose to pull up the same manual.

So other than the Airbrush scrollwheel how is everything with the Intuos2?  Looking good?

---

### Post by alexcrow on 2011-09-21
> **Favux said:**
> Thanks, but I'm not sure what if anything they'd let me put in.  That's what I have to think about.  I'm reasonably sure they consider it covered by the *SEE ALSO man xorg.conf* at the bottom.

Man xorg.conf has a INPUTCLASS SECTION in its nightmarishly long self.  That has "InputClass" and matching.  I do notice that *man xorg.conf.d* doesn't work though.  I think that's a bug.  It's probably suppose to pull up the same manual.

So other than the Airbrush scrollwheel how is everything with the Intuos2?  Looking good?

Well, GIMP looks OK at least, but I think on a couple of occasions I seem to have got a "stuck down" button while using the wacom tools, and I think once my normal mouse became unresponsive too.

However kexi and krita both are useless, while trying to draw lines and paths I keep getting lines jumping back to the top left of the page (normal Logitech mouse is OK), and both of them managed to crash at least once. Eg if I try to draw a circle, I get segments of a circle with lines darting back to the top left every few seconds. Very odd.

I will get a screenshot when I feel better, a bit ill tonight. :sad:

Cheers

Alex

---

### Post by roaldfre on 2011-09-21
Hmm, so that wheel on the airbrush still isn't working? Strange, your previous evtest dump 'air_in_wheel_eraser_out.log' showed that everything was getting reported like it should.

As far as I can tell, that wheel is an 'absolute' wheel that you can turn all the way to one side, and all the way back. Correct? Can you make an evtest dump where you start off at one extreme and turn it all the way to the other side?


Wrt jumping back to the top left corner of the screen. What tool are you using at that time, and what tools are in proximity? I've had such issues as well when trying to get 'dual channel' to work (protocol5 supports two tools in proximity at the same time, but X basically doesn't know what to do with that, so I've disabled/hacked around that iirc).

---

### Post by alexcrow on 2011-09-22
> **roaldfre said:**
> Hmm, so that wheel on the airbrush still isn't working? Strange, your previous evtest dump 'air_in_wheel_eraser_out.log' showed that everything was getting reported like it should.

As far as I can tell, that wheel is an 'absolute' wheel that you can turn all the way to one side, and all the way back. Correct? Can you make an evtest dump where you start off at one extreme and turn it all the way to the other side?


Wrt jumping back to the top left corner of the screen. What tool are you using at that time, and what tools are in proximity? I've had such issues as well when trying to get 'dual channel' to work (protocol5 supports two tools in proximity at the same time, but X basically doesn't know what to do with that, so I've disabled/hacked around that iirc).

The "jumping" is with just one tool, either the stylus or the airbrush. Actually it jumps in different directions, but mostly up or left. The attached image is me trying to draw a circle (came out as an ellipse do to not having adjusted my transformation matrix).

---

### Post by Favux on 2011-09-22
Hi guys,

That is a Qt bug.  I don't think it is related to the wacom_serial5.ko or xf86-input-wacom.  See this Launchpad bug report:  [https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/799202](https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/799202)  See if the linked PNG looks familiar.  Also the link to the other bug report which has the flip side of the Qt bug i.e. pressure problems.

The last post on the thread has a proposed test "fix" to Qt in the PPA.  It drops incoming coordinates that don't have both X&Y reported.  Hoping to localize the Qt problem.

---

### Post by alexcrow on 2011-09-22
> **Favux said:**
> Hi guys,

That is a Qt bug.  I don't think it is related to the wacom_serial5.ko or xf86-input-wacom.  See this Launchpad bug report:  [https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/799202](https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/799202)  See if the linked PNG looks familiar.  Also the link to the other bug report which has the flip side of the Qt bug i.e. pressure problems.

The last post on the thread has a proposed test "fix" to Qt in the PPA.  It drops incoming coordinates that don't have both X&Y reported.  Hoping to localize the Qt problem.

Looks like the bug has now been narrowed down to be in Krita (and hopefully applies to Kexi too).

As for the wheel, I think it's not a big deal as there seems to be no Linux graphics app that can associate more than pressure and tilt with any drawing property. I will provide an event dump for you soon enough though.

Cheers

Alex

---

### Post by alexcrow on 2011-09-23
> **roaldfre said:**
> Hmm, so that wheel on the airbrush still isn't working? Strange, your previous evtest dump 'air_in_wheel_eraser_out.log' showed that everything was getting reported like it should.

As far as I can tell, that wheel is an 'absolute' wheel that you can turn all the way to one side, and all the way back. Correct? Can you make an evtest dump where you start off at one extreme and turn it all the way to the other side?


Wrt jumping back to the top left corner of the screen. What tool are you using at that time, and what tools are in proximity? I've had such issues as well when trying to get 'dual channel' to work (protocol5 supports two tools in proximity at the same time, but X basically doesn't know what to do with that, so I've disabled/hacked around that iirc).

Attached log of airbrush in with wheel all the way down, then wheel moved all the way up (it rolling finger toward the eraser) then back down again.

Cheers

Alex

---

### Post by roaldfre on 2011-09-24
Well, that's the behaviour I'd expect. The driver is correctly sending the commands and the value of the reported wheel is ramping up from the minimum (0) to the correct maximum (1023) and back down again.

How did you come to the conclusion that the wheel does not work? Do you have an application that normally (used to) works (work) with the wheel, and doesn't with this driver?

I know of no other way besides evtest to check if everything is working/getting reported correctly (which seems to be the case here). Maybe Favux knows more?

---

### Post by Favux on 2011-09-24
Hi guys,

What follows is contingent on the current *xinput list* output looking like my guess in post #199.

Huh, this may be the first time I've tried to set up an airbrush scroll wheel.  For Gimp I guess it would be:
```
xsetwacom set "Wacom protocol 5 serial tablet Airbrush stylus" AbsWheelDown "key minus"  # Zoom out
xsetwacom set "Wacom protocol 5 serial tablet Airbrush stylus" AbsWheelUp  "key plus"  # Zoom in
```
Since you're in Europe I assume it is "key plus" rather than "key shift plus" for zoom out for your key map.  This should work in Inkscape too, I don't remember about MyPaint or Krita etc.  Or to control brush size, which is also handy, provided you know how to map the key command in GIMP:
```
xsetwacom set "Wacom protocol 5 serial tablet Airbrush stylus" AbsWheelDown "key alt up"  # Increase brush radius (must be mapped in GIMP)
xsetwacom set "Wacom protocol 5 serial tablet Airbrush stylus" AbsWheelUp "key alt down"  # Decrease brush radius (must be mapped in GIMP)
```
The quotes around the keys aren't needed anymore I leave them in just to delineate things.  Run the commands before starting GIMP.

---

### Post by alexcrow on 2011-09-24
> **Favux said:**
> Hi guys,

What follows is contingent on the current *xinput list* output looking like my guess in post #199.

Huh, this may be the first time I've tried to set up an airbrush scroll wheel.  For Gimp I guess it would be:
```
xsetwacom set "Wacom protocol 5 serial tablet Airbrush stylus" AbsWheelDown "key minus"  # Zoom out
xsetwacom set "Wacom protocol 5 serial tablet Airbrush stylus" AbsWheelUp  "key plus"  # Zoom out
```Since you're in Europe I assume it is "key plus" rather than "key shift plus" for zoom out for your key map.  This should work in Inkscape too, I don't remember about MyPaint or Krita etc.  Or to control brush size, which is also handy, provided you know how to map the key command in GIMP:
```
xsetwacom set "Wacom protocol 5 serial tablet Airbrush stylus" AbsWheelDown "key alt up"  # Increase brush radius (must be mapped in GIMP)
xsetwacom set "Wacom protocol 5 serial tablet Airbrush stylus" AbsWheelUp "key alt down"  # Decrease brush radius (must be mapped in GIMP)
```The quotes around the keys aren't needed anymore I leave them in just to delineate things.  Run the commands before starting GIMP.

OK, I think this clears things up a lot. I thought that the wheel did something in some application before but I guess it was either a fault of my memory or I'd done something like the above quote. I think brush size is a good one to start with, so the next chance I get I'll have a go at it!

I will keep my eye on the k* apps issue as well, but I'm pretty sure it has nothing to do with this topic.

All the best

Alex

---

### Post by Favux on 2011-09-24
Alex the bug report says it is coming through Monday.  I'd take that with a grain of salt but it sounds like the fix will be soon because the patch was accepted.

---

### Post by Gizmoatwork on 2011-10-08
Hi.
I'm here again to test the driver for my serial Intuos 2 tablet (Protocole V).

I try to follow the Readme file.
I've unpacked the "**_[wacom_serial5]("https://github.com/RoaldFre/wacom_serial5")_" ** archive [B].
[/B]Then

```
make all
```But it doesn't seem to work :
```

make all
make -C /lib/modules/2.6.35-22-generic/build M=/home/gizmo/Bureau/wacom_serial modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.35-22-generic »
  CC [M]  /home/gizmo/Bureau/wacom_serial/wacom_serial5.o
/home/gizmo/Bureau/wacom_serial/wacom_serial5.c: In function ‘handle_configuration_response’:
/home/gizmo/Bureau/wacom_serial/wacom_serial5.c:188: error: implicit declaration of function ‘input_abs_set_res’
make[2]: *** [/home/gizmo/Bureau/wacom_serial/wacom_serial5.o] Erreur 1
make[1]: *** [_module_/home/gizmo/Bureau/wacom_serial] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.35-22-generic »
make: *** [all] Erreur 2

```It should produce a *w**acom_serial.ko* file, but it doesn't.
What am I doing wrong ?

---

### Post by Favux on 2011-10-09
Hi again Gizmoatwork,

Thank you for trying.

The wacom_serial5.ko will only compile in Natty or higher, i.e. kernel 2.6.38 or higher.  A new input API dependency was added.  See my little note at the bottom of II. a).

Actually I don't know for sure where the break is, maybe it would compile on 2.6.37?  But definitely not Maverick's 2.6.35 which is the problem you are having.

Sorry.  :(

---

### Post by Gizmoatwork on 2011-10-09
Hi Favux.

Thanks for fast support again !
So I will stick with *xf86-input-wacom-0.10.6* until I update my kernel.

---

### Post by Gizmoatwork on 2011-10-09
Ok, so I get stuck at step I. d.

```
aclocal && automake && autoconf
aclocal: `configure.ac' or `configure.in' is required

```Can you help ?

---

### Post by Favux on 2011-10-09
I believe you are missing autoconf.  When you entered the library command you must have missed some of it.  Make sure you copy and paste the whole thing:
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev

```
Notice how it extends way to the right?

---

### Post by Gizmoatwork on 2011-10-10
No it's not it. I copy the entire line.
When I do so, I have a long message. One line says autoconf is already up to date...

I think I did it incorrectly, or in the incorrect folder. i re-did it, and this time it worked.

---

### Post by Favux on 2011-10-10
Great!

lol.  I just finished running through it again in Maverick and it worked for me too.  So I was going to post asking you for your entire terminal output up until the error.  But you fixed it without me.  :)

---

### Post by thorwil on 2011-10-20
Hi!

I have a serial Intuos 2 that I got working under Ubuntu 10.10 with a downgrade and a patch, as I recall vaguely.

Now I would like to make it work with Oneiric. Went to [https://github.com/RoaldFre/wacom_serial5](https://github.com/RoaldFre/wacom_serial5), followed [http://cipht.net/2011/07/02/wacom_serial-initial-release.html](http://cipht.net/2011/07/02/wacom_serial-initial-release.html) with obvious adjustments, no success. Then I saw the different steps in the first post of this thread. Now I'm confused :)

Briefly grepped for wacom in my logs, saw nothing interesting.

So what are the right steps to take in my case and/or what can I do for diagnosis, please?

---

### Post by Favux on 2011-10-20
Hi thorwill,

You're the first to try in Oneiric that I know of.  Can you try the instructions in the HOW TO using the protocol 5 version i.e. *II. a) Download and compile the protocol 5 wacom_serial5.ko (Intuos and Intuos2 tablets) - by roaldfre*.

Just post the output from the terminal so we can see where it goes wrong if it does.  Oneiric has a new toolchain that basically requires linked libraries at the end of of the compile command.  We'll have to see if that makes a difference.

If you're successful you should see a freshly compiled wacom_serial5.ko.

---

### Post by thorwil on 2011-10-20
I followed the instructions from II b) down, though I chose linuxconsoletools-1.4.2. No problem until:
```
$: inputattach --wacom_v /dev/ttyS0
inputattach: can't set line discipline
```

I then switched to patched linuxconsoletools-1.4.1, now inputattach says nothing and the wacom does not move the pointer.

---

### Post by Favux on 2011-10-20
Try:
```
sudo dmesg | grep ttyS
```
and check and see if the tablet is now on S4.
```
inputattach --wacom_v /dev/ttyS4
```
I'll have to check out the new version of linuxconsoletools.  I wonder if that has Ping's patch in it?

---

### Post by thorwil on 2011-10-20
No, 0 is right:

```
$ sudo dmesg | grep ttyS
[sudo] password for thorwil: 
[    0.316372] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.436542] 00:0f: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1828.508847] serio: Serial port ttyS0
[ 1828.538297] input: Wacom protocol 5 serial tablet as /devices/pnp0/00:0f/tty/ttyS0/serio2/input/input4
```

---

### Post by Favux on 2011-10-20
Did you use:
```
inputattach --wacom_v /dev/ttyS0

```
or?
```
sudo inputattach --wacom_v /dev/ttyS0

```

---

### Post by thorwil on 2011-10-21
Without *sudo*, it complains: *inputattach: can't set line discipline*. With *sudo* it just works now!

I could bet I made an attempt before, with *sudo* (as it did not complain), but no success. Well, main thing is it works! :)

Thanks! Favux, tokenrove, Roaldfre, you people are awesome ;)

---

### Post by Favux on 2011-10-21
Good!  :)  By the way which Intuos2 model do you have?

Say thorwil do you have an airbrush?  If so does its scrollwheel work if you follow the xsetwacom instructions in [this post]("http://ubuntuforums.org/showpost.php?p=11281442&postcount=211")?

Also if you have a mouse is it working?

---

### Post by mpGoodwin on 2011-10-21
OK - here goes

Favux

I've followed your excellent collections of net wisdom over several threads here on Ubuntu Forums, and had high hopes that my ageing Artpad II would finally be usable again...

I have installed and compiled as instructed in the Oneiric section, and added the udev rules. I can see my tablet responding when using minicom - so the serial port on /dev/ttyUSB0 has the correct speed settings, but still no joy. I find no trace of wacom in my Xorg.0.log, or in /var/log/udev and have run out of ideas. This thread has unfortunately become so long that apart from reading the first and last pages, I have difficulty finding my way around - but was heartened by thorwils sucess.

What do I do - what do I get to attach to provide any leads?

Martin

---

### Post by Favux on 2011-10-21
Hi mpGoodwin,

Welcome to Ubuntu forums and the thread!

Assuming all went well with the compiling it may be your serial to usb convertor.  Some of them need their kernel driver patched.  Which one do you have?  As much detail as possible please.

---

### Post by mpGoodwin on 2011-10-21
Well...

lsusb gives me:
```

Bus 008 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port

```

stty -F /dev/ttyUSB0 -a yields
```

speed 9600 baud; rows 0; columns 0; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>; eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S;
susp = ^Z; rprnt = ^R; werase = ^W; lnext = ^V; flush = ^O; min = 1; time = 0;
-parenb -parodd cs8 hupcl -cstopb cread clocal -crtscts
-ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr icrnl ixon -ixoff -iuclc -ixany -imaxbel -iutf8
opost -olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
isig icanon iexten echo echoe echok -echonl -noflsh -xcase -tostop -echoprt echoctl echoke

```

and if i start minicom (pointed at /dev/ttyUSB0) i can see activity when I move the stylus over the pad.

---

### Post by Favux on 2011-10-21
Alright, I think, if I recall correctly, that the PL2303 patch made it into the kernel.  If so I assume it's at least in the 3.0 kernel.  See post #119 & 120:  [http://ubuntuforums.org/showthread.php?p=11098431](http://ubuntuforums.org/showthread.php?p=11098431)

What do you see with?
```
sudo dmesg | grep ttyUSB
```

---

### Post by mpGoodwin on 2011-10-21
I have been looking around the forums with some of the searching tools that seem to become available when you log in - and found your comment to rBrown3rd: [http://ubuntuforums.org/showthread.php?p=9214358&highlight=artpad#post9214358](http://ubuntuforums.org/showthread.php?p=9214358&highlight=artpad#post9214358)
that it was unlikely to work for the very old generation that Artpad II is. I wonder if it would be possible for someone only half trained in C to write up a protocol converter.

---

### Post by mpGoodwin on 2011-10-21
sudo dmesg | grep ttyUSB
```
[   10.652400] usb 8-1: pl2303 converter now attached to ttyUSB0

```

---

### Post by mpGoodwin on 2011-10-21
Yep, kernel 3.0.0.12 - most recent Oneiric

---

### Post by Favux on 2011-10-21
That reply doesn't apply anymore thanks to the serial driver patch for xf86-input-wacom or the new wacom_serial.ko's.

If you are interested the protocol is here:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Serial_Protocol_IV](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Serial_Protocol_IV)  by tokenrove on the DeveloperPages:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:DeveloperPages](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:DeveloperPages)

Alright and the pl2303 module must be loading and in *lsmod*.  Is the wacom_serial.ko in there also?

---

### Post by mpGoodwin on 2011-10-21
```
lsmod | grep wacom
``` yields nothing, 

*modprobe wacom* followed by *lsmod | grep wacom*
```

wacom                  37975  0 

```
So there was a problem getting the module loaded...

---

### Post by mpGoodwin on 2011-10-21
And of course followed by *sudo modprobe wacom_serial* and that is then present in the lsmod too:
```

wacom_serial           12702  0 
wacom                  37975  0 

```
. The tablet still does not seem to move my pointer or appear in system settings (this is then Kubuntu, where differences may apply)

---

### Post by mpGoodwin on 2011-10-21
Just to be specific - I followed alternative I in the HOWTO - thinking that the old Artpad would be more likely to be version 4 than 5...

EDIT: 
the alternative is not numbered - I used the first alternative given.

---

### Post by Favux on 2011-10-21
Well the *wacom* is wacom.ko and that's for usb tablets.  The wacom_serial is what you want to see and that should be loaded when you use the inputattach command.  So that could be the problem.  What are you using?  And did you see the convertor's module too?

I believe only the Intuos and Intuos2 are protocol v.

---

### Post by mpGoodwin on 2011-10-21
Ah - so step b) was not part of alternative two - there is some stuff to do yet :-)

---

### Post by mpGoodwin on 2011-10-21
Maybe I'm just thick, but I cannot find references to the actual patch files themselves... It is getting quite late here - if that serves as an excuse

---

### Post by Favux on 2011-10-21
The patch for inputattach is in the folder you downloaded from tokenrove.  Not enough coffee is always an excuse in my book.  :)

---

### Post by mpGoodwin on 2011-10-21
There - now it actually works - at least the moving about of the system pointer.

It did not seem to find the inputattach that I put into /etc/rc.local... but just being able to put it in at the command line is a lot better than I thought I'd get tonight.

Now to try out what the gimp can do with this new toy.

---

### Post by Favux on 2011-10-21
Congratulations.  Almost there.  :)  I wonder if the convertor has something to do with that?

Regarding Gimp, you might need to update to 2.7.  See this Launchpad bug report:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154)  Ubuntu sort of shot itself in the foot with Oneiric and graphics tablets maybe.


Edit:  Oh and you should contact tokenrove by e-mail using the link on his site to report that you have an Artpad working and how it does.

---

### Post by mpGoodwin on 2011-10-21
That may be - but as I mentioned I am running Kubuntu, and there far worse things happen at sea - the browser has been extremely unstable while trying to get all these downloads. The mail client no longer keeps track of un/read messages, sigh, but all good things come to those who wait (and file bug reports) :)

If you are ever passing by in my neck of the woods (Copenhagen) I'll buy you your choice of beverage

---

### Post by thorwil on 2011-10-22
> **Favux said:**
> Good!  :)  By the way which Intuos2 model do you have?

Say thorwil do you have an airbrush?  If so does its scrollwheel work if you follow the xsetwacom instructions in [this post]("http://ubuntuforums.org/showpost.php?p=11281442&postcount=211")?

Also if you have a mouse is it working?

Ooh, I don't remember how they called it, but it's close to 30 x 30 cm. I got it cheap, used but good as new directly from Wacom. That's also the reason it's serial :)

No airbrush, but the mouse (which I had to dug out of a drawer, as I never use it) does work.

---

### Post by Favux on 2011-10-22
Great another confirmation that the Wacom tablet mouse works for roaldfre!

I think he's got it all working.  Maybe even the airbrush scrollwheel.  Just need verification on that.  Which would mean he is ready to submit it to the kernel and to the Linux Console Project.

The newer tablets have the model numbers on a sticker on the back of the tablet.  By any chance does your serial tablet have a similar sticker?

---

### Post by luminol on 2011-10-22
Got an Intuous 2 (XD-0912-R) working under Natty with roaldfre's protocol V driver.

Don't know if it makes a difference, but on the inputattach command, I used one dash instead of two i.e.

```
inputattach -wacom_v /dev/ttyUSB0
```

instead of

```
inputattach --wacom_v /dev/ttyUSB0
```

Also, fwiw "Wacom 5 protocol serial tablet driver" now shows up as an option alongside my Nvidia drivers in Additional Drivers under Settings.

---

### Post by Favux on 2011-10-22
Hi again luminol.  Great!  :D

So you got the ch341.ko working?  Did you have to patch it?
> on the inputattach command, I used one dash instead of two
So did two dashes also work?  Sometimes syntax is not so strict depending on how it is coded so you can use a variant.  For example xinput has gone from requiring dash(es) to allowing just the option or switch as has xsetwacom.
> Also, fwiw "Wacom 5 protocol serial tablet driver" now shows up as an option alongside my Nvidia drivers in Additional Drivers under Settings. 
lol  Don't know what that means!  I think that's a question for roaldfre and tokenrove.

I assume if you have one your Wacom tablet mouse works?  Also if you have an airbrush it would be very good if you could test the scrollwheel.

---

### Post by thorwil on 2011-10-22
> **Favux said:**
> The newer tablets have the model numbers on a sticker on the back of the tablet.  By any chance does your serial tablet have a similar sticker?

Ah, yes:
Model: GD-1212-R
       *GD-1212-R00*

---

### Post by Favux on 2011-10-22
Thanks thorwil.

---

### Post by luminol on 2011-10-23
> **Favux said:**
> Hi again luminol.  Great!  :D

So you got the ch341.ko working?  Did you have to patch it?

So did two dashes also work?  Sometimes syntax is not so strict depending on how it is coded so you can use a variant.  For example xinput has gone from requiring dash(es) to allowing just the option or switch as has xsetwacom.

I assume if you have one your Wacom tablet mouse works?  Also if you have an airbrush it would be very good if you could test the scrollwheel.

Didn't have to patch for the ch341. Followed all the steps for protocol V under Natty (a new Xubuntu install, actually) and it all worked out of the box. This is my least painful wacom installation to date.

Tried two dashes on inputattach and it works the same.

The tablet mouse moves the cursor but the buttons don't work. Don't own an airbrush.

---

### Post by Favux on 2011-10-23
> This is my least painful wacom installation to date.
Cool.
> Tried two dashes on inputattach and it works the same.
Thanks for looking into that.
> The tablet mouse moves the cursor but the buttons don't work.
They should by default.  We may want to ask roaldfre to look at that.  What is the output of *xinput list* and *xsetwacom list* in a terminal?
> Don't own an airbrush.
Shoot.  Still need someone to verify the airbrush scrollwheel.

---

### Post by dreh on 2011-10-24
Hi Favux, tokenrove et al
I finally upgraded from maverick to oneiric (I hope I ever get used to unity...sigh). Unfortunately my 3D package is making problems ... blablabla.
But fortunatly my Wacom Digitizer II works (basicly) with tokenroves driver. Eraser is still acting funny but stylus works like a charm.
Ty all for your work
dreh

---

### Post by Favux on 2011-10-24
Hi dreh,

Thanks for letting us know.  :)  I'll add your name to the successful Oneiric testers of course.

---

### Post by luminol on 2011-10-25
> **Favux said:**
> 
We may want to ask roaldfre to look at [the tablet mouse not working] .  What is the output of *xinput list* and *xsetwacom list* in a terminal?

*xinput list* comes back with

```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 5 serial tablet eraser   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 5 serial tablet cursor   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 5 serial tablet pad      	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 5 serial tablet stylus   	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]

```

*xsetwacom list* comes back with

```
Wacom protocol 5 serial tablet eraser	id: 10	type: ERASER    
Wacom protocol 5 serial tablet cursor	id: 11	type: CURSOR    
Wacom protocol 5 serial tablet pad	id: 12	type: PAD       
Wacom protocol 5 serial tablet stylus	id: 13	type: STYLUS  
```

Also, beware! I installed Gimp 1.7.3 unstable from ppa:matthaeus123/mrw-gimp-svn and the tablet stopped working, coming up with "Device is busy" on /dev/ttyUSB0.

I purged 1.7.3, reinstalled Gimp from the Ubuntu repos, re-setup the wacom and things are back to normal.

---

### Post by Favux on 2011-10-25
Weird, hope it is an unstable bug.

OK, let's see what button maps X input and wacom sees for the mouse.
```
xinput list-props "Wacom protocol 5 serial tablet cursor"
```
and
```
xsetwacom get "Wacom protocol 5 serial tablet cursor" all
```

---

### Post by luminol on 2011-10-26
> **Favux said:**
> Weird, hope it is an unstable bug.

OK, let's see what button maps X input and wacom sees for the mouse.
```
xinput list-props "Wacom protocol 5 serial tablet cursor"
```
and
```
xsetwacom get "Wacom protocol 5 serial tablet cursor" all
```

xinput is:

```
Device 'Wacom protocol 5 serial tablet cursor':
	Device Enabled (121):	1
	Coordinate Transformation Matrix (123):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (239):	0
	Device Accel Constant Deceleration (240):	1.000000
	Device Accel Adaptive Deceleration (241):	1.000000
	Device Accel Velocity Scaling (242):	10.000000
	Wacom Tablet Area (262):	0, 0, 30480, 24060
	Wacom Rotation (263):	0
	Wacom Serial IDs (265):	36, 0, 6, 0
	Wacom Proximity Threshold (277):	10
	Wacom Capacity (266):	-1
	Wacom Pressure Threshold (267):	27
	Wacom Sample and Suppress (268):	2, 4
	Wacom Enable Touch (269):	0
	Wacom Enable Touch Gesture (270):	0
	Wacom Touch Gesture Parameters (271):	50, 20, 250
	Wacom Tool Type (272):	"CURSOR" (8)
	Wacom Button Actions (273):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
	Wacom Debug Levels (274):	0, 0
```

xsetwacom is

```
Option "Area" "0 0 30480 24060"
Option "ToolDebugLevel" "0"
Option "TabletDebugLevel" "0"
Option "Suppress" "4"
Option "RawSample" "2"
Property 'Wacom Pressurecurve' does not exist on device.
Option "Mode" "Absolute"
Property 'Wacom Hover Click' does not exist on device.
Option "Touch" "off"
Option "Gesture" "off"
Option "ZoomDistance" "50"
Option "ScrollDistance" "20"
Option "TapTime" "250"
Option "Capacity" "-1"
Option "CursorProximity" "10"
Option "Rotate" "none"
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Option "RawFilter" "on"
Option "Threshold" "27"
Option "ToolID" "8"
Option "ToolSerial" "0"
Option "TabletID" "36"
```

---

### Post by Favux on 2011-10-26
Hmmm.  Xinput is claiming the puck/cursor buttons do nothing i.e. aren't assigned:
```
Wacom Button Actions (273):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)

```
But at least you have 16 buttons available!  Unfortunately xsetwacom all didn't tell us what button mapping xsetwacom is seeing.  So we'll have to get them one at a time.  Enter these three commands:
```

xsetwacom get "Wacom protocol 5 serial tablet cursor" Button 1
xsetwacom get "Wacom protocol 5 serial tablet cursor" Button 2
xsetwacom get "Wacom protocol 5 serial tablet cursor" Button 3

```
and post the output associated with each button.  There are 3 buttons correct?  Is the middle button clicking the scroll wheel?  Depending on what we see could try mapping the puck buttons with either xsetwacom (or Options in a xorg.conf.d wacom.conf?) or xinput.

---

### Post by mpGoodwin on 2011-10-30
I've noticed that the inputattach command to be put in rc.default does not work on my system - unless I append a "&" to the line, allowing it to return. This might be good for the HOWTO on the first page

I furthermore have yet to see the eraser on my pen moving the pointer, much less actually erasing anything in krita or Gimp. (The Gimp is still quite useless in Oneiric as the pen is not used as such by default, and when enabled (in windowed mode) it keeps jumping to the top and right hand side - smearing the drawing)

---

### Post by luminol on 2011-10-30
> **Favux said:**
> Hmmm.  Xinput is claiming the puck/cursor buttons do nothing i.e. aren't assigned:
```
Wacom Button Actions (273):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)

```
But at least you have 16 buttons available!  Unfortunately xsetwacom all didn't tell us what button mapping xsetwacom is seeing.  So we'll have to get them one at a time.  Enter these three commands:
```

xsetwacom get "Wacom protocol 5 serial tablet cursor" Button 1
xsetwacom get "Wacom protocol 5 serial tablet cursor" Button 2
xsetwacom get "Wacom protocol 5 serial tablet cursor" Button 3

```
and post the output associated with each button.  There are 3 buttons correct?  Is the middle button clicking the scroll wheel?  Depending on what we see could try mapping the puck buttons with either xsetwacom (or Options in a xorg.conf.d wacom.conf?) or xinput.

Results are 1, 2 and 3, respectively.

This mouse has 4 buttons, 5 if you count the middle-click on the scroll wheel.

Changed monitors and the tablet stopped working again. Ran through the install and it was back to normal. Easily fixed, but I would like to know what's causing that.

---

### Post by royleith on 2011-11-03
Oneiric with Intuos (the first series) and wacom_serial5.ko,

Having got the pen to work in Lucid Lynx I tried again with Oneiric. At first I tried with xorg.conf and then with 52-wacom-options.

I won't bore you with the journey, but the driver disappeared and I had to insmod it back. With configuration in either xorg.conf or 52-wacom-options the mouse (cursor) moves around as with Lucid, but the buttons don't work. I hate using the mouse and so this is a great bonus! 

The pen and stylus have a major drawback. The first time I got it going, Gimp defaulted to the pen being paintbrush and the eraser being eraser. The pen worked with pressure sensitivity, but the pen trace kept darting back to random co-ordinates down the left-hand-side leaving a tracery of lines in the image. The erase seems to work as intended.

Neither pen nor eraser work as left-click and thus neither stylus nor erase can be assigned to another tool in Gimp. The second time I got it working (via 52-wacom-options) the pen had defaulted to the 'Move' tool. It moves the image, but it no longer darts to a L-H-S co-ordinate.

xsetwacom is working fine and lists the device. However, I don't know if any of the settings will restore correct stylus and eraser operation. I am wondering if setting one of the buttons to emulate a left-click would be a short term work-around.

> :~$ xsetwacom get "Wacom protocol 5 serial tablet stylus" Button 1
button +1 
:~$ xsetwacom get "Wacom protocol 5 serial tablet stylus" Button 2
button +1 
:~$ xsetwacom get "Wacom protocol 5 serial tablet stylus" Button 3
button +3 
:~$ xsetwacom get "Wacom protocol 5 serial tablet eraser" Button 1
button +1 
:~$ xsetwacom get "Wacom protocol 5 serial tablet eraser" Button 2
button +1 
:~$ xsetwacom get "Wacom protocol 5 serial tablet eraser" Button 3
button +3 


The top position of the (rocking) pen button works as a right-hand mouse click. The bottom position is being detected, but I am not quite sure what it is emulating. Both the touch of the stylus/eraser and the operation of the lower button act to pull down menus and 'select' menu items. They also appear to 'operate' the Gimp tool icons, but no tool icon nor menu item can actually be launched. 

It is the same with the desktop and other programs. Clicking on the KDE 'K' (menu) button brings up the 'Favourite' applications and the icons can be 'rolled over', but a tap on an icon fails to launch the application. A tap, or the lower button, will cause a slight shake of the selection, but that is all.

I never worked out how the buttons were numbered in xsetwacom and so I have sent the results for the first three in the hope that I have covered both.

Any observations gratefully received.

Regards
Roy Leith

---

### Post by Favux on 2011-11-03
Hi mpGoodwin,

The ampersand fix is now in the HOW TO, thanks.


@ mpGoodwin and royleith,

There is a bug, call it the Button 1 1 bug, in current xf86-input-wacoms.  This is because a button release function that xsetwacom uses in wcmCommon.c didn't get a name update in the big switch over to valuators a while ago.  This causes that rapid cursor jump.  So if you use a xsetwacom set command with Button 1 1 for the stylus or eraser, i.e.:
```
xsetwacom set "stylus device name" Button 1 1
```
You break left click and if you grab a window and move it it flies off when released.

Since Button 1 1 for the stylus tip and eraser are the driver defaults there is really no reason to restate them in xsetwacom commands.  So if you've done that just comment them out or remove them as a temporary fix.  To actually fix it go into the xf86-input-wacom source code before you compile it (appendix 1).  In wcmCommon.c around line #258 change:
```
						xf86PostButtonEvent(pInfo->dev,
```
to
```
						xf86PostButtonEventP(pInfo->dev,
```
So it reads like:
```
 					if (countPresses(btn_no, &keys[i], nkeys - i))
						xf86PostButtonEventP(pInfo->dev,
 								is_absolute(pInfo), btn_no,
 								0, first_val, num_val,
 								VCOPY(valuators, num_val));
```
Yep, it was a 'P' that was left out.  Then go ahead and compile it.


@ luminol and royleith,

Alright, that's two Intuous' using wacom_serial5.ko's where the mouse buttons don't work and one where they do.  Unless the above fix fixes your buttons we'll need to ask Roadlfre to take a look at this.

Also because Button's 4 through 7 are reserved for scrolling (Buttons 4 & 5 for vertical and 6 & 7 for horizontal) the Button assignments might be 1, 2, 3, 8, etc.  But Buttons 1 though 3 should be unaffected on the puck.


Hi royleith,

Your other issue in Gimp is a known bug in Oneiric.  See:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154).  Deevad says using the 'Xorg Edger' ppa fixes it.  If true then hopefully an update that will fix this bug is pending.  Sure hope so.

With the stylus side buttons Button 2 is middle click (2) and Button 3 is right click (3).  After user request they actually reversed the assignments in the driver with Button 2 3 and Button 3 2, since most people like it that way.

I think that's most of your issues.

---

### Post by royleith on 2011-11-05
@Favux

Yes, Yes, YES!... erm, yes it worked. 

I recompiled the wcmCommon.c in the patched version of xf86-input-wacom after adding the 'P'. In my file the code you quoted did not appear and so I just did the reckless thing and modified all nine appearances of the phrase xf86PostButtonEvent.

Now, stylus and eraser work fine. I launched Gimp with the pen and started a new document. The Gimp problem was still there just as reported in the bugs page you quoted.

The puck has not changed. It moves the cursor around, but none of the buttons work. Please don't put it right or I will have to start using it, again.

I'm not too fretful about the Gimp problem, atm, as I have a more major problem with my various Oneiric installs: I cannot get my HP laser printer to work. Yes, I cannot get a Postscript printer to work on Linux!

Anyway, many congrats on the Wacom serial tablet front and on the Bamboo front, as well. 

Regards
Roy Leith

---

### Post by thorwil on 2011-11-06
As reported, I had my serial Intuos 2 working in Oneiric ... until today.

Yesterday it still worked, now the tablet is ignored. A manual ```
inputattach
``` is answered with ```
inputattach: device initialization failed
```.

The only changes on my system I'm aware of are a bunch of updates, mainly of project-neon packages from a PPA. All KDE related, only installed to take a look at the recent Krita Beta. As far as I can tell, there hasn't been any single update to any xserver related package. Still the same kernel version. I checked the cable and plug, seems to be fine.

Any ideas?

Xorg.0.log contains:
```
[    24.278] (II) config/udev: Adding input device Wacom protocol 5 serial tablet (/dev/input/mouse1)
[    24.278] (II) No input driver/identifier specified (ignoring)
[    24.278] (II) config/udev: Adding input device Wacom protocol 5 serial tablet (/dev/input/event4)
[    24.278] (**) Wacom protocol 5 serial tablet: Applying InputClass "evdev tablet catchall"
[    24.278] (**) Wacom protocol 5 serial tablet: Applying InputClass "Wacom class"
[    24.278] (II) LoadModule: "wacom"
[    24.279] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    24.294] (II) Module wacom: vendor="X.Org Foundation"
[    24.294] 	compiled for 1.10.4, module version = 0.11.0
[    24.294] 	Module class: X.Org XInput Driver
[    24.294] 	ABI class: X.Org XInput driver, version 12.3
[    24.294] (II) Using input driver 'wacom' for 'Wacom protocol 5 serial tablet'
[    24.294] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    24.294] (**) Wacom protocol 5 serial tablet: always reports core events
[    24.294] (**) Option "Device" "/dev/input/event4"
[    24.294] (II) Wacom protocol 5 serial tablet: type not specified, assuming 'stylus'.
[    24.294] (II) Wacom protocol 5 serial tablet: other types will be automatically added.
[    24.294] (--) Wacom protocol 5 serial tablet stylus: using pressure threshold of 27 for button 1
[    24.295] (--) Wacom protocol 5 serial tablet stylus: Wacom USB Intuos1 tablet maxX=30480 maxY=31680 maxZ=1023 resX=100000 resY=100000  tilt=enabled
[    24.295] (II) Wacom protocol 5 serial tablet stylus: hotplugging dependent devices.
[    24.295] (II) Wacom protocol 5 serial tablet stylus: hotplugging completed.
[    24.328] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0f/tty/ttyS0/serio2/input/input4/event4"
[    24.328] (II) XINPUT: Adding extended input device "Wacom protocol 5 serial tablet stylus" (type: STYLUS)
[    24.328] (**) Wacom protocol 5 serial tablet stylus: (accel) keeping acceleration scheme 1
[    24.328] (**) Wacom protocol 5 serial tablet stylus: (accel) acceleration profile 0
[    24.328] (**) Wacom protocol 5 serial tablet stylus: (accel) acceleration factor: 2.000
[    24.328] (**) Wacom protocol 5 serial tablet stylus: (accel) acceleration threshold: 4
[    24.328] (**) Wacom protocol 5 serial tablet eraser: Applying InputClass "evdev tablet catchall"
[    24.328] (**) Wacom protocol 5 serial tablet eraser: Applying InputClass "Wacom class"
[    24.328] (II) Using input driver 'wacom' for 'Wacom protocol 5 serial tablet eraser'
[    24.328] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    24.328] (**) Wacom protocol 5 serial tablet eraser: always reports core events
[    24.328] (**) Option "Device" "/dev/input/event4"
[    24.328] (--) Wacom protocol 5 serial tablet eraser: Wacom USB Intuos1 tablet maxX=30480 maxY=31680 maxZ=1023 resX=100000 resY=100000  tilt=enabled
[    24.344] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0f/tty/ttyS0/serio2/input/input4/event4"
[    24.344] (II) XINPUT: Adding extended input device "Wacom protocol 5 serial tablet eraser" (type: ERASER)
[    24.344] (**) Wacom protocol 5 serial tablet eraser: (accel) keeping acceleration scheme 1
[    24.344] (**) Wacom protocol 5 serial tablet eraser: (accel) acceleration profile 0
[    24.344] (**) Wacom protocol 5 serial tablet eraser: (accel) acceleration factor: 2.000
[    24.344] (**) Wacom protocol 5 serial tablet eraser: (accel) acceleration threshold: 4
[    24.344] (**) Wacom protocol 5 serial tablet cursor: Applying InputClass "evdev tablet catchall"
[    24.344] (**) Wacom protocol 5 serial tablet cursor: Applying InputClass "Wacom class"
[    24.344] (II) Using input driver 'wacom' for 'Wacom protocol 5 serial tablet cursor'
[    24.344] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    24.344] (**) Wacom protocol 5 serial tablet cursor: always reports core events
[    24.344] (**) Option "Device" "/dev/input/event4"
[    24.344] (--) Wacom protocol 5 serial tablet cursor: Wacom USB Intuos1 tablet maxX=30480 maxY=31680 maxZ=1023 resX=100000 resY=100000  tilt=enabled
[    24.360] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0f/tty/ttyS0/serio2/input/input4/event4"
[    24.360] (II) XINPUT: Adding extended input device "Wacom protocol 5 serial tablet cursor" (type: CURSOR)
[    24.360] (**) Wacom protocol 5 serial tablet cursor: (accel) keeping acceleration scheme 1
[    24.360] (**) Wacom protocol 5 serial tablet cursor: (accel) acceleration profile 0
[    24.360] (**) Wacom protocol 5 serial tablet cursor: (accel) acceleration factor: 2.000
[    24.360] (**) Wacom protocol 5 serial tablet cursor: (accel) acceleration threshold: 4
[    24.360] (**) Wacom protocol 5 serial tablet pad: Applying InputClass "evdev tablet catchall"
[    24.360] (**) Wacom protocol 5 serial tablet pad: Applying InputClass "Wacom class"
[    24.360] (II) Using input driver 'wacom' for 'Wacom protocol 5 serial tablet pad'
[    24.360] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    24.360] (**) Wacom protocol 5 serial tablet pad: always reports core events
[    24.360] (**) Option "Device" "/dev/input/event4"
[    24.360] (--) Wacom protocol 5 serial tablet pad: Wacom USB Intuos1 tablet maxX=30480 maxY=31680 maxZ=1023 resX=100000 resY=100000  tilt=enabled
[    24.376] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0f/tty/ttyS0/serio2/input/input4/event4"
[    24.376] (II) XINPUT: Adding extended input device "Wacom protocol 5 serial tablet pad" (type: PAD)
[    24.376] (**) Wacom protocol 5 serial tablet pad: (accel) keeping acceleration scheme 1
[    24.376] (**) Wacom protocol 5 serial tablet pad: (accel) acceleration profile 0
[    24.376] (**) Wacom protocol 5 serial tablet pad: (accel) acceleration factor: 2.000
[    24.376] (**) Wacom protocol 5 serial tablet pad: (accel) acceleration threshold: 4
[    28.744] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[    39.347] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[    45.457] (II) XKB: reuse xkmfile /var/lib/xkb/server-CAD9C38809CD0DACE973EEC3AFC1B3B2536F9F90.xkm
```

---

### Post by thorwil on 2011-11-07
As sudden as it stopped working yesterday, it's working again today. I guess this suggests a loose contact, rather than a software problem.

Sorry for the noise!

---

### Post by odd on 2011-11-09
@Favux: You mentioned something about Wacom Airbrush verifying? I own one since today. I'll be glad to help.

My setup:
- Ubutnu Lucid 64bit 2.6.32-34-generic #77-Ubuntu SMP
- Oneiric 64bit (up-to-date)
- Wacom Intuos3 6x4" (PTZ-630)
- Wacom Airbrush (ZP-400E-01A)

I'm not sure which linuxwacom ver. I have on Lucid, I did some fu*k-up recently, but I guess I'm back to 0.10.5-0ubuntu4 (with macroos-1.8-things from HOW-TO I did some while ago, if that makes any difference).

Grip-pen works, Airbrush coords went crazy after reboot, reported constant scrollwheel while in range (when I (re?)installed 0.10.5), but now seems to work... except the wheel...
xsetwacom list & xinput list don't see Airbrush device.

Same on Oneiric (no airbrush wheel) (I've got default linuxwacom there from distro repos, did't mess around anything there (yet:))

Any ideas how to make the wheel work on Lucid at least?

---

### Post by Favux on 2011-11-09
Hi odd, thanks for volunteering for airbrush testing.  Just to be sure your Intuos3 is serial not usb?  So the first 3's were also serial tablets?

What we're interested in is does roaldfre's wacom_serial5.ko get the airbrush's scrollwheel working.  He thinks his most recent changes should have done the trick.  My guess is you need some xsetwacom commands to get it working.  I make a stab at it in post #211:  [http://ubuntuforums.org/showthread.php?t=1780154&page=22](http://ubuntuforums.org/showthread.php?t=1780154&page=22)

These should also apply to the old serial patch to 0.10.6 for Lucid.  And a usb tablet for that matter.  Although I'm not sure if the Lucid default 0.10.5 would handle it correctly.

---

### Post by odd on 2011-11-09
> **Favux said:**
> Hi odd, thanks for volunteering for airbrush testing.  Just to be sure your Intuos3 is serial not usb?  So the first 3's were also serial tablets?


Aww crap - wrong thread, my bad ;). Mine is USB, so I guess I won't be useful here.

But nevertheless, problem persists in Wacom Intuos3 USB Airbrush pen so... where to look for help? From ubuntuforums search I see that this airbrush toy is either unpopular or problem is not that commont with the wheel.

---

### Post by Favux on 2011-11-11
odd went to another thread.  If we figure out the scrollwheel it should apply the the wacom_serial.ko's because they use the usb code too.  So far everything seems to indicate it's like what I had in post #211, but still not working.


Looking more at the mouse the wacom_serial5.c code:
```
	/* Reset everything, otherwise we lose the initial states
	 * when in-prox next time */
	input_report_abs(dev, ABS_X, 0);
	input_report_abs(dev, ABS_Y, 0);
	input_report_abs(dev, ABS_DISTANCE, 0);
	input_report_abs(dev, ABS_TILT_X, 0);
	input_report_abs(dev, ABS_TILT_Y, 0);
	if (state->tool >= BTN_TOOL_MOUSE) { //XXX not so nice...
		input_report_key(dev, BTN_LEFT, 0);
		input_report_key(dev, BTN_MIDDLE, 0);
		input_report_key(dev, BTN_RIGHT, 0);
		input_report_key(dev, BTN_SIDE, 0);
		input_report_key(dev, BTN_EXTRA, 0);
		input_report_abs(dev, ABS_THROTTLE, 0);
		//input_report_abs(dev, ABS_RZ, 0);
	} else {
		input_report_abs(dev, ABS_PRESSURE, 0);
		input_report_key(dev, BTN_STYLUS, 0);
		input_report_key(dev, BTN_STYLUS2, 0);
		//input_report_key(dev, BTN_TOUCH, 0);
		input_report_abs(dev, ABS_WHEEL, 0);
	}
```
Is essentially identical to the wacom.ko (actually the wacom_wac.c) code.

Roaldfre does say he's tested with his old 5-button mouse on his Intuos1.  In the code he goes on to say:
```
	/* 4D mouse */ //UNTESTED
	if (MOUSE_4D(state->tool_id)) {
		throttle = (((data[5] & 0x07) << 7) |
			(data[6] & 0x7f));
		if (data[8] & 0x08)
			throttle = -throttle;
		input_report_abs(dev, ABS_THROTTLE, throttle);
	}

	/* Lens cursor */
	else if (LENS_CURSOR(state->tool_id)) {
		buttons = data[8];
		send_buttons(dev, buttons, 0);
	}

	/* 2D mouse */ //UNTESTED
	else if (MOUSE_2D(state->tool_id)) {
		buttons = (data[8] & 0x1C) >> 2;
		send_buttons(dev, buttons, 0);

		relwheel = (data[8] & 1) - ((data[8] & 2) >> 1);
		input_report_rel(dev, REL_WHEEL, relwheel);
```
So I guess the "old 5 button mouse" is a Lens cursor type.

But anyway it looks like the Wacom mice should be supported.  So if it is a bug it likely is a minor glitch.

---

### Post by roaldfre on 2011-11-11
> **Favux said:**
> So I guess the "old 5 button mouse" is a Lens cursor type.

That is correct. Here is an image of the model I have: [https://wacom.com/en/Store/Pages/~/media/Images/Products/OlderProducts/GC210_lg.ashx?mw=350]("https://wacom.com/en/Store/Pages/%7E/media/Images/Products/OlderProducts/GC210_lg.ashx?mw=350")

---

### Post by Favux on 2011-11-17
Thanks roaldfre.


Could someone try the new xf86-input-wacom-0.12.0 tar and see if that makes any difference for the airbrush scrollwheel?

---

### Post by luminol on 2011-11-19
I dual boot XP and natty, and (for some reason) /dev/ttyUSB0 has been hanging when I reboot into natty from windows. I haven't been able to reliably reproduce the error yet, but the following seemed to fix it.

Followed the instructions found [here]("http://www.question-defense.com/2009/09/09/how-to-reset-a-serial-port-in-linux-ttys0-ttyam0-etc").

Found the process ID for inputattach thusly:

```
ps -ef | grep tty
```

Which gave me:

```
root      1003     1  0 08:37 tty4     00:00:00 /sbin/getty -8 38400 tty4
root      1008     1  0 08:37 tty5     00:00:00 /sbin/getty -8 38400 tty5
root      1020     1  0 08:37 tty2     00:00:00 /sbin/getty -8 38400 tty2
root      1021     1  0 08:37 tty3     00:00:00 /sbin/getty -8 38400 tty3
root      1025     1  0 08:37 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1031   991  1 08:37 tty7     00:00:14 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-o1VoSB/database -nolisten tcp vt7
root      1253     1  0 08:37 ?        00:00:00 inputattach --wacom_v /dev/ttyUSB0
root      1254     1  0 08:37 tty1     00:00:00 /sbin/getty -8 38400 tty1
ultra7    1702  1676  0 08:53 pts/0    00:00:00 grep tty
```

Killed the offending process, 1253 in my case.

```

sudo kill -9 1253 
```

(The first time I did this, for good measure, I went back and edited /etc/rc.local to make sure I put the missing "&" at the end of the inputattach command.)

From there it was

```
sudo inputattach --wacom_v /dev/ttyUSB0
```

close the terminal window, and the tablet works. And continues working after reboot.

---

### Post by HarM_triade on 2011-12-04
Hello all,
Trying to get my gd-0912-r to work using roaldfre's wacom_serial5.ko.

On using "sudo inputattach --wacom_v /dev/ttyS0", I get nothing i.e. after a while there's a time-out with the following error in dmesg:

[ 7862.367335] input (null): throwing away 32 bytes of garbage
[ 7862.382317] input (null): throwing away 32 bytes of garbage
[ 7862.388104] input (null): Timed out waiting for tablet to respond with model and version.
[ 7862.388134] wacom_serial5: probe of serio391 failed with error -5

The "sudo inputattach --wacom_iv /dev/ttyS0" does nothing either, not even errors or a time-out.

Thus in dmesg:
[ 7862.388104] input (null): Timed out waiting for tablet to respond with model and version.
[ 7862.388134] wacom_serial5: probe of serio391 failed with error -5
[ 8673.901650] serio: Serial port ttyS0

Asuming the first _v is the correct command,
What am I looking at?

---

### Post by Favux on 2011-12-04
Hi HarM_triade,

What release are you using Natty or Oneiric?

Since you appear to have an Intuos then _v is correct.

Are you sure your tablet is on the S0 port?  What did/does:
```
sudo dmesg | grep ttyS

```
show for the port(s) in use?

---

### Post by webbp on 2011-12-23
great work, many thanks for putting this together. doesn't work for me though.

oneiric, cintiq 15x, no usb adapter, just serial. dmesg shows only ttyS0. followed the latest guide carefully.

inputattach hangs forever.

could it be a hardware problem with the serial port on the computer or cintiq?

other suggestions?

many thanks
webb

---

### Post by Favux on 2011-12-23
Hi webbp,

> inputattach hangs forever.
Did you try?
```
inputattach --wacom_iv /dev/ttyS0 &
```

---

### Post by webbp on 2012-01-01
Hi Favux,

Thanks for your reply. I did try:

inputattach --wacom_iv /dev/ttyS0 &

as suggested in the howto. It does not result being able to move the mouse with the Cintiq.

Could you recommend a tool to show the raw serial input from the Cintiq, to determine whether the tablet is actually sending input signals?

Many thanks,
Webb

---

### Post by Favux on 2012-01-01
Right, since inputattach isn't working you can't use evtest in a console because there isn't an event node on input.

You should be able to use xxd (hidrawX hexdump).  As in:
```
xxd /dev/ttyS0
```
Using the port the tablet is on of course.

---

### Post by webbp on 2012-01-03
xxd /dev/ttyS0

yields no output. Nor for ttyS2. All other serial ports produce I/O error...

Thanks,
Webb

---

### Post by Favux on 2012-01-03
Did you also try sudo?  As in:
```
sudo xxd /dev/ttyS0
```
or to group output:
```
sudo xxd -g1 /dev/ttyS0
```
The fact xxd didn't exit would seem to indicate something is on S0.

Any chance if you know the tablet works on another OS to rule out hardware problem?  I suppose something else could be grabbing/competing for S0.

---

### Post by roaldfre on 2012-01-16
Just an update for the protocol 5 driver: 4D mouse support is added and is confirmed to work! :-)

This basically means that all features of the driver are tested, afaict.
When I have some more time on my hands, I'll thoroughly clean the code and see if I can send it to to the kernel devs.

---

### Post by tmtke on 2012-01-25
Hi everyone, I have an Intuos I serial tablet, which I tried to revitalize on my ubuntu (oneiric) machine. For a time, there was no real solution, but with the new wacom_serial5.ko package I finally made a big step ahead.

Everything seems to be ok, the pointer moves, middle/right button works as expected, but the pen tip is always in pressed state (if I switch the pen to eraser, the issue remains), so it is pretty unusable.

Is this anything you know about, or some weird issue, maybe just a configuration problem? :confused:

---

### Post by Favux on 2012-01-25
Hi tmtke,

Welcome to Ubuntu forums!

Glad you found us.  I'm not sure what you mean by:
> but the pen tip is always in pressed state (if I switch the pen to eraser, the issue remains)
I'm hearing that as both the stylus tip and eraser are sending a Button 1 press with no release.  So that can't be hardware related, at least in terms of a defective stylus tip, i.e. broken nib etc.  That isn't something I've heard of with the wacom_serial5.ko before, as far as I can recall.

So could you describe what is happening in a little more detail.  Can you draw in say Gimp or MyPaint?  Do you get pressure when you draw a line?  Can you select tools with the stylus tip?  That sort of thing.

---

### Post by tmtke on 2012-01-25
Ok, going more technical.

At first, the tablet is perfectly in good condition, I have used it under XP like half a year ago, so no HW problem there.

I did the stuff as it is in this thread's first post under the "new driver" section.

After this, I had a tablet which was recognised on driver level (/dev/input/event6 & /dev/input/mouse2 sections appeared), and with cat or xxd or inputattach --dump I was able to see that something is received as I move the pen.

There was still no wacom control panel, nor cursor movement, or anything else.

I was searching through the forums, and finally I have constructed an udev rule for this, I will post it here, but currently I am at work :)

I think the key is the last step, maybe the rule is not good, or confuses something. If I understand the logic correctly, the control panel and so on notices the /dev/input/wacom device.

Maybe this helps (for both of us :))

---

### Post by tmtke on 2012-01-25
Oh, sorry, to your question: it seems like it in a constant mouse_left_down state, and mouse_left_up does not work.

As I tried in myPaint, the pressure sensitivity doesn't work, but I did not pay a lot of attention to it, however, it was drawing lines constantly.

---

### Post by Favux on 2012-01-25
Not sure what is happening.

I'm a little concerned about the udev rule, you should not need one.

I don't understand where the /dev/input/mouse2 node is coming from.  Do you have a Wacom tablet mouse?  Maybe we should look at your Xorg.0.log in /var/log.  Since the nodes are appearing it doesn't appear that inputattach is hanging.

The linuxwacom wacomcpl (wacom control panel) is not present in xf86-input-wacom.  Instead Oneiric has Gnome 3.2 which has the first implementation of the Wacom tablet applet in System Settings.  It uses the gnome-settings-daemon, see:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon)

Not quite sure what you mean when you say the cursor doesn't move but then say lines were constantly drawn in MyPaint.  There is a bug in Oneiric that because of its history buffer shows up in Gimp.  All sorts of spurious lines are drawn.  There is a PPA that applies a patch to disable the history buffer and that makes Gimp usable:  [https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline](https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline)

---

### Post by tmtke on 2012-01-25
Uh, maybe my english :)

So, the cursor movement is fine, only the pen tip is problematic. I wrote that it is drawing lines constantly, because if the cursor is over the canvas, the always-pressed-button stuff is doing its job perfectly, drawing lines :)

I'll check the rest at home, and thank you for the answers! :)

---

### Post by tmtke on 2012-01-26
I checked the Xorg.0.log:

At first, there is:

```
[    22.248] (II) LoadModule: "wacom"
[    22.249] (WW) Warning, couldn't open module wacom
[    22.249] (II) UnloadModule: "wacom"
[    22.249] (II) Unloading wacom
[    22.249] (EE) Failed to load module "wacom" (module does not exist, 0)
[    22.249] (EE) No input driver matching `wacom'
[    22.249] (II) LoadModule: "wacom"
[    22.249] (WW) Warning, couldn't open module wacom
[    22.249] (II) UnloadModule: "wacom"
[    22.249] (II) Unloading wacom
[    22.249] (EE) Failed to load module "wacom" (module does not exist, 0)
[    22.249] (EE) No input driver matching `wacom'
[    22.249] (II) LoadModule: "wacom"
[    22.249] (WW) Warning, couldn't open module wacom
[    22.249] (II) UnloadModule: "wacom"
[    22.249] (II) Unloading wacom
[    22.249] (EE) Failed to load module "wacom" (module does not exist, 0)
[    22.249] (EE) No input driver matching `wacom'

```

But later, because of the udev rule:

```
[    26.662] (II) config/udev: Adding input device Wacom protocol 5 serial tablet (/dev/input/mouse2)
[    26.662] (II) No input driver/identifier specified (ignoring)
[    26.662] (II) config/udev: Adding input device Wacom protocol 5 serial tablet (/dev/input/event6)
[    26.662] (**) Wacom protocol 5 serial tablet: Applying InputClass "evdev tablet catchall"
[    26.662] (II) Using input driver 'evdev' for 'Wacom protocol 5 serial tablet'
[    26.662] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.662] (**) Wacom protocol 5 serial tablet: always reports core events
[    26.662] (**) Wacom protocol 5 serial tablet: Device: "/dev/input/event6"
[    26.662] (--) Wacom protocol 5 serial tablet: Found 12 mouse buttons
[    26.662] (--) Wacom protocol 5 serial tablet: Found scroll wheel(s)
[    26.662] (--) Wacom protocol 5 serial tablet: Found relative axes
[    26.662] (--) Wacom protocol 5 serial tablet: Found absolute axes
[    26.663] (II) evdev-grail: failed to open grail, no gesture support
[    26.663] (--) Wacom protocol 5 serial tablet: Found x and y absolute axes
[    26.663] (--) Wacom protocol 5 serial tablet: Found absolute tablet.
[    26.663] (II) Wacom protocol 5 serial tablet: Configuring as tablet
[    26.663] (II) Wacom protocol 5 serial tablet: Adding scrollwheel support
[    26.663] (**) Wacom protocol 5 serial tablet: YAxisMapping: buttons 4 and 5
[    26.663] (**) Wacom protocol 5 serial tablet: EmulateWheelButton: 4, Emulate WheelInertia: 10, EmulateWheelTimeout: 200
[    26.663] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb6/6-1/6-1:1.0/ttyUSB0/tty/ttyUSB0/serio2/input/input6/event6"
[    26.663] (II) XINPUT: Adding extended input device "Wacom protocol 5 serial tablet" (type: TABLET)
[    26.663] (WW) Wacom protocol 5 serial tablet: touchpads, tablets and touchscreens ignore relative axes.
[    26.663] (II) Wacom protocol 5 serial tablet: initialized for absolute axes.
[    26.663] (**) Wacom protocol 5 serial tablet: (accel) keeping acceleration scheme 1
[    26.663] (**) Wacom protocol 5 serial tablet: (accel) acceleration profile 0
[    26.663] (**) Wacom protocol 5 serial tablet: (accel) acceleration factor: 2
.000
[    26.663] (**) Wacom protocol 5 serial tablet: (accel) acceleration threshold
: 4

```

And the udev rule for this:


```
ACTION=="add|change", SUBSYSTEM=="serio", DRIVER=="serial_wacom5", ATTRS{name}=="Wacom protocol 5 serial tablet", SYMLINK="input/wacom", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"

```

Now I'm trying something out without the udev rules.

---

### Post by tmtke on 2012-01-26
I tried without the udev rule. No success, tablet not working.

Correct me, if I'm wrong, I've built and installed the xf86-input-wacom (newest version from git), it has to be there if I want to use the wacom_serial5.ko kernel driver?

---

### Post by Favux on 2012-01-26
I think any version starting with 0.10.11 or later should be good.  Like you I'm starting to wonder if something has gone wrong with your xf86-input-wacom compile.  A couple of other compile references for Ubuntu include part II. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") or Section 2 of the [LinuxWacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949").

You're using Oneiric, correct?  What's the output of *lsmod* and *ls -l /dev/input*?

---

### Post by tmtke on 2012-01-28
lsmod:


wacom_serial5          16969  0 
serport                12936  1 
rfcomm                 47946  0 
nfs                   354830  2 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
lockd                  86161  1 nfs
fscache                61593  1 nfs
auth_rpcgss            53320  1 nfs
nfs_acl                12883  1 nfs
sunrpc                240950  16 nfs,lockd,auth_rpcgss,nfs_acl
binfmt_misc            17540  1 
dm_crypt               23199  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_via      71209  1 
snd_hda_intel          33390  2 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
sp5100_tco             13791  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
edac_core              53746  0 
i2c_piix4              13301  0 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
lp                     17799  0 
pl2303                 17993  1 
usbserial              47107  3 pl2303
ppdev                  17113  0 
k10temp                13166  0 
psmouse                73882  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13166  0 
shpchp                 37345  0 
parport_pc             36962  1 
joydev                 17693  0 
edac_mce_amd           23709  0 
asus_atk0110           18078  0 
parport                46562  3 lp,ppdev,parport_pc
radeon               1016211  3 
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
drm                   236290  5 radeon,ttm,drm_kms_helper
usbhid                 47198  0 
hid                    95463  1 usbhid
r8169                  52788  0 
wmi                    19256  0 
i2c_algo_bit           13423  1 radeon
pata_atiixp            13164  0 
ahci                   26002  4 
libahci                26861  1 ahci

pl2303 + usbserial is the usb2serial device, and there is the wacom driver of course.

/dev/input is:


drwxr-xr-x 2 root root    240 2012-01-28 11:24 by-id
drwxr-xr-x 2 root root    200 2012-01-28 11:24 by-path
crw-r----- 1 root root 13, 64 2012-01-28 11:24 event0
crw-r----- 1 root root 13, 65 2012-01-28 11:24 event1
crw-r----- 1 root root 13, 66 2012-01-28 11:24 event2
crw-r----- 1 root root 13, 67 2012-01-28 11:24 event3
crw-r----- 1 root root 13, 68 2012-01-28 11:24 event4
crw-r----- 1 root root 13, 69 2012-01-28 11:24 event5
crw-r----- 1 root root 13, 70 2012-01-28 11:24 event6
crw-r----- 1 root root 13, 63 2012-01-28 11:24 mice
crw-r----- 1 root root 13, 32 2012-01-28 11:24 mouse0
crw-r----- 1 root root 13, 33 2012-01-28 11:24 mouse1
crw-r----- 1 root root 13, 34 2012-01-28 11:24 mouse2

event6 and mouse2 is there because of inputattach.

---

### Post by tmtke on 2012-01-30
Ok, I solved the problem, here's what I did:

1. At first, removed all (possibly junk) drivers which has wacom in their name (except serial_wacom5.ko of course).

2. Recompiled the freshest X driver from git, and installed.

3. Removed the udev rule I mentioned.

4. Suprisingly, the X driver crashed on restarting X, so I had to remove it temporarily.

5. After checking /var/log/Xorg.0.log, there was a stacktrace which was showing that the driver crashed somewhere in calling fclose(...).

6. Heck, I'm a senior developer anyway, it's my field of play. I checked the driver code, and found these ugly lines:

```

out:
	udev_device_unref(device);
	udev_unref(udev);
	fclose(file);

```

   Let me tell you, I would slap my programmers, if they dare to do a goto, even in vanilla C.

7. Corrected the function (wcmISDV4.c @ model_from_sysfs) to use proper if's to check device and file availability, recompiled and installed the driver,

and it WORKS.

Thanks for helping me out in this.

---

### Post by Favux on 2012-01-30
Hi tmtke,

Outstanding!

That is a really nice find.  I would not have thought to look at wcmISDV4.c as it was extensively rewritten by Peter Hutterer (lead xf86-input-wacom developer) a while ago.  He's an Xorg guru who works for RedHat.  He just finished adding the new multi-touch code to X server 1.12.  Your comment on the goto made me smile, shhh.  Getting a clean stacktrace was obviously helpful.

Would you be interested in submitting a git patch for that to [linuxwacom-devel]("https://lists.sourceforge.net/lists/listinfo/linuxwacom-devel")?  That would be a good thing.  Or if you are not interested in taking the time maybe at least show me the diff for the changes you made, i.e. the if's, and I could whip up a submission you could review.

I only wish I had been of more help.  Sounds more likely you would be helping me in short order.  :)

Edit:  Oh and my response to your post #293 would not have been helpful because I would have said the lsmod looked good and that the ioctl patch to get the pl2303 usb2serial convertor working with xf86-input-wacom had been in the kernel for a while.

---

### Post by tmtke on 2012-01-30
Sure, I'll submit the patch, if I can borrow some extra time :) I can understand that sometimes a goto can be helpful, but most of the time it is an antipattern, for it can go really wrong :) Maybe it is just a bad habit, every developer has some 8-[

---

### Post by twgray on 2012-02-17
Has anyone gotten a Wacom PenPartner, CT-405-R, to work in 11.10, Onieric?

I have gone through this 'guide' step by step and end up exactly where HarM_triade, in Post #275 was:

The "sudo inputattach --wacom_iv /dev/ttyS0" does nothing, not even errors or a time-out, but if I ctrl-c out and run DMESG I get:

[ 7862.367335] input (null): throwing away 32 bytes of garbage
[ 7862.382317] input (null): throwing away 32 bytes of garbage
[ 7862.388104] input (null): Timed out waiting for tablet to respond with model and version.
[ 7862.388134] wacom_serial4: probe of serio391 failed with error -5

I did not see a resolution to his, or my probem posted.

For whatever reason, xxd /dev/ttyUSB0 nor sudo xxd /dev/ttyUSB0 yield anything. There is no output until I ctrl-c out.

Can anyone help me?

---

### Post by tokenrove on 2012-02-17
> **twgray said:**
> Has anyone gotten a Wacom PenPartner, CT-405-R, to work in 11.10, Onieric?


As far as I know, no.  I have had several people with PenPartners contact me about it, and none of them have gotten it to work.  What would be ideal is if you could connect to the port with a serial comm program like minicomm and:
1) verify that when you move the pen, data appears.
2) set newline to carriage-return only, and send the various command sequences that the PenPartner does not seem to respond to: "~#\r", "~C\r", and "~R\r" (do not include quotes, \r means carriage return)
3) let me know what happens!
(or submit a patch... but I can't fix the driver without feedback from people who actually own the device)

Good luck.

---

### Post by tokenrove on 2012-02-17
> **tmtke said:**
> Sure, I'll submit the patch, if I can borrow some extra time :) I can understand that sometimes a goto can be helpful, but most of the time it is an antipattern, for it can go really wrong :) Maybe it is just a bad habit, every developer has some 8-[

Just a note on this.  Gotos are a part of the kernel style, for legitimate reasons (within that domain), so that's where that probably comes from.

---

### Post by bserem on 2012-02-23
> **tokenrove said:**
> As far as I know, no.  I have had several people with PenPartners contact me about it, and none of them have gotten it to work.  What would be ideal is if you could connect to the port with a serial comm program like minicomm and:
1) verify that when you move the pen, data appears.
2) set newline to carriage-return only, and send the various command sequences that the PenPartner does not seem to respond to: "~#\r", "~C\r", and "~R\r" (do not include quotes, \r means carriage return)
3) let me know what happens!
(or submit a patch... but I can't fix the driver without feedback from people who actually own the device)

Good luck.

Hello tokenrove!

I do have a penpartner in my posession, a friend of mine gave it to me a long time ago.

Can I, somehow, be of any assistance?
I do not use Ubuntu (don't shoot me!) though, I am an Arch user, but if there is anyway I could help please let me know!

---

### Post by tokenrove on 2012-02-23
> **bserem said:**
> Hello tokenrove!

I do have a penpartner in my posession, a friend of mine gave it to me a long time ago.

Can I, somehow, be of any assistance?
I do not use Ubuntu (don't shoot me!) though, I am an Arch user, but if there is anyway I could help please let me know!

This should be pretty distribution independent (in fact, I'm a Debian user, but Ubuntu seems to have the largest user community interested in these drivers).  If you can do what I mention above, it would be great.  If you'd like me to make any step more specific, please ask.

Thanks!  It would be great to support the PenPartners and would be a big push for me to try and get the driver into the kernel.

---

### Post by bserem on 2012-02-24
It is highly probable that I need some clarifications on some steps.
Also please forgive me if my english don't make sense all the time, it is now my native language.

So, here is what I have:
[LIST]
[*]A working PenPartner tablet (tested on a friends winxp machine yesterday).
[*]It is connected to /dev/ttyS0 on my linux installation.
[*]For testing purposes I created a Virtualbox Windows client and I added the serial port to the client OS (settings->serial->host device->/dev/ttyS0). It worked without any problem on the virtual machine. So my com-port is functional and the Wacom is working on the very same hardware we are trying to set it up.
[/LIST]


So lets see what going on inside linux:
All work is being done as root, to make sure everything goes on as intented.
```
# dmesg | grep tty
[    0.000000] console [tty0] enabled
[    1.531385] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.767583] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```

**CAT**
```
cat /dev/ttyS0
``` produces nothing (I do move the pen on the tablet).

**MINICOM**
Minicom is installed and its settings are: /dev/ttyS0 9600 8N1.
When I run minicom it opens and it says "offline".
Nothing I do on the wacom produces anything on the monitor.

I type ~# and minicom directly prints: ```
~#CT-0045R00,V1.3-5,
```
This is the model number on my wacom tablet. If I retype ~# I get the same answer.
If I type ~R or ~C I get nothing. If I type ~R or ~C **before** typing ~# then, typing ~# also returns nothing.

**CUTECOM**
Cutecom is installed. I run it and set it to /dev/ttyS0 9600 8 1.
I open the device, make some movements and still nothing gets displayed anywhere on the screen.

**I am in HEX output mode. **I set line end at CR and type:
[s]~C\r (or ~C): nothing happens[/s]
~C\r: nothing happens
~C: I have replies. After 8 queries the replies loop. Each reply consists of two lines. The sum of the 8 replies is this:
```
00000070: 7e 43 30 35 30 34 30 2c   30 33 37 38 30 0d 
7e 43 
00000080: 30 35 30 34 30 2c 30 33   37 38 30 0d 
7e 43 30 35 
00000090: 30 34 30 2c 30 33 37 38   30 0d 
7e 43 30 35 30 34 
000000a0: 30 2c 30 33 37 38 30 0d   
7e 43 30 35 30 34 30 2c 
000000b0: 30 33 37 38 30 0d 
7e 43   30 35 30 34 30 2c 30 33 
000000c0: 37 38 30 0d 
7e 43 30 35   30 34 30 2c 30 33 37 38 
000000d0: 30 0d 
7e 43 30 35 30 34   30 2c 30 33 37 38 30 0d 
```
~R\r (or ~R): nothing happens
~#\r (or ~#): I have replies. After 4 queries the replies loop. Each reply consists of two lines. The sum of the 4 replies is this:
```
00000000: 7e 23 43 54 2d 30 30 34   35 52 30 30 2c 56 31 2e 
00000010: 33 2d 35 2c
7e 23 43 54   2d 30 30 34 35 52 30 30 
00000020: 2c 56 31 2e 33 2d 35 2c
7e 23 43 54 2d 30 30 34 
00000030: 35 52 30 30 2c 56 31 2e   33 2d 35 2c
7e 23 43 54 
00000040: 2d 30 30 34 35 52 30 30   2c 56 31 2e 33 2d 35 2c 
```

**I am in normal output mode.**
~# and ~#\r replies ```
~#CT-0045R00,V1.3-5,
```
~R and ~R\r replies nothing.
~C replies ```
~C05040,03780
```
Positioning the pen on the tablet and quering for ~C again gives the same answer.
~C\r replies nothing.

Are the above of any help?

Is there anything else I can do to provide more info?

Thank you for your interest in this :)

---

### Post by bserem on 2012-02-24
UPDATE:

I did something I read [here]("http://forum.bongofish.co.uk/index.php?PHPSESSID=787707afe85086f80003adf6bc9a005e&topic=2059.msg16136#msg16136").

After opening Cutecom **I typed ST**.
When I placed the pen on my tablet Cutecom displayed raw data, lots of it. I assume it is the coordinates of the pen.
I bit of it is here:
```
\0xe0\0x03=\0x00\0x1aT@\0xe0\0x03@\0x00\0x1aP@\0xe0\0x03G\0x00\0x1aT@\0xe0\0x03K\0x00\0x1aR@\0xe0\0x03N\0x00\0x1aS@\0xe0\0x03M\0x00\0x1aS@\0xe0\0x03E\0x00\0x1aL@\0xe0\0x03?\0x00\0x1aI@\0xe0\0x039\0x00\0x1aB@\0xe0
```

If you need more, I pasted a lot on pastebin.
PEN output: [http://pastebin.com/Qw6LkCBa](http://pastebin.com/Qw6LkCBa)
ERASE output: [http://pastebin.com/MEub44ic](http://pastebin.com/MEub44ic)

By pressing SP the tablet stops sending data when I move the pen on it.

---

### Post by tokenrove on 2012-02-24
> **bserem said:**
> Are the above of any help?

Is there anything else I can do to provide more info?

Thank you for your interest in this :)

All of this is excellent, thank you!  I wanted to let you know that as I'm about to head out for the weekend and won't be around, but I should thereafter be able to send you a patched version of the driver to test that will hopefully function (at least in a basic manner) on the PenPartner.

Cheers.

---

### Post by bserem on 2012-02-25
I'm glad I could provide something!
Have fun this weekend :)
It is also a special weekend in Greece (it is our Carnival).

---

### Post by tokenrove on 2012-02-27
> **bserem said:**
> I'm glad I could provide something!
Have fun this weekend :)
It is also a special weekend in Greece (it is our Carnival).

Please give [http://www.cipht.net/releases/wacom_serial-120227-1.tar.bz2](http://www.cipht.net/releases/wacom_serial-120227-1.tar.bz2) a shot.  It includes a patched inputattach, so you should be able to just: (with any luck)

 $ make
 $ sudo insmod ./wacom_serial.ko
 $ sudo ./inputattach --wacom_iv /dev/ttyS0
 ( in another shell: )
 $ tail /var/log/kern.log
 ( or where-ever your kernel messages go )
and let me know what it spits out.

Thanks.

---

### Post by bserem on 2012-02-27
Okey, I have something!

```
Feb 27 19:13:25 redliner kernel: [ 3023.142678] serio: Serial port ttyS0
Feb 27 19:13:26 redliner kernel: [ 3024.141601] input (null): Timed out waiting for tablet to respond with model and version.
Feb 27 19:13:26 redliner kernel: [ 3024.141617] wacom_serial: probe of serio2 failed with error -5

```

This repeats itself indefinately. Each time it increments the "serio", just like that:

```
Feb 27 19:16:03 redliner kernel: [ 3181.040176] serio: Serial port ttyS0
Feb 27 19:16:04 redliner kernel: [ 3182.039440] input (null): Timed out waiting for tablet to respond with model and version.
Feb 27 19:16:04 redliner kernel: [ 3182.039455] wacom_serial: probe of serio160 failed with error -5
```

---

### Post by tokenrove on 2012-02-28
> **bserem said:**
> Okey, I have something!


Okay, try replacing inputattach.c with
  [http://cipht.net/tmp/inputattach.c](http://cipht.net/tmp/inputattach.c)
and recompiling (make).  We may have to go through this a few times as I figure out exactly what sequence is required to get the tablet responding.  Have patience, and thanks so much for testing this!

---

### Post by bserem on 2012-02-28
This is what I get:
```
Feb 28 22:09:04 redliner kernel: [13450.892742] serio: Serial port ttyS0
Feb 28 22:09:05 redliner kernel: [13451.892016] input (null): Timed out waiting for tablet to respond with model and version.
Feb 28 22:09:05 redliner kernel: [13451.892032] wacom_serial: probe of serio42 failed with error -5
```

I have a lot patience in this and I can test everything as long as it is explained to me how to test it :)

ps: Would it help you if I could somehow give you a shell in my machine (teamviewer?).

---

### Post by tokenrove on 2012-02-28
> **bserem said:**
> This is what I get:
```
Feb 28 22:09:04 redliner kernel: [13450.892742] serio: Serial port ttyS0
Feb 28 22:09:05 redliner kernel: [13451.892016] input (null): Timed out waiting for tablet to respond with model and version.
Feb 28 22:09:05 redliner kernel: [13451.892032] wacom_serial: probe of serio42 failed with error -5
```

I have a lot patience in this and I can test everything as long as it is explained to me how to test it :)

ps: Would it help you if I could somehow give you a shell in my machine (teamviewer?).

Try the latest [http://cipht.net/tmp/inputattach.c](http://cipht.net/tmp/inputattach.c) with the same instructions as before.  The file should have the following md5sum:

  00ca2e9a5785ee559f67e548d8c8412b  inputattach.c

A shell on your machine would certainly be easier, but if we can avoid it, all the better.  I've never used teamviewer.  Keep in mind that I would need to be root to fix this (or at least sudo entries for minicom and ./inputattach).  Let's see what happens with the above; you can email me at [email]julian@cipht.net[/email] if it turns out to be easier to give me a shell on your machine.

---

### Post by bserem on 2012-02-28
same output with the new .c file
```
Feb 29 03:58:49 redliner kernel: [  185.534884] serio: Serial port ttyS0
Feb 29 03:58:50 redliner kernel: [  186.534121] input (null): Timed out waiting for tablet to respond with model and version.
Feb 29 03:58:50 redliner kernel: [  186.534135] wacom_serial: probe of serio22 failed with error -5

```

and you've got mail

---

### Post by palhmbus on 2012-03-01
First of all...

A huge thanks to tokenrove &`Roaldfre :KS who got this working...

I'm a Intous2 GD-1218-R user on Ubuntu 11.10 (just upgraded today).

Using the awesome how to, I now have a working tablet (so long Windows XP!)

I have a couple of questions still though, can I enable Mode "Relative" ?

I've read that this mode is the equivalent "Mouse Mode" 
and that my cursor will behave more like a mouse, which is what I'd like for my normal use, (since I'm using a keyboard on top of my wacom).

Also, is there any way of using the new Wacom Control Panel in Ubuntu 11.10 ?

---

### Post by Favux on 2012-03-01
Hi palhmbus,

> can I enable Mode "Relative" ?
Sure.  You can use a xsetwacom command or the control panel applet.  See below or *man xsetwacom* (and *man wacom*) in a terminal.
> Also, is there any way of using the new Wacom Control Panel in Ubuntu 11.10 ? 
The Wacom tablet applet is in System Settings and lets you use Absolute or Relative Mode.  This Gnome 3.2 version is the first version and doesn't do much yet.  To access some of the gnome-settings-daemon hooks for Wacom you still have to use dconf-editor:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon)  Higher up on that page are examples re. the stylus and eraser.  From the LWP mediawiki HOWTO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

---

### Post by tokenrove on 2012-03-01
Thanks very much to **bserem**, the protocol 4 driver should now support PenPartners, and possibly other previously-failing tablets.

The latest version can be obtained here:
  [http://cipht.net/releases/wacom_serial-120301-1.tar.bz2](http://cipht.net/releases/wacom_serial-120301-1.tar.bz2)

I would appreciate feedback on it, as I may soon make an attempt to get it into the kernel mainline.  I know there are probably still some problems in tool switching and due to the lack of supression/filtering.

---

### Post by bserem on 2012-03-01
Since I am the only beta-tester at the moment I'll speak first and say many, many thanks to tokenrove! He did a magnificent job and in very little time I must say... You should see this guy coding!

I played a bit with the penpartner, it works just fine.
I fired up Gimp once tokenrove finished his job and tested the tablet there.

Gimp succesfully recognizes all three tools provided (pen, eraser, side button) and works with them fine. It can handle differences in pressure and it switches tools when I flip the pen.
So everything registers fine!

This was my first ever experience with tablets so I do not know if things could be better or not. I'm still trying to see if/how I can change the pressure sensitivity.
The tools available (GUIs) do not yet recognize the Penpartner. I'm pretty sure that once tokenrove polishes the code they will start to provide options for protocol IV devices too!

It is amazing how a really really old device, given to me by somebody that was going to trash it, is now fully functional again. The greatest hardware companies aren't capable of such things, yet tokenrove did it in linux. Congrats once again!

---

### Post by Favux on 2012-03-01
Hi bserem,

Thanks for your testing.  Glad to hear the PenPartner is working now.  :)

To change pressure you can use a xsetwacom command with the PressureCurve parameter.  Run *man xsetwacom* in a terminal for instructions.  To get the "device name" run *xinput list*.  You can read various useful HOWTOs here:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

So the Wacom tablet applet in System Settings doesn't see your PenPartner?

---

### Post by bserem on 2012-03-01
Thanks for the info on pressure, I'll look into it. You see I am a total nood when it comes to wacoms.

I also don't have a tablet applet (archlinux+xfce, I might haven't installed something)

---

### Post by Favux on 2012-03-01
Oops.  The applet is with Gnome 3.2.  That's why you don't have it using xfce.  They're working on the Gnome Wacom applet, trying to catch up to the KDE one.  The new libwacom (supplies tablet metadata) should help folks writing a tablet configuration gui.  So maybe someone will write an xfce one in the not too distant future.

---

### Post by palhmbus on 2012-03-01
> **Favux said:**
> 
Sure.  You can use a xsetwacom command or the control panel applet.  See below or *man xsetwacom* (and *man wacom*) in a terminal.

Afraid I've tried and it doesn't work...

sudo xsetwacom set "Wacom protocol 5 serial tablet pad" Mode "Relative"
X Error of failed request:  XI_BadMode (invalid Mode parameter)
  Major opcode of failed request:  140 (XInputExtension)
  Minor opcode of failed request:  5 (X_SetDeviceMode)
  Mode id in failed request: 0x17
  Serial number of failed request:  15
  Current serial number in output stream:  15

Please tell me I'm missing something obvious.

Also, I'm using the Lubuntu version of 11.10, I'll have to install gnome3 and swap over to get the wacom control panel working...

---

### Post by Favux on 2012-03-01
Ah Lubuntu, so you don't have the System Settings control panel applet.  That's with the Gnome 3.2 in regular Ubuntu.  KDE has a applet too.

You don't need sudo with a xsetwacom command.  They're runtime so once entered in a terminal they apply immediately but you lose them if you hot plug, log out, or restart.  So a startup script is helpful.

The Mode parameter doesn't apply to the Pad.  The Pad is the Linux version of the Wacom ExpressKeys, the tablet buttons in other words.  The name difference isn't to confuse you, it's because Wacom has apparently trademarked ExpressKeys.

Mode applies to stylus, eraser, cursor (Wacom tablet mouse), or touch.  So what you are looking for is:
```
xsetwacom set "Wacom protocol 5 serial tablet stylus" Mode "Relative"
```
Assuming "Wacom protocol 5 serial tablet stylus" is the "device name" *xinput list* is returning for the stylus.

---

### Post by palhmbus on 2012-03-03
> **Favux said:**
> 
```
xsetwacom set "Wacom protocol 5 serial tablet stylus" Mode "Relative"
```


Ah, that's so the reason, thanks for helping me fix this!

Unfortunatley, now I need to swap my stylus pens somehow.

I set my no-button stylus to mouse mode (Relative) with good sensitivity (don't have to move all round the board to do things).

I want my no-button stylus to be my main drawing pen!!

Can you differentiate between stylus like this with xsetwacom?

My wacom obviously recognises both stylus's seperately, cause it's applying different rules to them, but then again maybe it  is X that is doing that.

---

### Post by Favux on 2012-03-03
Good, Mode is straightened out.

Yes you can since protocol 5 devices report tool serial #'s.  You use Alexia Death's (a Gimp developer) BindToSerial xsetwacom paramater.  See *man xsetwacom* in a terminal.

---

### Post by bruis on 2012-03-04
Hello Favux
 I am trying to run a Wacom UD1212R on  Oneiric Ocelot (Kubuntu) with  X-server-xorg-input-wacom and kde-config-tablet installed.
 Following your how-to instructions and using a fresh [SIZE=2][COLOR=#000000]wacom_serial and [/COLOR][/SIZE][SIZE=2][COLOR=#000000]l[/COLOR][/SIZE][COLOR=#000000][SIZE=3][SIZE=2]inuxconsoletools-1.42[/SIZE]  [/SIZE][/COLOR]things went well only to stop here:
 

 [COLOR=#000000]bruis@celtic:~/linuxconsoletools-1.4.2$ patch -p1 < ~/wacom_serial/inputattach.patch[/COLOR]
 [COLOR=#000000]can't find file to patch at input line 3[/COLOR]
 [COLOR=#000000]Perhaps you used the wrong -p or --strip option?[/COLOR]
 [COLOR=#000000]The text leading up to this was:[/COLOR]
 [COLOR=#000000]|--- /home/julian/dl/joystick-1.4.2/utils/inputattach.c 2011-08-09 01:43:10.000000000 -0400[/COLOR]
 [COLOR=#000000]|+++ inputattach.c      2012-03-01 13:52:56.369310089 -0500[/COLOR]
 [SIZE=2][COLOR=#000000]File to patch: [/COLOR][/SIZE] 
 


 I will be happy to help with feedback  once my tablet is on the road.

---

### Post by Favux on 2012-03-05
Hi bruis,

And welcome to the Ubuntu forums!

Right you are.  Try:
```
patch utils/inputattach.c < ~/Desktop/wacom_serial/inputattach.patch
```
Linuxconsole has the inputattach.c in the utils folder.

---

### Post by Favux on 2012-03-05
Any feed back is appreciated.  :)

---

### Post by bruis on 2012-03-05
Thanks Favux, the patching worked but I then hit another speed bump:

bruis@celtic:~/linuxconsoletools-1.4.2$ make
make -C utils compile
make[1]: Entering directory `/home/bruis/linuxconsoletools-1.4.2/utils'
gcc -g -O2 -Wall -I../linux/include    inputattach.c   -o inputattach
inputattach.c:630:2: error: &#8216;SERIO_WACOM_IV&#8217; undeclared here (not in a function)
make[1]: *** [inputattach] Error 1
make[1]: Leaving directory `/home/bruis/linuxconsoletools-1.4.2/utils'
make: *** [compile] Error 2

On inspecting the patched inputattach.c  :

{ "--wacom_iv",        "-wacom_iv",    "Wacom protocol 4 tablet",
    B9600, CS8 | CRTSCTS,
    SERIO_WACOM_IV,        0x00,    0x00,    0,    wacom_iv_init },

---

### Post by Favux on 2012-03-05
Check the serio-ids.h file in the linuxconsoletools-1.4.2/utils source code.  If it looks like:
```
#ifndef SERIO_PSMULT
# define SERIO_PS2MULT		0x3c
#endif

#endif
```
at the end of the *Serio types* list change it to read:
```
#ifndef SERIO_PSMULT
# define SERIO_PS2MULT		0x3c
#endif
#ifndef SERIO_WACOM_IV
# define SERIO_WACOM_IV		0x3d
#endif

#endif
```
or copy the serio-ids.h file from wacom_serial into linuxconsoletools-1.4.2/utils.  Then try to compile inputattach again.  Looks like we need another patch.

Edit:  lol  As I finally drink enough coffee to wake up the old noggin I realize tokenrove has actually supplied us with everthing.  No need to download linuxconsoletools for inputattach.c anymore.  Just look into the wacom_serial source code folder and check if when you ran *make all* the inputattach binary was made (the diamond shape).  I doubt we still need to install the library:
```
sudo apt-get install libsdl1.2-dev
```
because I think linuxconsoletools needed that, not inputattach specifically.  I didn't uninstall it to test though.  If inputattach is there then all that is needed is to copy it into place.
```
sudo cp inputattach /usr/bin
```

---

### Post by bruis on 2012-03-05
I have tracked the compile problem to serio.h.patch. When wacom_serial-120301-1.tar.bz2 is extracted a space/tab goes awol:

--- linux/include/linux/serio.h    2011-05-19 00:06:34.000000000 -0400
+++ serio.h    2011-07-02 10:37:02.000000000 -0400
@@ -199,5 +199,6 @@
 #define SERIO_DYNAPRO    0x3a
 #define SERIO_HAMPSHIRE    0x3b
 #define SERIO_PS2MULT    0x3c
+#define SERIO_WACOM_IV0x3d
 
 #endif

This might only happen on my PC?

---

### Post by Favux on 2012-03-05
Hi, going from the old joystick package to the new Linux Console package the name of the file goes from serio.h to serio-ids.h.  So the patch changes.

I changed the HOW TO.  Please follow the new steps.  Tokenrove now includes inputattach with wacom_serial.ko and they both compile together.  He doesn't include a patch for serio-ids.h he includes the whole file and the latest inputattach.c.  No need to download inputattach from the Linux Console Project anymore.

---

### Post by bruis on 2012-03-06
After I read tokenrove's post #306  I have tried his suggestion a few times with partial success:

bruis@celtic:~/wacom_serial$ sudo dmesg | grep tty
[    0.000000] console [tty0] enabled
[    0.293606] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.364430] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.700578] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.720982] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[11017.961363] serio: Serial port ttyS0
[11018.050844] input: Wacom protocol 4 serial tablet as /devices/pnp0/00:06/tty/ttyS0/serio2/input/input6
[11050.054219] serio: Serial port ttyS0
[11050.143936] input: Wacom protocol 4 serial tablet as /devices/pnp0/00:06/tty/ttyS0/serio3/input/input7

The result is that the pen works as a cursor only.
I believe another entry    ...../input8   is needed before full initialisation.

---

### Post by Favux on 2012-03-06
I'm afraid you have lost me.  There is now reaction to the stylus which is good.

I gather you were able to compile inputattach and wacom_serial.ko?  Did you use my changes to the HOW TO for that?

Did you copy (cp) the wacom_serial.ko and inputattach into place?

Have you put the inputattach command into rc.local?  If so what do you see when you run list modules?
```
lsmod
```
You should see wacom_serial and inputattach.

What is the output of?
```
xinput list
```

---

### Post by bruis on 2012-03-06
Sorry, I guess my last post was a bit sparse. 

Following  your How To  section II,  subsection  a) ,  wacom_serial.ko (wacom_serial-120301-1) was installed.
NB: This was your earlier version of subsection a)
Then following tokenrove #306 a make  before leaving the wacom_serial dir. (Should this be make all  instead?)
Copied inputattach to /usr/bin
Then sudo ./inputattach --wacom_iv /dev/ttyS0 &  which returns a a four digit number like 4497.
Then added:  inputattach --wacom_iv /dev/ttyS0 to etc/ rc.local
Logging out and in  loads inputattach as shown in System Monitor.
However when I run lsmod I get: 
wacom_serial           12646  0   but no sign of inputattach

Xinput list  returns:
Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft  Microsoft Basic Optical Mouse v2.0     id=8    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Wired Keyboard 600              id=10   [slave  pointer  (2)]
&#9116;   &#8627; Wacom protocol 4 serial tablet            id=11   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; Microsoft Wired Keyboard 600              id=9    [slave  keyboard (3)]

Wacom Tablet setting is not working in System Settings. Xsetwacom also not working.

---

### Post by Favux on 2012-03-06
Thanks that helped.

My mistake, seeing wacom_serial in lsmod indicates inputattach is working.  Also seeing in *xinput list*:
```
&#9116; &#8627; Wacom protocol 4 serial tablet id=11 [slave pointer (2)]
```
indicates that.  So I think you have a working serio wacom_serial.ko with a /dev/input node being created by inputattach, which dmesg is showing you.

However it looks like there may be a problem with the Wacom X driver (xf86-input-wacom) because we should see stylus, and at least eraser appended to the Parent "device name" you're getting from *xinput list*.  A quick way to check if you are on the Wacom X driver is to run:
```
xsetwacom list
```
or
```
xinput list-props "Wacom protocol 4 serial tablet"
```
Since it is behaving like a mouse I suspect it will show the tablet is on the evdev X driver.

So we need to look at your Xorg.0.log and see if that will tell us what is going wrong.  It is in /var/log.  Since it is big compress it by right clicking on it and using Create Archive.  Then attach it to your next post.  I'm concerned you may be running into a problem similar to the one tmtke encountered, see [post #294]("http://ubuntuforums.org/showpost.php?p=11651065&postcount=294"), although X isn't crashing on your system.

---

### Post by bruis on 2012-03-07
The situation has worsened. After booting up today :
sudo ./inputattach -–wacom_iv /dev/ttyS0 $     returns:  inputattach: invalid mode '-–wacom_iv'.
I replaced inputtach but the result was the same. I have had this happen a few times and do not know why it stopped or why it has started again.  All that I did that might have some relevance was to tinker with xorg.conf and 50-wacom.rules.
With this situation I guess its not surprising that xsetcom list  does nothing and xinput list-props "Wacom protocol 4 serial tablet"  returns: unable to find device Wacom protocol 4 serial tablet.

It can be a rocky road to Serial Wacom Happiness...

---

### Post by tokenrove on 2012-03-07
> **bruis said:**
> Wacom Tablet setting is not working in System Settings. Xsetwacom also not working.

Hi,

I have to run so this is a bit quick, but make sure the udev rules are installed properly (70-serial-wacom.rules).  You should not need to patch anything with the 120301 driver.  I'll look at this again tonight in case that didn't fix it.

Cheers.

---

### Post by bruis on 2012-03-07
Here are my  /etc/udev/rules.d/70-serial-wacom.rules :

ACTION=="add|change", SUBSYSTEM=="pnp", ENV{PRODUCT}=='13/3d/*', ENV{NAME}=="Wacom protocol IV serial tablet",SYMLINK+="input/wacom",ENV{ID_INPUT}="1",ENV{ID_INPUT_TABLET}="1" 

There are also  /lib/udev/rules.d/69-xserver-xorg-input-wacom.rules.
Could there be a conflict?

---

### Post by Favux on 2012-03-07
I don't think so, and besides 70 runs after 69 not to mention /etc/udev/rules.d runs after /lib/udev/rules.d.  Whatever runs last controls so the custom serial rule should override anything earlier.

What the Xorg.0.log mainly shows us is:
```
[    16.862] (II) LoadModule: "wacom"
[    16.862] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    16.875] (II) Module wacom: vendor="X.Org Foundation"
[    16.875] 	compiled for 1.10.4, module version = 0.11.0
[    16.875] 	Module class: X.Org XInput Driver
[    16.875] 	ABI class: X.Org XInput driver, version 12.3
......
[    18.391] (II) Using input driver 'wacom' for 'stylus'
[    18.391] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    18.391] (**) stylus: always reports core events
[    18.391] (**) Option "Device" "/dev/ttyS0"
[    18.391] (**) Option "StopBits" "1"
[    18.391] (**) Option "DataBits" "8"
[    18.391] (**) Option "Parity" "None"
[    18.391] (**) Option "Vmin" "1"
[    18.391] (**) Option "Vtime" "10"
[    18.391] (**) Option "FlowControl" "Xoff"
[    18.391] (**) Option "Mode" "Relative"
[    18.391] (**) Option "Threshold" "5"
[    21.645] (WW) stylus: Waited too long for answer (failed after 3 tries).
[    21.645] (WW) stylus: Query failed with 19200 baud. Trying 38400.
[    24.898] (WW) stylus: Waited too long for answer (failed after 3 tries).
[    24.898] (II) stylus: serial tablet id 0x90.
[    24.898] (EE) PreInit returned 8 for "stylus"
[    24.898] (II) UnloadModule: "wacom"
[    24.898] (II) Unloading wacom
[    24.898] (II) Using input driver 'wacom' for 'eraser'
[    24.898] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    24.898] (**) eraser: always reports core events
[    24.898] (**) Option "Device" "/dev/ttyS0"
[    24.898] (**) Option "StopBits" "1"
[    24.898] (**) Option "DataBits" "8"
[    24.898] (**) Option "Parity" "None"
[    24.898] (**) Option "Vmin" "1"
[    24.898] (**) Option "Vtime" "10"
[    24.898] (**) Option "FlowControl" "Xoff"
[    24.898] (**) Option "Mode" "Relative"
[    24.899] (**) Option "Threshold" "5"
[    24.899] (WW) eraser: TPCButton option can only be set by stylus.
[    28.149] (WW) eraser: Waited too long for answer (failed after 3 tries).
[    28.149] (WW) eraser: Query failed with 19200 baud. Trying 38400.
[    31.403] (WW) eraser: Waited too long for answer (failed after 3 tries).
[    31.403] (II) eraser: serial tablet id 0x90.
[    31.403] (EE) PreInit returned 8 for "eraser"
[    31.403] (II) UnloadModule: "wacom"
[    31.403] (II) Unloading wacom
[    31.403] (II) Using input driver 'wacom' for 'cursor'
[    31.403] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    31.403] (**) cursor: always reports core events
[    31.403] (**) Option "Device" "/dev/ttyS0"
[    31.403] (**) Option "StopBits" "1"
[    31.403] (**) Option "DataBits" "8"
[    31.403] (**) Option "Parity" "None"
[    31.403] (**) Option "Vmin" "1"
[    31.403] (**) Option "Vtime" "10"
[    31.403] (**) Option "FlowControl" "Xoff"
[    31.403] (**) Option "Mode" "  Absolute"
[    31.403] (**) Option "Threshold" "5"
[    31.403] (WW) cursor: TPCButton option can only be set by stylus.
[    34.657] (WW) cursor: Waited too long for answer (failed after 3 tries).
[    34.657] (WW) cursor: Query failed with 19200 baud. Trying 38400.
[    37.910] (WW) cursor: Waited too long for answer (failed after 3 tries).
[    37.910] (II) cursor: serial tablet id 0x90.
[    37.910] (EE) PreInit returned 8 for "cursor"
[    37.910] (II) UnloadModule: "wacom"
[    37.910] (II) Unloading wacom
.....
[  4443.844] (II) config/udev: Adding input device Wacom Serial Touchscreen (/dev/input/event6)
[  4443.844] (II) No input driver/identifier specified (ignoring)

```
The part with stylus, eraser, and cursor repeats multiple times.  It would be nice if it said it was trying on /dev/input/event7, which I presume is the node it is using.

So I have two questions.  In the old wcmSerial.c the code seems to expect at least some serial tablets are on 9600 baud.  Has there been any evidence for that?  Given the error message 'Waited too long for answer' is from wcmWaitForTablet --wait for tablet data in wcmISDV4.c is it the Digitizer II (UD series) isn't responding with recognisable data or is it not at the right baud rate?

---

### Post by tokenrove on 2012-03-07
> **bruis said:**
> 
Copied inputattach to /usr/bin
Then sudo ./inputattach --wacom_iv /dev/ttyS0 &  which returns a a four digit number like 4497.
Then added:  inputattach --wacom_iv /dev/ttyS0 to etc/ rc.local
Logging out and in  loads inputattach as shown in System Monitor.


Forget about copying inputattach anywhere or adding it to rc.local until you have it working in one session -- there should be no need to log in and out to get it to work.  Immediately after you run sudo ./inputattach --wacom_iv /dev/ttyS0 (ensuring that no other inputattach is running), what lines appear in your kernel log? (/var/log/kern.log or /var/log/kernel.log)

Thanks.

---

### Post by tokenrove on 2012-03-07
> **Favux said:**
> So I have two questions.  In the old wcmSerial.c the code seems to expect at least some serial tablets are on 9600 baud.  Has there been any evidence for that?  Given the error message 'Waited too long for answer' is from wcmWaitForTablet --wait for tablet data in wcmISDV4.c is it the Digitizer II (UD series) isn't responding with recognisable data or is it not at the right baud rate?

I have tried for some time to confirm whether any of the protocol IV tablets handle a speed greater than 9600 bps.  This is the speed my driver runs at; you might note in the newer inputattach, I have added the same kind of reset sequence as the old wcmSerial, starting at 38400 and going down to 9600.

Certainly my Digitizer II doesn't seem to handle anything faster than 9600 bps, and that seems to be the report from other users, but I remain curious.  It must be a win to have a higher link speed, but as far as I could see, in the case of protocol IV tablets, the old driver always ran at 9600 bps.  Note that for protocol V tablets, it seemed to have some negotiation code for moving to a higher link speed.

It would be great if I could get consistent reports about this behavior from owners of other tablets, but I guess I would have to write an appropriate testing tool -- easy enough to do, but I don't have a lot of time to dedicate to it.

In this case, I'm wondering if my recent changes have broken older tablets -- my Digitizer II works fine, but it's a newer ROM version.

---

### Post by Favux on 2012-03-07
OK, that clears it up some.  I did see the new reset code which is why I brought it up.  So the serial tablets are at 9600 and not going to 19200, as far as we can tell.  So why the heck does the old wcmSerial.c code start negotiation at 38400?  Leftover before ISDV4 devices were moved to ISDV4.c?  And why duplicate that in inputattach?  Are we thinking one of the last models of serial V tablets was at 38400?  Maybe with 19200 skipped altogether?

Maybe there is a "secret" command/request to turn on a higher link speed we don't know?

Since wcmISDV4.c only seems to handle 19200 and 38400 for the ISDV4 devices I was wondering if that was a problem.  I gather from what you're saying it isn't, what matters is what inputattach has negotiated for the baud speed.  And once the correct one is determined we're golden baud-wise.
> In this case, I'm wondering if my recent changes have broken older tablets -- my Digitizer II works fine, but it's a newer ROM version. 
I hope not.

---

### Post by bruis on 2012-03-07
After running sudo ./inputattach --wacom_iv /dev/ttyS0, which is still failing with:
         inputattach: invalid mode '-–wacom_iv'
and nothing appears in my kern.log. No sign of anything to do with Wacom since booting up.
But I do see signs of life from previous days:
         Mar  7 06:43:09 celtic kernel: [ 2552.614403] serio: Serial port ttyS0
         Mar  7 06:43:09 celtic kernel: [ 2552.676859] input (null): Wacom tablet: Digitizer II, version 1.5
         Mar  7 06:43:09 celtic kernel: [ 2552.676863] input (null): Max pressure: 255.
         Mar  7 06:43:09 celtic kernel: [ 2552.714715] input (null): Configuration string: ~RE202C900,002,02,1270,1270
         Mar  7 06:43:09 celtic kernel: [ 2552.737523] input (null): Coordinates string: ~C15240,15240
         Mar  7 06:43:09 celtic kernel: [ 2552.737645] input: Wacom protocol 4 serial tablet as /devices/pnp0/00:06/tty/ttyS0/serio2/input/input6

I had my suspicions about baud rates also.  
Using CuteCom, with device set to /dev/ttyS0, I tried various baud rates while moving the pen on the tablet.
At 9600 and up to about 38400 the output looked varied but at 115200 the output was all zeros.

---

### Post by tokenrove on 2012-03-08
> **bruis said:**
> After running sudo ./inputattach --wacom_iv /dev/ttyS0, which is still failing with:
         inputattach: invalid mode '-–wacom_iv'
and nothing appears in my kern.log. No sign of anything to do with Wacom since booting up.


Okay, this suggests that somehow the wrong version of inputattach is being run.  Make sure the md5sum of the .c file matches:
0cfc5eebd39abd26c61ea3fcd43c82b0  src/wacom_serial/inputattach.c
remove the inputattach binary and recompile it.  The above can only happen if an unmodified inputattach is being used (maybe the patch in the directory got applied by accident, and assumed -R?).

As for below:

> **bruis said:**
> 
But I do see signs of life from previous days:
         Mar  7 06:43:09 celtic kernel: [ 2552.614403] serio: Serial port ttyS0
         Mar  7 06:43:09 celtic kernel: [ 2552.676859] input (null): Wacom tablet: Digitizer II, version 1.5
         Mar  7 06:43:09 celtic kernel: [ 2552.676863] input (null): Max pressure: 255.
         Mar  7 06:43:09 celtic kernel: [ 2552.714715] input (null): Configuration string: ~RE202C900,002,02,1270,1270
         Mar  7 06:43:09 celtic kernel: [ 2552.737523] input (null): Coordinates string: ~C15240,15240
         Mar  7 06:43:09 celtic kernel: [ 2552.737645] input: Wacom protocol 4 serial tablet as /devices/pnp0/00:06/tty/ttyS0/serio2/input/input6


This looks good; if you can get back to this state again (as I suggested: not putting inputattach in the background, not starting it from any scripts, just getting it running in the foreground) we can move forward to seeing why X isn't liking it.

Baud rates should have nothing to do with it for this tablet -- it's a newer ROM version than mine (1.5 instead of 1.4) but otherwise should be quite similar.

---

### Post by bruis on 2012-03-09
There's good news and not so good news.
Not so good first. The behavior of the PC that I have been using has got very flaky. Looks like the graphics card is on the way out so checking out inputattach as you suggest will have to wait a day or two.

The good news is that my tablet is running nicely on my backup PC. It's Oneiric Kubuntu with the latest wacom-serial.ko and I am testing in MyPaint. Pressure is working nicely and the drawing speed is more than fast enough.

I have not yet installed any xorg.conf or rules, not even 70-serial-wacom.rules. 
I assume a 50-wacom.conf in /usr/share/X11/xorg.conf.d is involved in things.

I am happy to supply any logs or further details.

---

### Post by Favux on 2012-03-09
Sorry to hear about your video card but the UD working on the backup PC is good news.  :)

You can check things out quickly by posting the output of *xinput list*.  Then using the stylus <device name> from that output post the output of:
```
xinput list-props "device name"
```
I assume wacom_serial is showing in *lsmod*.

---

### Post by bruis on 2012-03-09
The second day and the UD1212 is still running OK.
How well is yet to be determined but some preliminary sketching in Gimp is promising.

I have started inputattach in a terminal several times now and success depends on either letting it 'hang' or closing the terminal. Ctrl-C stops inputattach and adding '&' does nothing but return a number.

I'll try 70-serial-wacom.rules as soon as I'm familiar enough with the current situation to notice any changes.

From the attachment you will see that  xinput list-props "device name" has not worked but everything else that I could think of did.

Many thanks to tokenrove and Favux.

---

### Post by Favux on 2012-03-10
Hi bruis,

Thanks for the diagnostics.  Looking pretty good.

With list-props you have to put the "device name" in quotes:
```
xinput list-props "Wacom protocol 4 serial tablet stylus"
```
Sorry I wasn't clear.

The ampersand is for use of inputattach in rc.local.  Run in the terminal with sudo it is a running process dependent on the terminal which is why Ctrl-C stops it.  Closing the terminal would stop it too.

Just for fun why don't you open a second terminal and run *top*.  I'm curious if wacom_serial uses much memory, or even enough to be seen in the top 10 or 20.  Does it use noticeably more when the stylus is on the tablet?  And if it shows you can watch it disappear when you Ctrl-C inputattach.

---

### Post by bruis on 2012-03-10
Thanks, input list-prop worked. Very interesting.
Am I looking for something with wacom in top? If so there no sign of it in the list.
The list does go off the terminal window so I assume its just out of sight?

My tablet stays active when I close the terminal. So far.

---

### Post by bruis on 2012-03-10
[QUOTE=tokenrove;11750223]Okay, this suggests that somehow the wrong version of inputattach is being run.  Make sure the md5sum of the .c file matches:
0cfc5eebd39abd26c61ea3fcd43c82b0  src/wacom_serial/inputattach.c
remove the inputattach binary and recompile it.  The above can only happen if an unmodified inputattach is being used (maybe the patch in the directory got applied by accident, and assumed -R?).

Back at my main PC. 
Tried md5sum and it was good. Tried new compile. Still getting  *invalid mode '--wacom_iv'*
For the last hour or so I have been trying to find what relevant differences between my recalcitrant PC and the PC with the working UD1212 might exist.
Now I have found that when *inputattach --help* is run there is a  --wacom_iv entry with the working PC but not with the other one.

---

### Post by tokenrove on 2012-03-27
Hi,

I've updated the Wacom IV driver again.  The current version can be found at:
  [http://cipht.net/releases/wacom_serial-120327-1.tar.bz2](http://cipht.net/releases/wacom_serial-120327-1.tar.bz2)

Notably, I think this fixes some issues with the eraser I've been having.  I would appreciate it if anyone with a protocol 4 tablet could try this driver and let me know: (email [email]julian@cipht.net[/email] or post here)
1) Does the eraser work?  Is it recognized as a separate tool in Gimp? (with the input devices window open)
2) Does your pen register touch before you have actually made contact with the surface of the tablet? (I received a bug report and patch for this behavior, which doesn't occur for me in current versions of the driver.  I'd like to determine whether it happens for anyone else on the current version.)
3) Do you have a puck?  Does it work?  How about when you switch between the puck and the pen without leaving the tablet surface?
4) Do you have any use for the pad buttons on the tablet?  Do you know any software that makes use of them? (Pad button support is easy enough to add, but I haven't bothered for lack of compelling reasons to add it.)

If I don't hear from anyone with a Graphire, I'm going to remove that code from the driver.  After that, I'm going to try to get this integrated into the kernel mainline.

Thanks to everyone, especially Favux for maintaining this thread.

---

### Post by bserem on 2012-03-27
For some reason the forum hadn't send any emails all this time about this issue being updated. It did just know.

I'll look into the last 3-4 pages that I've lost and see where this is going.
I do not have me Penpartner connected but I can plug it in to test the new drivers :)

---

### Post by Kinst on 2012-03-30
Wait, so I have a Thinkpad x61t with an integrated tablet pc pen, but I'm stuck here.

sudo inputattach --wacom_iv /dev/ttyS0

inputattach: device initialization failed


How do I know whether mine is ttyS0 or some other location by the way? I'm lost right now :-(

---

### Post by Favux on 2012-03-30
Hi Kinst,

The Thinkpads have an ISDV4 wacom serial digitizer.  ISDV4's are still supported by the standard xf86-input-wacom driver.  No need to patch it.

Are you using Oneiric (11.10) by any chance?

Actually right now there are two drivers for ISDV4 devices.  The xf86-input-wacom driver and you can also use a serio driver like the ones on this HOW TO called wacom_w8001.ko that works with input-attach.  Are you trying to set up wacom_w8001.ko?

---

### Post by Kinst on 2012-03-31
Oh thanks, that helps a lot! I actually was using 10.10, but a synaptic update recently broke my pen driver, and then I updated again to the 12.04 beta. I guess it must be a totally different driver problem though!

---

### Post by Favux on 2012-03-31
Then I suspect the problem in Precise is the same as in Oneiric if it isn't working out of the box.  The Distros including Ubuntu have added a new udev rule to enable the inputattach/wacom_w8001.ko combo which means they inadvertently disabled the normal driver providing out of the box support.

The udev rule is in /lib/udev/rules.d/40-inputattach.rules.
```
# Attach Wacom W8001 devices
SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="FUJ02e5|WACf00c", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 19200 --w8001 /dev/%k"

```
So you comment (#) it out:
```
# Attach Wacom W8001 devices
#SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="FUJ02e5|WACf00c", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 19200 --w8001 /dev/%k"

```
Using:
```
gksudo gedit /lib/udev/rules.d/40-inputattach.rules
```
After a reboot you should see the digitizer in xinput list and hopefully it will be working. Provided of course you didn't mess up xf86-input-wacom or reinstall the package it is in xserver-xorg-input-wacom.

---

### Post by Kinst on 2012-04-01
Hmm, after your instructions, this is what I get:

```
mshaw@Pierre:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons 
```

It hasn't responded yet... xserver-xorg-input-wacom is installed.

---

### Post by Favux on 2012-04-01
Likely either your 50-wacom.conf isn't installed or is wrong or you need to reinstall the Wacom package.

What are the contents of /usr/share/X11/xorg.conf.d/50-wacom.conf?

---

### Post by Kinst on 2012-04-01
```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM|Hanwang|PTK-540WL|ISD-V4"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection

# Waltop tablets
Section "InputClass"
	Identifier "Waltop class"
	MatchProduct "WALTOP"
	MatchIsTablet "on"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection

```

---

### Post by Favux on 2012-04-01
Well that looks good so one of the two serial snippets should be matching.  The PnP identifier begins with 'WACf' which is why one of the snippets uses it in the match.

Lets see if we can find out what ttyS port it is on.  Enter in a terminal:
```
sudo dmesg | grep ttyS
```
and post the output.

---

### Post by Kinst on 2012-04-01
The output is blank :confused:

If I put tty I get:

```
sudo dmesg | grep tty
[    0.000000] console [tty0] enabled
```

---

### Post by Favux on 2012-04-01
> The output is blank
Well now we have to wonder about a hardware problem.  Does the digitizer work in another release or Distro or Windows?  It could be a loose connection i.e. digitizer to motherboard.  It would be good to r/o hardware problems before going on.

---

### Post by Kinst on 2012-04-01
Well it works in Windows (dual boot).

---

### Post by Favux on 2012-04-01
Good, so it isn't a hardware problem.

You should start a new thread and move the discussion there.

On the new thread post your Xorg.0.log.  It is in /var/log.  Because it is big right click on it and compress it and attach it to your post in the new thread.  We'll see if anything is showing up in Xorg.0.log to explain the why the digitizer isn't being seen.

---

### Post by bruis on 2012-04-04
I have recently got my Digitizer II with Oneiric working nicely.
Very usable in Gimp or Krita. Except for two things: Stylus Button 3 and eraser.
They would do nothing, sound asleep.

Installed wacom-serial-120327 today and now both are active.
In fact one is a bit too active, whatever I assign to the eraser (number or key) is also assigned to Button 3, overriding any setting that Button 3 might have. 
For example in MyPaint, Krita or Gimp I get two erasers. Or two zoom ins.

Must hold down Stylus Buttons 2 or 3 and then touch the tablet surface before they work. Similar with eraser, although all three cause the tablet status light to blink when hovering.

By pad buttons do you mean the menu strip with 22 buttons?

---

### Post by Favux on 2012-04-04
Hi bruis,

Are you using Oneiric?
> Installed wacom-serial-120327 today and now both (button 3 and eraser) are active.
Good!
> In fact one is a bit too active, whatever I assign to the eraser (number or key) is also assigned to Button 3, overriding any setting that Button 3 might have. 
There have been a couple of xsetwacom fixes recently.  One today.  Could you compile the git repository for xf86-input-wacom?  Instructions on part II. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Which reminds me that I'm way overdue to update appendix 1.  That will hopefully tell us if the problem is in the X driver or wacom_serial.
> Must hold down Stylus Buttons 2 or 3 and then touch the tablet surface before they work. Similar with eraser, although all three cause the tablet status light to blink when hovering.

That sounds like the TPCButton (tablet PC button) option is on.  The gnome-settings-daemon was turning that on for drawing tablets which was a bug.  Check with dconf-editor (probably have to install it) in org.gnome.settings-daemon.peripherals.wacom.  I don't remember if the Wacom tablet applet in System Settings can access that key.  You can test first by setting the xsetwacom parameter TabletPCButton to off.

---

### Post by bruis on 2012-04-04
I am using Kubuntu 11.10 and a Digitizer II  UD-1212-R

Sorry about my Hover Click button remarks.  I did not intend them to sound like a problem, but was responding to tokenrove #349.  
 
With TabletPCButton "off"/Hover Click = 0 the pen tip must touch the tablet surface before any action happens. 
With TabletPCButton "on"/Hover Click = 1  the pen tip can hover and click to cause some actions.  It seems this applies to "number actions"  not "key type actions".

I did not realise that my xsetwacom  was slipping behind. It is version 0.11.0 installed with xserver-xorg-input-wacom. I assume this would need to be uninstalled before going to the git repository for xf86-input-wacom?

Don't use the KDE Wacom applet, more trouble than it was worth. A few xsetwacom settings in a xsessionrc file works fine.

---

### Post by Favux on 2012-04-05
> my xsetwacom was slipping behind. It is version 0.11.0 installed with xserver-xorg-input-wacom. I assume this would need to be uninstalled before going to the git repository for xf86-input-wacom?
No you can compile xf86-input-wacom right over it.  The only gotcha is if you end up with two versions of the xsetwacom executable/binary but the flag in the HOW TO should prevent that.
> With TabletPCButton "off"/Hover Click = 0 the pen tip must touch the tablet surface before any action happens.
With TabletPCButton "on"/Hover Click = 1 the pen tip can hover and click to cause some actions. It seems this applies to "number actions" not "key type actions".
That's reversed from what it should be.  I suspect that is the problem and I'm thinking your version of xf86-input-wacom had a bug that reversed them.  So the driver default is correct but it is having the opposite of the intended effect, follow?
> Don't use the KDE Wacom applet, more trouble than it was worth. A few xsetwacom settings in a xsessionrc file works fine. 
That's what I do too.  The configuration applets have been having trouble keeping up with all the changes.  But the KDE developer has done much better than the Wacom Control Panel developer.  The GNOME Wacom tablet applet is catching up now.  However I noticed that it appears broken in Precise right now in Beta2 (I just installed it).  So that isn't good.  Peter just made some commits for it that may fix the problem but Precise is in freeze now so who knows if and when the commits will be backported to Precise?  Oh well.

Jason just posted a bunch of new patches that will affect configuration.  So some more fun should ensue.

---

### Post by bruis on 2012-04-05
> There have been a couple of xsetwacom fixes recently.  One today.  Could  you compile the git repository for xf86-input-wacom?  Instructions on  part II. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562"). 

Now have Xsetwacom 0.14.0, compiled and installed smoothly thanks to your clear instructions. 

However nothing has changed in regard to either the "Button 3 / Eraser" 
or the Hover Click "reverse" problems.  The latter has always been confusing because when setting  TabletPCButton "off" with xsetwacom and then '"xsetwacom get "Wacom protocol 4 serial tablet stylus" all" will display "TabletPCButton" "on".

While Button 3 takes whatever action that the Eraser has been assigned there is also another effect. For example assigning Eraser Button 1 "3"  causes both Button 3 and the Eraser to have a dual function. When within the drawing area they both behave like an Eraser and outside of the drawing area they behave as a Right Click.

Anyway it is still very good to have my old UD1212-R  back in business.

---

### Post by Favux on 2012-04-05
> Now have Xsetwacom 0.14.0, compiled and installed...However nothing has changed in regard to either the "Button 3 / Eraser" or the Hover Click "reverse" problems. The latter has always been confusing because when setting TabletPCButton "off" with xsetwacom and then '"xsetwacom get "Wacom protocol 4 serial tablet stylus" all" will display "TabletPCButton" "on".

Alright, then maybe we're dealing with a wacom_serial problem and we need **tokenrove** to take a look at this.
> While Button 3 takes whatever action that the Eraser has been assigned there is also another effect. For example assigning Eraser Button 1 "3" causes both Button 3 and the Eraser to have a dual function. When within the drawing area they both behave like an Eraser and outside of the drawing area they behave as a Right Click.
That is a bit weird, isn't it?  :)
> Anyway it is still very good to have my old UD1212-R back in business. 
I think so too.

---

### Post by tokenrove on 2012-04-05
> **bruis said:**
> 
In fact one is a bit too active, whatever I assign to the eraser (number or key) is also assigned to Button 3, overriding any setting that Button 3 might have. 
For example in MyPaint, Krita or Gimp I get two erasers. Or two zoom ins.

Right, I'm pretty sure this is a simple bug in my driver.  I will try to take a look at it this weekend.  I also have reports of the eraser occasionally jumping around.

BTW, as for the TabletPCButton stuff, it's on the xorg driver side, so I suspect the problem is that I need to register a specific ID to send that won't have TPC associated with it (the Xorg wacom code just looks at the device ID information and has a static table of properties associated with it -- of course being unaware of my driver, they wouldn't have a correct entry in these tables for it).

> **bruis said:**
> 
By pad buttons do you mean the menu strip with 22 buttons?

Right.  (16 buttons on mine)

---

### Post by bruis on 2012-04-15
> **tokenrove said:**
> 

4) Do you have any use for the pad buttons on the tablet?  Do you know any software that makes use of them? (Pad button support is easy enough to add, but I haven't bothered for lack of compelling reasons to add it.)


I think that any program like Gimp or Inkscape that has configurable shortcut keys may be able to use Pad buttons by xsetwacom mapping the buttons to the same key(s) that Gimp or Inkscape use for the required action. I use this method for the two stylus buttons.
Griatch, the Gimptalk administrator, recommends this method for setting up tablet buttons or menustrips in Gimp. He advises leaving the Pad disabled as he claims Gimp does not use it and turning it on will only mess things up. This last info is about 5 years ago so perhaps it is not the case now.

It would be great to have the Pad buttons available.

---

### Post by dreh on 2012-04-19
hello list,
12.04 final beta is around. Did someone test tokenroves driver already. Is the architecture complete different again? Will wacom (serial 4) will be functioning native without patches?

I'm curious about the LTS release. Favux will you open a new thread?
Best
dreh

---

### Post by dreh on 2012-04-19
> **tokenrove said:**
> Hi,
1) Does the eraser work?  Is it recognized as a separate tool in Gimp? (with the input devices window open)
2) Does your pen register touch before you have actually made contact with the surface of the tablet? (I received a bug report and patch for this behavior, which doesn't occur for me in current versions of the driver.  I'd like to determine whether it happens for anyone else on the current version.)
3) Do you have a puck?  Does it work?  How about when you switch between the puck and the pen without leaving the tablet surface?
4) Do you have any use for the pad buttons on the tablet?  Do you know any software that makes use of them? (Pad button support is easy enough to add, but I haven't bothered for lack of compelling reasons to add it.)

Hi Tokenrove,
I used your NEW driver and indeed my eraser is working for the first time. (Wacom Digitizer II UD-1218-R Linux ali 3.0.0-17-server #30-Ubuntu SMP Thu Mar 8 22:15:30 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
)
Answers:
1) Yes
2) No
3) No
4) Yes I would love to use the PAD buttons got 32 + setup button + softer/firmer button. Though I don't know any (linux) programms that can access these. But it would be awesome if you could use these in the system (Cut Copy Paste Undo New Open Save Print) switch between ABS/REL change Pressure Curve, automatize anything in unity or with shell scripts. Maybe even double functions with ALT key+click

Hope this helps and thanks for doing this. 
dreh

---

### Post by Favux on 2012-04-19
Hi dreh,

> 12.04 final beta is around. Did someone test tokenroves driver already. Is the architecture complete different again?
I've installed Beta2.  It looks like wacom_serial and wacom_serial5 should work the same as Oneiric.
> Will wacom (serial 4) will be functioning native without patches?

No, the drivers need to be submitted to the kernel first along with patches to inputattach.
> I'm curious about the LTS release. Favux will you open a new thread?
Unity in Precise seems the best Unity so far.  Hadn't planned on a new thread.  I suppose it depends on how things work in Precise.  I've been hoping to update the HOW TO to installing input-wacom anticipating once the drivers are submitted to the kernel that they'll also be submitted to input-wacom.  I already asked Chris if that would be OK and he said yes provided they were working.  His only concern is none of the LWP developers has a serial tablet to test with anymore (although I wonder if Ping does), so they couldn't fix the drivers if they aren't working.

---

### Post by dreh on 2012-04-23
Hi,
i updated to 12.04 and everything seemd to work and it did for some days. Now I can't get it work anymore and I'm quite puzzled.

This is what I do:
download latest driver von tokenrove --> compile --> insmod --> inputattach (compiled version)
nothing happends

This is what I checked:
1. no (old) inputattach in processes
2. no (old) kernel modul
3. tail -f /var/log/syslog
```
Apr 23 23:10:35 ali kernel: [  795.051015] serio: Serial port ttyS0
Apr 23 23:10:35 ali kernel: [  795.051172] input: TSC-10/25/40 Serial TouchScreen as /devices/pnp0/00:08/tty/ttyS0/serio4/input/input7
```

/usr/share/X11/xorg.conf.d/50-wacom.conf:
```

Section "InputClass"
        Identifier "Wacom class"
        MatchProduct "Wacom|WACOM|Hanwang|PTK-540WL|ISD-V4"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class"
        MatchProduct "Serial Wacom Tablet"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection

# Waltop tablets
Section "InputClass"
        Identifier "Waltop class"
        MatchProduct "WALTOP"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001|N-Trig Pen"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        Option "Button2" "3"
EndSection
```

dmesg | grep ttyS:
```

[    2.528044] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.754027] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  186.960953] serio: Serial port ttyS0
[  186.973561] input: TSC-10/25/40 Serial TouchScreen as /devices/pnp0/00:08/tty/ttyS0/serio2/input/input5
[  291.942251] serio: Serial port ttyS0
[  291.942502] input: TSC-10/25/40 Serial TouchScreen as /devices/pnp0/00:08/tty/ttyS0/serio3/input/input6
[  795.051015] serio: Serial port ttyS0
[  795.051172] input: TSC-10/25/40 Serial TouchScreen as /devices/pnp0/00:08/tty/ttyS0/serio4/input/input7
[ 1927.213147] serio: Serial port ttyS0
[ 1927.213313] input: TSC-10/25/40 Serial TouchScreen as /devices/pnp0/00:08/tty/ttyS0/serio5/input/input8
```

I have not a clue what TSC-10/25/40 Serial TouchScreen is. I never had that before.
I think some udev rule is automagically ?blocking? something. and the touchscreen driver is loaded. How can I debug this.
Thank you. 
dreh

---

### Post by Favux on 2012-04-23
My first guess is somehow that the tablet is being placed on the tsc40.ko serio driver.  Your right, probably through a udev rule.  See if you see ***tsc40*** in *lsmod*.  Since it is located in /lib/modules/`uname -r`/kernel/driver/touchscreen you could try renaming it:
```
sudo mv /lib/modules/`uname -r`/kernel/driver/touchscreen/tsc40.ko /lib/modules/`uname -r`/kernel/driver/touchscreen/tsc40.ko.bak
```
and restarting.

Probably need to download the kernel source and look at tsc40.c and see if that tells us anything.  Or get lucky and find the rule in /lib/udev/rules.d.  But my first look there didn't have anything jumping out.  Since it should be matching after 69-xserver-xorg-input-wacom.rules it shouldn't be impossible to find.

---

### Post by Bones.Kendall on 2012-04-24
Hi,

I've been reading and trying to resolve my problem, the odd behavior of the pen with my Toshiba Portege Tablet PC. 

I read this post: [http://ubuntuforums.org/showthread.php?t=1780154]("http://ubuntuforums.org/Hi,%20%20I%27ve%20been%20reading%20and%20trying%20to%20resolve%20my%20problem,%20the%20odd%20behavior%20of%20the%20pen%20with%20my%20Toshiba%20Portege%20M800.%20%20%20I%20read%20this%20post:%20http://ubuntuforums.org/showthread.php?t=1780154"). 

I tried to install tokenrove's wacom_serial.ko, but I get an error.

```
make -C /lib/modules/2.6.32-41-generic/build M=/home/bones/Desktop/wacom_serial modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-41-generic'
  CC [M]  /home/bones/Desktop/wacom_serial/wacom_serial.o
/home/bones/Desktop/wacom_serial/wacom_serial.c: In function ‘handle_model_response’:
/home/bones/Desktop/wacom_serial/wacom_serial.c:165: error: implicit declaration of function ‘input_abs_set_res’
make[2]: *** [/home/bones/Desktop/wacom_serial/wacom_serial.o] Error 1
make[1]: *** [_module_/home/bones/Desktop/wacom_serial] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-41-generic'
make: *** [modules] Error 2

```I figure something is off with my system. I have been updating a lot just hoping that this problem goes away, but I use my pen to grade essays, so if I could figure this out I'd get back on track. 

Any help is appreciated.

Thank you,

Bones

---

### Post by Favux on 2012-04-24
Hi Bones.Kendall,

Welcome to Ubuntu forums!

This thread is for Wacom serial graphics tablets or legacy serial tablets.  You have a ISDV4 device/wacom digitizer.  All ISDV4 devices so far have been in tablet PCs.  And ISDV4 devices are supported by the xf86-input-wacom X driver unlike the legacy serial graphics tablets.  The wacom_serial.ko won't work for you.  However the wacom_w8001.ko with inputattach should.

It looks like you are using Lucid because I see the 2.6.32 kernel.  Is that correct?  Would you mind starting a new thread for your problem?  On it post the output of the following terminal command:
```
xinput list
```
Also do you have the default xf86-input-wacom for Lucid or have you updated it?  What is
> the odd behavior of the pen with my Toshiba Portege Tablet PC
you're seeing?

---

### Post by dreh on 2012-04-24
> **Favux said:**
> tsc40.ko --> tsc40.ko.bak and restarting.

did the trick. But still odd why this happend. Thanks Favux!
dreh

---

### Post by dreh on 2012-04-24
me again,
I found some wierdness going on here:
pen works:
```
xsetwacom  --set "Wacom protocol 4 serial tablet stylus" Threshold 400
xsetwacom  --get "Wacom protocol 4 serial tablet stylus" Threshold
400
```
If I turn the pen and use the eraser the Stylus changes back to default (27)
```
xsetwacom  --get "Wacom protocol 4 serial tablet stylus" Threshold
27
```
So the eraser is "erasing" my settings. Inputattach is running in another shell (and blocking it) - my 2 cents: can it be that inputattach is "reconfiguring" the tablet everytime another "input device" is used?
Is there something I can do to debug the driver?
Best
dreh

---

### Post by Favux on 2012-04-24
Hi dreh,

I see the same thing with Threshold.  It could be tokenrove's recent change to eraser with the latest wacom_serial but I think it is xf86-input-wacom.  What version do you have?

My guess is unlike PressureCurve, which can be different for the stylus and eraser, Threshold is tablet wide so whatever you have stylus set to is what is used.  Or else there's a bug in xf86-input-wacom.  Were you able to use different values before?

Both *man wacom* and *man xsetwacom* have the debug commands.  They've changed in xsetwacom so you want to check your manual.  What you should be able to do for any static option is add a custom xorg.conf.d .conf file to /etc/X11/xorg.conf.d called say 52-wacom-options.conf.  Something like:
```
Section "InputClass"
	Identifier "Wacom Bamboo stylus options"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"

	# Apply custom Options to this device below.
	Option "Button2" "3"
	Option "Button3" "2"
	Option "PressCurve" "0,10,90,100"
EndSection

Section "InputClass"
	Identifier "Wacom Bamboo eraser options"
	MatchDriver "wacom"
	MatchProduct "eraser"

	# Apply custom Options to this device below.
	Option "PressCurve" "5,0,100,95"
EndSection

Section "InputClass"
	Identifier "Wacom Bamboo cursor options"
	MatchDriver "wacom"
	MatchProduct "cursor"

	# Apply custom Options to this device below.
	Option "Button1" "1"
	Option "Button2" "2"
	Option "Button3" "3"
EndSection
```
Where the debug options for the stylus would be:
```
	Option "DebugLevel" "12"
	Option "CommonDebug" "12"
```
Of course it's easy for eraser and cursor but we'd have to figure out a stylus snippet that would match.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d)
For xsetwacom:
```

xsetwacom set <stylus device name or ID #> TabletDebugLevel 12
xsetwacom set <stylus device name or ID #> ToolDebugLevel 12

```
And Xorg.0.log in /var/log would start filling with debug info. since 12 is the max. level.

> tsc40.ko --> tsc40.ko.bak and restarting did the trick. But still odd why this happend. 
Agreed.  Thanks for confirming that which makes it a udev rule match problem.

So far no luck figuring out why.  The tsc40.c doesn't look to be the culprit:
```
	input_dev->name = "TSC-10/25/40 Serial TouchScreen";
	input_dev->phys = ptsc->phys;
	input_dev->id.bustype = BUS_RS232;
	input_dev->id.vendor = SERIO_TSC40;
	input_dev->id.product = 40;
	input_dev->id.version = 0x0001;
	input_dev->dev.parent = &serio->dev;
```
Don't see anything in rules.d that would do it.  And I was wrong since there is no match in 69-wacom.rules to the legacy serial tablets the match could be happening anywhere.  We'll need tokenrove to figure this one out I'm afraid.

Now that we know "for sure" it is a rule probably the correct way to handle it would be to use tokerove's rule rather than renaming the tsc40.ko module.  Need create a .rules file for it in /etc/udev/rules.d and use say 99 for its number.

---

### Post by tokenrove on 2012-04-24
> **Favux said:**
> So far no luck figuring out why.  The tsc40.c doesn't look to be the culprit:
```
    input_dev->name = "TSC-10/25/40 Serial TouchScreen";
    input_dev->phys = ptsc->phys;
    input_dev->id.bustype = BUS_RS232;
    input_dev->id.vendor = SERIO_TSC40;
    input_dev->id.product = 40;
    input_dev->id.version = 0x0001;
    input_dev->dev.parent = &serio->dev;
```Don't see anything in rules.d that would do it.  And I was wrong since there is no match in 69-wacom.rules to the legacy serial tablets the match could be happening anywhere.  We'll need tokenrove to figure this one out I'm afraid.


Sorry I haven't had time to take a look at this, but what is the value of SERIO_TSC40?  If it's the same as SERIO_WACOM_IV (which I stupidly set to the lowest unused number, thinking I would have gotten the driver merged shortly after releasing it), that could be causing the problem.

As for the Threshold stuff, the kernel driver doesn't control many things like that so I doubt it's at issue, but I am going to review all such reports about behavior shortly.

Thanks everyone.

---

### Post by Favux on 2012-04-24
Ah, thanks tokenrove, that's it.  In serio.h at linux-3.2/include/linux it's 0x3d, and the last one:
```
#define SERIO_HAMPSHIRE	0x3b
#define SERIO_PS2MULT	0x3c
#define SERIO_TSC40	0x3d

#endif
```
So dreh since we're up to kernel 3.4 rc changing it in wacom_serial.c from:
```
/* XXX To be removed before (widespread) release. */
#ifndef SERIO_WACOM_IV
#define SERIO_WACOM_IV 0x3d
#endif
```
to:
```
/* XXX To be removed before (widespread) release. */
#ifndef SERIO_WACOM_IV
#define SERIO_WACOM_IV 0x3e
#endif
```
before you compile should work.  But tokenrove will have to see what it is up to when he submits to the kernel.

Edit:  The 3.4 rc kernel shows the tsc40.ko's 0x3d is the last serio protocol added to serio.h so in the HOW TO I've suggested shifting both wacom serio .ko's by one, 0x3e for wacom_serial.ko and 0x3f for wacom_serial5.ko.  That should be safe with luck provided the kernel submissions are in the near future.

---

### Post by dreh on 2012-04-25
This is what I did:
sudo mv tsc40.ko.bak tsc40.ko
reboot
changed wacom_serial.c from:
#define SERIO_WACOM_IV 0x3d --> #define SERIO_WACOM_IV 0x3e
make all
sudo insmod ./wacom_serial.ko
sudo inputattach --wacom_iv /dev/ttyS0
dmesg | grep tty
```
[    0.000000] console [tty0] enabled
[    2.513300] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.739314] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  238.801468] serio: Serial port ttyS0
[  238.814157] input: TSC-10/25/40 Serial TouchScreen as /devices/pnp0/00:08/tty/ttyS0/serio2/input/input5
```
Unfortunately this doesn't work for me.

---

### Post by Favux on 2012-04-25
Interesting.  I think it should have.  Could you check the date on the wacom_serial.ko you are insmodding?  Make sure it is the new one with 0x3e.

---

### Post by dreh on 2012-04-25
I don't think I made a mistake changing this.
#define SERIO_WACOM_IV 0x3d --> #define SERIO_WACOM_IV 0x3e
and recompiling and inserting the new driver.

What I found out is if I backup the tsc40.ko --> tsc40.ko.bkp again
I can't use the new compiled driver with 0x3e. The driver has to be 0x3d again. Otherwise nothing will show up in dmesg. I'm guessing something else has to match than just 0x3e in wacom_serial.c. Can it be that now a udev rule has to get updated too?
70-serial-wacom.rules shows:
```
ACTION=="add|change", SUBSYSTEM=="pnp", ENV{PRODUCT}='13/3d/*', ENV{NAME}=="Wacom protocol IV serial tablet",SYMLINK+="input/wacom",ENV{ID_INPUT}="1",ENV{ID_INPUT_TABLET}="1"
```
I have not really understand the udev system.

---

### Post by Favux on 2012-04-25
Ah ha.  Was that udev rule active when you tried the edited wacom_serial.c?  Try commenting out (#) that rule and using the new wacom_serial.ko with 0x3e.

Or let's see, to fix that rule, maybe:
```
ACTION=="add|change", SUBSYSTEM=="pnp", ENV{PRODUCT}=='13/3e/*', ENV{NAME}=="Wacom protocol IV serial tablet",SYMLINK+="input/wacom",ENV{ID_INPUT}="1",ENV{ID_INPUT_TABLET}="1"
```
I'm not entirely sure how the ENV{PRODUCT} works, especially without seeing an attributes walk.


Edit:  Fix ENV{PRODUCT}='13/3e/*' to ENV{PRODUCT}=='13/3e/*'.

---

### Post by dreh on 2012-04-25
Both ways don't work. There has to be something else than just addressing the wacom_serial driver.

---

### Post by Favux on 2012-04-25
OK, thank you for checking this out though.  :)

I'm stumped right now, have to look some more.

---

### Post by Favux on 2012-04-25
Doh, think I found it almost right away.  :redface:

In the wacom_serial folder open the file serio-ids.h and change line #129 from:
```
#ifndef SERIO_WACOM_IV
# define SERIO_WACOM_IV		0x3d
#endif

#endif
```
to:
```
#ifndef SERIO_WACOM_IV
# define SERIO_WACOM_IV		0x3e
#endif

#endif
```
and then recompile inputattach.

---

### Post by dreh on 2012-04-25
> **Favux said:**
> Doh, think I found it almost right away.  :redface:

In the wacom_serial folder open the file serio-ids.h and change line #129 from:
```
#ifndef SERIO_WACOM_IV
# define SERIO_WACOM_IV		0x3d
#endif

#endif
```
to:
```
#ifndef SERIO_WACOM_IV
# define SERIO_WACOM_IV		0x3e
#endif

#endif
```
and then recompile inputattach.
YIHA! This did the trick! No interference with the tsc40 driver. Well done Favux!

---

### Post by Favux on 2012-04-25
Thanks, but you were the one who figured it out.  You sensed something else was grabbing it and you were right.

Cripes, now I have to change the HOW TO again.  Have to put in editing serio-ids.h and the rule (assuming I fixed it correctly).  Should I maybe leave roaldfre's wacom_serial5 with 0x3e?  How many people have both a serial IV and serial V tablet after all?

---

### Post by dreh on 2012-04-25
The udev rule is not working for me. I actually never got the driver running on boot. Maybe thats the next task for me.
Should wacom_serial.ko gets automatically loaded when inputattach is called? My kernel module is not getting loaded. I always did this with a shell script. Is this a udev rule?

---

### Post by Favux on 2012-04-25
> The udev rule is not working for me.
Alright, I'll leave it up to tokenrove and not put it in the HOW TO.  So just leave the udev rule for wacom_serial commented out.
> I actually never got the driver running on boot...
Should wacom_serial.ko gets automatically loaded when inputattach is called? My kernel module is not getting loaded. I always did this with a shell script. 
When inputattach gets loaded in rc.local it should bring along wacom_serial.ko automatically just like it was just doing with tsc40.ko.  It's been reported that adding a '&' helps in some systems, as described in the HOW TO.  Do you have your current working wacom_serial.ko copied to /lib/modules/`uname -r`/kernel/drivers/input/tablet?  And then ran 'sudo depmod -a'?

---

### Post by dreh on 2012-04-26
I have another question the ubuntu system settings -> wacom graphics tablet recognizes that a tablet is connected but it seems like values are ignored. Is this a known issue?

---

### Post by dreh on 2012-04-26
> **Favux said:**
> Alright, I'll leave it up to tokenrove and not put it in the HOW TO.  So just leave the udev rule for wacom_serial commented out.


To answer my own questions. The udev rule works I've overseen the "="-typo in ENV{PRODUCT}=='13/3d/*'. Even the system settings are now recognized. Now I have to adjust the threshold in a custom 52 rule and I'm a happy user! I've seen an odd behaviour that maybe helps for the "&"-workaround in rc.local: I copied my own inputattach to /usr/bin but theres another one in /lib/udev I ignored till now. If i type sudo /lib/udev/inputattach --wacom_iv /dev/ttyS0 my tablet starts working although that file is untouched and my shell stays interactive!
ps aux | grep inputattach gives
```
root      3580  0.0  0.0   4160   348 ?        S    11:27   0:00 inputattach --wacom_iv /dev/ttyS0
```
although it's not a softlink from /lib/udev/ to /usr/bin. I'm not sure what to make out of this since I have not a clue how linux works in the background.

---

### Post by Favux on 2012-04-26
Outstanding dreh!

When you corrected:
```
ENV{PRODUCT}='13/3d/*'
```
to
```
ENV{PRODUCT}=='13/3d/*'
```
did you use?
```
ENV{PRODUCT}=='13/3e/*'
```
Or did you leave it as d?  So you need the rule for Wacom Graphics Tablet to work, i.e. recognize the tablet.  They did add a fix to libwacom for the generic stylus so that tablets not reporting stylus ID (e.g. protocol 4 tablets) would work.  I guess that's in the Precise GNOME System Settings.

I wonder if that is true for the protocol 5's also?  If so we need to get that rule I was messing with working.

I need to think about what you're telling me about your inputattaches a little more.

---

### Post by Favux on 2012-04-26
Alright that was worth doing as I'm now a little more up to speed on what Ubuntu is doing with inputattach.  I followed the input-wacom instuctions for inputattach and the wacom_w8001.ko modified for the wacom_serial.ko's.  Which is why we're putting inputattach in rc.local.

What Ubuntu is doing is adding rules, /lib/udev/rules.d/40-inputattach.rules:
```
# Attach Wacom W8001 devices
SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="FUJ02e5", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 19200 --w8001 /dev/%k"
SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="WACf00c", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 38400 --w8001 /dev/%k"
```
Then the RUN+ is calling a script (not a symlink) at /lib/udev/inputattach:
```
#!/bin/sh -e
#
# udev script for inputattach

(
	. /lib/udev/hotplug.functions
	wait_for_file /usr/bin/inputattach
	exec /usr/bin/inputattach $*
) &
```
Which in turn is executing the inputattach binary at /usr/bin/inputattach.

So to join the fun we should add the serial protocol 4, assuming 3d is now 3e, to the rules.  Something like:
```
# Attach Wacom W8001 devices
SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="FUJ02e5", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 19200 --w8001 /dev/%k"
SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="WACf00c", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 38400 --w8001 /dev/%k"

# Attach Wacom legacy protocol IV serial tablets
ACTION=="add|change", SUBSYSTEM=="pnp", ENV{PRODUCT}=='13/3e/*', ENV{NAME}=="Wacom protocol IV serial tablet",SYMLINK+="input/wacom",ENV{ID_INPUT}="1",ENV{ID_INPUT_TABLET}="1", RUN+="/lib/udev/inputattach --wacom_iv /dev/%k"
```
And then we wouldn't need to run inputattach out of rc.local, assuming our rule works.  Also since it is a custom rule we should actually add it to say /etc/udev/rules.d/42-wacomlegacyserial-inputattach.rules and let Ubuntu eventually add it to /lib/udev/rules.d/40-inputattach.rules.

However there is a problem.  Ubuntu and some other Distros added this rule and inputattach setup around Natty (2.6.38 ) and it doesn't seem to work.  It has been breaking ISDV4 serial devices (tablet PCs) that should run out of the box.  Since xf86-input-wacom still supports ISDV4 directly and doesn't need wacom_w8001.ko, I've been telling folks to comment out the rules in 40-inputattach.rules.  After a reboot their tablet PC works.

I haven't bothered to figure out if the problem is in the rule, say the port isn't being matched, or if the script is broken.  Or what.

---

### Post by Favux on 2012-04-26
Just a thought.  Does inputattach load your wacom_serial.ko if you make the path to it explicit in rc.local?
```
/usr/bin/inputattach --wacom_iv /dev/ttyS0
**or**
/usr/bin/inputattach --wacom_iv /dev/ttyS0 &
```

---

### Post by dreh on 2012-04-27
sry took a while.
I use this:
> **Favux said:**
> 
```
ENV{PRODUCT}=='13/3d/*'
```


---

### Post by tushantin on 2012-04-27
What's a Protocol IV or V tablet?

Also, I upgraded to Precise (via the standard "Upgrade" method) but... the tablet still seems to have the broken pressure as it did with the distro before. 

Since I'm in Precise, is there a different way of installing it? Different drivers? Reinstall? If so, how?

---

### Post by Favux on 2012-04-27
@ dreh,

So we need tokenrove to explain what that part of the rule is doing or else udevadmin dump and see if we can figure it out.  You can guess what I favor.  :)


Hi tushantin,

What Wacom tablet and model do you have?  If it is a usb tablet this HOW TO doesn't apply.  And you can get information by entering:
```
lsusb
```
in a terminal and looking for (and posting) the tablet line.

Whatever you have Pressure should be working.  What application lacks pressure?

---

### Post by tushantin on 2012-04-27
I think you remember my problem; remember "Wacom Bamboo One", with the pressure maxing out at a certain level and restarting? Breaking the lines? 

As for my model, hitting "lsusb" gives me:
*Bus 002 Device 002: ID 056a:006b Wacom Co., Ltd *

---

### Post by Favux on 2012-04-27
Yes I do remember now that you have reminded me.  We should be able to get it working.  Do you mind starting another thread for the Bamboo One?  I'd appreciate it.

---

### Post by tushantin on 2012-04-27
> **Favux said:**
> Yes I do remember now that you have reminded me.  We should be able to get it working.  Do you mind starting another thread for the Bamboo One?  I'd appreciate it.
Alright; You'd like me to post the same queries in that post?

---

### Post by Favux on 2012-04-27
Yes please.

---

### Post by tokenrove on 2012-04-27
> **Favux said:**
> @ dreh,

So we need tokenrove to explain what that part of the rule is doing or else udevadmin dump and see if we can figure it out.  You can guess what I favor.  :)


I don't know too much about udev rules, to be honest, but it seems to be common to match on the product ID when it's available -- probably much faster and more accurate than trying to match by name.  However, it should be a double = (==), not single = as I appear to be distributing it.  That was actually a typo.  Oops.  So I guess it's been matching on name all this time.  This is something I need to review, evidently.

I'm going to try to look at getting appropriate patches to linux-input in the next week so these most recent hassles can go away sooner.  Maybe pad buttons this weekend, too.

---

### Post by dreh on 2012-04-28
```
# Attach Wacom W8001 devices
 SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="FUJ02e5", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 19200 --w8001 /dev/%k"
 SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="WACf00c", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 38400 --w8001 /dev/%k"
# Attach Wacom legacy protocol IV serial tablets 
 SUBSYSTEM=="pnp", ACTION=="add|change", ENV{PRODUCT}=='13/3d/*', ENV{NAME}=="Wacom protocol IV serial tablet",SYMLINK+="input/wacom",ENV{ID_INPUT}="1",ENV{ID_INPUT_TABLET}="1", RUN+="/lib/udev/inputattach --wacom_iv /dev/%k"
```
This is not working for me

What would the id be? I'm guessing this is the call for the id: ATTRS{id}=="FUJ02e5". What does this do: KERNEL=="ttyS[0-9]*"?


I'm guessing maybe something like this could work:
```
SUBSYSTEM=="pnp", KERNEL=="ttyS[0-9]*", ATTRS{id}=="Wacom protocol IV serial tablet", ACTION=="add|change", RUN+="/lib/udev/inputattach --wacom_iv /dev/%k"
```

---

### Post by dreh on 2012-04-28
```
udevadm info -a -p  $(udevadm info -q path -n /dev/ttyS0)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pnp0/00:08/tty/ttyS0':
    KERNEL=="ttyS0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pnp0/00:08':
    KERNELS=="00:08"
    SUBSYSTEMS=="pnp"
    DRIVERS=="serial"
    ATTRS{id}=="PNP0501"

  looking at parent device '/devices/pnp0':
    KERNELS=="pnp0"
    SUBSYSTEMS==""
    DRIVERS==""

```
I'm not really sure what I should make out of this. Is ATTRS{id}=="PNP0501" the tablet or is this the serial connector on my computer?

---

### Post by dreh on 2012-04-28
sudo udevadm info --path=/devices/pnp0/00:08/tty/ttyS0/serio2/input/input5 --query=all
```

P: /devices/pnp0/00:08/tty/ttyS0/serio2/input/input5
E: ABS=1000003
E: DEVPATH=/devices/pnp0/00:08/tty/ttyS0/serio2/input/input5
E: EV=b
E: ID_INPUT=1
E: ID_INPUT_TABLET=1
E: ID_SERIAL=noserial
E: KEY=c43 0 0 0 0 0
E: MODALIAS=input:b0013v003Ep0000e5544-e0,1,3,k140,141,146,14A,14B,ra0,1,18,mlsfw
E: NAME="Wacom protocol 4 serial tablet"
E: PHYS="ttyS0/serio0/input0"
E: PRODUCT=13/3e/0/5544
E: PROP=0
E: SUBSYSTEM=input
E: UDEV_LOG=3
E: USEC_INITIALIZED=50911311
```

---

### Post by Favux on 2012-04-28
Hi tokenrove,

My fault, I spotted the typo a while ago (appendix 2) and I guess I forgot to tell you.


Excellent dreh!

Now we know for sure tokenrove is matching to the ID:
```
PRODUCT=13/3e/0/5544
```
and so I was right it should be **ENV{PRODUCT}=='13/3e/*'**.  Apparently there is a duplicative match with ENV{NAME} which is why using 3d is working for you.  I think this means we can get rid of one of them.  Tokenrove is telling us an ID match is better than a name match.
> Is ATTRS{id}=="PNP0501" the tablet or is this the serial connector on my computer? 
"PNP0501" is actually a generic serial driver/module, the one that handles most, if not all, legacy Wacom serial tablets.  It used to be a loadable module but after upstream rewrote it Ubuntu made it a built-in last I checked.  We were using it as an ersatz PnP ID for Wacom legacy serial tablets (since they don't have a real PnP ID) in .fdi files with HAL.  You can get away with that as long as the Wacom tablet is the only device using "PNP0501".
> What would the id be? I'm guessing this is the call for the id: ATTRS{id}=="FUJ02e5".
Yes, the PnP ID's for ISDV4 tablet PC's start with FUJ for Fujitsu and WAC for all other serial tablet PC's.
> What does this do: KERNEL=="ttyS[0-9]*"?
That matches the serial port.  The [0-9] is a range which is allowed.  So as long as the port number is one of the numbers in the range it will match.  If you had a range of [0-4] (you could also write it as [01234]) the match would be made to ttyS0 or ttyS1 etc. but not ttyS5 or higher.

For up to date ISDV4 serial rules:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Fixed_device_files_with_udev](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Fixed_device_files_with_udev)  I give you a useful link there for writing udev rules which I'll duplicate:  [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

The serial rules were changed about a year ago when a udev expert came through and explained that the serial rules the Linux Wacom Project (actually Fedora/RedHat) had been using up to then were wrong.  And in certain situations they could be bad, bad, bad.  His explanation was pretty esoteric but the upshot is Peter Hutterer rewrote them in compliance to what he was telling us.  Unfortunately I don't think I ever totally followed things.  The udev expert did help me a little when I was trying to come up with the serial5 rule, so I think I'm probably on the right track with it.

---

### Post by Favux on 2012-04-28
Hi dreh,

After looking at your udev info. I'm thinking for stand alone rules we could try the following for the matches:  add ttyS port match (I agree with you),  use SUBSYSTEMS=="pnp" instead of SUBSYSTEM=="pnp", instead of ATTRS{id} for the tablet ID we use either ENV{PRODUCT} or ENV{NAME}.  We should only need one of the latter for a unique match.  Continue to assign ID_INPUT and ID_INPUT_TABLET 1 (true) and move symlink to end.  I'm not quite sure we need "ttyS[0-9]*".  Since Natty, Ubuntu went from the standard 4 ports (ttyS0-ttyS3) to 32 ports (ttyS0-ttyS31).  My guess is that had something to do with upstart.  But we know yours is on ttyS0 and the only other port I've seen used is ttyS4.

match ID:
```

ACTION=="add|change", KERNEL=="ttyS[0-9]*", SUBSYSTEMS=="pnp", ENV{PRODUCT}=='13/3e/*', ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", SYMLINK="input/wacom"
```
or match name:
```
ACTION=="add|change", KERNEL=="ttyS[0-9]*", SUBSYSTEMS=="pnp", ENV{NAME}=="Wacom protocol IV serial tablet", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", SYMLINK="input/wacom"
```
When we call inputattach from the rule we don't need the symlink and can substitute the inputattach commandline parameters for it.
match ID:
```
# Attach Wacom legacy protocol IV serial tablets
ACTION=="add|change", KERNEL=="ttyS[0-9]*", SUBSYSTEMS=="pnp", ENV{PRODUCT}=='13/3e/*', ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", RUN+="/lib/udev/inputattach --wacom_iv /dev/%k"
```
or match name:
```
# Attach Wacom legacy protocol IV serial tablets
ACTION=="add|change", KERNEL=="ttyS[0-9]*", SUBSYSTEMS=="pnp", ENV{NAME}=="Wacom protocol IV serial tablet", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1", RUN+="/lib/udev/inputattach --wacom_iv /dev/%k"
```
And if inputattach doesn't start maybe try adding & to the rule as in:
```
RUN+="/lib/udev/inputattach --wacom_iv /dev/%k &"
```

---

### Post by bruis on 2012-05-01
I am losing my UD-1212 after kernel updates to Oneiric.
Shoud this be happening?
Going through the driver compile routine restores the tablet.

BTW, I notice reference recently to multiple installs of inputattach.
Most, if not all, of the frustration at getting my tablet working was due to an
univited inputattach that was installed in /usr/local/bin/

---

### Post by Favux on 2012-05-02
Hi bruis,
> I am losing my UD-1212 after kernel updates to Oneiric.
Shoud this be happening?
Going through the driver compile routine restores the tablet.
Yes, when you copy the wacom_serial.ko in place:
```
sudo cp wacom_serial5.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet

```
that's to the current kernel i.e. /lib/modules/`uname -r`/.  So a new kernel installs a new /kernel directory tree and the module isn't in it.

We can fix that by implementing a dkms (dynamic kernel module support) of wacom_serial.ko and wacom_serial.ko5 if you are interested.  Now that we're close to final form for both of them.
> BTW, I notice reference recently to multiple installs of inputattach.
Most, if not all, of the frustration at getting my tablet working was due to an
univited inputattach that was installed in /usr/local/bin/ 
Thanks for reminding us.  I should put that in the HOW TO, shouldn't I?

---

### Post by bruis on 2012-05-03
> **Favux said:**
> 
We can fix that by implementing a dkms (dynamic kernel module support) of wacom_serial.ko and wacom_serial.ko5 if you are interested.  Now that we're close to final form for both of them.  

Thanks, it's OK, good to hear it's in the pipeline. I'm happy to know nothing is going off the rails at my end.

---

### Post by tushantin on 2012-05-03
Favux, I've started the topic you requested here: [http://ubuntuforums.org/showthread.php?t=1972163](http://ubuntuforums.org/showthread.php?t=1972163)

---

### Post by Graiden on 2012-05-15
Hi all. I have graphire 1 serial tablet and I'm use xubuntu 12.04 with 3.3.5 kernel. I compile kernel drivers and tablet works with some limitations. Pen is fully works but one of buttons does nothing and seems like eraser works only as second pen. Is there any patch for new xorg drivers? Or reason of it may be somewhere else?

---

### Post by Favux on 2012-05-15
Hi Graiden,

Welcome to Ubuntu forums!

> Pen is fully works but one of buttons does nothing
Which version of wacom_serial did you use?  What is the output of?
```
xsetwacom list
```
> Is there any patch for new xorg drivers?
Any reasonably recent xf86-input-wacom should work.  The 12.04 default is 0.14.0 which should be fine.
> seems like eraser works only as second pen.
In Gimp, for example, have you tried pointing the eraser to the eraser icon in the tool palette on the left.  After it assigns and you test it Save it in the tool palette.

---

### Post by Graiden on 2012-05-15
wacom_serial with changes (0x3d to 0x3e) and inputattach from wacom_serial-120327-1.tar.bz2

xinput --list:
```

Virtual core pointer                        id=2    [master pointer  (3)]
  &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
  &#8627; ImPS/2 Generic Wheel Mouse                  id=10    [slave  pointer  (2)]
  &#8627; Wacom protocol 4 serial tablet stylus       id=11    [slave  pointer  (2)]
  &#8627; Wacom protocol 4 serial tablet eraser       id=12    [slave  pointer  (2)]
  &#8627; Wacom protocol 4 serial tablet cursor       id=13    [slave  pointer  (2)]

```In gimp eraser and stylus both work as last picked tool (doesn't matter how it was selected).

---

### Post by Favux on 2012-05-15
Alright.
> In gimp eraser and stylus both work as last picked tool (doesn't matter how it was selected). 
The Save isn't making the assignment to the eraser permanent?  Do you see pressure when you draw a line?

What have you done to assign the stylus buttons?  Have you tried?
```

xsetwacom set "Wacom protocol 4 serial tablet stylus" Button 2 3
xsetwacom set "Wacom protocol 4 serial tablet stylus" Button 3 2

```
Does that work?

---

### Post by Graiden on 2012-05-15
Save isn't work. Pressure work well. To assign buttons I have two line in /usr/share/X11/xorg.conf.d/52-wacom-options.conf 

```

Section "InputClass"
    Identifier "Wacom stylus options"
...
    Option "Button 2" "3"
    Option "Button 3" "2"
...
EndSection

```Button 2 binds as it should be. Button 3 bind command return no any error but it hasn't any effect.

---

### Post by Favux on 2012-05-15
This is sounding more like a wacom_serial.ko problem.

What do you see with?
```
xsetwacom get "Wacom protocol 4 serial tablet stylus" Button 2

xsetwacom get "Wacom protocol 4 serial tablet stylus" Button 3
```
Do the values change when you do a xsetwacom set command on them?

Also let's check your xf86-input-wacom version:
```
xsetwacom -V
```

---

### Post by jellysheep on 2012-05-16
Hello, 
today I tested this how-to and are happy that I finally got my serial tablet working on Ubuntu for the first time! :)
> **Favux said:**
> **[COLOR=Blue][SIZE=3]Graphire testers are urgently needed![/SIZE][/COLOR]**
I can confirm that these drivers work very well for serial Graphire I on Ubuntu Precise, until now without bugs. 
Thank you!
jellysheep

EDIT:
> Hi all. I have graphire 1 serial tablet and I'm use xubuntu 12.04 with  3.3.5 kernel. I compile kernel drivers and tablet works with some  limitations. Pen is fully works but one of buttons does nothing and  seems like eraser works only as second pen. Is there any patch for new  xorg drivers? Or reason of it may be somewhere else?
Oh, someone reported nearly the same thing, sorry for the duplicate post.

---

### Post by Graiden on 2012-05-16
Output of xsetwacom -V is 0.14.0.
Get value of buttons returns 2 for 2 and 3 for 3 and is changed correctly with set option. I tried to remove rules for wacom and tablet mouse behavior is change. Before left mouse buttons didn't work and now is fine. It looks like I do something wrong in rules file. Have some one correct one?

---

### Post by Favux on 2012-05-16
Hi jellysheep,

Welcome to Ubuntu forums!

You are not a duplicative poster!  Tokenrove will appreciate multiple Graphire testers.  Please feel free to join in and add anything you want on your Graphire I's behavior.


@ Graiden,

> I tried to remove rules for wacom and tablet mouse behavior is change. Before left mouse buttons didn't work and now is fine. It looks like I do something wrong in rules file. Have some one correct one? 
We should be able to sort you out.  Could you post your current 50-wacom.conf and the custom .conf that was causing the problem?

I assume you are talking about a .conf file in xorg.conf.d and not say xorg.conf or an xsetwacom script.  If I'm wrong let me know.

---

### Post by tokenrove on 2012-05-17
> **jellysheep said:**
> Hello, 
today I tested this how-to and are happy that I finally got my serial tablet working on Ubuntu for the first time! :)

I can confirm that these drivers work very well for serial Graphire I on Ubuntu Precise, until now without bugs. 
Thank you!
jellysheep

EDIT:

Oh, someone reported nearly the same thing, sorry for the duplicate post.

No, it's great to hear multiple reports, especially since before now, no one had reported on the graphire.  I'm sorry to all that I haven't had time lately to work on the driver, but some work I'm involved in will be slowing down in a couple of weeks and I'll focus on all bug reports and submitting the patch to the mainline kernel.

Thanks for all the reports and keep the bug reports (and success reports) coming!

---

### Post by luminol on 2012-05-20
Trying again, same computer, same Intuos2 XD-0912-R tablet, same HL-340 usb-serial adapter, but under 64-bit Xubuntu Precise.

Compiled and installed the protocol5 drivers, modprobe shows everything loaded. Didn't patch wacom_serial.c because I didn't need protocol4.

Compiling linuxconsoletools-1.4.2 fails when I apply the patch:

```
~/Desktop/linuxconsoletools-1.4.2$ patch utils/inputattach.c < ~/Desktop/wacom_serial5/inputattach.patch
The next patch would create the file utils/inputattach.c,
which already exists!  Assume -R? [n] y
patching file utils/inputattach.c
Hunk #1 FAILED at 1.
File utils/inputattach.c is not empty after patch, as expected
1 out of 1 hunk FAILED -- saving rejects to file utils/inputattach.c.rej
patching file utils/inputattach.c
patching file utils/inputattach.c
Hunk #1 FAILED at 125.
1 out of 1 hunk FAILED -- saving rejects to file utils/inputattach.c.rej
```

Compiled without the patch and got:

```
make -C utils compile
make[1]: Entering directory `/home/ultra7/Desktop/linuxconsoletools-1.4.2/utils'
gcc -g -O2 -Wall -I../linux/include    inputattach.c   -o inputattach
inputattach.c: In function ‘logitech_command’:
inputattach.c:92:8: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result [-Wunused-result]
inputattach.c: In function ‘magellan_init’:
inputattach.c:103:7: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result [-Wunused-result]
inputattach.c: In function ‘spaceball_cmd’:
inputattach.c:153:8: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result [-Wunused-result]
inputattach.c:154:7: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result [-Wunused-result]
gcc -g -O2 -Wall -I../linux/include   -c -o jstest.o jstest.c
gcc -g -O2 -Wall -I../linux/include   -c -o axbtnmap.o axbtnmap.c
gcc   jstest.o axbtnmap.o   -o jstest
gcc -g -O2 -Wall -I../linux/include   -c -o jscal.o jscal.c
jscal.c: In function ‘wait_for_event’:
jscal.c:115:8: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result [-Wunused-result]
gcc -g -O2 -Wall -I../linux/include  jscal.o axbtnmap.o -lm -o jscal
gcc -g -O2 -Wall -I../linux/include    fftest.c   -o fftest
fftest.c: In function ‘main’:
fftest.c:223:8: warning: ignoring return value of ‘scanf’, declared with attribute warn_unused_result [-Wunused-result]
gcc -c -g -O2 -Wall -I../linux/include  ffmvforce.c -o ffmvforce.o `sdl-config --cflags`
gcc ffmvforce.o -o ffmvforce  -g -lm `sdl-config --libs`
gcc -g -O2 -Wall -I../linux/include    ffset.c   -o ffset
gcc -O2 -funsigned-char ffcfstress.c -lm -o ffcfstress
sed "s^@@PREFIX@@^/usr/local^g" < jscal-restore.in > jscal-restore
sed "s^@@PREFIX@@^/usr/local^g" < jscal-store.in > jscal-store
make[1]: Leaving directory `/home/ultra7/Desktop/linuxconsoletools-1.4.2/utils'
```

When I do the make install:

```
ultra7@ultra7-desktop:~/Desktop/linuxconsoletools-1.4.2$ sudo PREFIX=/usr make install
[sudo] password for ultra7: 
make -C utils install
make[1]: Entering directory `/home/ultra7/Desktop/linuxconsoletools-1.4.2/utils'
install -d /usr/bin
install inputattach jstest jscal fftest ffmvforce ffset ffcfstress jscal-restore jscal-store /usr/bin
install -d /usr/share/joystick
install extract filter ident /usr/share/joystick
make[1]: Leaving directory `/home/ultra7/Desktop/linuxconsoletools-1.4.2/utils'
make -C docs install
make[1]: Entering directory `/home/ultra7/Desktop/linuxconsoletools-1.4.2/docs'
install -d /usr/share/man/man1
install inputattach.1 jstest.1 jscal.1 fftest.1 ffmvforce.1 ffset.1 ffcfstress.1 jscal-store.1 jscal-restore.1 /usr/share/man/man1
make[1]: Leaving directory `/home/ultra7/Desktop/linuxconsoletools-1.4.2/docs'
```

But when I try inputattach, I get:

```
ultra7@ultra7-desktop:~/Desktop/linuxconsoletools-1.4.2$ sudo inputattach --wacom_v /dev/ttyUSB0
inputattach: invalid mode '--wacom_v'

```

Thought it may be a 64-bit thing. Booted off a 32-bit 12.04 CD, repeated the process and got the same results.

Where do I start?

---

### Post by Favux on 2012-05-20
Hi luminol,

Without the wacom_serial5 stuff added for inputattach by the patch to linuxconsoletools-1.4.2 the resultant inputattach won't work.  So the problem appears to be:
```
The next patch would create the file utils/inputattach.c,
which already exists!  Assume -R? [n] y
patching file utils/inputattach.c
Hunk #1 FAILED at 1.
File utils/inputattach.c is not empty after patch, as expected
1 out of 1 hunk FAILED -- saving rejects to file utils/inputattach.c.rej
```
What's in inputattach.c.rej?  And what does ***uname -m*** show?

Don't understand it because the linuxconsoletools-1.4.2 is one I've tried the patch on.  The tar appears unchanged, it has the same date anyway.

---

### Post by luminol on 2012-05-20
> **Favux said:**
> 
What's in inputattach.c.rej?  And what does ***uname -m*** show?

Don't understand it because the linuxconsoletools-1.4.2 is one I've tried the patch on.  The tar appears unchanged, it has the same date anyway.

I wondered about that. I looked in the patch & 
all the versions are 1.4.1 (Disclaimer: I am not a programmer).

**inputattach.c.rej** contains:

```
--- inputattach.patch	2011-07-11 12:06:30.331999922 +0200
+++ inputattach.patch	1970-01-01 01:00:00.000000000 +0100
@@ -1,25 +0,0 @@
-diff -u joystick-1.4.1/utils/inputattach.c joystick-patched/utils/inputattach.c
---- joystick-1.4.1/utils/inputattach.c	2011-06-25 09:16:58.000000000 -0400
-+++ joystick-patched/utils/inputattach.c	2011-07-01 13:48:15.000000000 -0400
-@@ -588,6 +588,9 @@
- { "--w8001",		"-w8001",	"Wacom W8001",
- 	B38400, CS8,
- 	SERIO_W8001,		0x00,	0x00,	0,	NULL },
-+{ "--wacom_iv",		"-wacom_iv",	"Wacom protocol 4 tablet",
-+	B9600, CS8,
-+	SERIO_WACOM_IV,		0x00,	0x00,	0,	NULL },
- { NULL, NULL, NULL, 0, 0, 0, 0, 0, 0, NULL }
- };
- 
-diff -u joystick-1.4.1/utils/serio-ids.h joystick-patched/utils/serio-ids.h
---- joystick-1.4.1/utils/serio-ids.h	2010-11-04 02:15:02.000000000 -0400
-+++ joystick-patched/utils/serio-ids.h	2011-07-01 13:48:33.000000000 -0400
-@@ -125,5 +125,8 @@
- #ifndef SERIO_PSMULT
- # define SERIO_PS2MULT		0x3c
- #endif
-+#ifndef SERIO_WACOM_IV
-+# define SERIO_WACOM_IV		0x3d
-+#endif
- 
- #endif
--- serio-ids.h	2010-11-04 07:15:02.000000000 +0100
+++ serio-ids.h	2011-07-13 13:11:55.223000078 +0200
@@ -125,5 +125,11 @@
 #ifndef SERIO_PSMULT
 # define SERIO_PS2MULT		0x3c
 #endif
+#ifndef SERIO_WACOM_IV
+# define SERIO_WACOM_IV		0x3d
+#endif
+#ifndef SERIO_WACOM_V
+# define SERIO_WACOM_V		0x3e
+#endif
 
 #endif
```

**uname -m** says x86_64

---

### Post by Favux on 2012-05-20
Yep, looks like a bunch of the patch failed at first glance.  I'll have to look at it closer.

I went ahead and tried it myself and got the same thing.  As I remember there were some serious offsets on some of the humks.  So my guess is the Precise version of Patch is balking at them whereas Oneiric's let them happen.

I might have my stuff on that in Oneiric.  I'm currently in Precise.  But I doubt that'll have anything helpful.  I think we'll have to make a new patch set.  Maybe combining tokenrove's and roaldfre's stuff?  What the heck.

Bad timing as I'm doing a bunch of stuff.  Just finished the DIGImend update.  So it'll probably be a day or two before I get myself back up to speed and get the patch out.

---

### Post by jellysheep on 2012-05-21
Thank you, Favux and tokenrove! :)
The tablet is working really well, also the pressure detection works great!

Fortunately I have noticed now that I don't have to install xf86-input-wacom in Precise. :D
With versions >0.11.1 xserver was crashing when using inputattach. 

> In Gimp, for example, have you tried pointing the eraser to the eraser  icon in the tool palette on the left.  After it assigns and you test it  Save it in the tool palette.
Where can I find these options in Gimp?

Thank you in advance!
jellysheep

---

### Post by knip on 2012-05-23
Hi, I know that this is not a debian forum, but I didn't find any information on this topic in debian websites. 
I have a thinkpad x41. I'm trying to configure the stylus pen of this tablet without success.
I saw that with the following command:
cat /dev/ttyS0
when I make my tablet pen closer to the screen some characters are printed out.

I have the last version of debian (squeeze).
This is my /usr/share/X11/xorg.conf.d/20-wacom.conf file: [http://www.heypasteit.com/clip/0CA1]("http://www.heypasteit.com/clip/0CA1")

This one is the link to the Xorg log: [http://www.heypasteit.com/clip/0CAA]("http://www.heypasteit.com/clip/0CAA")
It seems as the input device of the serial pen is not added.

I saw that linuxwacom drivers are not more needed with the new Xorg server.
Is it necessary to install some additional drivers ?

Thank you guys.

---

### Post by Favux on 2012-05-23
Hi knip,

Welcome to Ubuntu forums!

The first problem I see is there are xorg.conf sections in your 20-wacom.conf.  Xorg.conf sections are not equivalent to xorg.conf.d .conf file snippets and should be removed:
```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection
```
You could use those along with a "ServerLayout" section in xorg.conf but there is no reason to do so.  My guess is you added them trying to solve the problem.  Also the Identifier "cursor" section is for a Wacom tablet mouse/puck and there is no reason for it in any case.

Your Xorg.O.log shows the wacom module called but no indication of it setting up on the ISDV4 digitizer.  So a match is being made in one of the serial sections.  So it could be something is blocking the ttyS port.

In the latest releases of Ubuntu it is an inputattach rule in 40-inputattach.rules.  I looked at it briefly and do not know why it doesn't work.  It seems to match OK and the script it calls appears OK but for some reason the inputattach binary isn't started so the wacom_W8001.ko is never started.  While the ISDV4 digitizer will work with the serio .ko driver there is no reason for it as the xf86-input-wacom driver still supports ISDV4 serial digitizers directly.

So if the rule is there comment it out as instructed in this post:  [http://ubuntuforums.org/showpost.php?p=11953933&postcount=6](http://ubuntuforums.org/showpost.php?p=11953933&postcount=6)

But just in case, when you say:
> I saw that linuxwacom drivers are not more needed with the new Xorg server.
Is it necessary to install some additional drivers ?
you understand they are talking about the old linuxwacom driver that included both the kernel driver wacom.ko and the X drive wacom_wac.so?  What happened is with X Server 1.7 xf86-input-wacom was forked from it as the stand alone X driver and you do need that one.  Ubuntu has it in the xorg-xserver-input-wacom package.  The kernel driver is now treated like any other kernel module and is updated by the kernel through linux-input.

By the way you posted on the wrong thread.  This one is for legacy serial graphics tablets.  The two serio .ko's here are to enable them with current kernels and X Servers.  They are both now basically ready to be submitted to the kernel.

That was necessary because xf86-input-wacom dropped support for the old serial graphics tablets with the fork from linuxwacom.  So this is a little community project outside the Linux Wacom Project to continue to support them.  You might want to mention this on the Debian forum if the opportunity arises.


@ luminol

Taking longer than I thought as usual.  But I'm finally over the hump and hopefully can start on a patch today.

---

### Post by Favux on 2012-05-24
Hi luminol,

Got a late start but fortunately after finally looking at it a bit it required only a simple fix.  I just set the correct strip level to the command and now it appears to apply the patch fine.  Corrected the HOW TO.  Let me know if it works for you now.

I no longer remember what I was doing to end up with the command that wasn't working.  But I clearly wasn't thinking.  :redface:

It's still probably worth doing to combine both serial.ko's into one patch.  I'll try to get to that soon.

---

### Post by knip on 2012-05-24
I didn't understand what I have to do. However, I reset the /usr/share/X11/xorg.conf.d/20-wacom.conf  as the original one.

```
  
Section "InputClass"
        Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#       MatchProduct "Wacom|WALTOP|WACOM"
        MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class"
        MatchProduct "Serial Wacom Tablet"
        Driver "wacom"
        Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection

```The content of the /lib/udev/rules.d/60-inputattach.rules, as you told me, is
```

# Attach Wacom W8001 devices
#SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="FUJ02e5", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 19200 --w8001 /dev/%k"
#SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="WACf00c", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 38400 --w8001 /dev/%k"

```I tried with just the first line commented out and also with both lines commented.
It didn't work.

In addition I typed the following commands:
root@kpne# dmesg | grep -i wacom
root@kpne# inputattach --baud 19200 --w8001 /dev/ttyS0
root@kpne# dmesg | grep -i wacom
[ 1306.816263] input: Wacom W8001 Penabled Serial TouchScreen as /devices/serio2/input/input9

In fact if I type:
cat /dev/input/input9
I see some strange characters when I put my stylus near the monitor.

The package xorg-xserver-input-wacom was already installed.
I don't know if I have to install some additional package.

Thanks for your help.

---

### Post by Favux on 2012-05-24
The configuration is not correct correct in 20-wacom.conf.  You left out this serial snippet:
```
Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|WACf004|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection

```
Normally it comes after the first serial snippet:
```
Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|WACf004|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection

```

The inputattach rule is correctly commented out and you have the needed Wacom X driver in the package xorg-xserver-input-wacom.
> I tried with just the first line commented out and also with both lines commented.
It didn't work.
It's the second like you wanted commented out, but both is fine.  Did you restart?  Sometimes several restarts are need to shake things out.  Anyway fix the 20-wacom.conf and try again.  Maybe your ISDV4 digitizer matches through the missing snippet.

> # inputattach --baud 19200 --w8001 /dev/ttyS0
That executes inputattach which in turn loads the kernel module Wacom W8001 (wacom_w8001).  My point is you don't need that serio kernel driver, although you could use it.  The point of inputattach is to turn the serial input into a pseudo usb input using the serio kernel driver.  That's why you see:
```
/devices/serio2/input/input9
```
instead of /devices/ttyS0 or whatever port it is on.  If you look at the second rule the baudrate you want to use is --baud 38400.

In fact that inputattach command would have probably worked with the right baud rate.  And you could add it to rc.local so it starts automatically rather than use the udev rule.  That is what the input-wacom README tells you to do:  [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/input-wacom/](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/input-wacom/)  And we copy that on this HOW TO.  But again you shouldn't need it.  Something to keep in mind though if it won't work normally.

The plan is to eventually drop the direct ISDV4 support from xf86-input-wacom and require the serio kernel driver.  But they haven't done that yet.

---

### Post by luminol on 2012-05-26
> **Favux said:**
> Hi luminol,

Got a late start but fortunately after finally looking at it a bit it required only a simple fix.  I just set the correct strip level to the command and now it appears to apply the patch fine.  Corrected the HOW TO.  Let me know if it works for you now.

Works perfectly. Put the inputattach in rc.local and rebooted, still working perfectly. Also, the tablet's mouse works now, with right and left buttons -- no middle click/mouse wheel, but I'm not complaining. And the tracking is totally smooth where there was a tiny bit of lag under previous (32-bit) Ubuntu versions.

Oh, and thanks.:)

---

### Post by Favux on 2012-05-27
Great!  It's working.  :)

> Also, the tablet's mouse works now, with right and left buttons -- no middle click/mouse wheel, but I'm not complaining.
Precise basically has xf86-input-wacom-0.14.0 with some backports.  So that version has the broken scroll wheel, at least for the scroll wheel on the Graphire's pad.  I don't know if your puck scroll wheel is now considered an RelWheel instead of AbsWheel.  But maybe.  I don't have the wacom_serial5 code to look at right this minute.  If so you'd need to clone and patch xf86-input-wacom's wcmCommon.c with this patch:  [https://mail.google.com/mail/?ui=2&shva=1#label/linuxwacom-devel/137850f4762387fa](https://mail.google.com/mail/?ui=2&shva=1#label/linuxwacom-devel/137850f4762387fa)  And then compile it.

Then for the xsetwacom command:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#Graphire4](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#Graphire4)

---

### Post by Graiden on 2012-06-01
Hi Favux, sorry for late reply (I was attacked by other problems).

So my first version (stylus button 3, mouse left/middle/wheel buttons and eraser don't work) of rules in /usr/share/X11/xorg.conf.d is:
```

Section "InputClass"
    Identifier "Wacom Graphire stylus options"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"

    # Apply custom Options to this device below.
    Option "Button2" "3"
    Option "Button3" "2"
    Option "PressCurve" "0,10,90,100"
EndSection

Section "InputClass"
    Identifier "Wacom Graphire eraser options"
    MatchDriver "wacom"
    MatchProduct "eraser"

    # Apply custom Options to this device below.
    Option "PressCurve" "5,0,100,95"
EndSection

Section "InputClass"
    Identifier "Wacom Graphire cursor options"
    MatchDriver "wacom"
    MatchProduct "cursor"

    # Apply custom Options to this device below.
    Option "Button1" "1"
    Option "Button2" "2"
    Option "Button3" "3"
EndSection

Section "InputClass" #
    Identifier "Wacom Graphire pad options"
    MatchDriver "wacom"
    MatchProduct "pad"

    # Apply custom Options to this device below.
    Option "Button1" "1"
    Option "Button2" "3"
    Option "Button3" "2"
    Option "Button4" "0"
    Option "AbsWheelUp" "5"
    Option "AbsWheelDown" "4"
EndSection

```Second is none rules for wacom -> mouse left button works.
And I don't use any xorg.conf lines and xsetwacom script. I run inputattach with only --wacom_iv /dev/ttyS3 option. Maybe problem in my pci to com card?

---

### Post by Favux on 2012-06-01
Hi Graiden,

> Maybe problem in my pci to com card? 
I don't think so.

For your Graphire eraser I was looking at wacom_serial.c and it looks like tokenrove disabled the eraser.  And that's why your eraser isn't working.  
```
	/* NOTE: According to old wcmSerial code, button&8 is the
	 * eraser on Graphire tablets.  I have removed this until
	 * someone can verify it. */
	tool = stylus_p ? ((button & 4) ? ERASER : STYLUS) : CURSOR;
```
We likely need to get him to add (button & 8 ) for the eraser back into:
```
	tool = stylus_p ? ((button & 4) ? ERASER : STYLUS) : CURSOR;
```
You did a nice job on your xorg.conf.d wacom.conf file.  But a couple of things.  The /usr/share/X11/xorg.conf.d directory is for the Distro.  You should be adding, call it 52-wacom.conf, in /etc/X11/xorg.conf.d.  You may need to make the directory:
```
sudo mkdir /etc/X11/xorg.conf.d
```
Also there is no need to restate driver defaults in it so either comment them out or remove them:
```
Section "InputClass"
    Identifier "Wacom Graphire stylus options"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"

    # Apply custom Options to this device below.
    Option "Button2" "3"
    Option "Button3" "2"
    Option "PressCurve" "0,10,90,100"
EndSection

Section "InputClass"
    Identifier "Wacom Graphire eraser options"
    MatchDriver "wacom"
    MatchProduct "eraser"

    # Apply custom Options to this device below.
    Option "PressCurve" "5,0,100,95"
EndSection

Section "InputClass"
    Identifier "Wacom Graphire cursor options"
    MatchDriver "wacom"
    MatchProduct "cursor"

    # Apply custom Options to this device below.
#    Option "Button1" "1"
#    Option "Button2" "2"
#    Option "Button3" "3"
EndSection

Section "InputClass" #
    Identifier "Wacom Graphire pad options"
    MatchDriver "wacom"
    MatchProduct "pad"

    # Apply custom Options to this device below.
    Option "Button1" "1"
    Option "Button2" "3"
    Option "Button3" "2"
    Option "Button4" "0"
    Option "AbsWheelUp" "5"
    Option "AbsWheelDown" "4"
EndSection
```
Now there are a couple of issue with the Graphire scroll wheel.  First of all it is now a RelWheel not an AbsWheel.  So that needs changing.

Second I'm not sure RelWheelUp and RelWheelDown parameters work as .conf Options.  They may only be for xsetwacom.  But you are correct they have to be integers and 4 & 5 would be for vertical scroll.

Third and most important they broke the scroll wheel for the Graphire a while ago and the fix was just comitted to the xf86-input-wacom git repository a couple of days ago.

So the first thing you need to do is clone the xf86-input-wacom git repository and compile it.

---

### Post by tokenrove on 2012-06-01
> **Favux said:**
> For your Graphire eraser I was looking at wacom_serial.c and it looks like tokenrove disabled the eraser.  And that's why your eraser isn't working.  
```
	/* NOTE: According to old wcmSerial code, button&8 is the
	 * eraser on Graphire tablets.  I have removed this until
	 * someone can verify it. */
	tool = stylus_p ? ((button & 4) ? ERASER : STYLUS) : CURSOR;
```
We likely need to get him to add (button & 8 ) for the eraser back into:


That's right.  And, I just finished a crazy period of work, so I was thinking I would start the process of getting wacom_serial into the kernel shortly.  I will try to make a release with the graphire eraser enabled tomorrow or the next day, but feel free to hack it in yourself as Favux suggested and see what happens!

I'm also going to add pad button support, and as a bonus, make sure the driver works on ARM as well as I'm now using a Genesi Efika Smartbook regularly.

---

### Post by Gizmoatwork on 2012-06-03
Hi.

I have an Intuos 2 serial tablet. I made it work a year ago on Maverick. Now I use Linux  Mint 13, and right now, the tablet does't work.

I have a fresh intall.
Kernel : 3.2.0.23
X.Org X Server : 1.11.3

I've followed the steps until 
```
sudo inputattach --wacom_v /dev/ttyS0
```

The terminal get stuck at this point, and I don't what I should do next.

---

### Post by Favux on 2012-06-03
Hi Gizmoatwork,

Does the command throw off an error message?  If so what is it?

Does wacom_serial5 appear in lsmod?

Have you checked which serial port you are on?
```
sudo dmesg | grep ttyS
```

---

### Post by Gizmoatwork on 2012-06-03
Hi Favux.

- The console doesn't throw off any error message. Just nothing, like something was running, but with no feedback.

- Yes, *wacom_serial5* appears first in lsmod.


```
sudo dmesg | grep ttyS
``` - I get this feedback :
```
[ 3625.168149] serio: Serial port ttyS0
```

---

### Post by Favux on 2012-06-03
Let's check the output of ***xinput list*** and ***xsetwacom list*** when you see wacom_serial5 in lsmod.

---

### Post by Gizmoatwork on 2012-06-03
```
xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)    id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; STV06xx                                     id=8    [slave  keyboard (3)]
``````
xsetwacom list
```Nothing happens. no outpout.

I can see that *wacom_serial5* apperas in *lsmod* only after typing the line :
```
sudo inputattach --wacom_v /dev/ttyS0
```

---

### Post by Favux on 2012-06-03
OK, we need to look at your Xorg.0.log in /var/log.

To summarize.  You installed Linux Mint 13.  Compiled and installed wacom_serial5.ko and inputattach without any problems.  The tablet appears to be on the ttyS0 port.  Running the inputattach command loads wacom_serial5 like it is suppose to because you can see it happen with lsmod.  But no response from the tablet.  X (xinput list) doesn't see it and it is not on the Wacom X driver (xsetwacom list).

So it seems like either the Wacom X driver is rejecting the tablet for some reason or something else is claiming the tablet.

---

### Post by Gizmoatwork on 2012-06-04
Thank you for your help and explanation. It's good to be explained why I'm typing this lingo :).

I'm attaching theXorg.0.log file you requested.

---

### Post by Favux on 2012-06-04
Your Xorg.0.log doesn't show any sign of the tablet or a ttyS0 port.

Did you take the Xorg.0.log after you ran?
```
sudo inputattach --wacom_v /dev/ttyS0
```
And saw the wacom_serial5 module load in **lsmod**?

---

### Post by Gizmoatwork on 2012-06-04
Yes, 

sudo inputattach --wacom_v /dev/ttyS0

is runnig right now.
And I can see *wacom_serial5* module in lsmod.

But I'm not sure the log file is updated automatically when I'm typing the lines in the terminal. Its date (Xorg.0.log)  is from when I started my computer, not when I typed everything in the terminal.

---

### Post by Favux on 2012-06-04
Good point.  If it was a usb device you were hot plugging the hot plug event would show up.  But I'm not sure about inputattach.

In that case why don't you go ahead and add the inputattach command to rc.local and restart.  If the wacom_serial5 is in lsmod then send that Xorg.0.log.

---

### Post by Gizmoatwork on 2012-06-04
Ok, so now the *inputattach *command is in *rc.local*.
I reboot, then *wacom_serial5* module is listed with *lsmod*.

Here is the new Xorg.0.log file.

---

### Post by Favux on 2012-06-05
Still nothing in Xorg.0.log.  So X isn't getting any input from the tablet.

Since inputattach works correctly there doesn't appear to be a problem with its compile or installation.  Which leaves us at a problem with wacom_serial5.  That seems unlikely because it did compile and you have it installed correctly since we see it in lsmod.  Roadlfre hasn't made a commit in 4 months so the id/serio protocol hasn't been changed.  Did you change the ID?

After a fresh restart try searching dmesg with some various key words and see if something shows up:
```
dmesg | grep wacom_serial5
```
In addition to wacom_serial5 try:  ttyS, port, serio, Serial, port.  Maybe we'll get lucky and find something.

You might want to try recompiling wacom_serial5.  And if you changed the serio protocol before don't this time.

---

### Post by Gizmoatwork on 2012-06-05
```
dmesg | grep wacom_serial5
[   30.848082] wacom_serial5: probe of serio1 failed with error -5
[   31.848083] wacom_serial5: probe of serio2 failed with error -5
[   32.848087] wacom_serial5: probe of serio3 failed with error -5 and so on...
``````
dmesg | grep ttyS
[    0.690301] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.812635] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.825405] serio: Serial port ttyS0
[   30.848224] serio: Serial port ttyS0
[   31.848148] serio: Serial port ttyS0 and so on...
``````
dmesg | grep port
[    0.000000] KERNEL supported cpus:
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.012560] mce: CPU supports 5 MCE banks
[    0.149510] node 0 link 0: io port [c000, ffff]
[    0.180616] ACPI: (supports S0 S1 S3 S4 S5)
[    0.183973] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.184258] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.184305] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.185006] pci 0000:00:13.5: supports D1 D2
[    0.185008] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.185562] pci 0000:01:00.0: supports D1 D2
[    0.185647] pci 0000:01:00.1: supports D1 D2
[    0.192204] pci 0000:02:00.0: supports D1 D2
[    0.192206] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.192417] pci 0000:03:06.0: supports D1 D2
[    0.667571] pcieport 0000:00:02.0: setting latency timer to 64
[    0.667603] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.667698] pcieport 0000:00:07.0: setting latency timer to 64
[    0.667722] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
[    0.669808] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.827288] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    0.828450] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[    0.828453] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[    0.828457] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[    0.828460] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[    0.829522] ehci_hcd 0000:00:13.5: debug port 1
[    0.840176] hub 1-0:1.0: 10 ports detected
[    0.900132] hub 2-0:1.0: 2 ports detected
[    0.960125] hub 3-0:1.0: 2 ports detected
[    1.020129] hub 4-0:1.0: 2 ports detected
[    1.080145] hub 5-0:1.0: 2 ports detected
[    1.140139] hub 6-0:1.0: 2 ports detected
[    1.140325] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.140469] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.284637] hub 1-3:1.0: 4 ports detected
[    1.770048] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.282121] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.007871] parport_pc 00:09: reported by Plug and Play ACPI
[   26.007903] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   26.097022] lp0: using parport0 (interrupt-driven).
[   26.100669] [fglrx] ioport: bar 4, base 0xde00, size: 0x100
[   26.102281] [fglrx] Kernel PAT support is enabled
[   26.270000] ppdev: user-space parallel port driver
[   29.825405] serio: Serial port ttyS0
[   30.848224] serio: Serial port ttyS0
[   31.848148] serio: Serial port ttyS0 and so on...

```For serio, Serial and and port, I just have the end ([   31.848148] serio: Serial port ttyS0 and so on...), not the beginning. Too much entries ?

I don't know what you mean my changing the ID ?


*Thanks for your kind help.*

---

### Post by Favux on 2012-06-05
OK, now we are getting somewhere:
```
dmesg | grep wacom_serial5
[   30.848082] wacom_serial5: probe of serio1 failed with error -5
```
Now if only I knew what error -5 was.  :)

With ID I'm talking about the stuff under the blue colored "For the 3.2 kernel (Precise)".  Since you have an Intuos you should be able to ignore that.

Right now try recompiling wacom_serial5.ko using "a) Download and compile the protocol 5 wacom_serial5.ko (Intuos and Intuos2 tablets)" and reinstalling it and see if that fixes things.

---

### Post by Gizmoatwork on 2012-06-05
I recompiled wacom_serial5 (point a).
Note sure how to install it. Should I follow point b ?

At this point, I've just restarted my computer, but I just have the same error -5 message .

---

### Post by Favux on 2012-06-05
The copy command:
```
sudo cp wacom_serial5.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet
```
combined with
```
sudo depmod -a
```
installs it.  Try restarting a couple of times.  If you are still getting the error check in Troubleshooting about duplicate inputattach binaries and make sure that isn't the problem.

---

### Post by jellysheep on 2012-06-06
> **Favux said:**
> We likely need to get him to add (button & 8 ) for the eraser back into:
```
    tool = stylus_p ? ((button & 4) ? ERASER : STYLUS) : CURSOR;
```
Thanks to Favux' hint to re-enable the eraser in wacom_serial.c, my eraser is working brilliant now! :)

In the next few days a usb to serial connector arrives. Then I will test the Graphire, also on an ARM tablet pc. :)

---

### Post by Gizmoatwork on 2012-06-06
Oh my GOD, Favux, I fell so ashamed.

I've just double-checked the serial plug of my tablet, and it was...unplugged ! :oops:
I fell bad, very bad... Very sorry to have abused your time and expertise.
So now, the tablet works, the pressure works too. :):P:)

Just for the record, when I run 
```

dmesg | grep wacom_serial5
```I don't have any feedback. Maybe it's normal...

Anyways, again, sorry for being so noob, and great thanks for your kind help.

---

### Post by Favux on 2012-06-06
No worries.  :)

In fact you made me look at the HOW TO again and realize I needed to update it and fix some mistakes I had made.  So unplugged or not it was worth doing.

For example I found jellysheep's second post, which I had missed, and made a belated response to.  And now he's tested the Graphire eraser for us!
> Just for the record, when I run

```
dmesg | grep wacom_serial5
```

I don't have any feedback. Maybe it's normal...
Don't know for sure.  You see it in **lsmod** right?  What happens if you modinfo it?
```
modinfo wacom_serial5
```
Also in lsmod is it wacom_serial5 or wacom-serial5?

---

### Post by Gizmoatwork on 2012-06-06
Good to know this wasn't worthless...

In lsmod, it's *wacom_serial5*.

```
modinfo wacom_serial5
filename:       /lib/modules/3.2.0-23-generic/kernel/drivers/input/tablet/wacom_serial5.ko
license:        GPL
description:    Wacom protocol 5 serial tablet driver
author:         Roald Frederickx <roald.frederickx@gmail.com>
srcversion:     8EE3AE4CCAFC273EAF07575
alias:          serio:ty02pr3Eid*ex*
depends:        
vermagic:       3.2.0-23-generic SMP mod_unload modversions
```

---

### Post by Graiden on 2012-06-07
Jellysheep, it works for me too. And what about buttons? All works right?

---

### Post by iconnor on 2012-06-07
Just a note:  Doesn't work with my Motion LE1600.  The old code didn't work with it either.

Ubuntu Precise

---

### Post by Favux on 2012-06-07
Hi iconnor,

Tablet PC's use Wacom ISDV4 serial digitizers.  Those are different from the serial Wacom tablets we are talking about on this thread.

Likely your problem is the one discussed on post #354:  [http://ubuntuforums.org/showpost.php?p=11807798&postcount=354](http://ubuntuforums.org/showpost.php?p=11807798&postcount=354)

---

### Post by jellysheep on 2012-09-17
Hi, 
now I can also confirm the driver working for Graphire under Arch Linux (is this offtopic?). Buttons and pressure detection works, but in GIMP it doesnt switch automagically between stylus and eraser (even with button&8 ), like it does under Ubuntu. A usb to serial converter works however. :)

---

### Post by Favux on 2012-09-17
Hi jellysheep,
[QUOTE=jellysheep]I can also confirm the driver working for Graphire under Arch Linux (is this offtopic?).[/QUOTE]
No, that is not off topic.  Other Distros count too and it is good that you reported on Arch.  Thank you, that may be the first one on Arch.  Don't recall another one off hand anyway.  :)

---

### Post by klein de usa on 2012-11-06
hi 
i have a wacom digitizer 11 0608-r. will these drivers work on xubuntu 12.04 ? 64 bit 

i also have a wacom digitizer 11 1218-r will the same driver work for both digitizers.

---

### Post by Favux on 2012-11-06
Hi klein de usa,

I think the protocol IV serio driver should work for both.

---

### Post by klein de usa on 2012-11-06
hi Favux

i have two of these 0608-r's and one 1218-r  later to night i might try this on xubuntu 12.04 and ubuntu 10.04.

i also ran across this when googling [http://forum.bongofish.co.uk/index.php?topic=1942.0]("http://forum.bongofish.co.uk/index.php?topic=1942.0") might try this with the 1218-r

---

### Post by klein de usa on 2012-11-06
hay Favux

0608-r on xubuntu 12.04

i'm finding this thad to follow what i have done:

when't here
[http://www.cipht.net/2011/07/02/wacom_serial-initial-release.html](http://www.cipht.net/2011/07/02/wacom_serial-initial-release.html)

and downloaded 
wacom_serial-120327-1.tar.bz2

extracted it to /home/user

did 
sudo apt-get update

did
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev

did
sudo apt-get upgrade

changed line 49 in wacom_serial.c (d to e) 

changed line 129 in serio-ids.h (d to e) 


then i lost as to what to do next ?

---

### Post by Favux on 2012-11-06
Next you do "a) Download and compile the protocol 4 wacom_serial.ko - by tokenrove".

Follow that with "Using inputattach with the new kernel module".  Use:
```
inputattach --wacom_iv /dev/ttyS0
```
Provided the tablet is on ttyS0.

---

### Post by klein de usa on 2012-11-06
Favux
ok it works on xubuntu 12.04 64bit!!!!
i'm thinking of trying it in ubuntu 10.04 64bit is there any reason it wouldn't work with compiz draw on screen ?

---

### Post by Favux on 2012-11-06
> ok it works on xubuntu 12.04 64bit!!!!
Great!  Nice job.  :)
> is there any reason it wouldn't work with compiz draw on screen ? 
Don't recall anyone testing a serial tablet with Compiz Draw(?).  It should work as far as I know.
> 'm thinking of trying it in ubuntu 10.04 64bit
With Lucid you have to use the patch(es) for xf86-input-wacom, not the serio kernel driver.  See "Old serial tablet driver".

---

### Post by klein de usa on 2012-11-06
ok that worked to, so ubuntu 10.04 64bit , compiz draw on screen with 0608-r works!!!!
 thank you Favux

---

### Post by indri on 2012-11-17
Hallo, I would like to use my old Wacom serial tablet Intuos (1).
It is connected to /dev/ttyS0 - verified with gtkterm.

I used code from [https://github.com/RoaldFre/wacom_serial5](https://github.com/RoaldFre/wacom_serial5)
and tutorial at [http://www.cipht.net/2011/07/02/wacom_serial-initial-release.html](http://www.cipht.net/2011/07/02/wacom_serial-initial-release.html).
Tutorial is for wacom_serial. 
For wacom_serial5 was the steps almost the same.
But tablet doesn't work. Please can you help me?

There is difference:
At step 3 is needed file 70-serial-wacom.rules .
It is not available at directory wacom_serial5-master with compiled files.
There is 
```
$ cat joystick-1.4.2/debian/inputattach/lib/udev/rules.d/40-inputattach.rules 
# Attach Wacom W8001 devices
SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="FUJ02e5", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 19200 --w8001 /dev/%k"
SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="WACf00c", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 38400 --w8001 /dev/%k"
```But is should be to other type (?): w8001 

So I used 70-serial-wacom.rules from [http://cipht.net/releases/wacom_serial-120327-1.tar.bz2](http://cipht.net/releases/wacom_serial-120327-1.tar.bz2) (main for tutorial).
```
$ cat wacom_serial/70-serial-wacom.rules
ACTION=="add|change", SUBSYSTEM=="pnp", ENV{PRODUCT}='13/3d/*', ENV{NAME}=="Wacom protocol IV serial tablet",SYMLINK+="input/wacom",ENV{ID_INPUT}="1",ENV{ID_INPUT_TABLET}="1"
``````
$ sudo cp 70-serial-wacom.rules /etc/udev/rules.d
```Is it correct for Intuos (1)?

Next:
When I use
```
$ sudo inputattach --wacom_iv /dev/ttyS0
```there was no response. (Needed Ctrl-C for prompt.)
Is it normal?

I see:
 ```
$ tail /var/log/kern.log
Nov 18 00:32:49 pclu kernel: [11626.415024] serio: Serial port ttyS0
Nov 18 00:32:49 pclu kernel: [11626.420371] input: TSC-10/25/40 Serial TouchScreen as /devices/pnp0/00:0c/tty/ttyS0/serio1/input/input6
```or same:
```
$ dmesg | tail
[11626.415024] serio: Serial port ttyS0
[11626.420371] input: TSC-10/25/40 Serial TouchScreen as /devices/pnp0/00:0c/tty/ttyS0/serio1/input/input6
```kernel module was loaded:
```
$ lsmod | grep wacom
wacom_serial5          16969  0
```I use 64 bit xubuntu:
```
$ uname -a
Linux pclu 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise
```Thanks for help

---

### Post by Favux on 2012-11-17
Hi indri,

Please follow my instructions after the **[SIZE="3"]OR[/SIZE]** for an Intuos rather than tokenrove's.

You do not actually need a udev rule.  And roaldfre never developed one for wacom_v.

Also you need to use:
```
sudo inputattach --wacom_v /dev/ttyS0
```
for an Intuos.

Thanks for pointing out gtkterm.  :)

---

### Post by indri on 2012-11-19
Hi Favux,
tablet works! Thanks! :)

But first after folowing your instructions (after OR at [http://ubuntuforums.org/showthread.php?t=1780154](http://ubuntuforums.org/showthread.php?t=1780154)), there was working position of pen, but not pressure. Tested in MyPaint and GIMP 2.6.x (but in GIMP forgotten use menu Edit->InputDevices). Minimally in MyPaint it did not work. But text selecting and click to menu was OK.

When I saw old version of GIMP and info that in Ubuntu 12.10 (quantal) repository is version 2.8.x then I upgraded my Xubuntu.

After copying wacom_serial5.ko to /lib/... ; sudo depmod -a; in linuxconsoletools-1.4.3:  sudo PREFIX=/usr make install; sudo inputattach --wacom_v /dev/ttyS0 tablet did not work. Probably newer library versions was needed (?).

So I used clean directory of wacom_serial5-master (and linuxconsoletools-1.4.3); make all; sudo cp wacom_serial5.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet; sudo depmod -a; cd ../linuxconsoletools-1.4.3; patch -p1 < ../wacom_serial5-master/inputattach.patch; make; sudo PREFIX=/usr make install; cd ..; sudo inputattach --wacom_v /dev/ttyS0 and tablet started to work. :guitar:

PS: Also thanks to tokenrove for wacom_serial5-master.

Notes and questions:

1) Patching is probably intended for version 1.4.2. With newer version there is offset: linuxconsoletools-1.4.3$ patch -p1 < ../wacom_serial5-master/inputattach.patch 
patching file inputattach.patch
patching file utils/inputattach.c
Hunk #1 succeeded at 553 (offset 94 lines).
Hunk #2 succeeded at 705 (offset 106 lines).
patching file utils/serio-ids.h

2) Copy of file wacom_serial5.ko to /lib/modules/`uname -r`... will be needed after each automatic upgrade of kernel. It can be relatively often. (But it looks better to use /lib/... then command insmod after each reboot.) Is there some other way?

3) After 'sudo inputattach --wacom_v /dev/ttyS0' program did not jump into prompt. Is it normal?

---

### Post by Favux on 2012-11-19
Hi Indri,

Good!  :)

You might have needed to do a **make clean** before recompiling the patched linuxconsole.

1)  Offsets are OK.  If the patch fails then a newer patch would be needed.
2)  Yes, you could set up a dkms for wacom_serial5.ko.  I haven't done that.  An example dkms for wacom.ko is attached to the [Linuxwacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949") with instructions in appendix 2.  You would have to adapt it.
3)  Yes because the process is still running.  That's why to set it up "permanently" you add the inputattach command to rc.local.

---

### Post by Visioneer on 2012-12-10
Hi,

Please forgive my intrusion among some folks who obviously are quite busy doing work which is much beyond my capability.

I am trying to compile the wacom_serial.c against the 2.6.33.2 kernel in Lucid. When doing "*make all*", my gcc v4.4.3 compiler lists an error at line 144 like so:

*/wacom_serial/wacom_serial.c:144: error: implicit declaration of function 'input_abs_set_res'*

What can I do to get beyond that point? My goal is to regain the use of a Wacom Digitizer 2 serial tablet.

---

### Post by Favux on 2012-12-10
Hi Visioneer,

Welcome to Ubuntu forums!


The idea for Lucid is to use the xf86-input-wacom patch set [v3]xf86-input-wacom-0.10.6_serial-patches to get the old serial driver rather than use a wacom_serial.ko kernel serio driver.  That is in the second part of the HOW TO.

But in the first part of the HOW TO you can use the wacom_serial.ko linked in "Note for tokenrove's protocol 4 serial_wacom.ko in Lucid or Maverick" under "a) Download and compile the protocol 4 wacom_serial.ko - by tokenrove" if you would like.  It explains why you are seeing the error.

---

### Post by Visioneer on 2012-12-10
Favux,

Thank you for the rapid and courteous reply. I'm sorry that I didn't make my post clearer (It is my first). What I have done is _exactly_ what you suggest. I am working with Tokenrove's *wacom_serial-110702-0.tar.gz*. And you are right, the compiler does explain the error (an implicit declaration of a function). The problem is that my efforts to *explicitly* declare this function results in the compiler complaining about almost all of the other functions in wacom_serial.c.

My programming experience was in FORTRAN years ago. What I probably need now is to find a forum of C programmers and ask them to take a look at Tokenrove's wacom_serial.c.

You do this forum proud! Your response was quick and to the point and it was appreciated.

---

### Post by Visioneer on 2012-12-13
For anyone following this thread and having as much trouble as I am, here is what I have accomplished so far:

The compiler error */wacom_serial/wacom_serial.c:144: error: implicit declaration of function 'input_abs_set_res'* occurs at line 144 in the source. The same *'input_abs_set_res'* is also used on lines 145, 175 and 176. To verify that this is not a secondary error, I commented out those four lines. The compiler completed successfully. There were warnings of course because now the code has holes in it. But, it does prove that the original error is valid.

When I get this thing worked out the fix will posted here. User Tokenrove has done a fine job of giving us Wacom protocol 4 users a chance of working with our tablets again. It will be a fitting 'Thank You' to him if we can report success.

---

### Post by jaytho on 2012-12-14
Visioner- I just got it working on 12.04, well, I'm still working out the extents- but otherwise the cursor wiggles in the right directions.

I couldn't attach to ttyS0, I had to use a USB/serial port cable I had laying around, but 'yay!'  I think there probably is an answer in the 50 pages of comments in here.

I had compile errors until ran apt-get for the following build/toolchain:

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libxinerama-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev

which I copied blindly from another post somewhere related to building kernel drivers.

I did have to build the patch by hand as the inputattach source had changed, but it isn't much of a big deal.

---

### Post by Visioneer on 2012-12-14
Jaytho,

Congratulations and welcome here. It is encouraging to hear of your success. This thread is great information. I studied it for days before posting, and still am.

---

### Post by Favux on 2012-12-15
Nice job jaytho!  :)  And Welcome to Ubuntu forums!


Hi Visioneer,

I haven't looked at using tokenrove's "crippled" wacom_serial.ko for Lucid and Maverick in quite a while.  I gather what you decided to do was use his latest version and comment out the same four 'input_abs_set_res'.   So please let me know how it works once you get it working.

---

### Post by aMusicUser on 2012-12-22
I&#7743; having a strange problem or have forgotten something obvious as I can seem to get  ubunto to recognise my serial tablet.

Tablet Model: ET-0405-R
Linux version :  Ubuntu Studio 12.10     : 3.5.0-21-lowlatency

What I have done :
1. Downloaded wacom_serial-120327-1.tar
2.In wacom_serial.c
#define SERIO_WACOM_IV 0x3e 3. in serio-ids.h:   # define SERIO_WACOM_IV        0x3e
4. 
make all  sudo cp inputattach /usr/bin  sudo cp wacom_serial.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet  sudo depmod -a  cd ..5.  updated [B]70-serial-wacom.rules
[/B]
ACTION=="add|change", SUBSYSTEM=="pnp", ENV{PRODUCT}=='13/3d/*', ENV{NAME}=="Wacom protocol IV serial tablet", SYMLINK="input/wacom", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"6. 
sudo cp 70-serial-wacom.rules /etc/udev/rules.d/70-serial-wacom.rules 7.
sudo inputattach --wacom_iv /dev/ttyS0
 Process runs but no output

8. expected cursor to move with pen or mouse puck but nothing even after a reboot

9.
sudo dmesg | grep ttyS
gives :

[    0.249034] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.310025] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.376024] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.437023] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 1690.665375] serio: Serial port ttyS0
[ 1690.685349] input: TSC-10/25/40 Serial TouchScreen as /devices/pnp0/00:07/tty/ttyS0/serio2/input/input4
[ 4125.880979] serio: Serial port ttyS0
[ 4125.881160] input: TSC-10/25/40 Serial TouchScreen as /devices/pnp0/00:07/tty/ttyS0/serio3/input/input5
[ 9841.610030] serio: Serial port ttyS0
[ 9841.610188] input: TSC-10/25/40 Serial TouchScreen as /devices/pnp0/00:07/tty/ttyS0/serio4/input/input6
[10081.622078] serio: Serial port ttyS0
[10081.622244] input: TSC-10/25/40 Serial TouchScreen as /devices/pnp0/00:07/tty/ttyS0/serio5/input/input7


lsmod gives  :tsc40                  12579  0 

So I&#7743; guessing I missed an obvious step any ideas ?

Thanks

---

### Post by aMusicUser on 2012-12-23
Of course

13/3d should be 13/3e but linux still thinks  a TSC is connected

updated [B]70-serial-wacom.rules
[/B]
ACTION=="add|change", SUBSYSTEM=="pnp", ENV{PRODUCT}=='13/3e/*',  ENV{NAME}=="Wacom protocol IV serial tablet", SYMLINK="input/wacom",  ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"6. 
sudo cp 70-serial-wacom.rules /etc/udev/rules.d/70-serial-wacom.rules 7.

also edited serio.h.patch to changed the 0x3e

But noted that 
ls /etc/udev/rules.d/
40-timer-permissions.rules  70-persistent-net.rules  README
70-persistent-cd.rules      70-serial-wacom.rules
Is it a problem with three rule 70´s?

Also tried disabling tsc40.ko
sudo mv tsc40.ko. tsc40.ko.bak
gives
sudo dmesg | grep ttyS0
[    0.250021] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.376030] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1441.204982] serio: Serial port ttyS0

---

### Post by Favux on 2012-12-23
Hi aMusicUser,

Welcome to Ubuntu forums!


To simplify things for yourself just don't use the udev rule for the wacom_serial.ko.  It is not needed.  You are right that it needs to be changed as you did.  That's covered in some posts back a few pages.  But really there isn't any reason to use the rule typically.

I'm guessing the reason tsc40.ko keeps showing up is you didn't make the change from d to e somewhere.  You just think you did.  Maybe you needed to run **make clean** before recompiling?  Or you copied the wrong serial_wacom.ko or forgot to copy the new serial_wacom.ko into place?

Here's slightly different version of the [serial HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110412").  Looking at it may help.

---

### Post by aMusicUser on 2012-12-24
Thanks I went back and cleaned my system up as below and now it works :)))


Function report Graphire Model ET-0405-R
---------------------------------------------------------------
-Pen seems to work with gimp and my paint
 -Tip and eraser respond to pressure in My paint
 -Gimp has artifacts on screen due to redraw

-Eraser does not erase

-Tablet mouse Model : EC-100-00 uses Graphire tablet.
-Cursor moves but none of the buttons respond <- not a big deal just thought you would like to know.


________________________________________________________________________
# make sure we are really clean in the system
make clean

sudo mv /usr/bin/inputattach /usr/bin/inputattach.old

sudo rm /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom_serial.ko

sudo apt-get update
# use lower case x 11 instead of uppercase
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev

sudo apt-get upgrade

grep 3d *
# should be  blank
grep 3e *
# should give
# 70-serial-wacom.rules:ACTION=="add|change", SUBSYSTEM=="pnp", ENV{PRODUCT}=='13/3e/*', ENV{NAME}=="Wacom protocol IV serial tablet",SYMLINK+="input/wacom",ENV{ID_INPUT}="1",ENV{ID_INPUT_TABLET}="1"
# serio.h.patch:+#define SERIO_WACOM_IV    0x3e
# serio-ids.h:# define SERIO_WACOM_IV        0x3e
# wacom_serial.c:#define SERIO_WACOM_IV 0x3e
# wacom_serial.mod.c:    { 0xb1d9523e, "wait_for_completion_timeout" },

make all 

sudo cp inputattach /usr/bin 

sudo cp wacom_serial.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet 
sudo depmod -a 
# Do not need these rules
##sudo cp 70-serial-wacom.rules /etc/udev/rules.d/70-serial-wacom.rules 

sudo inputattach --wacom_iv /dev/ttyS0

________________________________________________________________________

> **Favux said:**
> Hi aMusicUser,

Welcome to Ubuntu forums!


To simplify things for yourself just don't use the udev rule for the wacom_serial.ko.  It is not needed.  You are right that it needs to be changed as you did.  That's covered in some posts back a few pages.  But really there isn't any reason to use the rule typically.

I'm guessing the reason tsc40.ko keeps showing up is you didn't make the change from d to e somewhere.  You just think you did.  Maybe you needed to run **make clean** before recompiling?  Or you copied the wrong serial_wacom.ko or forgot to copy the new serial_wacom.ko into place?

Here's slightly different version of the [serial HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110412").  Looking at it may help.

---

### Post by Favux on 2012-12-24
Looks good.  Nice job!  :)

Thanks for the report on function.  That's useful for tokenrove.
> Eraser does not erase
Are you assigning the eraser to the eraser tool in Gimp?
> Cursor moves but none of the buttons respond
I'm pretty sure the mouse buttons should work with tokenrove's latest wacom_serial.  You might want to look into that a bit more.  See **man wacom** and **man xsetwacom** in a terminal.  For example you might want to query the mouse/puck buttons:
```
xsetwacom get <device name> Button 2
```

---

### Post by oscarsfriend on 2013-02-05
Hi,

I have this working on Precise, with (what I am pretty sure is) an UltraPad (doesn't say what model it is anywhere on it and the box went out long ago), and it works almost perfectly.  However, the pen has a button that rocks both ways.

Rocking the button forward actives the middle mouse button (and the nib activates the left mouse button), but rocking the button back doesn't activate the right mouse button / context menu (as it used to way back when I used this tablet on Feisty).  Instead rocking it back activates the eraser, and in the input devices>hardware tab in Inkscape it only shows two buttons, and flips the icon of the pen to an eraser when I rock the button back.  (This button doesn't work in gimp either, or function as context menu anywhere.)

Anyone have any ideas how to get it working?  (I can use xsetwacom to set button 2 to rmb/context menu, but I'd like to get the extra button working! :) )

Thanks.

---

### Post by Ben63 on 2013-02-10
Hello!
I am "lazy" to try all that out and not really in hurry, but following this thread as I am looking forward being able to use again my wacom serial tablet in the latest versions of ubuntu.
Any chance it's gonna be submitted in some future Kernel or even ubuntu release?
thanks

---

### Post by Favux on 2013-02-10
@ oscarsfriend,

To be honest I don't really understand the problem.  As long as you can set the button with an xsetwacom set command what does it matter what the kernel default is?


@ Ben63,

I'm not sure why tokenrove and roaldfre haven't submitted their serio drivers to the kernel.  Or the patches to the Linux Console Project for input-attach.  They've been ready for months it seems to me.  But as far as I can tell the kernel mailing lists don't have them submitted.  But I might have missed them.

Also the the Linux Wacom developers are willing to consider adding them to input-wacom as long as they have some assurance of maintenance since they don't have serial tablets to test with.

---

### Post by oscarsfriend on 2013-02-10
> **Favux said:**
> @ oscarsfriend,

To be honest I don't really understand the problem.  As long as you can set the button with an xsetwacom set command what does it matter what the kernel default is?

Thanks for replying.  There are **two** buttons (although it looks like one, it rocks both ways), only one of which I can set. When I had the tablet working on Feisty, one would function as right mouse button and the other as left.  Now, one functions as middle-mouse button (but I can set it to rmb with xsetwacom, as I said), but the other functions as the eraser, and I am unable to alter its behaviour without also affecting the eraser.  That is: I have one button less than I used to.

---

### Post by Favux on 2013-02-10
Sorry for being dense.  Alright the Ultrapads were Digitizer II's I guess.  Which means they use protocol 4 or tokenrove's wacom_serial.ko.  Is that correct?

So you need tokenrove to fix wacom_serial.c to handle the stylus side button (number 2) correctly for your Ultrapad.  A rocker switch for the two stylus side buttons is common.  Unfortunately you can't give him a model number, but I'm not sure that even matters.  Given they were '92 to '94 I'm doubting there is a unique PNP identifier for them.

---

### Post by oscarsfriend on 2013-02-10
> **Favux said:**
> Sorry for being dense.  Alright the Ultrapads were Digitizer II's I guess.  Which means they use protocol 4 or tokenrove's wacom_serial.ko.  Is that correct?

Yes.

> **Favux said:**
> So you need tokenrove to fix wacom_serial.c to handle the stylus side button (number 2) correctly for your Ultrapad.  A rocker switch for the two stylus side buttons is common.  Unfortunately you can't give him a model number, but I'm not sure that even matters.  Given they were '92 to '94 I'm doubting there is a unique PNP identifier for them.

(I **think** it was a little later than '94, as I'm pretty sure I bought it new in the very late '90s, maybe 97/98.) 

OK, thanks.  It's not really a massive issue, but maybe I'll see about contacting tokenrove.  I've actually been using the button occasionally instead of the eraser, for small edits, since I posted to this thread, so I might just keep it that way! :D

---

### Post by skodela on 2013-02-16
Hi folks

I am an archlinux user and hopefully that does not exclude me from here? Well my wife uses ubuntu so it gives me some leeway here!

I have a wacom UD1212 R. I followed several of the last 50 or so pages, got completely lost and did the following. 

1. Followed [http://www.cipht.net/2011/07/02/wacom_serial-initial-release.html](http://www.cipht.net/2011/07/02/wacom_serial-initial-release.html)
1a. Did edit serio-id.h and wacom_serial.c to change the d->e for the protocol 4 devices IDs.

2. Installed wacom_serial.ko and inputattach in the right place.
3. added my name to uucp in the /etc/group 
4. started inputattach --wacom_iv /dev/ttyUSB0 -  a converter with ch341-uart.
5. dmesg shows
[ 2484.973865] ch341 2-1.2:1.0: ch341-uart converter detected
[ 2484.975689] usb 2-1.2: ch341-uart converter now attached to ttyUSB0
[ 2529.152891] serio: Serial port ttyUSB0
[ 2529.152975] input: TSC-10/25/40 Serial TouchScreen as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/ttyUSB0/tty/ttyUSB0/serio4/input/input17

6.xinput list shows among others
TSC-10/25/40 Serial TouchScreen          id=11   [slave  pointer  (2)]

7. xsetwacom list shows no devices.

8. Added this to xorg.conf [no original xorg.conf prior to me creating one]
Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"         "/dev/ttyUSB0"
    Option        "Type"           "stylus"
    Option        "ForceDevice"    "Serial"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"         "/dev/ttyUSB0"
    Option        "Type"           "eraser"
    Option        "ForceDevice"    "Serial"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"         "/dev/ttyUSB0"
    Option        "Type"           "cursor"
    Option        "ForceDevice"    "Serial"
EndSection

Section "ServerLayout"
    Identifier    "X.org Configured"
    InputDevice   "stylus"
    InputDevice   "eraser"
    InputDevice   "cursor"
EndSection

8. xorg log shows 
[   951.236] (II) Using input driver 'wacom' for 'stylus'
[   951.236] (**) stylus: always reports core events
[   951.236] (**) Option "Device" "/dev/ttyUSB0"
[   951.236] (**) Option "Type" "stylus"
[   951.237] (EE) stylus: usbDetect: can not ioctl version
[   951.237] (EE) stylus: cannot identify device class.
[   951.237] (EE) PreInit returned 8 for "stylus"
[   951.237] (II) UnloadModule: "wacom"

Any guidance on where to go from here?

This is a comprehensive beast this topic - so easy to get lost however!

Thanks a bunch

---

### Post by Favux on 2013-02-16
Hi skodela,

Welcome to Ubuntu forums!


For the serio kernel drivers you do not need the xorg.conf.  That's only older X Servers like Lucid's 1.7 using the patchset for xf86-input-wacom-0.10.6.  Since Arch is a rolling release it has a pretty recent kernel and X Server I'm sure (Xorg -version).  So you need the protocol 4 serio driver.

> Did edit serio-id.h and wacom_serial.c to change the d->e for the protocol 4 devices IDs.
Pretty sure that's the problem.  Either you didn't get that quite right or there is another new ID.  Seems to me the problem was d was now identifying the TSC40.  Since you are now seeing:
> TSC-10/25/40 Serial TouchScreen id=11 [slave pointer (2)]
We've got an extraneous,spurious touchscreen from somewhere.  Unless you actually do have one?  So you may need to tell me your kernel and we need to check if another ID has been added.  Or even more than one.  In other words e may longer be valid either.

---

### Post by skodela on 2013-02-16
My serio-id.h reads as below now:

#ifndef SERIO_WACOM_IV
# define SERIO_WACOM_IV         0x3e
#endif

and my wacom_serial.c reads

#ifndef SERIO_WACOM_IV
#define SERIO_WACOM_IV 0x3e
#endif

These reflect the changes I made. 

Now that it is recognized as something should I try to recompile the wacom_serial by randomly trying ox3[a..z]? Sounds terrible in terms of determinism but something to make it work :-)

Sree

---

### Post by Favux on 2013-02-16
No.  Tell me your kernel.  Either:
```
Xorg -version
```
or
```
uname -r
```

---

### Post by skodela on 2013-02-16
Oops. I missed that part of your reply in the excitement! I went back and tried to search for any 3d IDs, made a make clean and rebuilt the module. Installed the new inputattach and removed the old one. still no joy. When I connect the tablet it does not load the wacom_serial module by itself and it does not do that even when I start the inputattach. When the tablet is connected and switched on it does not say anything about the tablet in dmesg. However once inputattach is launched it says about the touchscreen! Just as a blind shot I changed the 3d to 3f in both files and re-tried. Still no luck. Wasn't expecting such a blind try to work but ...


uname -r says 3.7.7-1-ARCH

Xorg -version says

X.Org X Server 1.13.2
Release Date: 2013-01-24
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.7.4-1-ARCH x86_64 
Current Operating System: Linux sreelap 3.7.7-1-ARCH #1 SMP PREEMPT Mon Feb 11 20:20:58 EET 2013 x86_64
Kernel command line: root=/dev/sda5 ro

---

### Post by skodela on 2013-02-16
Also wanted to say that this is amazing how fast my message was answered on a saturday PM. Thanks a bunch.

---

### Post by Favux on 2013-02-16
I went to [http://kernel.org/](http://kernel.org/) and picked the 3.7 kernel.  It took a bit more time than I figured because they moved serio.h from:  [linux/kernel/git/stable/linux-stable.git] / include / linux / serio.h
to:  [linux/kernel/git/stable/linux-stable.git] / include / uapi / linux / serio.h 

I had to track it down through the includes.  A bit of a pain.

Anyway e is still good and the TSC40 ID is still the last one at d:  [http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=blob_plain;f=include/uapi/linux/serio.h;hb=836dc9e3fbbab0c30aa6e664417225f5c1fb1c39](http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=blob_plain;f=include/uapi/linux/serio.h;hb=836dc9e3fbbab0c30aa6e664417225f5c1fb1c39)

And despite you being convinced you've done things correctly you appear to be IDing TSC40 and that seems to be the problem.  You can see where the names you are getting are coming from:  [http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=blob_plain;f=drivers/input/touchscreen/tsc40.c;hb=836dc9e3fbbab0c30aa6e664417225f5c1fb1c39](http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=blob_plain;f=drivers/input/touchscreen/tsc40.c;hb=836dc9e3fbbab0c30aa6e664417225f5c1fb1c39)

So we need to go over the instructions for changing the ID from d to e.  Take a quick peek at the ones on the updated [Serial Graphic Tablet HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110412").  Maybe I wrote them a little clearer?

---

### Post by skodela on 2013-02-16
I don't know what to say. I did what I thought I did last time - I thought I did EXACTLY the same. I downloaded it to a different directory and did a clean build. I guess that only difference is this time I built everything as root. Lo and behold !! It shows up as I launch inputattach!

I feel so embarrassed. Sorry to waste your time!!

It however goes bananas - it launches a click even before the tip touches the surface and seem to cause a release when the pen is moved out of surface reach. I am sure it is just configuration and now that it is alive I will go and search in the 51 pages to make it usable.

Thanks a lot and again sorry for the trouble.

---

### Post by Favux on 2013-02-16
Great and no trouble.  Hopefully the click is easily solvable.  Hate to get this far and hit another roadblock.  :)

---

### Post by skodela on 2013-02-17
I used threshold set to 80 and that seem to be working. Thanks a lot for the help.

---

### Post by bogamol on 2013-03-01
So, what protocol do I need if I am using a Lenovo Thinkpad x61t? 

I noticed that there were some very small differences between Ubuntu and Mint. I am primarily using Debian 6.0 Squeeze. I notice that Debian seems to call it xserver-xorg-input-wacom instead of xf86-input-wacom. Differences? Compatible?


What about Gentoo which I use on a separate hard drive to get more familiar with all the options I have in using linux? Things like this fix + rolling release do not give me warm fuzzies. :p

---

### Post by Favux on 2013-03-01
Neither of the two serio drivers on this HOW TO apply to a tablet PC.  Serial tablet PC's use the ISDv4 protocol.  The X driver for that is still built into xf86-input-wacom.  Although there is now a serio driver available for ISDV4 in input-wacom called wacom_w8001.ko it is easier to just use the X driver.

And the xserver-xorg-input-wacom package contains xf86-input-wacom.  It pretty much is the package now days.

For a bit more on Mint v.s. Ubuntu and Debian (LMDE) see:
[http://forums.linuxmint.com/viewtopic.php?f=42&t=110304](http://forums.linuxmint.com/viewtopic.php?f=42&t=110304)
[http://forums.linuxmint.com/viewtopic.php?f=42&t=110408](http://forums.linuxmint.com/viewtopic.php?f=42&t=110408)

With Mint you are not getting frequent kernel updates.  With Ubuntu you might be and with a rolling release like Gentoo you would be.  In that case you'd want to consider setting up a kernel module if you had one as a dkms.  The Linux Wacom HOW TO shows how to do that for wacom.ko in the appendix.  But you don't have to worry about that because ISDV4 doesn't need a kernel module.  :)

---

### Post by bogamol on 2013-03-01
Hmm... Well I have xserver-xorg-input-wacom and xinput installed, but:

```
$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=11	[slave  keyboard (3)]
    &#8627; ACPI Virtual Keyboard Device            	id=13	[slave  keyboard (3)]
```

I did find a reference to it in lshal (Debian still uses HAL? Are they going to pick up systemd at some point?) ```
 [...] WACf004 [...] 
``` so I suspect it is being seen by something. I was worried that the device itself was not since I couldn't find it in lspci.

```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
05:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
05:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
```

```
$ uname -a
Linux heartOfGold-debian 2.6.32-5-amd64 #1 SMP Mon Feb 25 00:26:11 UTC 2013 x86_64 GNU/Linux
```

What kernel is Ubuntu using nowadays? 
In Gentoo, my kernel is 3.6.XX but I think I had some configuration issues going on so even if it is in the newer kernel, I don't have it set up right.

---

### Post by Favux on 2013-03-01
This thread really isn't the appropriate one to set up a ISDv4 on.  A new thread would be better.

That said let's find out your kernel and X Server version.  Debian, correct?
```
Xorg -version
```
If X Server 1.7 then HAL or more likely X Server 1.8 or later and xorg.conf.d.  Either way it does sound like it might be a configuration issue.  So we'd be checking either the Wacom .fdi file or the .conf file.

My point was with a ISDv4 serial device you do not need a kernel driver.  Just a X driver.

---

### Post by bogamol on 2013-03-02
Ok. the new thread is coming.

---

### Post by bogamol on 2013-03-02
Ok, the new thread is [here](http://ubuntuforums.org/showthread.php?t=2121465&p=12537200#post12537200).

---

### Post by Cognuss on 2013-03-29
Hello,
I am an archlinux user with a newly set up system running xfce, with kernel 3.8.4-1. 
I am trying to get a wacom artz2(UD-1212-R) tablet to work using a pl2303 usb-serial converter.

1 I have downloaded wacom_serial-120327-1.tar.bz2.

2 I have modified wacom_serial.c(changed #define SERIO_WACOM_IV 0x3d to #define SERIO_WACOM_IV 0x3e)
   and serio-ids.h(changed # define SERIO_WACOM_IV      0x3d to # define SERIO_WACOM_IV      0x3e)

3 I then did these commands to make and install it:
   make all
  sudo cp inputattach /usr/bin
  sudo cp wacom_serial.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet
  sudo depmod -a

4 I then started inputattach with the command:
   sudo inputattach --wacom_iv /dev/ttyUSB0

dmesg shows the error:
wacom_serial: probe of serio5 failed with error -5
serio: Serial port ttyUSB0
input (null): Timed out waiting for tablet to respond with model and version.
This is repeated over and over again.
If I touch the pen to the tablet dmesg shows:
input (null): got a garbled response of length #.
input (null): Timed out waiting for tablet to respond with configuration string.  Continuing anyway.
input (null): Timed out waiting for tablet to respond with coordinates string.  Continuing anyway.
input: Wacom protocol 4 serial tablet as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/ttyUSB0/tty/ttyUSB0/serio15/input/input14

Xorg.0.log shows this:
[   175.135] (II) config/udev: Adding input device Wacom protocol 4 serial tablet (/dev/input/event14)
[   175.135] (**) Wacom protocol 4 serial tablet: Applying InputClass "Wacom class"
[   175.135] (II) LoadModule: "wacom"
[   175.135] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[   175.182] (II) Module wacom: vendor="X.Org Foundation"
[   175.182]     compiled for 1.14.0, module version = 0.20.0
[   175.182]     Module class: X.Org XInput Driver
[   175.182]     ABI class: X.Org XInput driver, version 19.1
[   175.182] (II) Using input driver 'wacom' for 'Wacom protocol 4 serial tablet'
[   175.182] (**) Wacom protocol 4 serial tablet: always reports core events
[   175.182] (**) Option "Device" "/dev/input/event14"
[   175.182] (II) Wacom protocol 4 serial tablet: type not specified, assuming 'stylus'.
[   175.182] (II) Wacom protocol 4 serial tablet: other types will be automatically added.
[   175.182] (EE) Wacom protocol 4 serial tablet stylus: unable to ioctl xmax value.
[   175.186] (EE) PreInit returned 8 for "Wacom protocol 4 serial tablet stylus"
[   175.186] (II) UnloadModule: "wacom"

Any help would be appreciated.
Cognuss

---

### Post by Favux on 2013-03-31
Hi Cognuss,

Welcome to Ubuntu forums!


Not sure what is going on.  You're the first to report trying the 3.8 kernel as far as I am aware.  What is the X Server?
```
Xorg -version
```

I'm assuming:
> [ 175.182] (EE) Wacom protocol 4 serial tablet stylus: unable to ioctl xmax value.
[ 175.186] (EE) PreInit returned 8 for "Wacom protocol 4 serial tablet stylus"
[ 175.186] (II) UnloadModule: "wacom"
is due the dmesg error.

I'm trying to remember if the pl2303 usb-serial converter has the ioctl patch for xf86-input-wacom.  I think it did last time I looked.  Which was a long time ago admittedly.  I have the impression most the the converter's kernel drivers had been updated.  Discussed a bit in:
> "Configuring A Wacom Tablet In Lucid Lynx" thread: [http://ubuntuforums.org/showthread.php?t=1462026&page=3](http://ubuntuforums.org/showthread.php?t=1462026&page=3) - setting up a serial Wacom ArtzII tablet using a Keyspan serial->USB adapter, posts #24 to #34 with HOW TO at #34. Kernel patch for the Keyspan serial-to-USB driver, adds a dummy TIOCGSERIAL ioctl, on post #30.
Although it seems to me the ioctl grab was dropped in xf86-input-wacom a few releases ago and you now have to request it with a .conf option.  What version do you have?
```
xsetwacom -V
```

---

### Post by Cognuss on 2013-04-01
The X Server is version: 1.14.0 and xsetwacom -V returns: 0.20.0.
Also in case I wasn't clear nothing recognizes the tablet unless, 
the pen is being pressed onto the tablet like your drawing.

I forgot to tell you that I added the 70-serial-wacom.rules to /etc/udev/rules.d and this is what it contains:
ACTION=="add|change", SUBSYSTEM=="tty|pnp", ENV{NAME}="Wacom protocol IV serial tablet", 
SYMLINK+="input/wacom", ENV{ID_INPUT}="1", ENV{ID_INPUT_TABLET}="1"

Incase you need it, here is what 50-wacom.conf, for xorg, contains:

Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM|Hanwang|PTK-540WL"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection

# Waltop tablets
Section "InputClass"
    Identifier "Waltop class"
    MatchProduct "WALTOP"
    MatchIsTablet "on"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001|N-Trig Pen"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
EndSection

I do not have an xorg.conf file.
I don't know anything about ioctl.
Thank you for your help.
Cognuss

---

### Post by Favux on 2013-04-01
You shouldn't need the udev rule.  Go ahead and comment it out and see if it makes a difference.

You appear to be the first person reporting trying the wacom_serial.ko on basically the latest kernel, X Server, and xf86-input-wacom.  Perhaps that's where the problem is.  If so we'd need tokenrove to take a look.

When the serio driver is querying the tablet you are getting:
```
dmesg shows the error:
wacom_serial: probe of serio5 failed with error -5
serio: Serial port ttyUSB0
input (null): Timed out waiting for tablet to respond with model and version.
This is repeated over and over again.
If I touch the pen to the tablet dmesg shows:
input (null): got a garbled response of length #.
input (null): Timed out waiting for tablet to respond with configuration string. Continuing anyway.
input (null): Timed out waiting for tablet to respond with coordinates string. Continuing anyway.
input: Wacom protocol 4 serial tablet as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/ttyUSB0/tty/ttyUSB0/serio15/input/input14
```
So either the tablet is not responding in the expected time windows or it is garbling the protocol:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Serial_Protocol_IV](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Serial_Protocol_IV)

You need to establish communication with the tablet.  Does the tablet work in another release or OS?  That would rule out bad hardware.

It is possible setting it up through xorg.conf might help initialize it.

---

### Post by Cognuss on 2013-04-01
Commenting out the udev rule doesn't appear to do anything.  So I'll leave it commented out.
I should clarify that I don't always get the configuration and coordinates string errors,
sometimes it is just one or the other or none.
No it isn't a hardware problem, it works on windows xp.
What should I put in xorg.conf?
Thanks again.
Cognuss

---

### Post by Favux on 2013-04-07
Good, hardware ruled out.

Be sure you are comfortable editing xorg.conf with nano from the command line using the Recovery Mode option in case you break X.

The second part of the HOW TO post "Old serial tablet driver - for Lucid & Maverick" has a sample xorg.conf.  Start with just the stylus section.  If that doesn't break X with a restart then add the ServerLayout section.  But you can comment out the eraser and pad lines for now since you haven't added those sections yet.  Of course instead of:
```
    Option        "Device"         "/dev/ttyS0"
```
you would use:
```
    Option        "Device"         "/dev/ttyUSB0"
```

---

### Post by Cognuss on 2013-04-11
Okay I added:

Section "ServerLayout"
    Identifier    "X.org Configured"
    InputDevice   "stylus"
EndSection

and:

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"         "/dev/ttyUSB0"
    Option        "Type"           "stylus"
    Option        "ForceDevice"    "Serial"
EndSection

to the xorg.conf file created by nvidia.

Then I started the computer with tablet plugged in, without the pen drawing on the tablet.
xorg log shows this about the tablet:
[    14.289] (==) Using config file: "/etc/X11/xorg.conf"
[    14.289] (==) Using config directory: "/etc/X11/xorg.conf.d"
[    14.393] (==) ServerLayout "X.org Configured"
[    14.393] (**) |-->Screen "Screen0" (0)
[    14.393] (**) |   |-->Monitor "Monitor0"
[    14.393] (**) |   |-->Device "Device0"
[    14.393] (**) |-->Input Device "stylus"
[    14.393] (==) Automatically adding devices
[    14.393] (==) Automatically enabling devices
[    14.393] (==) Automatically adding GPU devices

[    18.766] (II) Using input driver 'wacom' for 'stylus'
[    18.766] (**) stylus: always reports core events
[    18.766] (**) Option "Device" "/dev/ttyUSB0"
[    18.766] (**) Option "Type" "stylus"
[    18.767] (**) Option "StopBits" "1"
[    18.767] (**) Option "DataBits" "8"
[    18.767] (**) Option "Parity" "None"
[    18.767] (**) Option "Vmin" "1"
[    18.767] (**) Option "Vtime" "10"
[    18.767] (**) Option "FlowControl" "Xoff"
[    22.022] (WW) stylus: Waited too long for answer (failed after 3 tries).
[    22.022] (WW) stylus: Query failed with 19200 baud. Trying 38400.
[    25.276] (WW) stylus: Waited too long for answer (failed after 3 tries).
[    25.276] (II) stylus: serial tablet id 0x90.
[    25.373] (EE) PreInit returned 8 for "stylus"
[    25.373] (II) UnloadModule: "wacom"

I then opened the terminal and typed sudo inputattach --wacom_iv /dev/ttyUSB0
dmesg shows this:
[  182.536439] serio: Serial port ttyUSB0
and xorg log doesn't show anything else.

I started the computer with the tablet plugged in and with the pen drawing on the tablet.
xorg log shows three different variants.
it shows this:
[    13.910] (==) Using config file: "/etc/X11/xorg.conf"
[    13.910] (==) Using config directory: "/etc/X11/xorg.conf.d"
[    14.031] (==) ServerLayout "X.org Configured"
[    14.031] (**) |-->Screen "Screen0" (0)
[    14.031] (**) |   |-->Monitor "Monitor0"
[    14.031] (**) |   |-->Device "Device0"
[    14.031] (**) |-->Input Device "stylus"
[    14.031] (==) Automatically adding devices
[    14.031] (==) Automatically enabling devices
[    14.031] (==) Automatically adding GPU devices

[    18.362] (II) Using input driver 'wacom' for 'stylus'
[    18.362] (**) stylus: always reports core events
[    18.362] (**) Option "Device" "/dev/ttyUSB0"
[    18.362] (**) Option "Type" "stylus"
[    18.363] (**) Option "StopBits" "1"
[    18.363] (**) Option "DataBits" "8"
[    18.363] (**) Option "Parity" "None"
[    18.363] (**) Option "Vmin" "1"
[    18.363] (**) Option "Vtime" "10"
[    18.364] (**) Option "FlowControl" "Xoff"
[    18.616] (II) stylus: serial tablet id 0x90.
[    18.616] (--) stylus: using pressure threshold of 27 for button 1
[    18.616] (--) stylus: Wacom General ISDV4 tablet maxX=51092 maxY=5116 maxZ=127 resX=100000 resY=100000  tilt=disabled
[    18.750] (II) XINPUT: Adding extended input device "stylus" (type: STYLUS, id 6)
[    18.750] (**) stylus: (accel) keeping acceleration scheme 1
[    18.750] (**) stylus: (accel) acceleration profile 0
[    18.750] (**) stylus: (accel) acceleration factor: 2.000
[    18.750] (**) stylus: (accel) acceleration threshold: 4
[    18.751] (**) Option "BaudRate" "19200"

and then there are warnings through out the log like this:

(WW) stylus: bad data at 1 v=fe l=9

and at the end it goes on for ~4000 lines as I scrolled the pen on the tablet:
(WW) stylus: bad data at 1 v=9e l=9
(WW) stylus: bad data at 1 v=fe l=9
(WW) stylus: bad data at 1 v=80 l=9
(WW) stylus: bad data at 1 v=9e l=9
(WW) stylus: bad data at 1 v=fe l=9
(WW) stylus: bad data at 1 v=9e l=9
(WW) stylus: bad data at 1 v=fe l=9
(WW) stylus: bad data at 1 v=e0 l=9
(WW) stylus: bad data at 1 v=fe l=9
(WW) stylus: bad data at 1 v=80 l=9
(WW) stylus: bad data at 1 v=e0 l=9
(WW) stylus: bad data at 1 v=fe l=9
(WW) stylus: bad data at 1 v=f8 l=9
(WW) stylus: bad data at 1 v=fe l=9
(WW) stylus: bad data at 1 v=f8 l=9
(WW) stylus: bad data at 1 v=fe l=9

or it shows this:
[    13.038] (==) Using config file: "/etc/X11/xorg.conf"
[    13.038] (==) Using config directory: "/etc/X11/xorg.conf.d"
[    13.175] (==) ServerLayout "X.org Configured"
[    13.175] (**) |-->Screen "Screen0" (0)
[    13.175] (**) |   |-->Monitor "Monitor0"
[    13.175] (**) |   |-->Device "Device0"
[    13.175] (**) |-->Input Device "stylus"
[    13.175] (==) Automatically adding devices
[    13.175] (==) Automatically enabling devices
[    13.175] (==) Automatically adding GPU devices

[    18.769] (II) Using input driver 'wacom' for 'stylus'
[    18.769] (**) stylus: always reports core events
[    18.769] (**) Option "Device" "/dev/ttyUSB0"
[    18.769] (**) Option "Type" "stylus"
[    18.770] (**) Option "StopBits" "1"
[    18.770] (**) Option "DataBits" "8"
[    18.770] (**) Option "Parity" "None"
[    18.770] (**) Option "Vmin" "1"
[    18.770] (**) Option "Vtime" "10"
[    18.770] (**) Option "FlowControl" "Xoff"
[    19.026] (WW) stylus: Query failed with 19200 baud. Trying 38400.
[    19.278] (II) stylus: serial tablet id 0x90.
[    19.376] (EE) PreInit returned 8 for "stylus"
[    19.377] (II) UnloadModule: "wacom"

or this:
[    19.252] (II) Using input driver 'wacom' for 'stylus'
[    19.253] (**) stylus: always reports core events
[    19.253] (**) Option "Device" "/dev/ttyUSB0"
[    19.253] (**) Option "Type" "stylus"
[    19.253] (**) Option "StopBits" "1"
[    19.253] (**) Option "DataBits" "8"
[    19.253] (**) Option "Parity" "None"
[    19.253] (**) Option "Vmin" "1"
[    19.253] (**) Option "Vtime" "10"
[    19.253] (**) Option "FlowControl" "Xoff"
[    19.505] (EE) stylus: Error while parsing ISDV4 query.
[    19.505] 
[    19.636] (EE) PreInit returned 8 for "stylus"
[    19.637] (II) UnloadModule: "wacom"

I opened the terminal and typed sudo inputattach --wacom_iv /dev/ttyUSB0
dmesg shows this:
[  182.536439] serio: Serial port ttyUSB0
and xorg log doesnt show anything else.

I started the computer without the tablet plugged in.
xorg log now shows this:
[    13.612] (==) Using config file: "/etc/X11/xorg.conf"
[    13.612] (==) Using config directory: "/etc/X11/xorg.conf.d"
[    13.732] (==) ServerLayout "X.org Configured"
[    13.732] (**) |-->Screen "Screen0" (0)
[    13.732] (**) |   |-->Monitor "Monitor0"
[    13.732] (**) |   |-->Device "Device0"
[    13.732] (**) |-->Input Device "stylus"
[    13.732] (==) Automatically adding devices
[    13.732] (==) Automatically enabling devices
[    13.732] (==) Automatically adding GPU devices

[    18.689] (II) Using input driver 'wacom' for 'stylus'
[    18.689] (**) stylus: always reports core events
[    18.689] (**) Option "Device" "/dev/ttyUSB0"
[    18.689] (**) Option "Type" "stylus"
[    18.689] (EE) xf86OpenSerial: Cannot open device /dev/ttyUSB0
    No such file or directory.
[    18.689] (EE) stylus: Error opening /dev/ttyUSB0 (No such file or directory)
[    18.689] (EE) PreInit returned 8 for "stylus"
[    18.689] (II) UnloadModule: "wacom"

then I plugged in and turned on the tablet.
opened the terminal and typed sudo inputattach --wacom_iv /dev/ttyUSB0
dmesg shows this:
[  377.974905] serio: Serial port ttyUSB0
xorg log doesnt show anything else.
Cognuss

---

### Post by Favux on 2013-04-12
Well it looks like the xorg.conf entries didn't end the initialization problem.  Sometimes it does.  The one time it initialized is when you got the "stylus bad data" entries.  So sort of progress.  Was the pointer arrow tracking the pen/stylus with that one?

The one thing you could do is comment out **Option "ForceDevice" "Serial"**.  That was only needed with very early versions of xf86-input-wacom soon after the fork from linuxwacom.  I'm dubious that will help though.

I think you'll have to contact tokenrove for this.  Hopefully he has some time available to take a look.

---

### Post by Cognuss on 2013-04-12
No unfortunatly the pointer arrow doesn't track the pen.
I commented out the Option "ForceDevice" "Serial" but it didn't make any difference.
How should I contact tokenrove?
Cognuss

---

### Post by Favux on 2013-04-12
He has a link to his e-mail on his page.  Tokenrove's [EMAIL="julian@cipht.net"]e-mail address[/EMAIL].

---

### Post by Cognuss on 2013-04-15
I have e-mailed tokenrove, hopefully with his help all this will work out.
Thanks for all the help Favux.
Cognuss

---

### Post by sino1992 on 2013-04-17
1 Download wacom_serial-120327-1.tar.bz2

 2 Change 0x3d to 0x3e (wacom_serial.c, serio-ids.h)

 3 make all
   sudo cp inputattach /usr/bin
   sudo cp wacom_serial.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet
   sudo depmod -a
   sudo inputattach --wacom_iv /dev/ttyS0

However, can't move mouse cursor with touch pen.

wacom_serial-120327-1.tar.bz2
it was works on UbuntuStudio13.04 until yesterday.
  
Tablet   Wacom PL-550
OS       UbuntuStudio13.04

---

### Post by Favux on 2013-04-19
Hi sino1992,

Welcome to Ubuntu forums!


Hard to believe you had a hardware failure just then.  I assume you reinstalled wacom_serial.ko because Update Manager installed a new kernel?  So reinstalling it should have worked which means something else changed.  Do you remember what else it installed?  Anything to do with the X Server or xf86-input-wacom?  If you don't remember you can check Update Manger's log at /var/log/apt/history.log.

---

### Post by klein5366 on 2013-04-26
Information that might be of some use to some of you i’d like to share.

sometime ago i got a digitizer ii ud-1218-r  but it did not have the wall wart or serial cable with it, in my quest for a serial cable i came across one man that had used a serial cable to usb hack and one drawing of the original serial cable used. and at that time no serial driver in Linux. 

so getting this ud-1218-r working was looking pretty thin, until i came across a forum where they are using a teency 2.0 to complicate with the tablet  over usb, you do need to take the tablet  apart and do some soldering  and some programing . but in the end if all goes well your tablet works and all you have is a usb cable coming out of it. the tablet will get it’s power from the teency through usb connection.   

i did everything from xubuntu 12.04 64bit and i have tested it on ubuntu 10.04 64bit and xubuntu 12.04 64bit the kernel drivers were already installed.  

lsusb:
Bus 005 Device 003: ID 056a:0045 Wacom Co., Ltd Intuos2 12x18

so now ubuntu or xubuntu See’s my digitizer ii ud-1218-r  as a  ID 056a:0045 Wacom Co., Ltd Intuos2 12x18.

link below for forum doing the hack 
[http://forum.bongofish.co.uk/index.php?board=25.0](http://forum.bongofish.co.uk/index.php?board=25.0)

---

### Post by tokenrove on 2013-05-08
> **Cognuss said:**
> I have e-mailed tokenrove, hopefully with his help all this will work out. Thanks for all the help Favux. Cognuss

Hi everyone.

I just wanted to make a public statement about the status of the driver; here seems to be the best place as most of the users looking for support come through this thread.  Everyone who has emailed me knows I haven't had much time to troubleshoot issues with the driver, and I apologize for that.  I think many of these problems come from the driver not being integrated in the kernel.

In February, I submitted a patch to the linux-input maintainer, which was said to be acceptable, but I was asked to look into unifying my driver with the USB wacom drivers instead.  There are two reasons why this hasn't happened yet, and may not happen:

[LIST=1]
[*]I haven't had much time to work on the driver in general, let alone try  to merge it with other code (which I do not expect to be a fruitful  effort given the significant differences between the drivers).
[*]This will require significant cooperation from the "modern" Wacom driver  maintainers, who history has shown would be happy to see Wacom serial  devices disappear from the face of the Earth.  I hate to put this so  antagonistically, but I can't help seeing it this way after the reaction  to my kernel submission.
[/LIST]

I wanted to let everyone know that there is a good chance I will work on this again in the next couple of months (perhaps an intermediary solution would at least be to get a serio ID reserved for the driver in future kernels), but overall, I don't have a lot of time to work on it, and if someone else wants to step up and maintain the code (which probably actually mostly means more politicking and less coding), the opportunity is there.  The code's all GPL, you'd have my blessing, et cetera.

Thanks to everyone using the driver, and let's hope there's a brighter future for these excellent devices than tossing them in the garbage.

---

### Post by Cognuss on 2013-08-13
Hello I'm back again.  It turns out that last time I didn't have the driver correctly installed. :oops:
Now that I have it installed properly, can we try this again?
 Xorg shows this about it:
```
[ 12639.137] (II) config/udev: Adding input device Wacom protocol 4 serial tablet (/dev/input/event13)
[ 12639.137] (**) Wacom protocol 4 serial tablet: Applying InputClass "evdev tablet catchall"
[ 12639.137] (**) Wacom protocol 4 serial tablet: Applying InputClass "Wacom class"
[ 12639.137] (II) Using input driver 'wacom' for 'Wacom protocol 4 serial tablet'
[ 12639.137] (**) Wacom protocol 4 serial tablet: always reports core events
[ 12639.137] (**) Option "Device" "/dev/input/event13"
[ 12639.137] (II) Wacom protocol 4 serial tablet: type not specified, assuming 'stylus'.
[ 12639.137] (II) Wacom protocol 4 serial tablet: other types will be automatically added.
[ 12639.137] (EE) Wacom protocol 4 serial tablet stylus: unable to ioctl xmax value.
[ 12639.208] (EE) PreInit returned 8 for "Wacom protocol 4 serial tablet stylus"
[ 12639.208] (II) UnloadModule: "wacom"
```

My 50-wacom.conf contains this:
```
Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM|Hanwang|PTK-540WL"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection

# Waltop tablets
Section "InputClass"
    Identifier "Waltop class"
    MatchProduct "WALTOP"
    MatchIsTablet "on"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001|N-Trig Pen"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
EndSection

```
and my xorg.conf file has this:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 310.44  (buildmeister@swio-display-x86-rhel47-07)  Wed Mar 27 15:56:20 PDT 2013

#Section "Files"
#EndSection

Section "ServerLayout"
    Identifier    "X.org Configured"
    InputDevice   "stylus"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"         "/dev/ttyUSB0"
    Option        "Type"           "stylus"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    Gamma          0.5
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
    Option         "NoLogo" "true"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080"
    EndSubSection
EndSection
```

Any help you can give would greatly be appreciated.
Cognuss

---

### Post by computer2 on 2013-08-16
Oh boy, sorry to bump this thread with nothing useful, but I felt I needed to register to the forums to express my gratitude.
I got my stupid Graphire2 working thanks to the gathered knowledge in this thread!

 One line should be bolded though ... or written in 50pt ;)
**When you run the make all command both the compiled inputattach.ko along with wacom_serial.ko will now no longer conflict with tsc40.ko.**

I usually don't believe in magic, but I spent hours wondering why an installed driver would work perfectly, and completely disappear after a reboot.

[IMG]http://i.imgur.com/0VtETuY.gif[/IMG]

To everyone involved!

---

### Post by Favux on 2013-08-24
@ Cognuss,

Inspiration is not jumping out at me.  Have you tried commenting out the xorg.conf Wacom stylus stuff and checked if there is any difference with just xorg.conf.d?  Did we establish what version of xf86-input-wacom you are using?
```
xsetwacom -V
```
What are you seeing in **lsmod**?  Did you specify what serial to usb converter you are using?  We may have to check its kernel driver to see if it has the support for the Wacom X driver ioctl.  But as I mentioned that was dropped a while ago so I'm a bit puzzled by that error message.  Maybe we should be going the other way and be specifying the ioctl option in xorg.conf or xorg.conf.d?  Somehow your converter's kernel driver requires that?  Never needed to do that before.  Might be a pain to figure out the details because I sure don't remember.  If we're lucky maybe there was a wiki entry somewhere.

I gather no help from tokenrove?


@ computer2,

Glad you got set up.  Nice job.  :)

Unfortunately I can't update the HOW TO in this thread.  They locked us out in May of 2012.  All HOW TOs were suppose to be transformed into wiki pages and transferred to the community wiki.  The up-datable version of this HOW TO is [here]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110412").

---

### Post by Cognuss on 2013-09-01
I tried commenting out the Wacom stylus stuff in xorg.conf but it didn't make a difference.
The version of xf86-input-wacom that I am using is 0.22.1
Here is what lsmod shows:
```

Module                  Size  Used by
wacom_serial            5786  0 
serport                 2767  1 
usbmon                 20019  0 
nfnetlink_queue        11322  0 
nfnetlink_log           8313  0 
nfnetlink               4301  2 nfnetlink_log,nfnetlink_queue
nls_utf8                1320  1 
udf                    78961  1 
crc_itu_t               1363  1 udf
fuse                   74541  5 
ath3k                   7557  0 
btusb                  18496  0 
bluetooth             308366  3 ath3k,btusb
uvcvideo               72761  0 
pl2303                 12414  1 
videobuf2_vmalloc       3272  1 uvcvideo
videobuf2_memops        2335  1 videobuf2_vmalloc
videobuf2_core         27797  1 uvcvideo
videodev              105373  2 uvcvideo,videobuf2_core
usbserial              32697  3 pl2303
crc16                   1359  1 bluetooth
arc4                    2000  2 
nvidia              11246640  52 
media                  10916  2 uvcvideo,videodev
ath9k                  88768  0 
ath9k_common            1991  1 ath9k
intel_powerclamp        8802  0 
ath9k_hw              370370  2 ath9k_common,ath9k
coretemp                6038  0 
ath                    15681  3 ath9k_common,ath9k,ath9k_hw
mac80211              455011  1 ath9k
joydev                  9663  0 
cfg80211              406112  3 ath,ath9k,mac80211
kvm_intel             128977  0 
kvm                   376394  1 kvm_intel
snd_hda_codec_hdmi     29701  1 
iTCO_wdt                5407  0 
iTCO_vendor_support     1929  1 iTCO_wdt
crc32_pclmul            3019  0 
asus_nb_wmi             6600  0 
atl1c                  36674  0 
snd_hda_codec_via      19814  1 
ghash_clmulni_intel     4501  0 
psmouse                85132  0 
snd_hda_intel          35309  4 
evdev                   9880  13 
shpchp                 25489  0 
i2c_i801               11237  0 
aesni_intel            46124  0 
serio_raw               5041  0 
aes_x86_64              7399  1 aesni_intel
snd_hda_codec         147506  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
lrw                     3565  1 aesni_intel
i2c_core               23720  3 i2c_i801,nvidia,videodev
snd_hwdep               6332  1 snd_hda_codec
snd_pcm                77765  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc          7234  2 snd_pcm,snd_hda_intel
snd_timer              18718  1 snd_pcm
snd                    58950  15 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_hda_codec,snd_hda_intel
mei_me                  9688  0 
soundcore               5418  1 snd
gf128mul                5858  1 lrw
mei                    61444  1 mei_me
glue_helper             4609  1 aesni_intel
ac                      3324  0 
thermal                 8620  0 
lpc_ich                12849  0 
ablk_helper             1972  1 aesni_intel
cryptd                  8473  3 ghash_clmulni_intel,aesni_intel,ablk_helper
button                  4669  0 
battery                 6925  0 
mperf                   1267  0 
pcspkr                  2027  0 
microcode              13172  0 
processor              27755  0
vboxnetflt             17612  0
vboxdrv              1823264  1 vboxnetflt
nfs                   145074  0
lockd                  76773  1 nfs
sunrpc                220799  2 nfs,lockd
fscache                44575  1 nfs
asus_wmi               16242  1 asus_nb_wmi
sparse_keymap           3114  1 asus_wmi
rfkill                 15666  4 cfg80211,bluetooth,asus_wmi
wmi                     8283  1 asus_wmi
video                  11328  1 asus_wmi
xfs                   784867  1
libcrc32c               1002  1 xfs
sr_mod                 14898  1
sd_mod                 30730  3
cdrom                  34848  1 sr_mod
hid_generic             1153  0
usbhid                 41466  0
hid                    88502  2 hid_generic,usbhid
ahci                   22792  3
libahci                21169  1 ahci
crc32c_intel           14249  1
libata                171016  2 ahci,libahci
ehci_pci                4120  0
xhci_hcd               89455  0
scsi_mod              127772  3 libata,sd_mod,sr_mod
ehci_hcd               47640  1 ehci_pci
usbcore               177151  10 ath3k,btusb,uvcvideo,usbserial,ehci_hcd,ehci_pci,pl2303,usbhid,usbmon,xhci_hcd
usb_common              1648  1 usbcore
```

The serial to usb converter I am using is a pl2303, and I believe the pl2303 driver
has support for the Wacom X driver ioctl.
I don't think xorg or ioctl is the problem.  As far as I can tell the driver is requesting
information from the tablet, but the tablet isn't responding.  And since the tablet
isn't responding xorg can't get the information it needs.
No I haven't heard anything else from tokenrove, but I might send him another email
now that I have had a look at the driver.
Cognuss

---

### Post by zxcvbs3 on 2013-09-09
Hi im having this problem with my hp elitebook 2740p tablet.

[http://www.youtube.com/watch?v=c3cfg4NolWQ](http://www.youtube.com/watch?v=c3cfg4NolWQ)

When doing intensive tasks the mouse gets crazy, if i disable the touch from xinput, the mouse works ok.
Also disabling any of the wacom devices (stylus, eraser, or touch), disables all the functionality.

```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=15    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                   id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; HP Webcam [2 MP Macro]                      id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=14    [slave  keyboard (3)]

```

I know there is an official hp firmware fix:
[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?cc=us&prodSeriesId=4145567&prodNameId=4145452&taskId=135&swItem=ob-94092-1](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?cc=us&prodSeriesId=4145567&prodNameId=4145452&taskId=135&swItem=ob-94092-1)

Thanks.

---

### Post by zxcvbs3 on 2013-09-11
Hi searching a little more, this is a hp firmware issue.
I couldnt get to install the lastest firmware. 

Before doing anything please check instructions, and display models (flashing a wrong firmware can break the touch functionality). I downloaded:
[ftp://ftp.hp.com/pub/softpaq/sp49001-49500/sp49201.exe](ftp://ftp.hp.com/pub/softpaq/sp49001-49500/sp49201.exe)
I couldnt get to install the lastest firmware. Using it on windows it searches for a Hydis Display, but as win detects the driver as generic pnp monitor,(dont know what string is searching the installer), it ends on detecting display. 
My screen is a Hydis. This is the hw id (on win): 
```

MONITOR\BOE08A0
*PNP09FF

```
How can i unpack this exe, to get the firmware files and loaders? i tried some tools like universal extractor without success, will try ollydbg.
[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c02688956&dimid=1197316750&dicid=alr_jan11&jumpid=em_alerts/us/jan11/all/xbu/emailsubid/mrm/mcc/loc/rbu_category/alerts](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c02688956&dimid=1197316750&dicid=alr_jan11&jumpid=em_alerts/us/jan11/all/xbu/emailsubid/mrm/mcc/loc/rbu_category/alerts)

---

### Post by zxcvbs3 on 2013-09-12
> **zxcvbs3 said:**
> Hi searching a little more, this is a hp firmware issue.
I couldnt get to install the lastest firmware. 

Before doing anything please check instructions, and display models (flashing a wrong firmware can break the touch functionality). I downloaded:
[ftp://ftp.hp.com/pub/softpaq/sp49001-49500/sp49201.exe](ftp://ftp.hp.com/pub/softpaq/sp49001-49500/sp49201.exe)
I couldnt get to install the lastest firmware. Using it on windows it searches for a Hydis Display, but as win detects the driver as generic pnp monitor,(dont know what string is searching the installer), it ends on detecting display. 
My screen is a Hydis. This is the hw id (on win): 
```

MONITOR\BOE08A0
*PNP09FF

```
How can i unpack this exe, to get the firmware files and loaders? i tried some tools like universal extractor without success, will try ollydbg.
[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c02688956&dimid=1197316750&dicid=alr_jan11&jumpid=em_alerts/us/jan11/all/xbu/emailsubid/mrm/mcc/loc/rbu_category/alerts](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c02688956&dimid=1197316750&dicid=alr_jan11&jumpid=em_alerts/us/jan11/all/xbu/emailsubid/mrm/mcc/loc/rbu_category/alerts)


PLEASE READ THIS:

DONT USE [sp49201.exe]("ftp://ftp.hp.com/pub/softpaq/sp49001-49500/sp49201.exe") FW PATCH, it will make the fan work harder, and on linux at least on ubuntu, shut off the machine after some minutes.
Dont know about the last patch because i couldnt try it, but if you do PLEASE, USE THE FIRMWARE UPDATE TOOLS TO BACK UP, YOUR FACTORY FW, AND THEN TRY UPDATE. THE DEFAULT BAT DOESNT MAKE THIS BACKUP.

Well i installed win7 32 bits (i was trying the wacom firmware updater on Win8 x64), it ugraded to the lastest fw fix ( [SP52649 )]("ftp://ftp.hp.com/pub/softpaq/sp52501-53000/sp52649.exe") 35D_0F0E/35D_0C6F REV: A   
At the moment i dont get ghost clicks, but ubuntu halts/shut down, when the cpu load is higher.

---

### Post by daco2 on 2014-05-13
Hi,
I'm trying to reinstall my Intuos GD-0608-R tablet on ubuntu 14.04 (which worked very well on 10.04) with no success.
I don't know if it's an IV or V protocol so I tried both :
- with wacom_serial, the pointer move but the behavior is anarchic
- with wacom_seral5, no module is loaded and nothing appear in xorg.0.log

I have to change the tablet ID to 0x3e and 0x3f otherwise the tsc40 module is loaded.
Is there someone to help me ?
Thanks.

---

### Post by daco2 on 2014-05-17
Problem solved !
After a lot of hours testing drivers, I found the solution :
The wacom_v_init function in inputattach.c doesn't test every speed connection while wacom_iv_init does.

I just had to change to this in wacom_v_init :
[COLOR=#0000cd]    setline(fd, CS8, B9600);
    if (write(fd, "$\r", 5) != 5)
                return -1;
    usleep(100 * 1000);
    return 0;
[/COLOR]where "$/r" is to reset baud rate to 9600 bauds. Is it just my hardware posing problem ?

Changing SERIO_WACOM_V to 0x3e or more avoid module tsc40 loading. And no need to put a wacom_rule.
Now everything is working well under ubuntu 14.04 !!!

---

### Post by Brent_Santin on 2014-12-21
Hi,

I've been trying to get my Wacom ArtPad II (KT-0405-R, protocol IV tablet.) working under Lubuntu Trusty Tahr (Ubuntu 14.04 LTS) and haven't had any success. Part of this has been that there seems to be an overwhelming and confusing amount of tutorials online, all from different dates and with different instructions, and no way to determine which one works with the latest release of the operating system. Some early tutorials suggest patching the kernal to add serial tablet support, other later ones say that serial tablet support has been added to the kernal and their is no need to patch, and still other threads suggest that serial support was dropped from the Wacom drivers at some point.

I'm really not sure what advice to follow.  It also seems that the latest update to the original tutorial in this thread was made in 2012, so I don't even know if any of the information is still valid.

What I have tried (without success) is to install the Wacom drivers from the Synaptic Software repository:

[B]xserver-xorg-input-wacom 0.23.0 ubuntu
libwacom2-dbg
libwacom-common[/B]

There also seems to be a package on the repository which I've been reluctant to install because it doesn't install by default and I'm not sure what it does (description is simply "This is used for upgrading from precise to trusty"):

[B]xserver-xorg-input-wacom-lts-trusty
[B]xserver-xorg-input-wacom-lts-trusty-dbg

[/B][/B]Then I edited my xorg.conf file to include the devices as suggested in the first message of this thread: 

[B]Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"         "/dev/ttyS0"
    Option        "Type"           "stylus"
    Option        "ForceDevice"    "Serial"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"         "/dev/ttyS0"
    Option        "Type"           "eraser"
    Option        "ForceDevice"    "Serial"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"         "/dev/ttyS0"
    Option        "Type"           "cursor"
    Option        "ForceDevice"    "Serial"
EndSection

Section "ServerLayout"
    Identifier    "X.org Configured"
    InputDevice   "stylus"
    InputDevice   "eraser"
    InputDevice   "cursor"
EndSection

[/B]Rebooted, etc. none of this did anything to detect my serial tablet.

So I'm not really sure what to do.  I only switched to Linux about 8 months ago.  I really liked the way Lubuntu detected and made a lot of my old hardware useable again (SCSI scanner, etc.) when the newer versions of Windows had abandoned them.  But it seems too bad that this serial tablet cannot be used (but I probably just don't know what I'm doing).

I'm not afraid of Command Line work (I grew up using MS-DOS and the Amiga CLI), I just am not sure which instructions I should even be using, or whether serial tablet support is even something that is possible anymore.

Is there anyone that has knowledge in this area? I'm not sure even where to start.

Thanks.

---

### Post by tokenrove on 2014-12-23
The driver for your tablet is included in the Linux kernel as of version 3.17.  You'll need a corresponding version of inputattach and so on.  Unfortunately I can't speak for the Ubuntu side of things and I'm not sure what steps you'll need to take, but you will need the new driver in one form or another to get it working.  I'm sure the instructions can be updated to be much simpler once distributions are shipping this kernel by default.  You do need the driver, a udev rule, and inputattach; you shouldn't need to edit any X configuration to get it working -- any instructions about that are probably very out of date.

(By the way, I wrote this driver because I feel the same way about older hardware; Linux should continue to support devices people are still using.)

Oh, if you need to get the last source for the driver before it went into the kernel, please see Hans de Goede's repository on github:
  [https://github.com/jwrdegoede/wacom_serial](https://github.com/jwrdegoede/wacom_serial)

---

### Post by Brent_Santin on 2014-12-30
> **tokenrove said:**
> The driver for your tablet is included in the Linux kernel as of version 3.17.

Hi Tokenrove,

Thanks for the reply.  Sorry for my delay in responding - I am new to Linux and had to research many of the terms you used. 
I used the "uname -r" command to try and determine my kernal version in Lubuntu Trusty Tahr.

The command reported:
3.13.0-43-generic

Which I assume means I am several versions behind the 3.17 kernal that would include the driver I need.
So for now I'm stuck?

I don't know how to get the driver otherwise.  I've never compiled anything from source code before.

---

### Post by tokenrove on 2015-01-02
> **Brent_Santin said:**
> 
Which I assume means I am several versions behind the 3.17 kernal that would include the driver I need.
So for now I'm stuck?

I don't know how to get the driver otherwise.  I've never compiled anything from source code before.

Perhaps someone else here can help you but I'm afraid I won't be too much help; at least the situation should improve in the future when this kernel is shipped with your distribution.

If you're willing to try, you should be able to piece together instructions from this thread and my blog post on the topic: [http://www.cipht.net/2011/07/02/wacom_serial-initial-release.html]("http://www.cipht.net/2011/07/02/wacom_serial-initial-release.html;"); I'll try to give you an overview of what you need to do.  You'll probably want the last version of the driver from the github repository I linked to in my previous post; you can clone it with ```
git clone https://github.com/jwrdegoede/wacom_serial.git
```; this means in step 1 in my blog post, you'll clone instead of unpacking the tar.gz file, but otherwise cd into the directory that is created and run ```
make all
```.  If you get any errors, you're missing some packages, most likely build-essential and linux-headers-<your kernel version>, which you can install with ```
apt-get install build-essential linux-headers-amd64
``` or similar.  I'm afraid that I can't be too specific because I'm primarily a Debian user.

Let us know how it goes.

---

### Post by kb8923 on 2015-02-06
> **tokenrove said:**
> 

If you're willing to try, you should be able to piece together instructions from this thread and my blog post on the topic: [http://www.cipht.net/2011/07/02/wacom_serial-initial-release.html]("http://www.cipht.net/2011/07/02/wacom_serial-initial-release.html;")

Let us know how it goes.

Hi, I am affraid this link is dead, that's too bad, I am also trying to make my Intuos GD 405-R work with my new Linux machine. Right now I'm on Linux 3.13.0-45-generic x86_64 and  KDE 4.14.2. I was able to use this tablet on my previous Linux system, but haven't been able to do so on this new one .

---

### Post by ziad2 on 2015-02-07
Hello, I have installed Ubuntu 14.04 on my chromebook (with crouton) and I want to use my Wacom (model CTL-480) Tablet on it.

"uname -r" indicates : 3.10.18

I downloaded "input-wacom-0.26.0.tar.bz2"

I followed the tutorial but when I write : "[FONT=Ubuntu Mono]./configure --prefix=/usr"

[/FONT]I have that : 

"BUILD ENVIRONMENT : 
linux kernel - yes
kernel source - no

We could not find the kernel development environment to build the driver. Please install the kernel source or the kernel development package and try again."

Is there a solution to set up my tablet ? Thank you !

---

### Post by tokenrove on 2015-02-07
> **kb8923 said:**
> Hi, I am affraid this link is dead, that's too bad, I am also trying to make my Intuos GD 405-R work with my new Linux machine. Right now I'm on Linux 3.13.0-45-generic x86_64 and  KDE 4.14.2. I was able to use this tablet on my previous Linux system, but haven't been able to do so on this new one .

Oops, the actual link isn't dead, but a semicolon was accidentally included in the link.  It's
  [http://www.cipht.net/2011/07/02/wacom_serial-initial-release.html](http://www.cipht.net/2011/07/02/wacom_serial-initial-release.html)
and I should also note that the Wacom IV patch is now included with linuxconsole upstream.

---

### Post by tokenrove on 2015-02-07
> **ziad2 said:**
> 
We could not find the kernel development environment to build the driver. Please install the kernel source or the kernel development package and try again."

Is there a solution to set up my tablet ? Thank you !

Try ```
apt-get install build-essential linux-headers
```; you might have to install a specific version of linux-headers that matches your kernel.

I should note that PenPartner devices are broken in the version of the driver in kernel 3.17; when I get a moment soon, I'm going to try to fix this.  If anyone has a PenPartner device and would be interested in testing for me, please email me.  Thanks.

---

### Post by kb8923 on 2015-02-11
It seems that no matter what I try I always end up with bunch of errors such as "invalid mode '--wacom_v'"and the same "No tablet device detected" in my System Settings panel in the end.
Yet my serial to usb adapter appears properly mounted and listed when I lsusb.
It would be nice to start a new walk through.

---

### Post by tokenrove on 2015-02-18
> **kb8923 said:**
> It seems that no matter what I try I always end up with bunch of errors such as "invalid mode '--wacom_v'"and the same "No tablet device detected" in my System Settings panel in the end.

Which version of inputattach are you using?  Is this for roaldfre's protocol V driver?

> **kb8923 said:**
> It would be nice to start a new walk through.

Now that the suitable patches are in for linuxconsole and the kernel, it would make sense to write a new tutorial.

---

### Post by kb8923 on 2015-02-19
I did try a bunch of different versions and I'm losing track now, that's why it's getting confusing.

---

### Post by Ti-nérisson on 2015-02-24
Hi. I'm trying to get my old Intuos 1 to work so I followed the tutorial [here]("http://www.cipht.net/2011/07/02/wacom_serial-initial-release.html"). But I'm stuck at the dpkg-buildpackage step. Here is what I get :
```
root@me-laptop:/home/me/Intuos/wacom_serial5-master/joystick-1.4.3# dpkg-buildpackage
dpkg-buildpackage: source package joystick
dpkg-buildpackage: source version 1:1.4.3-1
dpkg-buildpackage: source changed by Stephen Kitt <steve@sk2.org>
dpkg-buildpackage: host architecture amd64
 dpkg-source --before-build joystick-1.4.3
 debian/rules clean
PREFIX=/usr dh clean
   dh_testdir
   dh_auto_clean
make[1]: Entering directory `/home/me/Intuos/wacom_serial5-master/joystick-1.4.3'
make -C utils distclean
make[2]: Entering directory `/home/me/Intuos/wacom_serial5-master/joystick-1.4.3/utils'
rm -f *.o *.swp inputattach jstest jscal fftest ffmvforce ffset ffcfstress jscal-restore jscal-store *.orig *.rej map *~
make[2]: Leaving directory `/home/me/Intuos/wacom_serial5-master/joystick-1.4.3/utils'
make[1]: Leaving directory `/home/me/Intuos/wacom_serial5-master/joystick-1.4.3'
   dh_clean
 dpkg-source -b joystick-1.4.3
dpkg-source: info: using source format `3.0 (quilt)'
dpkg-source: info: building joystick using existing ./joystick_1.4.3.orig.tar.bz2
dpkg-source: info: local changes detected, the modified files are:
 joystick-1.4.3/inputattach.patch
 joystick-1.4.3/utils/inputattach.c
 joystick-1.4.3/utils/serio-ids.h
dpkg-source: info: you can integrate the local changes with dpkg-source --commit
dpkg-source: error: aborting due to unexpected upstream changes, see /tmp/joystick_1.4.3-1.diff.xG1_Np
dpkg-buildpackage: error: dpkg-source -b joystick-1.4.3 gave error exit status 2
```

I'm sorry if this probleme has already been adressed but I didn't have the courage to read all 55 pages of this thread and I don't know if there's any way to make a search limited to one thread.
Edit: Ok, I found how to search the thread. I couldn't do it before I was logged in and I only logged in when I decided to post a message. I didn't find any answer to my question anyway.

I'm on Debian Wheezy by the way, not Ubuntu.

---

### Post by mrbigmouth502 on 2015-04-21
I recently acquired a Thinkpad X201 Tablet, and though I have been able to get the Wacom stylus working under Windows 7, I cannot for the life of me figure out how to get it working under the Xubuntu 15.04 beta. I've looked all over the internet, I've tried compiling kernels with support, and I've gotten absolutely nowhere. 

  I have found out however that this touchscreen is serial based, and that if I type "sudo inputattach --dump /dev/ttyS0" in the terminal and hover my stylus above the screen, I get output in the terminal window, I'm presuming raw serial data, until I hit ctrl-C.  If anyone here knew how I could get things working so that my stylus is actually usable for something, I would much appreciate it. :)    

Btw, if my username is somewhat familiar, I believe I had an account on this forum once before, but I lost my old login a long time ago so I just created a new Ubuntu One account. Hopefully the mods don't mind.

---

### Post by mrbigmouth502 on 2015-04-22
Bump.

---

### Post by pdc on 2015-04-22
not sure if you spotted the title of this huge, long-running thread that you have elected to post on; to me, it says Wacom tablet but you seem to have a Lenovo Thinkpad tablet computer?

You might find you get more help if you started a new thread; all for yourself; with the title mentioning your device ............. wacom serial would likely get little support .............as wacom these days are plug and play .......................

PS try googling on > ubuntu solved thinkpad x201 tablet and see if you have any joy there

......... you get things like this [http://etoby.de/technology/ubuntu-13-04-on-lenovo-x201-tablet/](http://etoby.de/technology/ubuntu-13-04-on-lenovo-x201-tablet/)

---

### Post by Steve_McNeil on 2015-06-01
I have compiled and I am using the wacom_serial5 driver.  Thank you for your great work on these drivers.  I have modified the driver such that the thumbwheel on my 4D puck mouse works as a proportional relative scroll wheel.  I am an electronics engineer, not a software developer.  If anyone is interested, I would be glad to post the modified code here or contribute it back to the active developers.  I am also not sure the way I did this modification is the right way to do it.  Thank you for your consideration and all the work to get these drivers going.   Ubuntu Studio 14.04 LTS    XFCE 4.12 Wacom Intous GD-0912-R tablet with stylus and 4d puck mouse.

---

### Post by tokenrove on 2015-06-03
> **Steve_McNeil said:**
> I have modified the driver such that the thumbwheel on my 4D puck mouse works as a proportional relative scroll wheel.  I am an electronics engineer, not a software developer.  If anyone is interested, I would be glad to post the modified code here or contribute it back to the active developers.  I am also not sure the way I did this modification is the right way to do it.

That's great!  Probably the easiest way to contribute changes back to the wacom_serial5 driver is to open a pull request on roaldfre's repo: [https://github.com/RoaldFre/wacom_serial5](https://github.com/RoaldFre/wacom_serial5)

Github has some help documents on their site that guide you through the process, but if you find the process a bit daunting, I could take a patch from you and open a suitable pull request.  I know the wacom_serial4 driver made it into the kernel but I'm not sure if there has been an effort to get wacom_serial5 in, so I'm not sure how active the maintainership on it is.

(On that note, if anyone here has a PenPartner and could verify whether the current driver ships with the kernel works for you, please let me know; I got one bug report about it, and I suspect I know what causes it, but I need to interact with someone who can try patches and report what is happening.)

---

### Post by Steve_McNeil on 2015-07-29
I have created a github account and created a pull request with my modified version of the code.

I have been using the 4D mouse as my daily driver for over a month now.

Thank you again for your work, this tablet is serving me well.

---

### Post by helgacecil on 2016-03-11
I'm using the wacom_serial5 driver since nearly 3 years for a wacom intuos2 on different hardware with also different distributions and it always had worked.

[LIST]
[*]                           [IMG]http://1.1.1.4/bmi/ubuntuforums.org/images/smilies/icon_biggrin.gif[/IMG] 
[/LIST]
Its really great and I want to say big Thank you to the people who have been involved.

Since some time the wacom_serial4 four- driver is integrated into the kernel and I think this is a long overdue progress.

Unfortunately the serial5 -driver doesn't work since this happened anymore just like this.
Everytime  I use the inputattach- command  (sudo inputattach --wacom_v /dev/ttyS0) [FONT=arial][SIZE=2]the wacom_serial4  modul kicks with in and the tablet isn't recognized(unknown wacom-model is shown in dmesg)

So if anyone else is running into this problem with a newer kernel,the solution is to blacklist the wacom_serial4 module.[/SIZE][/FONT]
[FONT=arial][SIZE=2]
[/SIZE][/FONT]

---

### Post by Ti-nérisson on 2016-12-22
It works ! I had abandonned after [the last time]("https://ubuntuforums.org/showthread.php?t=1780154&page=55&p=13234078#post13234078") but today I thought Ï'd give it another try. What's different this time is I'm using debian Jessie instead of Wheezy and I only followed instruction from the first page of this thread and not from [http://www.cipht.net/2011/07/02/wacom_serial-initial-release.html](http://www.cipht.net/2011/07/02/wacom_serial-initial-release.html) . The first page of this thread doesn't use the command that didn't work for me the last time :```
dpkg-buildpackage
``` Insead it uses :```
make

sudo PREFIX=/usr make install
```
Don't know if that made any difference.

I was surprised that the tablet didn't need any additional configuration. I used to have to configure it in the xorg.conf file when it still existed.

Edit : By the way, I tried using the latest version of linuxconsoletools but it didn't work so I tried with linuxconsoletools-1.4.2 and it worked. Didn't try the versions in-between.

---

### Post by Brent_Santin on 2016-12-23
> **Ti-nérisson said:**
> It works ! I had abandonned after [the last time]("https://ubuntuforums.org/showthread.php?t=1780154&page=55&p=13234078#post13234078") but today I thought Ï'd give it another try. What's different this time is I'm using debian Jessie instead of Wheezy and I only followed instruction from the first page of this thread and not from [http://www.cipht.net/2011/07/02/wacom_serial-initial-release.html](http://www.cipht.net/2011/07/02/wacom_serial-initial-release.html) . The first page of this thread doesn't use the command that didn't work for me the last time :```
dpkg-buildpackage
``` Insead it uses :```
make

sudo PREFIX=/usr make install
```
Don't know if that made any difference.

I was surprised that the tablet didn't need any additional configuration. I used to have to configure it in the xorg.conf file when it still existed.

Edit : By the way, I tried using the latest version of linuxconsoletools but it didn't work so I tried with linuxconsoletools-1.4.2 and it worked. Didn't try the versions in-between.

[FONT=arial][SIZE=2]Congratulations.

I've been trying for years.  Now that Ubuntu 16.X.X. is out and the driver for serial tablets is supposed to be included in the kernal, I thought I'd give it a try....but honestly....that first page of this thread is a daunting mess for anyone who is not an advanced Linux user to try and understand.  I am not new to computers. I grew up using the command line in many operating systems since the 1970s, but wow....I wish someone could write things out a little more clearly.  The information on the first page is old and the author assumes the reader knows what all the terms mean (for instance....what is  wacom_serial.ko?  Where do I get it?  Do I still need it now that the kernal is included?).[/SIZE][/FONT]

---

### Post by xd0912r on 2017-02-15
I had the same problem to keep using a serial Intos2. Why has it not been integrated into the kernel yet ? Where to ask for its integration ?

---

### Post by tokenrove on 2017-02-15
Hans de Goede was instrumental in getting the protocol IV driver integrated in the kernel, so perhaps you could contact him and persuade him to help get the protocol V driver in.

Also, it's worth noting there's a bug in the driver that ships with the kernel that prevents it from working with PenPartner devices, but I haven't tracked it down yet, not having one myself.  Hopefully I'll have the time to work on this again soon and perhaps if someone was interested in doing a lot of testing, I could try to get the protocol V driver into the kernel as well.

---

### Post by helgacecil on 2017-10-17
@tokenrove

Sorry, I saw this the first time today.

It's a long time ago, but if you still have the time and still are interessted to get the protocol V driver into the kernel I would really like to help with testing. 
I'm no linux-expert , but wouldn't give up, as long you have the patience.

My wacom is a intuos2 .

---

### Post by tokenrove on 2017-10-18
Hmm, this forum is a little janky and it's not clear to me if I've managed to respond to some private messages, so I'll also say here: I'm happy to help get the protocol V driver into the kernel; please email me at [email]julian@cipht.net[/email] instead of contacting me through this forum, though.  Thanks!

---

