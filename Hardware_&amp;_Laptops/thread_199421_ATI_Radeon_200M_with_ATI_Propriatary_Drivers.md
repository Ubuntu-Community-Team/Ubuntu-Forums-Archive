---
title: "ATI Radeon 200M with ATI Propriatary Drivers"
date: 2006-06-18
forum: Hardware &amp; Laptops
---

### Post by rekahsoft on 2006-06-18
Ok....i have been all over the net and the forums and have yet to get my ATI Radeon 200M working on my Compaq R4000 series laptop. I have tried everything and can not get it working. To those of you who where luck enough to get it working could you please show how in a clean fashion. I have heard that the newest ATI Propriatary driver (8.25.18-1) does not work with my card. Is this true? I also have heard that people have got it running. I have changed to every possable setting in my BIOS and nothing has worked yet. Currently i have it set to Sideport + UMA (128 shared). Thanks for the help.

---

### Post by siriusnova on 2006-06-18
Which version of Ubuntu are you using? Dapper 64 bit or Dapper 32 bit?

ATI's proprietary driver "fglrx" which is also in the repositories in Synaptic Package Manager should have them listed.. try installing them that way.

---

### Post by rekahsoft on 2006-06-19
I am using 32 bit dapper. I have downloaded fglrx from the repositories and they still do not work. When i type fglrxinfo in my console it says i am using the Mesa driver. What is happening??? I have tried the wiki (both wasys) and they both have not worked.

---

### Post by mochaspro on 2006-06-19
I hope this is good news for you... i have a laptop HP dv8000 with amd64 Turion and ATI radeon xpress 200M... i've been almost 1 month with this issue... now i can tell you 100% sure that 8.25 doesn't work with our card... and if you arleady install them i dont know how to help you... so i did this:

Got a fresh install of dapper 32 bits and downloaded the Ati bin version 8.24.8 and then built all the .deb

If you want just follow this guide [https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25](https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25)

(just the "using ati drivers")

and i got it :D 

Try it and post again

---

### Post by rekahsoft on 2006-06-20
I have read online that people have the 8.25.18 drivers working on the Radeon 200M. And i was hoping to get them working? Is there no other way? :'( Dumb ATI...make drivers that work...I am getting and error (shown in screenshot) when executing this command:
```
sudo module-assistant build,install fglrx-kernel
```

Here is the the thread that says that the newest ATI drivers work on Compaq R4000's: [http://ubuntuforums.org/showthread.php?t=185652&highlight=Compaq+R4000](http://ubuntuforums.org/showthread.php?t=185652&highlight=Compaq+R4000)

---

### Post by xolot1 on 2006-06-22
run
```
sudo module-assistant prepare
```
and then
```
sudo module-assistant build,install fglrx-kernel
```

worked for me (at least installing, dont have it working yet though)

---

### Post by xolot1 on 2006-06-22
i spend last evening and some time trying the various methods of getting the 200m working. havent got it yet, but ive tried to document everything ive done.

its rather long, but here goes. suggestions welcome.




i used 
[http://ensode.net/ati_radeon_xpress_200m_linux.html](http://ensode.net/ati_radeon_xpress_200m_linux.html)       SidePort + UMA

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300)

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

**first try**
```
sudo apt-get update 
willi@willi-laptop:~$ sudo apt-get install linux-restricted-modules-$(uname -r)
Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-2.6.15-25-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
wilsudo module-assistant build,install fglrx-kernelli@willi-laptop:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
willi@willi-laptop:~$ sudo aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-2
willi@willi-laptop:~$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-4
willi@willi-laptop:~$

```

my /etc/X11/xorg.conf (useful parts):
```

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection



Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver      "ati"
        BusID       "PCI:1:5:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1440x900"
        EndSubSection
....
Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

```

fglrxinfo:
```
willi@willi-laptop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

**second try**
```
https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.25.18-x86.run
from
https://support.ati.com/ics/support/KBAnswer.asp?questionID=3380

willi@willi-laptop:~$ sudo apt-get install fakeroot gcc-3.4 module-assistant build-essential debhelper
Password:
Reading package lists... Done
Building dependency tree... Done
fakeroot is already the newest version.
module-assistant is already the newest version.
build-essential is already the newest version.
debhelper is already the newest version.
The following extra packages will be installed:
  cpp-3.4
Suggested packages:
  gcc-3.4-doc libc6-dev-amd64 lib64gcc1
The following NEW packages will be installed:
  cpp-3.4 gcc-3.4
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 2181kB of archives.
After unpacking 8610kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com dapper/main cpp-3.4 3.4.6-1ubuntu2 [1687kB]
Get:2 http://archive.ubuntu.com dapper/main gcc-3.4 3.4.6-1ubuntu2 [494kB]
Fetched 2181kB in 3s (561kB/s)
Selecting previously deselected package cpp-3.4.
(Reading database ... 108580 files and directories currently installed.)
Unpacking cpp-3.4 (from .../cpp-3.4_3.4.6-1ubuntu2_i386.deb) ...
Selecting previously deselected package gcc-3.4.
Unpacking gcc-3.4 (from .../gcc-3.4_3.4.6-1ubuntu2_i386.deb) ...
Setting up cpp-3.4 (3.4.6-1ubuntu2) ...
Setting up gcc-3.4 (3.4.6-1ubuntu2) ...
willi@willi-laptop:~$


willi@willi-laptop:~/Desktop/video$ chmod +x ati-driver-installer-8.25.18-x86.run
willi@willi-laptop:~/Desktop/video$ fakeroot ./ati-driver-installer-8.25.18-x86.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.25.18.......................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: Xorg 7.0.0

"Generate distribution specific packages" and "Ubuntu" and "Ubuntu 6.06"

Removing temporary directory: fglrx-install
willi@willi-laptop:~/Desktop/video$ sudo dpkg -i *.deb
dpkg - warning: downgrading fglrx-control from 8.25.18+2.6.15.11-2 to 8.25.18-1.(Reading database ... 108643 files and directories currently installed.)
Preparing to replace fglrx-control 8.25.18+2.6.15.11-2 (using fglrx-control_8.25.18-1_i386.deb) ...
Unpacking replacement fglrx-control ...
dpkg - warning: downgrading fglrx-kernel-source from 8.25.18+2.6.15.11-2 to 8.25.18-1.
Preparing to replace fglrx-kernel-source 8.25.18+2.6.15.11-2 (using fglrx-kernel-source_8.25.18-1_i386.deb) ...
Unpacking replacement fglrx-kernel-source ...
Selecting previously deselected package fglrx-sources.
Unpacking fglrx-sources (from fglrx-sources_8.25.18-1_i386.deb) ...
Preparing to replace xorg-driver-fglrx 8.25.18-1 (using xorg-driver-fglrx_8.25.18-1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx ...
Selecting previously deselected package xorg-driver-fglrx-dev.
Unpacking xorg-driver-fglrx-dev (from xorg-driver-fglrx-dev_8.25.18-1_i386.deb) ...
Setting up fglrx-kernel-source (8.25.18-1) ...
Setting up fglrx-sources (8.25.18-1) ...
Setting up xorg-driver-fglrx (8.25.18-1) ...

Setting up xorg-driver-fglrx-dev (8.25.18-1) ...
Setting up fglrx-control (8.25.18-1) ...
willi@willi-laptop:~/Desktop/video$ sudo module-assistant build,install fglrx-kernel

error screen

willi@willi-laptop:~/Desktop/video$ sudo module-assistant prepare
Getting source for kernel version: 2.6.15-25-386
apt-get install linux-headers-2.6.15-25-386
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Done!
willi@willi-laptop:~/Desktop/video$ sudo module-assistant prepare
Getting source for kernel version: 2.6.15-25-386
apt-get install linux-headers-2.6.15-25-386
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.15-25
The following NEW packages will be installed:
  linux-headers-2.6.15-25 linux-headers-2.6.15-25-386
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 7751kB of archives.
After unpacking 79.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com dapper-security/main linux-headers-2.6.15-25 2.6.15-25.43 [6899kB]
Get:2 http://security.ubuntu.com dapper-security/main linux-headers-2.6.15-25-386 2.6.15-25.43 [852kB]
Fetched 7751kB in 13s (587kB/s)
Selecting previously deselected package linux-headers-2.6.15-25.
(Reading database ... 108658 files and directories currently installed.)
Unpacking linux-headers-2.6.15-25 (from .../linux-headers-2.6.15-25_2.6.15-25.43_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-25-386.
Unpacking linux-headers-2.6.15-25-386 (from .../linux-headers-2.6.15-25-386_2.6.15-25.43_i386.deb) ...
Setting up linux-headers-2.6.15-25 (2.6.15-25.43) ...

Setting up linux-headers-2.6.15-25-386 (2.6.15-25.43) ...

Done!
willi@willi-laptop:~/Desktop/video$ sudo module-assistant build,install fglrx-kernel
Extracting the package tarball, /usr/src/fglrx.tar.bz2, please wait...
Done with /usr/src/fglrx-kernel-2.6.15-25-386_8.25.18-1+2.6.15-25.43_i386.deb .
Selecting previously deselected package fglrx-kernel-2.6.15-25-386.
(Reading database ... 123901 files and directories currently installed.)
Unpacking fglrx-kernel-2.6.15-25-386 (from .../fglrx-kernel-2.6.15-25-386_8.25.18-1+2.6.15-25.43_i386.deb) ...
Setting up fglrx-kernel-2.6.15-25-386 (8.25.18-1+2.6.15-25.43) ...
```

....and no luck

then i realized i should have turned on sideport+uma, so i did that

i then reinstalled the ati drivers, but again got this message:
```
willi@willi-laptop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

then i tried to reinstall via the non-ati driver method, again did not work



suggestions?

---

### Post by rekahsoft on 2006-06-22
Hey xolot1...lets troubleshoot this so we can get it working...i have tried many methods and will document all methods that i try from here on in...It is really anoying not having 3 acceleration (i want xgl)

---

### Post by remusus on 2006-06-22
I have used the fglrx drivers in the repos with a Toshiba M55 with a radeon 200m with no problem, except for some reason it *always* fails the first attempt at hibernating and always works thereafter.  Hmm...

---

### Post by xolot1 on 2006-06-22
do i have the 'mesa issue'?

maybe i do, maybe not (im still kinda newbie-ish). anyone know?
either way, im gonna try the method described here:

[http://ubuntuforums.org/showthread.php?t=143283](http://ubuntuforums.org/showthread.php?t=143283)

ill post my results

btw, ive got an hp dv8210
1.8ghz turion 64 (but 32bit ubuntu)
512mb ram
ati xpress 200m  }
broadcom 4318   }what a pair](*,)

---

### Post by rekahsoft on 2006-06-22
hey xolot1, i have tried "the mesa issue" and have found that it is a problem specific to hp/compaq laptops...well that is what it is looking like...i have found from some articles i was reading...i will keep trying and post my results here ;) 
P.S: I have a compaq R4000 series laptop with the following specs:
AMD Athlon 3400+
512mb ram
Radeon xpress 200M
broadcom 4318

P.S.S: So basicly the same as yours xolot1 ;)

---

### Post by black math on 2006-06-22
I have the v2000z which has the 200M also. I tried the wiki instructions but I too am getting the Mesa driver when doing fglrxinfo.

---

### Post by rekahsoft on 2006-06-22
Ok back math...join up and lets solve this together...i have been trying to get this working for ever it seems... I will be working on it all night.

---

### Post by rekahsoft on 2006-06-22
Can anyone confirm they have the Radeon 200M working on a hp/compaq laptop? And can someone also confirm if the newest driver (8.25.18) is broken for the Radeon 200M. Ok...i tried it this way without success (note i left out all the garble to make it a easier read):
```
mkdir fglrx
cd fglrx
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.25.18-x86.run # gets the latest driver from the ATI site
chmod +x ati-driver-installer-8.25.18-x86.run
sudo ./ati-driver-installer-8.25.18-x86.run
# Then a window opens i select package generation then i choose the ubuntu/dapper packages
# after generating the packages i close the window (Note: the window is too big for the screen so to move it i press alt+left mouse button in the middle of the window and drag
sudo dpkg -i *.deb # it installs the packages
# it says there are updates (i didn't update), i just restarted

``` From fglrxinfo i get the mesa drivers...i update and still get the mesa drivers...Well...i will try another way and report back ;)...Hope

---

### Post by edJquarK on 2006-06-22
[QUOTE=rekahsoft]Can anyone confirm they have the Radeon 200M working on a hp/compaq laptop? And can someone also confirm if the newest driver (8.25.18) is broken for the Radeon 200M. [/QUOTE]

Good news for all of you having problems with ATI radeon xpress 200M. I have an HP dv8000 and have 3d acceleration right now. And yes, the new 8.25.18 driver gives problems with our card, so we're gonna use the 8.24.8, it works with xorg7 as well, so don't worry.

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 2.0.5755 (8.24.8)

$ glxinfo | grep direct
direct rendering: Yes
```
[SIZE="3"]
HowTo[/SIZE] (by **tommohawk** and **Galban** and the [Ubuntu Dapper Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_new_driver"). [Original thread here]("http://ubuntuforums.org/showthread.php?t=197471"))

1. Clean Dapper Install, or clean environment at least, clean everything containing fglrx.
2. Upgrade and update everything, and install the following
```
sudo apt-get update
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
```
3. Download the 8.24.8 drivers from the ATI website.
4. Build the ubuntu packages from these drivers.
```
chmod +x ati-driver-installer-8.24.8-x86.run
./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/dapper
```
and install deb's
```
sudo dpkg -i xorg-driver-fglrx_8.24.8-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.24.8-1_i386.deb
sudo dpkg -i fglrx-control_8.24.8-1_i386.deb
```
5. Recompile the Kernel with new kernel module.Important and easy, just do:
```
sudo module-assistant prepare,update
sudo module-assistant build,install fglrx
sudo depmod -a
```
6. Extract the libGL.so.1.2 driver from the ATI package you downloaded in step 3.
____6.1.Extract it : ```
sh ati-driver-installer-8.24.8-x86.run --extract /yourHome/someWhere/
```
____6.2.Search the file libGL.so.1.2 placed in /arch/x86/usr/X11R6/lib inside the folder where you extracted the driver in step 6.1 and copy it to /usr/lib replacing the one it already exists.
7.Configure your xorg.conf file like this
add this [COLOR="Red"](in red)[/COLOR] to your graphic card section and SAVE it:

Section "Device"
Identifier "ATI Technologies, Inc. Radeon xxxxxxx"
Driver "[COLOR="Red"]fglrx[/COLOR]"
BusID "PCI:1:0:0"
[COLOR="Red"]Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "UseInternalAGPGART" "no"[/COLOR]
EndSection

8. Reboot and all should work.

Note: in the ubuntu wiki says the following:
Before start installation:
Edit DISABLED_MODULES to include fglrx
File: /etc/default/linux-restricted-modules-common

```
DISABLED_MODULES="fglrx"
```

Note2: Remove this line once you have completed driver installation!

---

### Post by rekahsoft on 2006-06-22
So it is impossable to use the new ATI drivers? I have seen that people have it working...I will check up on it...i have heard both...i really want to use the new drivers...

---

### Post by edJquarK on 2006-06-22
[QUOTE=rekahsoft]So it is impossable to use the new ATI drivers? I have seen that people have it working...I will check up on it...i have heard both...i really want to use the new drivers...[/QUOTE]

Working correctly with the Radeon Xpress 200M?? I was able to install them, and in console i got the correct info, directrendering and all that. But in practice everything was doubled and windows were transparent when they shouldn't... a real mess.

With the "old" drivers it works ok, receiving 1200 fps in glxgears. You can keep trying anyway.

---

### Post by rekahsoft on 2006-06-22
hmmm...i will just install the older drivers...do i have to change my BIOS to Sideport+UMA with the old drivers or can i just use Sideport?

---

### Post by edJquarK on 2006-06-22
I did have change it to Sideport+UMA, otherwise with 3D accel it wouldn't boot, at least my laptop.

I have just seen the thread where people got new drivers working with our card. I will stick to 8.24.8, they're working perfectly and getting higher fps. Maybe the next version of the drivers gives less problems with 200M, but at the moment 8.25.18 are not a success.

---

### Post by rekahsoft on 2006-06-22
It is still not working with the 8.24.8 drivers and your how-to edJquarK :'( this is definitly a wtf moment...check the screenshot...it is still the mesa drivers usualy if ATI control opens and fglrx is not working it will say something about the Xorg FireGL extension not installed...and this is the output i am getting in glxgears:
```
collin@RekahSoft:~$ glxgears
X connection to :0.0 broken (explicit kill or server shutdown).
```Not to mention the gears barely move :'(

Edit: btw...you missed this step (from Galbans initial post at the original thread):
```
7.- Add this lines to your /etc/modules and SAVE it:
agpgart
fglrx
dri
``` Btw...thanks for the help so far :) it really means a lot ;) :)

Edit 2: I just did/got the following:
```
collin@RekahSoft:/usr/lib$ dmesg | grep fglrx
[4294716.253000] [fglrx] Maximum main memory to use for locked dma buffers: 314 MBytes.
[4294716.253000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294716.296000] [fglrx:firegl_pci_getinfo] *ERROR* Cannot find Asic ID: 0x0001
[4294716.296000] [fglrx:firegl_init_asic] *ERROR* Cannot get PCI info.
[4294717.988000] [fglrx:firegl_unlock] *ERROR* Process 4352 using kernel context 0

```

Edit 3: I have always been getting some error everytime after it loads the kernel...this is it right here:```
[4294670.919000] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
[4294670.919000] PCI: Cannot allocate resource region 8 of bridge 0000:00:04.0
``` I am also including my entire dmesg so we can figure out wtf is going on:```
collin@RekahSoft:~$ dmesg
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[4294667.296000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 0000000017ef0000 (usable)
[4294667.296000]  BIOS-e820: 0000000017ef0000 - 0000000017eff000 (ACPI data)
[4294667.296000]  BIOS-e820: 0000000017eff000 - 0000000017f00000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 0000000017f00000 - 0000000020000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 382MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000f7e20
[4294667.296000] On node 0 totalpages: 98032
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 93936 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI present.
[4294667.296000] ATI board detected. Disabling timer routing over 8254.
[4294667.296000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7df0
[4294667.296000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x17ef94f0
[4294667.296000] ACPI: FADT (v001 HP     Piranha  0x06040000 ATI  0x000f4240) @ 0x17efee06
[4294667.296000] ACPI: MCFG (v001 ATI    Piranha  0x06040000 LOHR 0x0000005f) @ 0x17efee7a
[4294667.296000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x17efeeb6
[4294667.296000] ACPI: MADT (v001 PTLTD          APIC   0x06040000  LTP 0x00000000) @ 0x17efefa6
[4294667.296000] ACPI: DSDT (v001     HP     3085 0x06040000 MSFT 0x0100000e) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x8008
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:15 APIC version 16
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[4294667.296000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[4294667.296000] ACPI: BIOS IRQ0 pin2 override ignored.
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda2 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 2189.067 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294669.400000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)[4294669.400000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294669.407000] Memory: 377908k/392128k available (1976k kernel code, 13620k reserved, 606k data, 288k init, 0k highmem)
[4294669.407000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294669.467000] Calibrating delay using timer specific routine.. 4382.12 BogoMIPS (lpj=2191060)
[4294669.467000] Security Framework v1.0.0 initialized
[4294669.467000] SELinux:  Disabled at boot.
[4294669.467000] Mount-cache hash table entries: 512
[4294669.467000] CPU: After generic identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[4294669.467000] CPU: After vendor identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[4294669.467000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294669.467000] CPU: L2 Cache: 512K (64 bytes/line)
[4294669.467000] CPU: After all inits, caps: 078bfbff e1d3fbff 00000000 00000010 00000000 00000000 00000000
[4294669.467000] mtrr: v2.0 (20020519)
[4294669.467000] CPU: AMD Athlon(tm) 64 Processor 3500+ stepping 00
[4294669.467000] Enabling fast FPU save and restore... done.
[4294669.467000] Enabling unmasked SIMD FPU exception support... done.
[4294669.467000] Checking 'hlt' instruction... OK.
[4294669.471000] checking if image is initramfs... it is
[4294669.944000] Freeing initrd memory: 6848k freed
[4294669.954000] ACPI: Looking for DSDT ... not found!
[4294670.586000] ENABLING IO-APIC IRQs
[4294670.586000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[4294670.698000] NET: Registered protocol family 16
[4294670.698000] EISA bus registered
[4294670.698000] ACPI: bus type pci registered
[4294670.698000] PCI: PCI BIOS revision 2.10 entry at 0xfd84c, last bus=4
[4294670.698000] PCI: Using MMCONFIG
[4294670.698000] ACPI: Subsystem revision 20051216
[4294670.700000] ACPI: Interpreter enabled
[4294670.700000] ACPI: Using IOAPIC for interrupt routing
[4294670.700000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.700000] PCI: Probing PCI hardware (bus 00)
[4294670.771000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[4294670.772000] Boot video device is 0000:01:05.0
[4294670.797000] PCI: Transparent bridge - 0000:00:14.4
[4294670.797000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.800000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[4294670.800000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[4294670.800000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[4294670.800000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[4294670.801000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[4294670.801000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[4294670.801000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[4294670.801000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[4294670.802000] ACPI: Embedded Controller [EC0] (gpe 26) interrupt mode.
[4294670.846000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[4294670.871000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[4294670.871000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294670.872000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.872000] pnp: PnP ACPI init
[4294670.919000] pnp: PnP ACPI: found 9 devices
[4294670.919000] PnPBIOS: Disabled by ACPI PNP
[4294670.919000] PCI: Using ACPI for IRQ routing
[4294670.919000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.919000] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
[4294670.919000] PCI: Cannot allocate resource region 8 of bridge 0000:00:04.0
[4294672.389000] pnp: 00:07: ioport range 0x1080-0x1080 has been reserved
[4294672.389000] pnp: 00:07: ioport range 0x220-0x22f has been reserved
[4294672.389000] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
[4294672.389000] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[4294672.389000] PCI: Bridge: 0000:00:01.0
[4294672.389000]   IO window: 9000-9fff
[4294672.389000]   MEM window: b0100000-b01fffff
[4294672.389000]   PREFETCH window: c0000000-cfffffff
[4294672.389000] PCI: Bridge: 0000:00:04.0
[4294672.389000]   IO window: disabled.
[4294672.389000]   MEM window: disabled.
[4294672.389000]   PREFETCH window: disabled.
[4294672.389000] PCI: Bus 4, cardbus bridge: 0000:03:04.0
[4294672.389000]   IO window: 0000a400-0000a4ff
[4294672.389000]   IO window: 0000a800-0000a8ff
[4294672.389000]   PREFETCH window: 30000000-31ffffff
[4294672.389000]   MEM window: 32000000-33ffffff
[4294672.389000] PCI: Bridge: 0000:00:14.4
[4294672.389000]   IO window: a000-afff
[4294672.389000]   MEM window: b0200000-b02fffff
[4294672.389000]   PREFETCH window: 30000000-31ffffff
[4294672.389000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[4294672.389000] ACPI: PCI Interrupt 0000:03:04.0[A] -> GSI 20 (level, low) -> IRQ 185
[4294672.389000] audit: initializing netlink socket (disabled)
[4294672.389000] audit(1151027267.388:1): initialized
[4294672.389000] VFS: Disk quotas dquot_6.5.1
[4294672.389000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294672.389000] Initializing Cryptographic API
[4294672.389000] io scheduler noop registered
[4294672.389000] io scheduler anticipatory registered
[4294672.389000] io scheduler deadline registered
[4294672.389000] io scheduler cfq registered
[4294672.389000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[4294672.389000] pcie_portdrv_probe->Dev[5a36:1002] has invalid IRQ. Check vendor BIOS
[4294672.389000] assign_interrupt_mode Found MSI capability
[4294672.390000] Allocate Port Service[pcie00]
[4294672.390000] Allocate Port Service[pcie01]
[4294672.390000] isapnp: Scanning for PnP cards...
[4294672.747000] isapnp: No Plug & Play device found
[4294672.757000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[4294672.764000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294672.764000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.764000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294672.765000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 209
[4294672.765000] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[4294672.766000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294672.766000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294672.766000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294672.766000] mice: PS/2 mouse device common for all mice
[4294672.766000] EISA: Probing bus 0 at eisa.0
[4294672.766000] Cannot allocate resource for EISA slot 1
[4294672.766000] Cannot allocate resource for EISA slot 8
[4294672.766000] EISA: Detected 0 cards.
[4294672.766000] NET: Registered protocol family 2
[4294672.772000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294672.777000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)[4294672.777000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[4294672.777000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294672.777000] TCP: Hash tables configured (established 16384 bind 16384)
[4294672.777000] TCP reno registered
[4294672.777000] TCP bic registered
[4294672.777000] NET: Registered protocol family 1
[4294672.777000] NET: Registered protocol family 8
[4294672.777000] NET: Registered protocol family 20
[4294672.777000] Using IPI Shortcut mode
[4294672.777000] ACPI wakeup devices:
[4294672.777000]  LID KBC0 MSE0  PB4  P2P ELAN
[4294672.777000] ACPI: (supports S0 S3 S4 S5)
[4294672.777000] Freeing unused kernel memory: 288k freed
[4294672.813000] vga16fb: initializing
[4294672.813000] vga16fb: mapped to 0xc00a0000
[4294672.896000] Console: switching to colour frame buffer device 80x25
[4294672.896000] fb0: VGA16 VGA frame buffer device
[4294673.984000] Capability LSM initialized
[4294674.014000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294674.018000] ACPI: Thermal Zone [THRM] (56 C)
[4294674.351000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[4294674.351000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 217
[4294674.351000] ATIIXP: chipset revision 0
[4294674.351000] ATIIXP: not 100% native mode: will probe irqs later
[4294674.351000]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[4294674.351000]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[4294674.351000] Probing IDE interface ide0...
[4294674.615000] hda: ST9100822A, ATA DISK drive
[4294675.228000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294675.308000] Probing IDE interface ide1...
[4294675.981000] hdc: TSSTcorpCD/DVDW TS-L532R, ATAPI CD/DVD-ROM drive
[4294676.605000] ide1 at 0x170-0x177,0x376 on irq 15
[4294676.620000] hda: max request size: 1024KiB
[4294676.620000] hda: 195371568 sectors (100030 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[4294676.625000] hda: cache flushes supported
[4294676.625000]  hda: hda1 hda2
[4294676.738000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, DMA
[4294676.739000] Uniform CD-ROM driver Revision: 3.20
[4294677.023000] ieee1394: Initialized config rom entry `ip1394'
[4294677.024000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294677.024000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 20 (level, low) -> IRQ 185
[4294677.087000] usbcore: registered new driver usbfs
[4294677.087000] usbcore: registered new driver hub
[4294677.088000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294677.088000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 225
[4294677.088000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[4294677.089000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[4294677.089000] ohci_hcd 0000:00:13.0: irq 225, io mem 0xb0000000
[4294677.102000] hub 1-0:1.0: USB hub found
[4294677.102000] hub 1-0:1.0: 4 ports detected
[4294677.113000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[185]  MMIO=[b0208000-b02087ff]  Max Packet=[2048]
[4294677.113000] ohci1394: fw-host0: Get PHY Reg timeout [0x02e20701/0x00000000/100]
[4294677.213000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 225
[4294677.213000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[4294677.213000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[4294677.213000] ohci_hcd 0000:00:13.1: irq 225, io mem 0xb0001000
[4294677.218000] hub 2-0:1.0: USB hub found
[4294677.218000] hub 2-0:1.0: 4 ports detected
[4294677.320000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 225
[4294677.320000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[4294677.320000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[4294677.320000] ehci_hcd 0000:00:13.2: irq 225, io mem 0xb0002000
[4294677.320000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294677.320000] hub 3-0:1.0: USB hub found
[4294677.320000] hub 3-0:1.0: 8 ports detected
[4294677.326000] usb 1-1: new low speed USB device using ohci_hcd and address 2
[4294677.470000] Attempting manual resume
[4294677.478000] ReiserFS: hda2: found reiserfs format "3.6" with standard journal
[4294677.793000] usb 1-1: new low speed USB device using ohci_hcd and address 3
[4294677.952000] usbcore: registered new driver hiddev
[4294677.996000] input: Microsoft Microsoft USB Wireless Mouse as /class/input/input1
[4294677.996000] input: USB HID v1.11 Mouse [Microsoft Microsoft USB Wireless Mouse] on usb-0000:00:13.0-1
[4294677.996000] usbcore: registered new driver usbhid
[4294677.996000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294678.213000] ohci1394: fw-host0: Get PHY Reg timeout [0x02e20701/0x00000000/100]
[4294678.569000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[573f020063934079][4294684.298000] ReiserFS: hda2: using ordered data mode
[4294684.326000] ReiserFS: hda2: journal params: device hda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294684.326000] ReiserFS: hda2: checking transaction log (hda2)
[4294684.370000] ReiserFS: hda2: Using r5 hash to sort names
[4294696.181000] ts: Compaq touchscreen protocol output
[4294697.452000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294697.477000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294697.939000] Linux agpgart interface v0.101 (c) Dave Jones
[4294697.972000] input: PC Speaker as /class/input/input2
[4294697.992000] sdhci: Secure Digital Host Controller Interface driver, 0.10
[4294697.992000] sdhci: Copyright(c) Pierre Ossman
[4294697.992000] ACPI: PCI Interrupt 0000:03:04.4[D] -> GSI 23 (level, low) -> IRQ 233
[4294698.042000] sdhci: ============== REGISTER DUMP ==============
[4294698.042000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[4294698.042000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[4294698.042000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[4294698.042000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[4294698.042000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[4294698.042000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[4294698.042000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[4294698.042000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[4294698.042000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[4294698.042000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[4294698.042000] sdhci: ===========================================
[4294698.092000] mmc0: SDHCI at 0xb020a000 irq 233 DMA
[4294698.192000] sdhci: ============== REGISTER DUMP ==============
[4294698.192000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[4294698.192000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[4294698.192000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[4294698.192000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[4294698.192000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[4294698.192000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[4294698.192000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[4294698.192000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[4294698.192000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[4294698.192000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[4294698.192000] sdhci: ===========================================
[4294698.242000] mmc1: SDHCI at 0xb0208c00 irq 233 DMA
[4294698.342000] sdhci: ============== REGISTER DUMP ==============
[4294698.342000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[4294698.342000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[4294698.342000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[4294698.342000] sdhci: Present:  0x000a0000 | Host ctl: 0x00000000
[4294698.342000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[4294698.342000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[4294698.342000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[4294698.342000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[4294698.342000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[4294698.342000] sdhci: Caps:     0x01821898 | Max curr: 0x00000000
[4294698.342000] sdhci: ===========================================
[4294698.392000] mmc2: SDHCI at 0xb0208800 irq 233 DMA
[4294698.393000] ACPI: PCI Interrupt 0000:03:04.0[A] -> GSI 20 (level, low) -> IRQ 185
[4294698.393000] Yenta: CardBus bridge found at 0000:03:04.0 [103c:3085]
[4294698.393000] Yenta: Enabling burst memory read transactions
[4294698.393000] Yenta: Using INTVAL to route CSC interrupts to PCI
[4294698.393000] Yenta: Routing CardBus interrupts to ISA
[4294698.393000] Yenta TI: socket 0000:03:04.0, mfunc 0x00aa1b22, devctl 0x64
[4294698.455000] Real Time Clock Driver v1.12
[4294698.542000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294698.576000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 209
[4294698.578000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 209
[4294698.621000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 185
[4294698.621000] Socket status: 30000820
[4294698.621000] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
[4294698.621000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[4294698.621000] cs: IO port probe 0xa000-0xafff: clean.
[4294698.622000] pcmcia: parent PCI bridge Memory window: 0xb0200000 - 0xb02fffff
[4294698.622000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x31ffffff
[4294698.624000] 8139cp: pci dev 0000:03:06.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[4294698.624000] 8139cp: Try the "8139too" driver instead.
[4294698.630000] 8139too Fast Ethernet driver 0.9.27
[4294698.678000] MC'97 0 converters and GPIO not ready (0x1)
[4294698.678000] ACPI: PCI Interrupt 0000:03:06.0[A] -> GSI 22 (level, low) -> IRQ 50
[4294698.679000] eth0: RealTek RTL8139 at 0xd8ac4400, 00:0f:b0:73:aa:3a, IRQ 50
[4294698.679000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294699.228000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x23a0b1, caps: 0xa04713/0x200000
[4294699.259000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[4294699.262000] pccard: CardBus card inserted into slot 0
[4294699.406000] cs: IO port probe 0x100-0x3af: clean.
[4294699.409000] cs: IO port probe 0x3e0-0x4ff: clean.
[4294699.409000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[4294699.410000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[4294699.411000] cs: IO port probe 0xa00-0xaff: clean.
[4294699.864000] PCI: Enabling device 0000:04:00.0 (0000 -> 0001)
[4294699.864000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 20 (level, low) -> IRQ 185
[4294699.864000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[4294699.872000] Audigy2 value: Special config.
[4294700.161000] eth0: link down
[4294701.075000] lp: driver loaded but no devices found
[4294701.145000] SCSI subsystem initialized
[4294701.156000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294701.156000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)[4294701.156000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294701.308000] NET: Registered protocol family 17
[4294701.318000] Adding 2096472k swap on /dev/hda1.  Priority:-1 extents:1 across:2096472k
[4294706.056000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294706.437000] cdrom: open failed.
[4294710.188000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[4294710.274000] ndiswrapper: driver bcmwl5 (Broadcom,12/22/2004, 3.100.46.0) loaded
[4294710.274000] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 21 (level, low) -> IRQ 177
[4294710.283000] ndiswrapper: using irq 177
[4294711.456000] wlan0: vendor: ''
[4294711.456000] wlan0: ndiswrapper ethernet device 00:90:4b:f6:88:a0 using driver bcmwl5, 14E4:4318.5.conf
[4294711.456000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[4294713.302000] ACPI: AC Adapter [ACAD] (on-line)
[4294713.339000] pcc_acpi: loading...
[4294713.349000] ACPI: Power Button (FF) [PWRF]
[4294713.349000] ACPI: Lid Switch [LID]
[4294713.349000] ACPI: Power Button (CM) [PWRB]
[4294713.436000] ibm_acpi: ec object not found
[4294713.565000] ACPI: Battery Slot [BAT1] (battery present)
[4294713.583000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294713.956000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
[4294713.960000] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x2 (1500 mV)
[4294713.960000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x6 (1400 mV)
[4294713.960000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa (1300 mV)
[4294713.960000] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x10 (1150 mV)
[4294713.960000] cpu_init done, current fid 0xe, vid 0x2
[4294717.961000] [fglrx] Maximum main memory to use for locked dma buffers: 314 MBytes.
[4294717.962000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294717.994000] [fglrx:firegl_pci_getinfo] *ERROR* Cannot find Asic ID: 0x0001
[4294717.994000] [fglrx:firegl_init_asic] *ERROR* Cannot get PCI info.
[4294719.420000] [fglrx:firegl_unlock] *ERROR* Process 4347 using kernel context 0
[4294719.544000] ppdev: user-space parallel port driver
[4294720.154000] apm: BIOS not found.
[4294724.989000] Bluetooth: Core ver 2.8
[4294724.989000] NET: Registered protocol family 31
[4294724.989000] Bluetooth: HCI device and connection manager initialized
[4294724.989000] Bluetooth: HCI socket layer initialized
[4294725.008000] Bluetooth: L2CAP ver 2.8
[4294725.008000] Bluetooth: L2CAP socket layer initialized
[4294725.010000] Bluetooth: RFCOMM socket layer initialized
[4294725.010000] Bluetooth: RFCOMM TTY layer initialized
[4294725.010000] Bluetooth: RFCOMM ver 1.7
[4294870.167000] NET: Registered protocol family 10
[4294870.167000] lo: Disabled Privacy Extensions
[4294870.167000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[4294870.168000] IPv6 over IPv4 tunneling driver
```

Edit 4: I just noticed it is loading the 8.25.18 fglrx driver so i will clean my system and try again.
Edit 5: WTF!! i just checked to see what version of fglrx and xorg-driver-fglrx and guess what...it is 8.24.8 (check the screenshot for confirmation)...WTF is going on???

---

### Post by rekahsoft on 2006-06-23
So what is wrong here? It is not my xorg.conf...fglrx is installed correctly but just won't load...please help...:( i am ](*,)

---

### Post by rekahsoft on 2006-06-23
Anybody have the same laptop that i have (the Compaq R4000 series laptop)? Has anyone with this laptop got it working?

---

### Post by edJquarK on 2006-06-23
You need a **Clean install**, if you're getting in dmesg something related to fglrx 8.25.18 it's because rests of fglrx 8.25.18 are still round there. Your system should have nothing to do with that driver version.

I did reinstall Kubuntu and installed the driver then, because i had made so many tries that it was imposible the system remained clean.

Now gonna sleep, tomorrow i'll read your posts more carefully and see what you can do. Good luck.

---

### Post by xolot1 on 2006-06-23
is there a way to remove all traces of fglrx, or is reinstalling just the easiest?

(i just got broadcom 4138 working ](*,) )

---

### Post by rekahsoft on 2006-06-23
I don't know xolot1...i thaught i got everything but it edits quite a lot of stuff and i am going to do what edJquarK said...on a new partition...i will install ubuntu intead of Kubuntu though (which will make no difference)...It would be nice but i have screwed around with a lot of stuff and by the way it looks neither me nor you will be able to get it working without a clean install...i will code a shell script that will install the broadcom drivers for us ;) nice and easy :)

---

### Post by rekahsoft on 2006-06-24
Ok...i just formatted and re-installed ubuntu...i did **exactly** as was posted...it still says i am using the mesa drivers ](*,) I am still getting basicly the same error...btw i used the 8.24.8 driver and it is still saying something about the 8.25.18 driver and i am on a fresh insall of ubuntu...wtf is going on? here is the error/s i am getting from dmesg | grep fglrx:
```
[17179616.756000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179616.756000] [fglrx] Maximum main memory to use for locked dma buffers: 314 MBytes.
[17179616.756000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0[17179616.792000] [fglrx:firegl_pci_getinfo] *ERROR* Cannot find Asic ID: 0x0001[17179616.792000] [fglrx:firegl_init_asic] *ERROR* Cannot get PCI info.
[17179618.412000] [fglrx:firegl_unlock] *ERROR* Process 4389 using kernel context 0

```Note: the only thing i have done so far with my system is install fglrx, nothing else.

---

### Post by edJquarK on 2006-06-24
[QUOTE=rekahsoft]Ok...i just formatted and re-installed ubuntu...i did **exactly** as was posted...it still says i am using the mesa drivers ](*,) I am still getting basicly the same error...btw i used the 8.24.8 driver and it is still saying something about the 8.25.18 driver and i am on a fresh insall of ubuntu...wtf is going on? here is the error/s i am getting from dmesg | grep fglrx:
```
[17179616.756000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179616.756000] [fglrx] Maximum main memory to use for locked dma buffers: 314 MBytes.
[17179616.756000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0[17179616.792000] [fglrx:firegl_pci_getinfo] *ERROR* Cannot find Asic ID: 0x0001[17179616.792000] [fglrx:firegl_init_asic] *ERROR* Cannot get PCI info.
[17179618.412000] [fglrx:firegl_unlock] *ERROR* Process 4389 using kernel context 0

```Note: the only thing i have done so far with my system is install fglrx, nothing else.[/QUOTE]

It really is a mistery. i suppose you didn't install the xorg-driver-fglrx package from apt or something, or didn't upgrade it. Because when you follow the howto and restart, it shows an available update for fglrx, which installs 8.25.18 version. Those are the only options i see, because if in a fresh install you simply download 8.24.8 drivers, build deb packages from there, install them, and recompile the kernel with that version, wtf is 8.25.18 appearing there??

---

### Post by rekahsoft on 2006-06-24
yes...i am going to backlist fglrx and see what it does...what is happening with the PCI errors? What are they for?
Edit: Crap i think i found the problem...i did not add fglrx to the disabled modules file...i am rebooting and we will c

---

### Post by rekahsoft on 2006-06-24
Ok...still no luck```
collin@RekahSoft:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```...here is my Xorg log file (part 1):
```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux RekahSoft 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun 24 12:58:17 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,5950 card 103c,3085 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,5a3f card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 1002,5a36 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:13:0: chip 1002,4374 card 1002,4374 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 1002,4375 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 1002,4373 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 103c,3085 rev 10 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 103c,3085 rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 0000,0000 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:14:5: chip 1002,4370 card 103c,3085 rev 01 class 04,01,00 hdr 80
(II) PCI: 00:14:6: chip 1002,4378 card 103c,3085 rev 01 class 07,03,00 hdr 80
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:05:0: chip 1002,5955 card 103c,3085 rev 00 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 104c,8023 card 103c,3085 rev 00 class 0c,00,10 hdr 00
(II) PCI: 03:02:0: chip 14e4,4318 card 103c,1355 rev 02 class 02,80,00 hdr 00
(II) PCI: 03:04:0: chip 104c,8031 card a400,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 03:04:3: chip 104c,8033 card 103c,3085 rev 00 class 01,80,00 hdr 80
(II) PCI: 03:04:4: chip 104c,8034 card 103c,3085 rev 00 class 08,05,00 hdr 80
(II) PCI: 03:06:0: chip 10ec,8139 card 103c,3085 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xb0100000 - 0xb01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:4:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:20:4), (0,3,7), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xb0200000 - 0xb02fffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x31ffffff (0x2000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 4: bridge is at (3:4:0), (3,4,7), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[1] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x31ffffff (0x2000000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE) rev 0, Mem @ 0xc0000000/28, 0xb0100000/16, I/O @ 0x9000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xb020a400 - 0xb020a4ff (0x100) MX[B]
	[1] -1	0	0xb0208800 - 0xb02088ff (0x100) MX[B]
	[2] -1	0	0xb0208c00 - 0xb0208cff (0x100) MX[B]
	[3] -1	0	0xb020a000 - 0xb020a0ff (0x100) MX[B]
	[4] -1	0	0xb0206000 - 0xb0207fff (0x2000) MX[B]
	[5] -1	0	0xb0204000 - 0xb0205fff (0x2000) MX[B]
	[6] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[7] -1	0	0xb0208000 - 0xb02087ff (0x800) MX[B]
	[8] -1	0	0xb0003800 - 0xb00038ff (0x100) MX[B]
	[9] -1	0	0xb0003400 - 0xb00034ff (0x100) MX[B]
	[10] -1	0	0xb0003000 - 0xb00033ff (0x400) MX[B]
	[11] -1	0	0xb0002000 - 0xb0002fff (0x1000) MX[B]
	[12] -1	0	0xb0001000 - 0xb0001fff (0x1000) MX[B]
	[13] -1	0	0xb0000000 - 0xb0000fff (0x1000) MX[B]
	[14] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[23] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xb020a400 - 0xb020a4ff (0x100) MX[B]
	[1] -1	0	0xb0208800 - 0xb02088ff (0x100) MX[B]
	[2] -1	0	0xb0208c00 - 0xb0208cff (0x100) MX[B]
	[3] -1	0	0xb020a000 - 0xb020a0ff (0x100) MX[B]
	[4] -1	0	0xb0206000 - 0xb0207fff (0x2000) MX[B]
	[5] -1	0	0xb0204000 - 0xb0205fff (0x2000) MX[B]
	[6] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[7] -1	0	0xb0208000 - 0xb02087ff (0x800) MX[B]
	[8] -1	0	0xb0003800 - 0xb00038ff (0x100) MX[B]
	[9] -1	0	0xb0003400 - 0xb00034ff (0x100) MX[B]
	[10] -1	0	0xb0003000 - 0xb00033ff (0x400) MX[B]
	[11] -1	0	0xb0002000 - 0xb0002fff (0x1000) MX[B]
	[12] -1	0	0xb0001000 - 0xb0001fff (0x1000) MX[B]
	[13] -1	0	0xb0000000 - 0xb0000fff (0x1000) MX[B]
	[14] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[17] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[18] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[19] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[20] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[23] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb020a400 - 0xb020a4ff (0x100) MX[B]
	[5] -1	0	0xb0208800 - 0xb02088ff (0x100) MX[B]
	[6] -1	0	0xb0208c00 - 0xb0208cff (0x100) MX[B]
	[7] -1	0	0xb020a000 - 0xb020a0ff (0x100) MX[B]
	[8] -1	0	0xb0206000 - 0xb0207fff (0x2000) MX[B]
	[9] -1	0	0xb0204000 - 0xb0205fff (0x2000) MX[B]
	[10] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[11] -1	0	0xb0208000 - 0xb02087ff (0x800) MX[B]
	[12] -1	0	0xb0003800 - 0xb00038ff (0x100) MX[B]
	[13] -1	0	0xb0003400 - 0xb00034ff (0x100) MX[B]
	[14] -1	0	0xb0003000 - 0xb00033ff (0x400) MX[B]
	[15] -1	0	0xb0002000 - 0xb0002fff (0x1000) MX[B]
	[16] -1	0	0xb0001000 - 0xb0001fff (0x1000) MX[B]
	[17] -1	0	0xb0000000 - 0xb0000fff (0x1000) MX[B]
	[18] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[19] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[23] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[29] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "agpgart"
(WW) Warning, couldn't open module agpgart
(II) UnloadModule: "agpgart"
(EE) Failed to load module "agpgart" (module does not exist, 0)
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
dlopen: /usr/lib/xorg/modules/drivers/fglrx_drv.so: undefined symbol: __glXActiveScreens
(EE) Failed to load /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) UnloadModule: "fglrx"
(EE) Failed to load module "fglrx" (loader failed, 7)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.24.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) ATI Radeon/FireGL: The following chipsets are supported:
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
	RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
	RADEON 9200 (RV280 5961), RADEON 9000 (RV280 5962),
	RADEON 9200 SE (RV280 5964), MOBILITY RADEON 9200 (M9+ 5C61),
	MOBILITY RADEON 9200 (M9+ 5C63), FireGL 8800 (R200 5148),
	RADEON 8500 (R200 514C), RADEON 9100 (R200 514D),
	RADEON 8500 AIW (R200 4242), RADEON 9600 (RV350 4150),
	RADEON 9600 SE (RV350 4151), RADEON 9600 PRO (RV360 4152),
	RADEON 9600 (RV350 4E51), MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9500 (M11 4E52), MOBILITY RADEON 9550 (M12 4E56),
	RADEON 9500 (R300 4144), RADEON 9600 TX (R300 4146),
	FireGL Z1 (R300 4147), RADEON 9700 PRO (R300 4E44),
	RADEON 9500 PRO/9700 (R300 4E45), RADEON 9600 TX (R300 4E46),
	FireGL X1 (R300 4E47), RADEON 9800 SE (R350 4148),
	RADEON 9500 (R350 4149), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9600 (RV351 4155),
	RADEON 9800 PRO (R350 4E48), RADEON 9800 (R350 4E49),
	RADEON 9800 XT (R360 4E4A), FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300 (RV370 5B60),
	RADEON X600 (RV380 5B62), RADEON X550 (RV370 5B63),
	FireGL V3100 (RV370 5B64), MOBILITY RADEON X300 (M22 5460),
	MOBILITY RADEON X300 (M22 5461), MOBILITY RADEON X600 (M24 5462),
	MOBILITY FireGL V3100 (M22 5464), RADEON X600 (RV380 3E50),
	FireGL V3200 (RV380 3E54), MOBILITY RADEON X600 (M24 3150),
	MOBILITY RADEON X300 (M22 3152), MOBILITY FireGL V3200 (M24 3154),
	RADEON X800 (R420 4A48), RADEON X800 PRO (R420 4A49),
	RADEON X800 SE (R420 4A4A), RADEON X800 XT (R420 4A4B),
	RADEON X800 (R420 4A4C), FireGL X3-256 (R420 4A4D),
	MOBILITY RADEON 9800 (M18 4A4E), RADEON X800 SE (R420 4A4F),
	RADEON X800 XT Platinum Edition (R420 4A50),
	RADEON X800 VE (R420 4A54), RADEON X800 (R423 5548),
	RADEON X800 PRO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 GT (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	MOBILITY RADEON X800 (M28 5D4A), RADEON X800 XL (R430 554D),
	RADEON X800 GT (R430 554E), RADEON X800 GTO (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X800 GTO (R480 5D4F), RADEON X850 XT (R480 5D52),
	RADEON X850 (R481 4B48), RADEON X850 XT (R481 4B49),
	RADEON X850 SE (R481 4B4A), RADEON X850 PRO (R481 4B4B),
	RADEON X850 XT Platinum Edition (R481 4B4C),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), FireGL V3300 (RV410 5E49),
	RADEON X700 XT (RV410 5E4A), RADEON X700 PRO (RV410 5E4B),
	RADEON X700 SE (RV410 5E4C), RADEON X700 (RV410 5E4D),
	RADEON X700 (RV410 5E4F), MOBILITY RADEON X700 (M26 5652),
	MOBILITY RADEON X700 (M26 5653), MOBILITY RADEON X700 XL,
	RADEON 9100 IGP (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62),
	RADEON X1800 (R520 7100), MOBILITY RADEON X1800 (M58 7101),
	MOBILITY RADEON X1800 (M58 7102), RADEON X1800 XT (R520 7108),
	RADEON X1800 PRO (R520 7109), RADEON X1800 SE (R520 710A),
``` I get no output from dmesg | grep fglrx.](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by rekahsoft on 2006-06-24
Here is part two of my Xorg log:```
	RADEON X1800 (R520 710B), RADEON X1800 (R520 710C),
	MOBILITY RADEON X1300 (M52 714B), MOBILITY RADEON X1300 (M52 714C),
	RADEON X1300 XT (RV515 7140), RADEON X1300 PRO (RV515 7142),
	MOBILITY RADEON X1400 (M54 7145), RADEON X1300 LE (RV515 7146),
	MOBILITY RADEON X1300 (M52 7149), MOBILITY RADEON X1300 (M52 714A),
	RADEON X1300 SE (RV515 714E), RADEON X1300 VE (RV515 715E),
	RADEON X1900 (R580 7240), RADEON X1900 (R580 7243),
	RADEON X1900 (R580 7244), RADEON X1900 (R580 7245),
	RADEON X1900 (R580 7246), RADEON X1900 (R580 7247),
	RADEON X1900 (R580 7248), RADEON X1900 (R580 7249),
	RADEON X1900 (R580 724A), RADEON X1900 (R580 724B),
	RADEON X1900 (R580 724C), RADEON X1900 (R580 724D),
	RADEON X1900 (R580 724E), RADEON X1900 (R580 724F),
	RADEON X1600 XT (RV530 71C0), RADEON X1600 PRO (RV530 71C2),
	MOBILITY RADEON X1600 (M56 71C5), RADEON (RV530 LE 71C6),
	RADEON (RV530 VE 71CE), RADEON (RV530 SE 71DE)
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.24.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.24g1                           
(II) ATI Proprietary Linux Driver Build Date: Apr 11 2006 13:36:57
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.24.1-driver-lnx-259766
(--) Chipset RADEON XPRESS 200M (RS480 5955) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb020a400 - 0xb020a4ff (0x100) MX[B]
	[5] -1	0	0xb0208800 - 0xb02088ff (0x100) MX[B]
	[6] -1	0	0xb0208c00 - 0xb0208cff (0x100) MX[B]
	[7] -1	0	0xb020a000 - 0xb020a0ff (0x100) MX[B]
	[8] -1	0	0xb0206000 - 0xb0207fff (0x2000) MX[B]
	[9] -1	0	0xb0204000 - 0xb0205fff (0x2000) MX[B]
	[10] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[11] -1	0	0xb0208000 - 0xb02087ff (0x800) MX[B]
	[12] -1	0	0xb0003800 - 0xb00038ff (0x100) MX[B]
	[13] -1	0	0xb0003400 - 0xb00034ff (0x100) MX[B]
	[14] -1	0	0xb0003000 - 0xb00033ff (0x400) MX[B]
	[15] -1	0	0xb0002000 - 0xb0002fff (0x1000) MX[B]
	[16] -1	0	0xb0001000 - 0xb0001fff (0x1000) MX[B]
	[17] -1	0	0xb0000000 - 0xb0000fff (0x1000) MX[B]
	[18] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[19] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[23] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[29] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81d9678
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb020a400 - 0xb020a4ff (0x100) MX[B]
	[5] -1	0	0xb0208800 - 0xb02088ff (0x100) MX[B]
	[6] -1	0	0xb0208c00 - 0xb0208cff (0x100) MX[B]
	[7] -1	0	0xb020a000 - 0xb020a0ff (0x100) MX[B]
	[8] -1	0	0xb0206000 - 0xb0207fff (0x2000) MX[B]
	[9] -1	0	0xb0204000 - 0xb0205fff (0x2000) MX[B]
	[10] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[11] -1	0	0xb0208000 - 0xb02087ff (0x800) MX[B]
	[12] -1	0	0xb0003800 - 0xb00038ff (0x100) MX[B]
	[13] -1	0	0xb0003400 - 0xb00034ff (0x100) MX[B]
	[14] -1	0	0xb0003000 - 0xb00033ff (0x400) MX[B]
	[15] -1	0	0xb0002000 - 0xb0002fff (0x1000) MX[B]
	[16] -1	0	0xb0001000 - 0xb0001fff (0x1000) MX[B]
	[17] -1	0	0xb0000000 - 0xb0000fff (0x1000) MX[B]
	[18] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[19] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[26] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[32] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[33] 0	0	0xb01203b0 - 0xb01203bb (0xc) IS[B]
	[34] 0	0	0xb01203c0 - 0xb01203df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "UseInternalAGPGART" "no"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON XPRESS 200M (RS480 5955)" (Chipset = 0x5955)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x3085)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xb0100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 262144 kB
(II) fglrx(0): VESA VBE OEM: ATI MOBILITY RADEON Xpress 200G Series
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: MS48
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.24.8
	ABI class: X.Org Server Extension, version 0.2
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) fglrx(0): Connected Display1: LCD on internal LVDS
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SEC  Model: 3345  Serial#: 0
(II) fglrx(0): Year: 2004  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) fglrx(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(II) fglrx(0):  SAMSUNG
(II) fglrx(0):  LTN154X3-L01
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 301/250MHz @ 60Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 13 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   68.94  1280 1296 1344 1408  800 801 804 816
(**) fglrx(0):  Default mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   68.94  1024 1168 1216 1408  768 785 788 816
(**) fglrx(0):  Default mode "848x480": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   68.94  848 1080 1128 1408  480 641 644 816
(**) fglrx(0):  Default mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   68.94  800 1056 1104 1408  600 701 704 816
(**) fglrx(0):  Default mode "720x576": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   68.94  720 1016 1064 1408  576 689 692 816
(**) fglrx(0):  Default mode "720x480": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   68.94  720 1016 1064 1408  480 641 644 816
(**) fglrx(0):  Default mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   68.94  640 976 1024 1408  480 641 644 816
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   68.94  640 976 1024 1408  400 601 604 816
(**) fglrx(0):  Default mode "640x350": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   68.94  640 976 1024 1408  350 576 579 816
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   68.94  512 912 960 1408  384 593 596 816
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   68.94  400 856 904 1408  150 701 704 816 doublescan
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   68.94  320 816 864 1408  120 641 644 816 doublescan
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   68.94  320 816 864 1408  100 601 604 816 doublescan
(--) fglrx(0): Display dimensions: (330, 210) mm
(--) fglrx(0): DPI set to (98, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): cpuSpeedMHz: 0x0000088d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xb0100000 - 0xb010ffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xb020a400 - 0xb020a4ff (0x100) MX[B]
	[7] -1	0	0xb0208800 - 0xb02088ff (0x100) MX[B]
	[8] -1	0	0xb0208c00 - 0xb0208cff (0x100) MX[B]
	[9] -1	0	0xb020a000 - 0xb020a0ff (0x100) MX[B]
	[10] -1	0	0xb0206000 - 0xb0207fff (0x2000) MX[B]
	[11] -1	0	0xb0204000 - 0xb0205fff (0x2000) MX[B]
	[12] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[13] -1	0	0xb0208000 - 0xb02087ff (0x800) MX[B]
	[14] -1	0	0xb0003800 - 0xb00038ff (0x100) MX[B]
	[15] -1	0	0xb0003400 - 0xb00034ff (0x100) MX[B]
	[16] -1	0	0xb0003000 - 0xb00033ff (0x400) MX[B]
	[17] -1	0	0xb0002000 - 0xb0002fff (0x1000) MX[B]
	[18] -1	0	0xb0001000 - 0xb0001fff (0x1000) MX[B]
	[19] -1	0	0xb0000000 - 0xb0000fff (0x1000) MX[B]
	[20] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[21] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[25] 0	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[29] -1	0	0x00008410 - 0x0000841f (0x10) IX[B]
	[30] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[31] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[32] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[35] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[36] 0	0	0xb01203b0 - 0xb01203bb (0xc) IS[B]
	[37] 0	0	0xb01203c0 - 0xb01203df (0x20) IS[B]
(II) fglrx(0): UMM Bus area:     0xc05e9000 (size=0x07a07000)
(II) fglrx(0): UMM area:     0x185e9000 (size=0x07a07000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0x18000000 FBMappedSize: 0x07ff0000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 800)
(II) fglrx(0): Largest offscreen area available: 1280 x 7387
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.3
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad touchpad found
ProcXCloseDevice to close or not ?
```

---

### Post by rekahsoft on 2006-06-24
Anybody know wtf is going on? I am clueless now...what is going wrong..is it just my laptop? If so i am going to buy a new one with nvidea graohics instead of this stupid ATI bs. Anybody ?? ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by oskie on 2006-06-25
Method one from this install guide worked for me (glxgears are working but VERY slow).
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) 

Haven't yet measured the fps though. I have a V2000 Presario with the dreaded ATI 200M and the broadcom 4318, both of which have given me endless headaches. ](*,)

---

### Post by rekahsoft on 2006-06-25
I got the broadcom card working without a hitch...but i have yet to get the propritary ATI driver working :(

---

### Post by black math on 2006-06-25
Same here I got the 4318 working, now just messing with the video drivers. Hope to ditch windows soon but this would be a showstopper if I cant this working but im trying.

---

### Post by rekahsoft on 2006-06-25
I have already got rid of windows...i got rid of it a month or two ago. :) Hopefully i can get the fglrx drivers working...it is a big pain in the arse tho :(

---

### Post by almahtar on 2006-06-26
Ok, I've been through hell and back with these fglrx drivers, and there are a few things I've learned.

#1: let's figure out how to clean your system up and get rid of ALL fglrx related stuff, so you can try again from scratch:

```
 sudo updatedb
```
This updates your computer's list of files present on the hard drive.  It takes a long time so be patient.

Next:
```
 locate fglrx 
```

This will show you everywhere that any ATI driver stuff resides.  First try deleting just the fglrx.ko files and installing the 8.24.8 drivers (you can use "locate fglrx | grep fglrx.ko" to find just those), or delete the source too from usr/src/modules or whatever the locate fglrx gives you.

Kill it all, you can get it back later.

Next, after you've installed module-assistant and all the stuff the other guy said, install the fglrx 8.24.8 the way he mentioned.  It should work.  I have an HP ZV 6000 series, which from what I hear is identical to the compaq R4000 series.  I'll give it a shot probably tomorrow with the 8.24.8 and see what happens.  If I run into any hitches I'll give you a heads up, but what I stated above should work great.  I have the 8.25 drivers installed as well, and I'm running with
```
 Option       "nodri"
``` currently (no 3d accel), but hopefully downgrading to 8.24 will fix it.

---

### Post by xolot1 on 2006-06-28
new ati drivers out
ATI 8.26.18

supposedly they support the 200m, tho im having trouble getting it to work. i still get

willi@willi-laptop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

---

### Post by Eversmann on 2006-06-28
[QUOTE=xolot1]new ati drivers out
ATI 8.26.18

supposedly they support the 200m, tho im having trouble getting it to work. i still get

[/QUOTE]

They support it? i don't think so, at least at release note they don't say a word about that. I read on other forums (coming from ati unofficial wiki drivers) that they know there have some issues with it and are working to resolve it.

---

### Post by doog on 2006-06-28
not sure if this'll help but I had to create a couple of links into the X11R6 directory for the ATI driver to work.

Try this:
sudo ln -s /usr/lib/dri/atiogl_a_dri.so /usr/X11R6/lib/modules/dri/
sudo ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri

ofcourse, ATI's driver is STILL broken for the Express 200m and so you have to disable( in BIOS ) the Sideport memory and enable 128MB of UMA( shared ) memory for DRI/3D to work.  If you only want 2D then you can use Sideport but you'll have to edit your xorg.conf and add { Option "no_dri" "yes" } to the Driver section for the fglrx driver.

Oh, and PLEASE login to ATI's site and leave them feedback that you want them to fix the driver for the Express 200M with regard to 3D accelleration and the onboard/Sideport memory. Here's the link:
[https://support.ati.com/ics/support/KBAnswer.asp?questionID=1714](https://support.ati.com/ics/support/KBAnswer.asp?questionID=1714)

---

### Post by randys on 2006-06-28
I too have this problem and am eagerly waiting on a solution. I look forward to having a 3d desktop on my compaq/ubuntu laptop. I also have an ati radeon 200m graphics card :(

---

### Post by doog on 2006-06-29
[QUOTE=randys]I too have this problem and am eagerly waiting on a solution. I look forward to having a 3d desktop on my compaq/ubuntu laptop. I also have an ati radeon 200m graphics card :([/QUOTE]

Well I hope you've already let ATI know about your problem because unless they know how many people this is a problem for, it's not going to get moved up the priority list.  The problems almost a year old already. So please don't sit on your hands just waiting for this to get fixed. Let them know you are waiting for them to get it fixed and it just might get fixed.

---

### Post by zhoux on 2006-07-02
i've read in PC World magazine that AMD may buy out ATI, hopefully that would happen, because ATI suck.....and I hear that AMD has a pretty good reputation among the processors, so hopefully they would help some of us linux guys/gals out

---

### Post by d-E-a-D on 2006-07-03
I have just send a ticket to ATI Customer Care.
If you have 200M please send to ATI a post asking to resolve the issue.

Cumps

---

### Post by Moldy Jello on 2006-07-03
ok, does anyone know if i can get good 3d accelleration on an ati x1900xtx, i am considering dual booting my desktop with this but i will not do it if i am getting choppy video on a $600 video card

---

### Post by Moldy Jello on 2006-07-03
well i followed edjquarks post to the T, and i must say it worked, it actually worked, i used the program called KillDisk to 100% erase EVERYTHING on my drive cuz it did not seem like the Ubuntu installer did a good job at that, then installed and it all just worked, thanks a lot for all the help

xim@xim-pow:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 2.0.5755 (8.24.8)

---

### Post by doog on 2006-07-03
[QUOTE=Moldy Jello]well i followed edjquarks post to the T, and i must say it worked, it actually worked, i used the program called KillDisk to 100% erase EVERYTHING on my drive cuz it did not seem like the Ubuntu installer did a good job at that, then installed and it all just worked, thanks a lot for all the help

xim@xim-pow:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 2.0.5755 (8.24.8)[/QUOTE]

So you've got DRI/3D with Sideport-ONLY memory using this build process and the ATI 8.24.8 driver? I know some have said they got it working but then I found that they didn't even have any Sideport memory so I just want to make sure it's clear what you have working. Thanks.

---

### Post by scrizer on 2006-07-04
Hey, am new to the forums and sorry for just leeching on to this thread from google. I currently have the 8.16 drivers, run on Winxp Sp2, CeleronM 1.4Ghz on the Toshiba A100-549. Tried playing the recently released [Prey ]("http://downloads.whichgame.net/Prey/demo/SetupPreyDemo.zip")demo yesterday and this is how it [ended up looking]("http://img188.imageshack.us/my.php?image=preyopeningscene1rp.jpg"). 

I have always been an nvidia customer and this ati drivers are doing my head in. From what i was searching on ggle, the 8.24 drivers are meant for linux...or am I just confused? 

[Here's some more detail]("http://img188.imageshack.us/my.php?image=driverss8lv.jpg"). Any idea what I am supposed to do?


Already registered a ticket with the customer support, will post as soon as I get a reply.

---

### Post by scrizer on 2006-07-04
Okhay, just checked out the front page *duh* of the forums and quite obviously its for linux. Bear stupid post on top, if anyone can help me out with my driver problem it would be much appreciated....and i mean that cause my father is a shaman, granting *****, money and killing neighbours is daily. All you got to do is send a little hair. (PM for address)

Do help, I WANT TO PLAY PREY.

---

### Post by d-E-a-D on 2006-07-05
Ok, after more than 10 formats and thousand tries to make it work, i get 8.26 drivers working on my hp pavilion dv5172 with ati radeon Xpress 200m.
***_I'm using UMA+SIDEPORT 128Mb._***
It gives me the right fglrxinfo:

OpenGL vendor string: ATI technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5879 (***_8.26.18_***)

Now my issue is that glxgears and fglx_gears hangs when i try to run it _***but things like screensaver and games do it great on OpenGL and fps.***_ but it is unstable. sometimes crash, others not.

The worst issue is that it seems that it doesn't refresh the image, everything just is it seems that the windows are over ones of the others, I see the images overlapped, icones disappears when I open something over them and closes.
To read console i have to underline the mouse over the letters. but if i maximize the console i can read it all great.

Now the steps.
Fresh Install of Ubuntu 6.06
update
distro-upgrade
restart
follow this thread but ***_WITH 8.26.18 DRIVER DOWNLOADED FROM ATI_***:
[http://www.ubuntuforums.org/showthread.php?t=199421&page=2&highlight=ati+8.24+200m]("http://www.ubuntuforums.org/showthread.php?t=199421&page=2&highlight=ati+8.24+200m")
restart

For now i can't go further... does anyone goes further than this with 8.26.18 drivers?

NOTE: 8.24.18 drivers worked for me with the thread i said. but i can't get XGL and COMPIZ working. And with fglx_glxgears i just see one piece rolling, the others don't appear like in glxgears.

If someone have this 200M card working well and with XGL and COMPIZ please give us a HOW-TO step by step !!!!

SORRY MY BAD ENGLISH.

Cumps

---

### Post by black math on 2006-07-06
Where do you get the 8.26.18 drivers at?

---

### Post by Eversmann on 2006-07-06
I have XGL and Compiz fully working and with a nice performance, BUT, fglrx hangs gdm after login, so sometimes works, sometimes not, i'm trying to figure what's the problem.

That's why i haven't post a how-to yet.

Waiting for the next ati drivers release.

---

### Post by Dimas on 2006-07-06
I'm having the same errors in Xorg.0.log with drm module than rekahsoft :(

```
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.26.18
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
```
But a few lines down...
```
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
```

---

### Post by cracker on 2006-07-07
Hello, I have an HP Pavillion ZV6000 which I have not yet gotten any linux installed on, due to other issues. I'd just like to say that I am very glad I saw this thread, as it also has the Radeon Xpress 200M 128MB, and I would not be very happy if I formatted my drive only to get unsatisfactory video. I hope a true fix emerges soon, as I am very tired of Windows letting me down. :(

---

### Post by d-E-a-D on 2006-07-07
> **cracker said:**
> Hello, I have an HP Pavillion ZV6000 which I have not yet gotten any linux installed on, due to other issues. I'd just like to say that I am very glad I saw this thread, as it also has the Radeon Xpress 200M 128MB, and I would not be very happy if I formatted my drive only to get unsatisfactory video. I hope a true fix emerges soon, as I am very tired of Windows letting me down. :(

Follow the link i said before and install 8.24 version... it will work.
BTW, I'm using UMA + SIDEPORT 128

Cumps

---

### Post by sturmdogg on 2006-07-07
anyone here manage to get the ati drivers working but are now having problems with their mouse freezing?

---

### Post by Eversmann on 2006-07-08
> **sturmdogg said:**
> anyone here manage to get the ati drivers working but are now having problems with their mouse freezing?

Have that problem. I went back to 8.24.8 and no more problems about mouse freezing..... but still have my usb disconnected randomnly

---

### Post by sturmdogg on 2006-07-12
how did you go about downgrading to 8.24.8?

---

### Post by Eversmann on 2006-07-12
Easy my dear Kakashi :-D

Just downloaded official from ati website (i think there's a link on [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) too). And installed by hand. If you use restricted modules, be sure to disable fglrx on /etc/default/linux-restricted-modules-common

---

### Post by DeRieux on 2006-07-15
> **rekahsoft said:**
> Ok....i have been all over the net and the forums and have yet to get my ATI Radeon 200M working on my Compaq R4000 series laptop. I have tried everything and can not get it working. To those of you who where luck enough to get it working could you please show how in a clean fashion. I have heard that the newest ATI Propriatary driver (8.25.18-1) does not work with my card. Is this true? I also have heard that people have got it running. I have changed to every possable setting in my BIOS and nothing has worked yet. Currently i have it set to Sideport + UMA (128 shared). Thanks for the help.

in the xorg.conf file did you change the driver from "ati" to "fglrx"?
like this:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	#Driver		"ati"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
EndSection

William

---

### Post by nixeri on 2006-07-25
Ok,I have an HP dv5000-series laptop (dv5132eu) /w ATI 200M graphics card. I just cant get fglrx working, i have tried many how-tos, no-go. Latest how-to, i tried was [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually")

That one, and all the others caused blank screen when starting X. When i got a tip to put some shared memory for ATI from BIOS (128M), then i got picture but its pretty messy, i.e. K-menu is transparent and at last, whole system hangs. 

Anyone got any suggestions, please tell them to me. Questions from my system or xorg.conf etc. are also welcome.

Im running Kubuntu Dapper, and latest ATI-drivers.
Sorry for my bad english.

---

### Post by hypersonic5 on 2006-07-30
I too have a Radeon Xpress 200M and have tried everything and can't get the fglrx drivers to work. I've reinstalled Ubuntu a bunch of times and I'm getting tired of doing so. Does anyone have a howto that actually works for the 200M?

---

### Post by doog on 2006-07-31
> **hypersonic5 said:**
> I too have a Radeon Xpress 200M and have tried everything and can't get the fglrx drivers to work. I've reinstalled Ubuntu a bunch of times and I'm getting tired of doing so. Does anyone have a howto that actually works for the 200M?

the only way to get ATI's broken driver to work with the ATI Express 200M is to go into your BIOS and disable all onboard/sideport video memory and set it to use 128MB of shared/UMA video memory. The driver will work with both 2D and 3D. BUT, because you can't use the onboard video memory, the 3D performance is about 30% slower than it once was this time last year when this worked with sideport memory.

Please go to ATI.com, go to their Linux driver page and at the bottom or elsewhere on the page there's a link to send them feedback. Tell them your Express 200M is not working as designed with current ATI drivers because of the UMA-only memory problems.

---

### Post by hypersonic5 on 2006-07-31
Yes, I've already sent them a complaint and all they replied with was that the drivers were provided "as-is" :-x Pretty rediculous.

However, there seem to be new drivers that recently came out, does anyone know if ATI fixed the 200M problems with the latest release?

---

### Post by gako on 2006-07-31
first post, hehehe, well, try [this guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2") with the ati driver (official) 8.24.8, its the only drive that works with sideport+uma, the newest versions only work if you configure UMA (not sideport+uma) in the bios

if still wanna try some other driver be sure to put only UMA

Also if u put less than 128MB of shared memory it will not work[-( 

i have my laptop working with that driver (hp zv6000)

(sorry about grammar, english is not my primary language)

---

### Post by hypersonic5 on 2006-07-31
Hey, thanks for the information. Have you gotten XGL/Compiz to work with those drivers?

---

### Post by hypersonic5 on 2006-07-31
Okay, I got the driver installed. I used the 8.24.8 drivers and the instructions from this howto:

[howto]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually")

I had to set the sideport+uma mode to add an extra 128 MB of my system memory. Fglrxinfo tells me that the drivers are installed correctly.

Now does anybody know how to install XGL/Compiz with this card?

Thanks.

---

### Post by gako on 2006-07-31
No problem.

For XGl/Compiz i used this [HOWTO]("http://www.compiz.net/viewtopic.php?id=389&p=1") (the second howto) but like 60% of the times XGL display everything in the wrong way, still searching for a way to fix it

If you are gonna try it install cgwd and use it instead of gnome-window-decorator in the scripts, it works better, and also use this line in the startcompiz script:

```
cgwd & LD_PRELOAD=/usr/share/fglrx/diversions/libGL.so.1.2 compiz --replace gconf &
```

instead of this:

```
gnome-window-decorator & compiz --replace gconf &
```

hope that helps

---

### Post by tellarite on 2006-08-06
Thank-you edJquarK!:KS  Following your guidelines (on page 2 of this thread) I was able to get full 3d acceleration working on my HP dv8000z with radeon 200M :) 

One thing to note: Using the "OpenGLOverlay" feature produced a white bar on the right hand side of my screen.. turning that feature off removed that problem and 3d performance is still good.. what does that feature do?

---

### Post by skatedawe on 2006-08-06
I got the fglrx to work with this howto: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

I have a msi S270, ati m200.

My problem though, is that the screen flicks 1/3 of my screen, from down to up in a mil sec. It's enoying. Anybody else who has experiense a similiar thing?

---

### Post by rekahsoft on 2006-08-07
OK...i have checked back into getting 3d acceleration with the Radeon 200M and i noticed that ATI released new drivers (8.27.10). Has anybody got them working with the Radeon 200M? do you have any problems?

---

### Post by nixeri on 2006-08-09
Plz, could somebody help me i.e. via e-mail (nixutus <at> gmail.com) or in this forum with this ATI-issue? :( I tried latest ati drivers but still the same thing. I have got some answers about turning Sideport off and using only UMA memory, but my laptop (HP Pavilion dv5132eu laptop, with Ati Xpress 200M Graphics card) does'nt allow that. 

There is only "Sideport" or "Sideport+UMA" options in bios. Everything else is working fine, so i would like to get rid of Windows, but now its impossible because i would like to play sum games too. Oh, and i have tried a bunch of how-tos, "this is the way it worked for me"'s and many others, every time the same thing (Only sideport memory == blank screen&hang up, Sideport+UMA 128Mb == crappy picture + hangup at last)

I would be thankful if anybody could help me with this ](*,) problem.

---

### Post by Melcar on 2006-08-12
I just finished installing the 8.27.10 drivers on my Compaq V2000Z.  "fglrxinfo" displays the correct settings so I guess it's working fine.  I used the Wiki guide.

---

### Post by rekahsoft on 2006-08-12
So it works nice...i may give it a try then...no hang ups or anything?

---

### Post by Melcar on 2006-08-12
> **rekahsoft said:**
> So it works nice...i may give it a try then...no hang ups or anything?

So far everything seems to work just fine.  The only slow downs are because of my RAM (I only have 256:shock: , need to upgrade soon).

---

### Post by rekahsoft on 2006-08-12
hmm...maybe i will give it a try again...do you xgl/compiz running? Can i just install it from the repos? Or do i still have to install it from the drivers on the ATI site?

---

### Post by rekahsoft on 2006-08-12
ok...i just checked the repos and i can't install them from the repos...so...Melcar could you post everything you did to get them working. Did you just use the wiki?

---

### Post by rekahsoft on 2006-08-12
ok...i am getting an error when i try to install the deb packages:```
sudo dpkg -i *.deb
Selecting previously deselected package fglrx-control.
(Reading database ... 108590 files and directories currently installed.)
Unpacking fglrx-control (from fglrx-control_8.27.10-1_i386.deb) ...
Selecting previously deselected package fglrx-kernel-source.
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.27.10-1_i386.deb) ...
Selecting previously deselected package fglrx-sources.
Unpacking fglrx-sources (from fglrx-sources_8.27.10-1_i386.deb) ...
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.27.10-1_i386.deb) ...
mkdir: `/usr/lib/fglrx' exists but is not a directory
dpkg-divert: cannot stat new name `/usr/lib/fglrx/libGL.so.1.2.xlibmesa': Not a directory
dpkg: error processing xorg-driver-fglrx_8.27.10-1_i386.deb (--install):
 subprocess pre-installation script returned error exit status 2

```. How do i fix this?

---

### Post by Melcar on 2006-08-12
I used the Wiki:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
I used the drivers from ATI (did not try using the one on the repos).
Another thing I noticed is that everyone seems to have problems installing the drivers if the video memory is less than 128MB.  I set my video memory to 128MB before I installed the drivers just to be sure.

---

### Post by Malac on 2006-08-12
I don't know if this is relevant as this thread seems to be about laptops but have you tried the "radeon" driver in xorg.conf and /etc/modules instead of the "ati" driver.
I mention it as not many peoople seem to know about it as it is part of the repo drivers.

My xorg.conf sections :
```
Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "dbe"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection
```
and :
```
Section "Device"
    Identifier    "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
    Driver        "radeon"
    BusID        "PCI:1:0:0"
##FGLRX options
#    Option        "VideoOverlay" "on"
#    Option        "OpenGLOverlay" "on"
#    Option        "UseInternalAGPGART" "no"
EndSection
```
And my /etc/modules:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
pctel_hw
pctel
linmodem
pppoatm
agpgart
#fglrx
radeon
dri
drm
```

This worked for me on a R200, I now have 3D and decent FPS.

Hope this helps.

---

### Post by rekahsoft on 2006-08-12
hmmm...wierd...could you list what you did.

---

### Post by Malac on 2006-08-13
> **rekahsoft said:**
> hmmm...wierd...could you list what you did.
If you mean me this is what I did.
Reset xorg.conf to default from the .backup file I made. (You could also do a dpkg-reconfigure xserver-xorg.)
Opened Synaptic and marked the fglrx driver for **Complete** Removal.
Then manually changed the "ati" to "radeon" in xorg.conf adding it to modules as listed above.
That was pretty much it.
I now get the following FPS from glxgears:
```
3663 frames in 5.0 seconds = 732.483 FPS
3672 frames in 5.0 seconds = 734.304 FPS
3664 frames in 5.0 seconds = 732.603 FPS
3672 frames in 5.0 seconds = 734.380 FPS
3670 frames in 5.0 seconds = 733.836 FPS
3669 frames in 5.0 seconds = 733.612 FPS
3666 frames in 5.0 seconds = 733.021 FPS
3678 frames in 5.0 seconds = 735.523 FPS
3668 frames in 5.0 seconds = 733.536 FPS
``` and glxinfo says:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
...........
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.5.1
...........
``` 
And 3D works for me. XGL/Compiz still runs quite slowly but just about passable but then this is an old machine. I have XGL setup as a seperate Session on the login window if I want to use it, that way I can run a normal gnome non-XGL session for most stuff.

Hope this helps.
_**Edit :**_
There is also a guide here that may help it does something similar.
[http://www.ubuntuforums.org/showthread.php?t=219336](http://www.ubuntuforums.org/showthread.php?t=219336)

---

### Post by rekahsoft on 2006-08-13
aw...you don't have fglrx...you are using the mesa drivers...so therefore you don't have 3d acceleration...that is probably the reason xgl/compiz is running slow.

---

### Post by truevox on 2006-08-13
I too am dealing with this nonsense from ATI. At least I think so (KInfo Center tells me this under PCI: ```
0000:00:00.0 Host Bridge: ATI Technologies Inc ATI Radeon Xpress 200 (RS480/RS482/RX480/RX482) Chipset - Host bridge (rev 01)
```). I too would like a workable solution, however, I don't really have too much leeway to experiment because reinstallation would be challangeing (I don't have a working CD rom drive).

And Rekahsoft, have you ever completed that script for the Broadcom Drivers? My internal Wifi would appreciate it.

Thank you all for your time and consideration. Any further information I could provide, please lemme know (and lemme know how to aquire it; I'm new to Linux). And I CAN experiment, just not without something that I can simply back up.

Oh, I'm using an AMD 64 with 32 bit dapper drake Ubuntu that's in KDE. 1 gig ram, um... what else is helpful?

Thanks!

Oh, and uh... FIRST POST! W00T! :D

---

### Post by rekahsoft on 2006-08-13
I have been working on some scripts for compaq R4000 series laptops (and the a like) and am still working on them...(i broke my leg so i was in pain for a month but i am going to get them done ASAP)...If you have the Broadcom 4318 bcm43xx-fwcutter does not work!! You have to use ndiswrapper...and i have found ndiswrapper to be a little picky...but anyway i will tell you how to do it here:

How to get the Broadcom 4318 working
1. install ndiswrapper-utils and ndisgtk like so:```
sudo apt-get install ndisgtk
``` Note: ndisgtk is just a front end for ndiswrapper and depends on ndiswrapper-utils...if you do not want the front end installed just do this:```
sudo apt-get install ndiswrapper-utils
```
2. Now extract the archive i have atached like so:```
tar -xf wifi-drivers.tar.gz
``` Note: The archive contains the windows drivers need by ndiswrapper
3. Now you have to give ndiswrapper the windows drivers so it can generate firmware like so:```
cd drivers
ndiswrapper -i bcmwl5.inf
``` Note: if you installed ndisgtk you can do the same by going to System > Administration > Windows Wireless Drivers and grabbing the windows driver.
4. Now you have to check to see if it worked like so:```
ndiswrapper -l
``` It should say something like this:```
Installed ndis drivers:
bcmwl5          driver present, hardware present

```...if not there is something wrong...report back and we will try and fix the problem.
5. Now we need to install network-manager-gnome like so:```
sudo apt-get install network-manager-gnome
```
6. Now do this:```
sudo modprobe ndiswrapper
```
7. restart
Your done...
Thanks to compwiz18...to see more troubleshooting tips check this:[http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318)

Note there are some scripts on the link above that would do the trick :)

---

### Post by Melcar on 2006-08-13
crapbox@ToGo:~$  /etc/default/linux-restricted-modules-common
bash: /etc/default/linux-restricted-modules-common: Permission denied

Why is it giving me this?  I have already maneged to get the drivers working several times before using the Wiki.  It's just not letting me access the file to disabel the Ubuntu provided fglrx.

---

### Post by rekahsoft on 2006-08-13
Did you use sudo? and don't you blacklist modules at /etc/modprobe.d/blacklist?

---

### Post by Malac on 2006-08-14
> **rekahsoft said:**
> aw...you don't have fglrx...you are using the mesa drivers...so therefore you don't have 3d acceleration...that is probably the reason xgl/compiz is running slow.
Weird :-k
I do seem to have 3D but then my eyes could be decieving me :)

---

### Post by rekahsoft on 2006-08-14
yea...it is a big pain getting fglrx working on Radeon 200M's...

---

### Post by Melcar on 2006-08-14
> **rekahsoft said:**
> yea...it is a big pain getting fglrx working on Radeon 200M's...

Already installed and reinstalled them several times, successfully.  Just use the ATI drivers from ATI's site (new ones are 8.27.10) and follow the Wiki.

---

### Post by rekahsoft on 2006-08-16
ok...i think i found out my problem...when i tried to install the fglrx debs i would get an error...i think it is because i did not use the fakeroot environment...i will see and then report back...

---

### Post by rekahsoft on 2006-08-16
Never mind...i still got the same problem...Does anybody know how to fix this:```
sudo dpkg -i xorg-driver-fglrx_8.27.10-1_i386.deb
(Reading database ... 108634 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.27.10-1_i386.deb) ...
mkdir: `/usr/lib/fglrx' exists but is not a directory
dpkg-divert: cannot stat new name `/usr/lib/fglrx/libGL.so.1.2.xlibmesa': Not a directory
dpkg: error processing xorg-driver-fglrx_8.27.10-1_i386.deb (--install):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx_8.27.10-1_i386.deb
``` All the other fglrx packages depend on this one so they can't be installed...wtf is going on...thanks for the help.

Edit: Note that i have all the dependancies that the wiki specifies (i followed it to the 'T'). So i have the following packages: fakeroot gcc-3.4 module-assistant build-essential debhelper

---

### Post by Malac on 2006-08-16
> **Melcar said:**
> Already installed and reinstalled them several times, successfully.  Just use the ATI drivers from ATI's site (new ones are 8.27.10) and follow the Wiki.
This finally worked for me straight from the box as it were.
I downloaded the 8.27.10 driver from the ATI site, built the Ubuntu/dapper package and just installed it.
Worked first time.
fglrxinfo output:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.27.6)
``` glxgears output:
```
4312 frames in 5.0 seconds = 862.317 FPS
4405 frames in 5.0 seconds = 880.884 FPS
4405 frames in 5.0 seconds = 880.915 FPS
4404 frames in 5.0 seconds = 880.734 FPS
4405 frames in 5.0 seconds = 880.934 FPS
4405 frames in 5.0 seconds = 880.912 FPS
4392 frames in 5.0 seconds = 878.360 FPS
4405 frames in 5.0 seconds = 880.888 FPS
4405 frames in 5.0 seconds = 880.919 FPS
4405 frames in 5.0 seconds = 880.933 FPS
``` This is the first time the fglrx driver has worked properly for me straight from the normal install. :D

---

### Post by mrojas73 on 2006-08-17
With my Presario V2000 which has the 200M graphics card I have no problems installing the ati drivers (fglrx).  The only problem is XGL,  it takes me several reboots before I can logon.  The machine locks up right after the spash screen, but like I said afeter a few reboots it works just fine.  It never locks up once I am able to get to my desktop.

I have done a lot of research trying to find a solution to the problem with no luck,  I always end up back in ubuntu forums and I haven't found a solution that works in here.

---

### Post by rekahsoft on 2006-08-17
Does anybody know how to fix my problem (from three posts ago?) I am stuck. Thanx

---

### Post by Malac on 2006-08-18
> **rekahsoft said:**
> Does anybody know how to fix my problem (from three posts ago?) I am stuck. Thanx
I haven't read back through the whole thread so please forgive if this is what you have already tried. It sounds like you have files left over from previous installs.

As I said I tried compiling my own driver and using the xorg-driver-fglrx...deb in repos but to no avail.
But the new ATI file "ati-driver-installer-8.27.10-x86.run" worked for me. Have you tried that?

First I had to mark fglrx in Synaptic for "Complete Removal". This removes all files and directories associated with previous attempts. Just "Remove" is not good enough as this leaves files and links still on your computer.
Then went to my /usr/src/ directory (this is where I do all my work compiling and so on) to remove any fglrx debs left there from previous attempts.
Then ran : ```
ati-driver-installer-8.27.10-x86.run --buildpkg Ubuntu/dapper
```
and installed the resulting .deb.
```
sudo dpkg -i xorg-driver-fglrx_8.27.10-1_i386.deb
sudo dpkg -i fglrx-control_8.27.10-1_i386.deb
```
Hope this helps.

---

### Post by rekahsoft on 2006-08-18
ok..i did remove previous installs completely but i did not remove the old debs from /usr/src....i will retry the install and report back with the results...

---

### Post by btboudreaux on 2006-08-18
Ok I've tried everything in these forums. Nothing has fully worked.

First I tried the 8.25 drivers. Didn't work.

Then I tried the 8.27 drivers in about a million different combinations but to no avail. (Good thing I created a partition image before I started this b/c I've restarted this at least 12 different times.

Then I tried the old driver, I think it was 8.24? That one boot up and worked, but froze everytime XGL was started. So it's a dud. 

Anymore suggestions???

I just looked on the ati site and a new driver was posted today it seems. 8.28.8... hummm has anyone tried this yet??

---

### Post by btboudreaux on 2006-08-18
Tried with the 8.28.8 driver. Still doesn't work. I'm starting to think eye candy just wasn't met for me.

---

### Post by rekahsoft on 2006-08-19
> **btboudreaux said:**
> Tried with the 8.28.8 driver. Still doesn't work. I'm starting to think eye candy just wasn't met for me.
I hear ya...i have been having problems with this for a couple months now...just wondering what hardware are you running? I have a compaq R4000 series laptop...with a Radeon 200M.

---

### Post by btboudreaux on 2006-08-19
> **rekahsoft said:**
> I hear ya...i have been having problems with this for a couple months now...just wondering what hardware are you running? I have a compaq R4000 series laptop...with a Radeon 200M.

HP Pavilion zv6000 series.

I actually got it to work with the 8.28.8 drivers! But... I had to set my card in the BIOS to UMA only... so I have no side port memory, which sucks. I don't understand why ati can't write drivers properly for their own cards!

---

### Post by Malac on 2006-08-20
Okay, just a heads up as the new 8.28.8 installer from ATI website worked perfectly for my system.
I now have fglrx working this is what I did.
[COLOR=Blue](The [COLOR=Black]**rm**[/COLOR] and [COLOR=Black]**rmdir**[/COLOR] commands are only needed if you have other driver debs in the directory from previous installs and can be missed out if you wish to keep them.)[/COLOR]
Put installer in /usr/src/ then ran following commands
In a **_root_** terminal 
[LEFT]```
cd /usr/src/
```
```
chmod +x [COLOR=Gray][I]"name of driver installer"
[/I][/COLOR]rm /usr/src/modules/fglrx/debian/*.*
rm /usr/src/modules/fglrx/*.*
rm /usr/src/ATI/*.*
rmdir /usr/src/modules/fglrx/debian
rmdir /usr/src/modules/fglrx
rmdir /usr/src/ATI
rm fglrx.tar.bz2
rm fglrx-*.deb
rm xorg-driver-fglrx*.deb
./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/dapper
dpkg -i *.deb
module-assistant prepare,update
module-assistant build,install fglrx
depmod
``` 
[COLOR=Sienna]EDIT:

Then :
```
gedit /etc/modules
``` [COLOR=Sienna]add:[/COLOR]
```
agpgart
drm
dri
fglrx
``` 
Make sure fglrx is not disabled in linux-restricted-modules-common
```
gedit /etc/default/linux-restricted-modules-common
``` should read:
```
DISABLED_MODULES=""
``` [/COLOR]
[/LEFT]
       Reboot and voila.
If you don't run this in a root terminal you will need **sudo** before each command

fglrxinfo output :
[LEFT]```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8 )
```[/LEFT]
       glxgears output :
[LEFT]```
4078 frames in 5.0 seconds = 815.554 FPS
4077 frames in 5.0 seconds = 815.391 FPS
4077 frames in 5.0 seconds = 815.330 FPS
4077 frames in 5.0 seconds = 815.383 FPS
4078 frames in 5.0 seconds = 815.418 FPS
4077 frames in 5.0 seconds = 815.371 FPS
``` [/LEFT]
      Hurrah!

---

### Post by Melcar on 2006-08-22
I have been trying to install the new 8.28 drivers with no success.  I think it's because I still have the 8.27 ones installed creating a driver conflict; so my question is, how to uninstall old drivers.

---

### Post by Melcar on 2006-08-22
I did a freash install of Ubuntu and installed the new 8.28 drivers.  Followed the Wiki and everything went smoothly.  I conclude that the reason I can't upgrade my drivers on my older partition (the one running the 8.27 drivers) is because I don't know how to uninstall old drivers.

---

### Post by rekahsoft on 2006-08-23
You have a Radeon 200M right?

---

### Post by Melcar on 2006-08-23
> **rekahsoft said:**
> You have a Radeon 200M right?


If you are refering to me then yes, I have a laptop running a 200M.

---

### Post by rekahsoft on 2006-08-23
have you had any problems with the 8.28.8 drivers? When i installed them they worked the first time i rebooted but everything was garbled and messy...Me and another forum member are having the same problem but u got off with out a hitch...what all did u do? Just follow the wiki? What does your xorg.conf look like? Thanks

---

### Post by r00tzz on 2006-08-23
Will ATI release a driver that works with only sieport, or its a problem with my Compaq R4012?? 

I can only use accel with UMA, and UMA only!

---

### Post by Malac on 2006-08-23
I forgot to include two steps in my previous post.
I have edited it with the inserted sections in[COLOR=Sienna] brown/red.[/COLOR]

---

### Post by rekahsoft on 2006-08-23
ok...i did what you did and everything boots fine but it says i am using the mesa drivers....how do i fix this? Also what does your xorg.conf look like. Thanx.

---

### Post by Malac on 2006-08-23
Here is my xorg.conf:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "aticonfig-Screen[0]" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

    # path to defoma fonts
    FontPath     "/usr/share/X11/fonts/misc"
    FontPath     "/usr/share/X11/fonts/cyrillic"
    FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath     "/usr/share/X11/fonts/Type1"
    FontPath     "/usr/share/X11/fonts/100dpi"
    FontPath     "/usr/share/X11/fonts/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load  "bitmap"
    Load  "dbe"
    Load  "ddc"
    Load  "dri"
    Load  "extmod"
    Load  "freetype"
    Load  "glx"
    Load  "int10"
    Load  "type1"
    Load  "v4l"
    Load  "vbe"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
    Option        "Device" "/dev/input/mice"
    Option        "Protocol" "ExplorerPS/2"
    Option        "ZAxisMapping" "4 5"
    Option        "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier  "stylus"
    Driver      "wacom"
    Option        "Device" "/dev/wacom"          # Change to 
    Option        "Type" "stylus"
    Option        "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier  "eraser"
    Driver      "wacom"
    Option        "Device" "/dev/wacom"          # Change to 
    Option        "Type" "eraser"
    Option        "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier  "cursor"
    Driver      "wacom"
    Option        "Device" "/dev/wacom"          # Change to 
    Option        "Type" "cursor"
    Option        "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier   "B1770NSL"
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
    Driver      "radeon"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]"
    Driver      "fglrx"
    Option        "VideoOverlay" "on"
    Option        "OpenGLOverlay" "off"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
    Monitor    "B1770NSL"
    DefaultDepth     24
    SubSection "Display"
        Depth     1
        Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     4
        Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     8
        Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     15
        Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     16
        Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     24
        Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]"
    Device     "aticonfig-Device[0]"
    Monitor    "aticonfig-Monitor[0]"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "DRI"
    Mode         0666
EndSection


```

---

### Post by btboudreaux on 2006-08-23
Has anyone gotten the sideport memory to work with the Radeon XPRESS 200m??? The 8.28.8 drivers work, but I have to turn off my sideport memory or it won't function. 

I guess I'll just have to wait for another ati driver release that may or may not work.

---

### Post by r00tzz on 2006-08-24
btboudreaux I have the same problem as you.

what a waste of memory(128Mb)!!!

---

### Post by btboudreaux on 2006-08-24
r00tzz, yeah it's absolutely ridicules. From my understanding, the sideport memory worked on an earlier version of the driver but then suddenly it was broken and 3 or 4 driver updates later it still doesn't work. I tried installing the earlier driver but XGL/Compiz froze up and was completely unusable. 

What a waste of 128megs.

---

### Post by rekahsoft on 2006-08-26
Hey Malac...your xorg.conf is a little different then mine (specificly where you use 'radeon' in the first driver section and you put the options in the next section)...i will see what results i get when i try it...also what is your memory setting in regards to your video card? (sideport or what)

---

### Post by proagg on 2006-09-01
Just wanted to add my own "Yahoo!" to the list. Followed the instructions after a clean reinstall and I get:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 2.0.5755 (8.24.8)

btw, no one mentioned where to find the drivers, so here's a link to the ati download: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run)

Also, I am on a R4000, 200m with both sideport and UMA. XGL/Compiz here I come!

---

### Post by Gio2k on 2006-09-09
I have a toshiba laptop (A100-507) with an ATI Radeon express 200m graphic card. I downloaded the latest binary driver from ATI. (8.28.8) which should work with the express 200m:
[http://www2.ati.com/drivers/linux/linux_8.28.8.html](http://www2.ati.com/drivers/linux/linux_8.28.8.html)
and followed the insltallation instructions:
[http://www2.ati.com/drivers/linux/linux_8.28.8-inst.html](http://www2.ati.com/drivers/linux/linux_8.28.8-inst.html)
Specifically, i just ran the command *sh ./ati-driver-installer-8.28.8.run*
The driver was installed, i rebooted and direct rendering was not working. Additionally, the performance was worse than before, totem was even having problems playing an avi clip.
So, on to the main questions:
I have been reading about this sideport / uma issue. The first problem i have is that the Toshiba bios doesn't have any option to enable / disable / modify the 200m settings. Anybody can help me with this?

On the other side, another thing that i didn't do was converting the .run package to .deb packages. Is that a big mistake? and if so, why?

thx

---

### Post by Adler on 2006-11-29
Hi All,

I've done Dapper, and now Edgy without success regarding my Radeon Express 200M COMPAQ Presario Notebook chipset.

Firtsly, I'd like to go 3-D acceleration, then XGL/Beryly/Compiz. Then do those cool XL/Beryl/Compiz 3-D Desktops.

Anybody, any luck?

I have all too often seen those Black Screens. LOL!

Adler

---

### Post by Adler on 2006-11-29
Hi All,

I've done Dapper, and now Edgy without success regarding my ATI Radeon Express 200M COMPAQ Presario Notebook chipset.

Firstly, I'd like to go 3-D acceleration, then XGL/Beryly/Compiz. Then do those cool XL/Beryl/Compiz 3-D Desktops.

Anybody, any luck?

I have all too often seen those Black Screens. LOL! And, hope to finally get my ATI card going.

Adler

---

### Post by 89camarorsv6 on 2006-11-30
hello, 

This is a very nice thread, I hope I had seen this before I got X200M on my laptop to do beryl,etc.

I originally had XGL, beryl with fglrx driver working perfectly on dapper. Then I upgraded to edgy, now I installed beryl from ubuntu2 repository (0.1.2) and also tried trevors 0.1.3 SVN rep.

When I log into the Xgl Desktop Session, using startxgl as described here 

[http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/XGL)

It just hangs.

I have done the following 

1. Reinstalled Xgl, 
2. Reinstalled fglrx
3. Reinstalled beryl like 100 times with different repositories and versions

It always ends up in a hard lock. I can go into regular gnome and fglrx is working as fgl_glxgears work as well as fglxrxinfo.

Can someone shed some light here?.

I have also tried the thread with X700 fix for Xserver
[http://ubuntuforums.org/showthread.php?t=150854&highlight=xgl+hard+lock](http://ubuntuforums.org/showthread.php?t=150854&highlight=xgl+hard+lock)

That doesnt work either.

Thanks

---

### Post by rekahsoft on 2006-11-30
> **btboudreaux said:**
> Has anyone gotten the sideport memory to work with the Radeon XPRESS 200m??? The 8.28.8 drivers work, but I have to turn off my sideport memory or it won't function. 

I guess I'll just have to wait for another ati driver release that may or may not work.

This is a kernel bug. I have filed a report. Look [here]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/72476") for more information (currently there is not fix).

---

### Post by Adler on 2006-12-01
Hi All,

I run Ubuntu, now EDGY, off a relatively new Compaq Presario, with the AMD Thurion chipset, and maxed out with RAM. Basically, all the bells and whistles. But, this pathetic ATI Radeon Xpress 200M card. This thing is a real killer.

H-P has sold millions of these PCs with the ATI card. Never in my life will I buy another ATI card. Driver support really has been the worst.

Adler

---

### Post by Malac on 2006-12-02
> **Adler said:**
> Never in my life will I buy another ATI card. Driver support really has been the worst.

Adler
I know I keep harping on about this but have you e-mailed ATI and told them this.
People should do this as a matter of course, not just post on the forum.
It may not do any good but if enough people _*actually*_ do this then ATI may get the message.

If everyone on the forum that I have seen complaining about ATI here, actually e-mailed ATI themselves it would probably overwhelm their server. :)

---

### Post by Adler on 2006-12-02
Malac,

You are very right. I'll try going after AMD / ATI today.

Thanks for that response.

Adler

---

### Post by Adler on 2006-12-03
Malac,

I have been trying several different ways to approach ATI, which is now owned by AMD. I've also tried to get to H-P concerning my Compaq Presario V5000Z.

**This all concerns the famous ATI Radeon Xpress 200M card on my Notebook.**

There is no reference to a V5000Z in the H-P databse, only V5000US. I've been -- on hold -- @ H-P Chat-wise concerning my (our) issues -- but no-one home. I do know that my PC was made / assembled in China. 

As far as I can tell everyone has given up on the ATI Radeon Xpress 200M Video driver/card. 

I'll not keep on torching my system! I'm a pretty experienced Linux user, and this Notebook cost well over US$1000.00. 

I've compiled, patched patches, ran devices where Microsoft could not, H-P said you can't, but did, and ran Beagle before most. Oh, I did that with my Linux Forum participation. 

Never again, both H-P, and a ATI Video card. Never!

BTW, I'm still on "hold" @ H-P chat.

Adler

---

### Post by Malac on 2006-12-04
@ Adler

Hopefully now AMD are associated with ATI things may get a little better for us Linux users.

I wouldn't have bothered phoning myself, but good on you for trying it.
I just e-mailed tech support and got a stock reply. At least I felt I'd registered some "protest".

Good luck.

---

### Post by Adler on 2006-12-04
Malac,

I just stopped @ a local PC store that sells H-P Notebooks, and asked if I could dump my ATI card, and go NVidia. It seem that the answer is yes.

I'm going to hit my local electronic superstore (Fry's Electronics) in the next couple of days, and see what I can find out. If it all seems reasonable I'll go for it.

I **want** that cool XGL/Beryl/Compiz desktop!

Adler

---

### Post by rekahsoft on 2006-12-05
> **Adler said:**
> Malac,

I just stopped @ a local PC store that sells H-P Notebooks, and asked if I could dump my ATI card, and go NVidia. It seem that the answer is yes.

I'm going to hit my local electronic superstore (Fry's Electronics) in the next couple of days, and see what I can find out. If it all seems reasonable I'll go for it.

I **want** that cool XGL/Beryl/Compiz desktop!

Adler

really? how much does this cost?

---

### Post by Gio2k on 2006-12-06
Maybe an online petition?
[http://www.petitiononline.com/create_petition.html](http://www.petitiononline.com/create_petition.html)

I will gladly sign it. Fed up with ati xpress 200m

---

### Post by Adler on 2006-12-06
rekahsoft,

> really? how much does this cost?

I've not yet talked to the Geeks as to cost replacing my pathetic ATI Radeon Xpress 200M card. It seems that H-P / COMPAQ dumped us into a POS, as this thread length shows. 

Hey, my Notebook was well the over US$1,000 model. 

> I will gladly sign it. Fed up with ati xpress 200m

Gio2k,

I've yet to go to your Petition Site, but @ mine I'll trash H-P / COMPAQ for a whole host of reasons, and with good reason. After about 6 months worth of crashes, and lack of support, I see that H-P / COMPAQ is old technology. That is concerning the Video card in my Notebook. 

And, support calls in general -- except if you want to buy something.

Hey, I have the seperate video card with 128MB of RAM on My Notebook.

As a Linux User I'm sure that Microsoft (M$) users have been, and will be going through, the same tings. LOL! 

I can't wait for Christmas, those M$ VISTA GIFT Cards, and the total melt down regarding hardware support. 

And, we think that we have problems....

I'm still having fun, and can do *almost* what I want to do.

Let me get to your petition...

Adler

---

### Post by Tenchi on 2006-12-07
Hello everyone,
Like you guys I have the crappy ATI 200m graphics card, mine is on a hp ze2315.
I managed to install Beryl and fglrx (will have to double check once I get home).  My issue is that I don’t have 3d via OpenGL, but all your post gave me some ideas to try out.  I will post again with my xorg.conf file if I am successful.  I really need OpenGL for WoW to run on Ubuntu.

---

### Post by Tenchi on 2006-12-07
Well here is my xorg.conf file 

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "Extensions"
Option "Composite" "false"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
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
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option   up
     "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by dzoster on 2006-12-14
Lady's and gents!   The new fglrx ati 8.32.5 driver now comes with a NO BLACK SCREEN OF DEATH FEATURE!!!!

Yes i am currently using 3d on my Compaq V5000z (Hp dv500z) radeon express 200m laptop!   so it compiles,boots and works!!


fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6234 (8.32.5)



Stay up a little later tonight and install it :)  


thanks ati......

---

### Post by marcele on 2006-12-14
Driver is working fine with beryl and compiz!

---

### Post by TusharG on 2006-12-14
I have tried drivers for ATI XPRESS 200M on different distros. I found that only Ubuntu/Dapper with 8.24 driver works fine. I have not seen any one posting ATI XPRESS 200M card working with edgy. Remember there is difference between 200 and 200M they are not same. I just received a news from ATI site that now they have release driver version 8.32 
 If anyone has tried please let me know. Unfortunately the release notes for 8.32 are not yet updated. 
 I'm also using HP Pavilion dv8000z with ATI Radeon XPRESS 200M notebook.

---

### Post by dzoster on 2006-12-14
I am using 8.32.5 with edgy.. This thread is about the 200m with proprietary drivers. not compiz.. i think getting current drivers to work in the first place is key here... 

Yes I have a 200m...
Yes I have a Compaq V5000z
Yes, the latest drivers work, (you can use X in edgy)

Stable... idk yet  i have had a few odd crashes and X restarts... i am blaming this on my own stupidity until there are more confirmed reports...  But as far as i know, ati at least showed some progress before the end of 2006. I am just glad i can use the s video output in edgy. :)

---

### Post by Adler on 2006-12-14
Hi All,

Does anyone have a screen shot of doing anything with the ATI Radeon 200M card e.g. Games, Compiz / Beryl? 

My idea of getting this card to work was to run tux racer, or GL-117, without it crashing, or being so slow that the screen said that I needed to adjust my video effects. Which I could not do.

There seems to be a major difference about running "fglrx" or "ati". I have yet to figure this out, and have been going @ this for about 6 months. Hey, I love the challenge. 

I'm here with Beryl, but have no 3-D effects. 

[[IMG]http://img72.imageshack.us/img72/4060/snapshot3rc5.th.png[/IMG]](http://img72.imageshack.us/my.php?image=snapshot3rc5.png)


The thread that I followed is @ [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

Importantly -- everyone should remember this --

When you get the "Black Screen of Death", go to Rescue Mode, then enter

sudo dpkg-reconfigure xserver-xorg.

This has saved me from having to do a complete re-install a few times, like yesterday. LOL!

Still all-in-all this card s*cks!

Adler

---

### Post by lnxusr on 2006-12-14
I don't usually post here, but I figured I'd let you guys know that the 8.32.5 drivers are working with sideport! (dedicated video mem) :D :D :D Yes, you can finally stop using system mem for the video card. I tested these drivers on kubuntu 6.06 with the 2.6.15 kernel and Xorg 7.0. Also, 3D performance seems to be doing better, the game Legends doesn't get as much input lag at the lobby menu anymore, I played for a few mins and it didn't crash (like it usually does with the 8.24.8 drivers) But I will have to play it for a longer period before rejoicing. I have not tried XGL yet, but I might later, If I do I will report my findings. All in all I think we're starting to see the fruits of the AMD-ATI acquisition and at long last, the drivers are finally getting better! Now I can hold off on trying to sell this laptop for a little longer :mrgreen:

---

### Post by Adler on 2006-12-14
lnxusr,

So -- what did you do here? D/L, compile? Tweak something?

I'm still stuck on UMA+SIDEPORT to save myself.

Adler

---

### Post by lnxusr on 2006-12-14
I used method 2 of this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
Other then that this is pretty much a stock install of Kubuntu 6.06 (2.6.15, Xorg 7.0) It should work with any *buntu variant
I wrote a script that should do it all for you: 
Dapper:
[http://lnxusr.phpnet.us/ati-8.32.5-builder.sh](http://lnxusr.phpnet.us/ati-8.32.5-builder.sh)
Edgy:
[http://lnxusr.phpnet.us/ati-8.32.5-builder-edgy.sh](http://lnxusr.phpnet.us/ati-8.32.5-builder-edgy.sh)


You may have to chmod +x ati-8.32.5-builder.sh or  ati-8.32.5-builder-edgy.sh. Both scripts have been tested on (K)Ubuntu dapper and edgy and are confirmed working. Run it by typing sudo ./ati-8.32.5-builder.sh or ./ati-8.32.5-builder-edgy.sh
You may need to unlock the package repositories in /etc/apt/sources.list
The script will download the driver package from AMD's server, if you already have it, open the script with gedit or kwrite and put a # in front of the "wget http://......." line.

You may have to add the following lines to your /etc/X11/xorg.conf in order to get full 3D acceleration on Edgy:
```
Section "Extensions"
        Option "Composite" "Disable"
EndSection
```

If you still cannot get it working, try the following commands:
sudo rmmod radeon
sudo rmmod drm
sudo modprobe fglrx
then restart X (Ctrl+alt+backspace) 
If none of this works, let me know what laptop model you have, Mine is an HP Pavilion DV5212us
I don't know it it matters (probably dosen't) but I built the packages with sideport+uma still enabled. Hope this helps.

---

### Post by Adler on 2006-12-14
lnxusr,

Did you pull down the latest ATI Driver for Linux? I've tried all the guides for 3-D acceleration. 

I'm over @ Beryl, but have none of those cool 3-D effects. And, I know fglrx, and glxgears. I now  re-boot to using XGL as my Desktop. Here's the Admin Panel.

[[IMG]http://img72.imageshack.us/img72/4060/snapshot3rc5.th.png[/IMG]](http://img72.imageshack.us/my.php?image=snapshot3rc5.png)

I still get the message when trying GL-117 that me video card needs adjustment, and running Tux Racer, the "Salmon" are now missing. 

I am probably missing something here, other than having this POS Video card ripped out of my system, then doing a FedEx to ATI. LOL!

Adler

---

### Post by xolot1 on 2006-12-14
lnxuser,


i tried using your script (thanks, btw), but ran into a few problems.

i got an x server error:
(EE) module ABI major version (0) doesn't match the server's version (1)
(EE) Failed to load module "fglrx" (module requirement mismatch, 0)
(EE) No drivers available.

i did a google search, found some results, and looked into your script.
**by changing the package build option to edgy from dapper, i can now successfully run X.**
ill edit this post when i get more information as to what is working.

willi

---

### Post by lnxusr on 2006-12-14
Yes, I'm using the latest driver. I haven't tried anything with XGL yet on here, so I probably won't be much help in that area.

I think we all feel the same about ATI at this point :D I look at my desktop w it's nvidia 5200 card running AIGLX and Beryl on Archlinux, then I look at my poor laptop with it's ATI mark of shame. I wish I would've waited and gotten the pavilion DV6105us with it's nvidia 6150 ](*,)  
The 5200 is an AGP card and it's GPU is clocked at 245MHz, the ATI card is PCI-e and is clocked at 350MHz and Nexuiz still runs *** slow with realtime world lighting running about ~15fps, whereas it runs at ~40 fps on nvidia. Sure says alot about ATI. And forget about using the OpenGL 2.0 shader w this card, ~3 fps for ATI, ~15 fps for nvidia. Even my friend's desktop version of the ATI xpress 200 chokes on Nexuiz, but at least he upgraded to an nvidia 6800 :D

---

### Post by Adler on 2006-12-14
> I think we all feel the same about ATI at this point I look at my desktop w it's nvidia 5200 card running AIGLX and Beryl on Archlinux, then I look at my poor laptop with it's ATI mark of shame. I wish I would've waited and gotten the pavilion DV6105us with it's nvidia 6150
The 5200 is an AGP card and it's GPU is clocked at 245MHz, the ATI card is PCI-e and is clocked at 350MHz and Nexuiz still runs *** slow with realtime world lighting running about ~15fps, whereas it runs at ~40 fps on nvidia. Sure says alot about ATI. And forget about using the OpenGL 2.0 shader w this card, ~3 fps for ATI, ~15 fps for nvidia. Even my friend's desktop version of the ATI xpress 200 chokes on Nexuiz, but at least he upgraded to an nvidia 6800 

lnxusr,

Well said. I've got plans for Compiz / Beryl, or to say the least 3-D, and my pathetic ATI Radeon XPress 200M card doesn't help me on my Notebook.

I can replace the card according to the Geeks @ my nearest PC Superstore. Do you have any recommendations?

Adler

---

### Post by TusharG on 2006-12-14
WOW!  ATI RADEON XPRESS 200M is running well with drivers 8.32.5 on Ubuntu/Edgy. I installed the same driver and my XPRESS card has started working. Remember 8.25 to 8.31 none of the drivers worked on Ubuntu/Edgy and Dapper only worked well with 8.24.

---

### Post by lnxusr on 2006-12-14
> **Adler said:**
> lnxusr,

Well said. I've got plans for Compiz / Beryl, or to say the least 3-D, and my pathetic ATI Radeon XPress 200M card doesn't help me on my Notebook.

I can replace the card according to the Geeks @ my nearest PC Superstore. Do you have any recommendations?

Adler

Upgradeable laptop vid card? o.O I wonder if my pavilion is capable of that, have to take it apart later :D 
As for recommendations, basically, go with anything that's not ATI, nVidia is awesome, and I hear Intel GMA cards have good linux (and AIGLX/XGL) support but i've not much experience with Intel GMA cards. I'd say, prefer nVidia, but if an nVidia option is unavailable for your model, get an Intel GMA. BTW, what make/model laptop are you using?

@xolot1
Have you got 3D acceleration on edgy? If not, post the output of the following command:
```
grep "fglrx" /var/log/Xorg.0.log
```
I'm upgrading to edgy right now (only thing keeping me on dapper was the dated ATI drivers not building for the 2.6.17 kernel) so I will post an updated script when I get a chance to test it. Maybe I can finally reinstall Archlinux on this laptop now!

---

### Post by lnxusr on 2006-12-14
Ok i can now confirm XGL/Beryl are running great under Edgy with the new drivers.....FINALLY!!!!! :D

---

### Post by someone7663663 on 2006-12-15
I've had problems from the start with these stupid drivers. Now i hear that i might finally have a chance of beryl working on my laptop. Is there any guide that i can folly for edgy that someone hs come across or used that could really help me. I keep trying to install the drivers but i keep getting xorg errors and idk the source of them. If anyone could help us noobs, it would greatly help. Thanks

---

### Post by lnxusr on 2006-12-15
> **someone7663663 said:**
> I've had problems from the start with these stupid drivers. Now i hear that i might finally have a chance of beryl working on my laptop. Is there any guide that i can folly for edgy that someone hs come across or used that could really help me. I keep trying to install the drivers but i keep getting xorg errors and idk the source of them. If anyone could help us noobs, it would greatly help. Thanks

What's the Xorg error say? You can find Xorg's output log in /var/log/Xorg.0.log How did you install the drivers? Did you use ATI's installer or the scripts posted above? What kernel version are you using? (get that by typing uname -r in the console) and your Xorg version (Get that by typing grep "X Window System" /var/log/Xorg.0.log in the console). I have a script somewhere that automatically installs and configures XGL/Beryl I wrote for a friend who was trying to get it installed. When I find it, I'll update/post it.

---

### Post by Tenchi on 2006-12-15
> **lnxusr said:**
> I used method 2 of this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
Other then that this is pretty much a stock install of Kubuntu 6.06 (2.6.15, Xorg 7.0) It should work with any *buntu variant
I wrote a script that should do it all for you: 
Dapper:
[http://lnxusr.phpnet.us/ati-8.32.5-builder.sh](http://lnxusr.phpnet.us/ati-8.32.5-builder.sh)
Edgy:
[http://lnxusr.phpnet.us/ati-8.32.5-builder-edgy.sh](http://lnxusr.phpnet.us/ati-8.32.5-builder-edgy.sh)


You may have to chmod +x ati-8.32.5-builder.sh or  ati-8.32.5-builder-edgy.sh. Both scripts have been tested on (K)Ubuntu dapper and edgy and are confirmed working. Run it by typing sudo ./ati-8.32.5-builder.sh or ./ati-8.32.5-builder-edgy.sh
You may need to unlock the package repositories in /etc/apt/sources.list
The script will download the driver package from AMD's server, if you already have it, open the script with gedit or kwrite and put a # in front of the "wget http://......." line.

You may have to add the following lines to your /etc/X11/xorg.conf in order to get full 3D acceleration on Edgy:
```
Section "Extensions"
        Option "Composite" "Disable"
EndSection
```

If you still cannot get it working, try the following commands:
sudo rmmod radeon
sudo rmmod drm
sudo modprobe fglrx
then restart X (Ctrl+alt+backspace) 
If none of this works, let me know what laptop model you have, Mine is an HP Pavilion DV5212us
I don't know it it matters (probably dosen't) but I built the packages with sideport+uma still enabled. Hope this helps.

Whoa, these drivers worked great,

I tried to use your script, but it did not work.
I opened it up as a text file and manually put the commands in the terminal with sudo infront of them and it worked like a charm. WoW runs in 3d accel mode no more need for opengl.  Can't get beryl to work with cedega need to look into that. Svideo out works great. And it comes with a little gui console which is neat.

I hope everyone gets this working, I know how much a pain it is without 3d accel.

---

### Post by Adler on 2006-12-15
lnxusr,

I've been following this post forever, and have finally got Beryl installed, and the ATI adventure fixed. I've now got everything installed. But see no action / improvement. 

I'm running a AMD Thurion 64-Bit chip, a Compaq Presario Notebook with everything, but don't know where to see an improvement. GL-117 is still the same (slow fps), and Beryl -- well it sits in my Task Bar.

Can anybody show something? Show what the ATI Radeon XPress 200M can do?

Adler

---

### Post by cracker on 2006-12-16
Well, I can tell you from first hand experience that it can't do much in Windows, either...but it should be able to handle a functional XGL setup and run basic games at playable levels.

---

### Post by Adler on 2006-12-16
cracker,

I'll keep going @ this, but don't see any results. However, I'm not crashing as I usually did in the past. 

I just don't seem to be able to launch Beryl. I do have XGL in my SESSION choices, but I do not getting the Beryl Splash Screen as expected. Nor, any special effects when my system loads. 

I'm following this @ [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html). Plus the other ATI Driver install threads. 

I follow another distro, and those Beryl screen shots are great. But, they aren't using the (in)famous ATI XPress 200M card. 

I still think that things need to be done here. 

> Well, I can tell you from first hand experience that it can't do much in Windows, either...but it should be able to handle a functional XGL setup and run basic games at playable levels.

Are you trying this with M$? Games? I'm not a Gamer, but check graphic acceleration against a few standards. Not much joy yet.

Adler

---

### Post by cracker on 2006-12-19
I only meant that this card is not powerful at all. I was very disappointed with it's overall performance.

---

### Post by d-E-a-D on 2006-12-19
Just follow this: [http://ubuntuforums.org/showthread.php?t=321766&highlight=200m](http://ubuntuforums.org/showthread.php?t=321766&highlight=200m)

And you can play games very well with the new drivers... tested with Quake 4.

---

### Post by alek01 on 2006-12-28
Hi Lnxusr,
Thank you for your great script which worked perfectly for my HP Livestrong with ATI Xpress 200M. Ihave the whole ATI menu in the system tray. However, when I make changes (I want the "big desktop") and then hit Ctr+alt+BckSpace to restart X, I come back to my original Login screen and charactersitics. Is there something else I should do to have the changes effective? + Does the Driver allow to set different sync and refresh or do I need to make these manually in the org.conf?
Thank you.

---

### Post by rekahsoft on 2006-12-28
Hi all, i am trying to work out a kernel bug having to do with the Radeon 200M. Is anybody getting any allocation errors during bootup. Check you system logs and report back. Hint: The easiest way to figure out if this is an issue for you is:
1. Do you have to use UMA mode (sharing meory from your RAM) and cannot use Sideport mode?
2. Are you getting an allocation error on boot up (after decompression of kernel)?

If you have either/both of these issues and you have a Radeon Xpress 200M then you probably have the allocation problem. To help out i need you to do the following:

1. Look for something like this:```
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36
``` when you do this:```
lspci
```
2. If you found something like the above do this:```
dmesg | grep $pci_bridge_of_radeon_200M
```Replace "$pci_bridge_of_radeon_200M" with the bridge number (in my case 00:04.0). Post the outout of what you got.

---

### Post by Adler on 2006-12-30
Well Guys,

I hacked my way through this, and I've got the ATI Radeon Xpress 200M card to work. It has taken a while.

I trashed my HDD, and installed Linux Mint (BEA). this Distro uses all the Ubuntu repos, but comes with all the codecs that you need for multimedia already installed. I was having problems getting all the 64-bit codecs, and support from Automatix2. So, I switched back to 32-bit. Ain't Linux fun? LOL! *We can do this!*

I did follow **lnxusr's** script, and I managed the compile / install of the needed ATI drivers for my fresh install. I used method #2 as he suggests. Please read through the whole post there to check for any problems.

**So far so good, and it gets better!**

I've now got Beryl running on my systems with great Desktop effects, and a huge number of themes. I'd recommend that you check out [this reference]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html").

It seems ATI has come up with a better driver.

Adler

---

### Post by demonhunter on 2007-01-29
hello fellows...

My eyes are full of watter since I was waiting for a driver that works on 200M without problems since 8.24 version was released.

I have a question. Are the new drivers working with UMA+Sideport configuration or do we need to use just UMA or just Sideport in BIOS configuration?

thnx. :guitar:

---

### Post by Adler on 2007-01-29
demonhunter,

For me I used only the UMA settings in BIOS when I created the .deb install packages from the latest available ATI Driver. I finally got my ATI Radeon Xpress 200M card to do amazing things. 

I've mentioned above this was after a fresh install. That might make a difference. 3D is geat, and I've gotten up to 200fps in some Games. I'm not a Gamer, but use a few things like GL-117 to check my cards performance.

Moving on I installed Beryl for those 3D effects, and have posted a few things to YouTube. Check this one out @ [http://www.youtube.com/watch?v=KVmH087F2AY](http://www.youtube.com/watch?v=KVmH087F2AY).

Stick with this!

Adler

---

### Post by rekahsoft on 2007-01-29
> **Adler said:**
> demonhunter,

For me I used only the UMA settings in BIOS when I created the .deb install packages from the latest available ATI Driver. I finally got my ATI Radeon Xpress 200M card to do amazing things. 

I've mentioned above this was after a fresh install. That might make a difference. 3D is geat, and I've gotten up to 200fps in some Games. I'm not a Gamer, but use a few things like GL-117 to check my cards performance.

Moving on I installed Beryl for those 3D effects, and have posted a few things to YouTube. Check this one out @ [http://www.youtube.com/watch?v=KVmH087F2AY](http://www.youtube.com/watch?v=KVmH087F2AY).

Stick with this!

Adler

Do you have a Radeon 200M card running fglrx? Because if you think you do then you are mistaken because it is currenly impossable. Why? because currently the fglrx drivers do not support texture_from_pixmap and composite which are needed for Beryl ;)

Btw i have fglrx 8.33.06 installed and working properly with sideport and my Radeon 200M card

---

### Post by Adler on 2007-01-29
rekahsoft,

I do what I do, and that is all off a Radeon Xpress 200M card, using a fresh install of Linux Mint, the latest ATI Linux Driver, building the packages, then the install. 

Beryl runs great, and I've posted all over showing off 3D Beryl Desktops, and YouTube Videos. On some games I get 200fps. This is all off a Compaq Pressario Notebook running a AMD 64-Bit Turion chip with 2Gb of RAM. Nothing too special.

What's the issue?

Adler

---

### Post by rekahsoft on 2007-01-31
> **Adler said:**
> rekahsoft,

I do what I do, and that is all off a Radeon Xpress 200M card, using a fresh install of Linux Mint, the latest ATI Linux Driver, building the packages, then the install. 

Beryl runs great, and I've posted all over showing off 3D Beryl Desktops, and YouTube Videos. On some games I get 200fps. This is all off a Compaq Pressario Notebook running a AMD 64-Bit Turion chip with 2Gb of RAM. Nothing too special.

What's the issue?

Adler

That makes no sense what so ever (i do not mean to be rude or anything btw) ;) :) but the open source drivers do not support DRI (3D acceleration) and fglrx does not support texture_from_pixmap and composite. Although it is possible if you are using XGL not AIGLX. so unless you hacked the open source driver yourself or did something to patch it is imposable. I have build the latest fglrx from source and have it working but it does not perform well at all...

---

