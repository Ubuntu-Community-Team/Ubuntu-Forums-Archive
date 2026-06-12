---
title: "ati rage 128 3d support?"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by ghostcoil on 2009-11-04
Hi,
I'm running karmic koala on an AMD xp 2200+ motherboard and have been trying to install an ATI Rage 128 video card... I've tried out a few things from other threads, but I'd really like to get 3d support from this card - even if it's just enough to get the deskcube : )

First of all, is this possible?

Secondly, how can I go about enabling this?

from lspci

sol@sol-desktop:~$ sudo lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
-(some USB stuff)-
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
**01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS**

I have the xserver-xorg-video-r128 driver installed and when I take a look at etc/X11/xorg.conf it comes up blank.

thanks!

---

### Post by ghostcoil on 2009-11-04
I ran compiz-check (from [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)) with these results:

sol@sol-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS
 Driver in use:         ati
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Your current resolution is too high to run Compiz. 

Would you like to know more? (Y/n) y

 Your resolution is 1024x768 but the maximum 3D texture size that your
 graphics card is capable of is 512x512. Thus Compiz will not be able to run
 on this setup. You have to decrease the resolution first (in case you are
 using a dual-head setup, try disabling one monitor and run the script again).

Looks like the drivers are working... I can't set it to 512x512 (and the other options make things quite funky). I read something about changing colour depth (or something like that) so I'll go there next...

---

### Post by MaindotC on 2009-11-04
I believe for 3D support you'll need to try using an experimental kernel & ATI driver.  See [this thread](http://ubuntuforums.org/showthread.php?t=1293110) and my post #19 shows step-by-step what I did.  However, I do suggest you read the whole thread and understand the consequences should something go wrong.

---

### Post by ghostcoil on 2009-11-05
Thanks for the thorough steps! I added xorg-edgers to my software sources and tried the rc5 and rc6 versions of the 2.6.32 kernel but no dice. I couldn't get either one of the headers (dependencies were unsatisfied) so that might have been the problem?

I believe that 3d rendering IS on:

sol@sol-desktop:~$ glxinfo |grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Rage 128 Pro 20051027 AGP 1x x86/MMX+/3DNow!+/SSE

so, to redefine my goal, I'm actually looking for how to use compiz at this resolution (1024x768) with my system.

I've only got 512M of RAM as well so that may be limiting me... off to check some compiz info!

---

### Post by MaindotC on 2009-11-05
> **ghostcoil said:**
> I couldn't get either one of the headers (dependencies were unsatisfied) so that might have been the problem?


What's this all about?  What happened when you tried to install the headers?  What command (or Synaptic) did you use and what was the exact output?  Copy/paste please.

---

### Post by ghostcoil on 2009-11-05
I went to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc5/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc5/) and clicked on the image and headers for i386.  Package Installer installed the image but had this to say about the headers "Error: Dependency is not satisfiable: linux-headers-2.6.32-020632rc5". I tried installing the headers after the image and got the same message.

I also gave it a shot in the terminal, although I'm not really that familiar with it yet:
sol@sol-desktop:~$ sudo apt-get install linux-headers-2.6.32-020632rc5-generic_2.6.32-020632rc5_i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.32-020632rc5-generic_2.6.32-020632rc5_i386.deb

---

### Post by ghostcoil on 2009-11-05
oops double post!

---

### Post by MaindotC on 2009-11-05
I don't believe you can use apt-get like that.  Do it this way:
```

sudo apt-get install linux-headers-2.6.32-020632rc5 linux-headers-2.6.32-020632rc5-generic

```

If you want, just type:
```

sudo apt-get install linux-headers

```
and then press the TAB button to display all available packages starting w/ linux-headers.

.deb files are installed using:
```

sudo dpkg -i <filename>.deb

```

---

### Post by ghostcoil on 2009-11-05
```
sol@sol-desktop:~$ sudo apt-get install linux-headers-2.6.32-020632rc5 linux-headers-2.6.32-020632rc5-generic
[sudo] password for sol: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.32-020632rc5

```okay... so I tried

```
sol@sol-desktop:~$ sudo apt-get install linux-headers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.31-9-rt 2.6.31-9.152
  linux-headers-2.6.31-14-generic-pae 2.6.31-14.48
  linux-headers-2.6.31-14-generic 2.6.31-14.48
  linux-headers-2.6.31-14-386 2.6.31-14.48
  linux-headers-2.6.31-14 2.6.31-14.48
You should explicitly select one to install.
E: Package linux-headers has no installation candidate
 
```2.6.32 isn't there... might there be a repo I haven't enabled?

It looks like I can boot up in 2.6.32, though...
 ```
sol@sol-desktop:~$ uname -r
2.6.32-020632rc5-generic 
```> I don't believe you can use apt-get like that man that made me laugh :D

---

### Post by MaindotC on 2009-11-05
What lines did you add to sources.list?  Should be:
```

deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main

```

---

### Post by ghostcoil on 2009-11-05
I originally added xorg-edgers with system>software sources, and now I went into sources.list and added the code above.  Still can't find the headers... should I install 2.6.32-*-_all as well as the 'i386'?

---

### Post by MaindotC on 2009-11-05
If you're running a 64-bit installation then don't install anything .i386.  Either the PPA is down (which I highly doubt) or you missed a step in the installation process.  Retrace your steps and document them in a post the way I did on the other thread.

Also, here's what the output of a cache search should look like:
```

xk@xk:~$ sudo apt-cache search linux-headers | more
[sudo] password for xk: 
linux-ec2-source-2.6.31 - Linux kernel source for version 2.6.31 with Ubuntu patches
linux-headers-2.6.31-14 - Header files related to Linux kernel version 2.6.31
linux-headers-2.6.31-14-generic - Linux kernel headers for version 2.6.31 on x86/x86_64
linux-headers-2.6.31-14-server - Linux kernel headers for version 2.6.31 on x86_64
linux-headers-2.6.31-302 - Header files related to Linux kernel version 2.6.31
linux-headers-2.6.31-302-ec2 - Linux kernel headers for version 2.6.31 on x86/x86_64
linux-headers-ec2 - Linux kernel headers for ec2 machines
linux-headers-generic - Generic Linux kernel headers
linux-headers-lbm-2.6.31-14-generic - Header files related to linux-backports-modules version 2.6.31
linux-headers-lbm-2.6.31-14-server - Header files related to linux-backports-modules version 2.6.31
linux-headers-server - Linux kernel headers on Server Equipment.
linux-headers-virtual - Linux kernel headers for virtual machines
linux-libc-dev - Linux Kernel Headers for development
linux-source-2.6.31 - Linux kernel source for version 2.6.31 with Ubuntu patches
linux-headers-2.6.31-9-rt - Linux kernel headers for version 2.6.31 on Ingo Molnar's full real time preemption patch
linux-headers-rt - Rt Linux kernel headers
linux-rt-headers-2.6.31-9 - Header files related to Linux kernel version 2.6.31
rt2400-source - source for rt2400 wireless network driver
rt2500-source - source for rt2500 wireless network driver
rt2570-source - source for rt2570 wireless network driver
linux-source-2.6.32 - Linux kernel source for version 2.6.32 with Ubuntu patches
linux-headers-2.6.32-020632rc5-generic - Linux kernel headers for version 2.6.32 on x86/x86_64
linux-headers-2.6.32-020632rc5 - Header files related to Linux kernel version 2.
6.32
xk@xk:~$ 

```

---

### Post by ghostcoil on 2009-11-05
I've cleared away what I'd already and am retracing my steps - does this
```
sol@sol-desktop:~$ uname -a
Linux sol-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
```mean I'm running a 32-bit install? My CPU is 32bits as well so that means I should stick with the x86 stuff, right?

**Edit:** Cache search looks like that now... :)

---

### Post by MaindotC on 2009-11-05
> **ghostcoil said:**
> I've cleared away what I'd already and am retracing my steps - does this
```
sol@sol-desktop:~$ uname -a
Linux sol-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
```mean I'm running a 32-bit install? My CPU is 32bits as well so that means I should stick with the x86 stuff, right?

**Edit:** Cache search looks like that now... :)

Yeah you are running a 32-bit installation but I'm not sure if there i686 packages.  Typically anything in this family is referred to as x86 but I'm not very knowledgeable on processor architectures so I'm not sure if you can just install a 386 or if you need a 686 package built for you.  Sorry!  Hope you make some progress in any event.

---

### Post by ghostcoil on 2009-11-05
Weeeeeell I got as far as putting this
```
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main
```
into sources.list but I can't seem to download the image or the headers via the terminal. I can get the image from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc5/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32-rc5/") but not the headers. I'm stumped for now, so I guess I'll roam the internet looking alternatives. Thanks a lot for all of your help!

---

### Post by MaindotC on 2009-11-05
> **ghostcoil said:**
> I'm stumped for now, so I guess I'll roam the internet looking alternatives. Thanks a lot for all of your help!

What are you stumped about?  You don't HAVE to install them via apt...download the .debs and used the dpkg command like I said!

---

### Post by ghostcoil on 2009-11-06
Opened sources.list with gedit and added
 ```
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main  
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu karmic main
``` downloaded
 linux-headers-2.6.32-020632rc5_2.6.32-020632rc5_all.deb
linux-headers-2.6.32-020632rc5-generic_2.6.32-020632rc5_i386.deb
linux-image-2.6.32-020632rc5-generic_2.6.32-020632rc5_i386.deb
linux-source-2.6.32_2.6.32-020632rc5_all.deb
 
ran dpkg
 
 ```
sol@sol-desktop:~/Desktop$ sudo dpkg -i linux-*  
 (Reading database ... 152664 files and directories currently installed.)  
 Preparing to replace linux-headers-2.6.32-020632rc5 2.6.32-020632rc5 (using linux-headers-2.6.32-020632rc5_2.6.32-020632rc5_all.deb) ...  
 Unpacking replacement linux-headers-2.6.32-020632rc5 ...  
 Preparing to replace linux-headers-2.6.32-020632rc5-generic 2.6.32-020632rc5 (using linux-headers-2.6.32-020632rc5-generic_2.6.32-020632rc5_i386.deb) ... 
 Unpacking replacement linux-headers-2.6.32-020632rc5-generic ...  
 Selecting previously deselected package linux-image-2.6.32-020632rc5-generic.  
 Unpacking linux-image-2.6.32-020632rc5-generic (from linux-image-2.6.32-020632rc5-generic_2.6.32-020632rc5_i386.deb) ...  
 Done.  
 Selecting previously deselected package linux-source-2.6.32.  
 Unpacking linux-source-2.6.32 (from linux-source-2.6.32_2.6.32-020632rc5_all.deb) ...  
 Setting up linux-headers-2.6.32-020632rc5 (2.6.32-020632rc5) ...  
 Setting up linux-headers-2.6.32-020632rc5-generic (2.6.32-020632rc5) ...  
 Examining /etc/kernel/header_postinst.d.  
 run-parts: executing /etc/kernel/header_postinst.d/dkms  
 run-parts: executing /etc/kernel/header_postinst.d/nvidia-common  
 

 Setting up linux-image-2.6.32-020632rc5-generic (2.6.32-020632rc5) ...  
 Running depmod.  
 update-initramfs: Generating /boot/initrd.img-2.6.32-020632rc5-generic  
 Running postinst hook script /usr/sbin/update-grub.  
 Generating grub.cfg ...  
 Found linux image: /boot/vmlinuz-2.6.32-020632rc5-generic  
 Found initrd image: /boot/initrd.img-2.6.32-020632rc5-generic  
 Found linux image: /boot/vmlinuz-2.6.31-14-generic  
 Found initrd image: /boot/initrd.img-2.6.31-14-generic  
 Found memtest86+ image: /boot/memtest86+.bin  
 Found Windows NT/2000/XP on /dev/sda1  
 done  
 Examining /etc/kernel/postinst.d.  
 run-parts: executing /etc/kernel/postinst.d/dkms  
 run-parts: executing /etc/kernel/postinst.d/nvidia-common  
 

 Setting up linux-source-2.6.32 (2.6.32-020632rc5) ... 
``` Restarted computer in 2.6.32
 ran update
 ```
sol@sol-desktop:~$ sudo apt-get update  
 [sudo] password for sol:  
 Hit http://security.ubuntu.com karmic-security Release.gpg  
 Ign http://security.ubuntu.com karmic-security/main Translation-en_US           
 Hit http://packages.medibuntu.org karmic Release.gpg                            
 Ign http://packages.medibuntu.org karmic/free Translation-en_US                 
 Ign http://packages.medibuntu.org karmic/non-free Translation-en_US             
 Hit http://us.archive.ubuntu.com karmic Release.gpg                             
 Ign http://us.archive.ubuntu.com karmic/main Translation-en_US        
 Get:1 http://ppa.launchpad.net karmic Release.gpg [307B]              
 Ign http://ppa.launchpad.net karmic/main Translation-en_US            
 Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US  
 Ign http://security.ubuntu.com karmic-security/universe Translation-en_US  
 Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US  
 Hit http://security.ubuntu.com karmic-security Release                          
 Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US            
 Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US              
 Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US            
 Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                     
 Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US          
 Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US    
 Hit http://packages.medibuntu.org karmic Release                                
 Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US  
 Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US  
 Get:2 http://ppa.launchpad.net karmic Release [66.0kB]               
 Hit http://us.archive.ubuntu.com karmic Release                          
 Hit http://us.archive.ubuntu.com karmic-updates Release                         
 Hit http://security.ubuntu.com karmic-security/main Packages                    
 Hit http://packages.medibuntu.org karmic/free Packages                          
 Hit http://us.archive.ubuntu.com karmic/main Packages                           
 Hit http://us.archive.ubuntu.com karmic/restricted Packages                     
 Hit http://us.archive.ubuntu.com karmic/main Sources                            
 Hit http://us.archive.ubuntu.com karmic/restricted Sources                      
 Hit http://us.archive.ubuntu.com karmic/universe Packages                       
 Hit http://security.ubuntu.com karmic-security/restricted Packages              
 Hit http://security.ubuntu.com karmic-security/main Sources                     
 Hit http://security.ubuntu.com karmic-security/restricted Sources               
 Hit http://security.ubuntu.com karmic-security/universe Packages                
 Hit http://packages.medibuntu.org karmic/non-free Packages                      
 Hit http://us.archive.ubuntu.com karmic/universe Sources                        
 Hit http://us.archive.ubuntu.com karmic/multiverse Packages                  
 Hit http://us.archive.ubuntu.com karmic/multiverse Sources                   
 Hit http://us.archive.ubuntu.com karmic-updates/main Packages                
 Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages          
 Hit http://us.archive.ubuntu.com karmic-updates/main Sources                 
 Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources           
 Hit http://us.archive.ubuntu.com karmic-updates/universe Packages            
 Hit http://security.ubuntu.com karmic-security/universe Sources              
 Hit http://security.ubuntu.com karmic-security/multiverse Packages           
 Hit http://security.ubuntu.com karmic-security/multiverse Sources            
 Hit http://us.archive.ubuntu.com karmic-updates/universe Sources             
 Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages  
 Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources  
 Get:3 http://ppa.launchpad.net karmic/main Packages [12.2kB]  
 Get:4 http://ppa.launchpad.net karmic/main Sources [3,593B]  
 Fetched 82.0kB in 1s (74.7kB/s)  
 Reading package lists... Done 
``` Restarted, booted into 2.6.32
 ran glxinfo
 ```
sol@sol-desktop:~$ glxinfo | grep render  
 glxinfo: ../common/drirenderbuffer.c:69: driNewRenderbuffer: Assertion `format == 0x1908 || format == 0x8050 || format == 0x8058 || format == 0x81A5 || format == 0x81A6 || format == 0x81A7 || format == 0x8D48' failed. 
``` Trying to enable desktop effects results in a quick black screen and then the login prompt, as does running compiz_check. The last thing I see running  compiz_check is something like ...texture_from_pixmap. I'm checking out what that failed message from glxinfo means right now...

---

### Post by MaindotC on 2009-11-06
Your Xserver is crashing. Post the contents of /var/log/X.0.log up to the point of the crash.

---

### Post by ghostcoil on 2009-11-06
I can't tell what is up to the point of the crash, so here's the whole thing (I apologize for the length)
```
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.6.4.901 (1.6.5 RC 1)
Release Date: 2009-10-1
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-24-xen i686 Ubuntu
Current Operating System: Linux sol-desktop 2.6.32-020632rc5-generic #020632rc5 SMP Fri Oct 16 09:56:56 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-020632rc5-generic root=UUID=7fcb0fed-571e-4129-99e6-008e3bdfd5cc ro quiet splash
Build Date: 05 October 2009  12:53:58AM
xorg-server 2:1.6.4.901+git20091005+server-1.6-branch.c07b2368-0ubuntu0sarvatt (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  7 00:11:50 2009
(II) Loader magic: 0x1bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 9

(--) PCI:*(0:1:0:0) 1002:5046:1002:0404 ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS rev 0, Mem @ 0xd8000000/67108864, 0xdd000000/16384, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
(==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
    Section "Device"
        Identifier    "Builtin Default ati Device 0"
        Driver    "ati"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default ati Screen 0"
        Device    "Builtin Default ati Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default vesa Device 0"
        Driver    "vesa"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default vesa Screen 0"
        Device    "Builtin Default vesa Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default fbdev Device 0"
        Driver    "fbdev"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default fbdev Screen 0"
        Device    "Builtin Default fbdev Device 0"
    EndSection
    Section "ServerLayout"
        Identifier    "Builtin Default Layout"
        Screen    "Builtin Default ati Screen 0"
        Screen    "Builtin Default vesa Screen 0"
        Screen    "Builtin Default fbdev Screen 0"
    EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default ati Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default ati Device 0"
(==) No monitor specified for screen "Builtin Default ati Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4.901, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4.901, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.4.901, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4.901, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4.901, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4.901, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
    compiled for 1.6.4.901, module version = 6.12.99
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers//r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 6.8.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 2.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.4.0
    ABI class: X.Org Video Driver, version 5.0
(II) R128: Driver for ATI Rage 128 chipsets:
    ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
    ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
    ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
    ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
    ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
    ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
    ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
    ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
    ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
    ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
    ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
    ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
    ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
    ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
    ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
    ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
    ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
    ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
    ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
    ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
    ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
    ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
    ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
    ATI Rage 128 Pro ULTRA TU (AGP?)
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.6.4.901, module version = 0.0.2
    ABI class: X.Org Video Driver, version 5.0
(EE) open /dev/fb0: No such file or directory
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) R128(0): PCI bus 1 card 0 func 0
(II) R128(0): Creating default Display subsection in Screen section
    "Builtin Default ati Screen 0" for depth/fbbpp 24/32
(==) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.4.901, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) R128(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.4.901, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) R128(0): initializing int10
(II) R128(0): Primary V_BIOS segment is: 0xc000
(--) R128(0): Chipset: "ATI Rage 128 Pro GL PF (AGP)" (ChipID = 0x5046)
(--) R128(0): Linear framebuffer at 0xd8000000
(--) R128(0): MMIO registers at 0xdd000000
(--) R128(0): VideoRAM: 16384 kByte (64-bit SDR SGRAM 1:1)
(**) R128(0): Using external CRT for display
(II) R128(0): Primary Display == Type 3
(WW) R128(0): Can't determine panel dimensions, and none specified.
    Disabling programming of FP registers.
(II) R128(0): PLL parameters: rf=2950 rd=65 min=12500 max=40000; xclk=14300
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.6.4.901, module version = 1.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) R128(0): VESA BIOS detected
(II) R128(0): VESA VBE Version 2.0
(II) R128(0): VESA VBE Total Mem: 16384 kB
(II) R128(0): VESA VBE OEM: ATI RAGE128
(II) R128(0): VESA VBE OEM Software Rev: 1.0
(II) R128(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) R128(0): VESA VBE OEM Product: R128
(II) R128(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) R128(0): VESA VBE DDC supported
(II) R128(0): VESA VBE DDC Level 2
(II) R128(0): VESA VBE DDC transfer in appr. 2 sec.
(II) R128(0): VESA VBE DDC read successfully
(II) R128(0): Manufacturer: SAM  Model: 22  Serial#: 1095643447
(II) R128(0): Year: 2003  Week: 28
(II) R128(0): EDID Version: 1.3
(II) R128(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) R128(0): Sync:  Separate
(II) R128(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) R128(0): Gamma: 1.82
(II) R128(0): DPMS capabilities: Off; RGB/Color Display
(II) R128(0): First detailed timing is preferred mode
(II) R128(0): redX: 0.639 redY: 0.323   greenX: 0.275 greenY: 0.597
(II) R128(0): blueX: 0.143 blueY: 0.062   whiteX: 0.283 whiteY: 0.298
(II) R128(0): Supported established timings:
(II) R128(0): 720x400@70Hz
(II) R128(0): 640x480@60Hz
(II) R128(0): 640x480@75Hz
(II) R128(0): Manufacturer's mask: 0
(II) R128(0): Supported standard timings:
(II) R128(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) R128(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) R128(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) R128(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) R128(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) R128(0): Supported detailed timing:
(II) R128(0): clock: 94.5 MHz   Image Size:  312 x 234 mm
(II) R128(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) R128(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) R128(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 71 kHz, PixClock max 110 MHz
(II) R128(0): Monitor name: SyncMaster
(II) R128(0): Serial No: HVBW726161
(II) R128(0): EDID (in hex):
(II) R128(0):     00ffffffffffff004c2d220037314e41
(II) R128(0):     1c0d0103682018522abbb9a352469824
(II) R128(0):     0f484ca4000031403159455961598180
(II) R128(0):     010101010101ea240060410028303060
(II) R128(0):     130038ea1000001e000000fd0032a01e
(II) R128(0):     470b000a202020202020000000fc0053
(II) R128(0):     796e634d61737465720a2020000000ff
(II) R128(0):     00485642573732363136310a20200016
(II) R128(0): EDID vendor "SAM", prod id 34
(II) R128(0): Using EDID range info for horizontal sync
(II) R128(0): Using EDID range info for vertical refresh
(II) R128(0): Printing DDC gathered Modelines:
(II) R128(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) R128(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) R128(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) R128(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) R128(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) R128(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) R128(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) R128(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) R128(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) R128(0): I2C bus "DDC" initialized.
(II) R128(0): I2C device "DDC:E-EDID segment register" registered at address 0x60.
(II) R128(0): I2C device "DDC:ddc2" registered at address 0xA0.
(EE) R128(0): No DFP detected
(II) R128(0): <default monitor>: Using hsync range of 30.00-71.00 kHz
(II) R128(0): <default monitor>: Using vrefresh range of 50.00-160.00 Hz
(II) R128(0): <default monitor>: Using maximum pixel clock of 110.00 MHz
(II) R128(0): Estimated virtual size for aspect ratio 1.3333 is 1024x768
(II) R128(0): Clock range:  12.50 to 400.00 MHz
(II) R128(0): Not using default mode "1152x864" (width too large for virtual size)
(II) R128(0): Not using default mode "1280x960" (width too large for virtual size)
(II) R128(0): Not using default mode "1280x960" (width too large for virtual size)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) R128(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (width too large for virtual size)
(II) R128(0): Not using default mode "1152x864" (width too large for virtual size)
(II) R128(0): Not using default mode "1152x864" (width too large for virtual size)
(II) R128(0): Not using default mode "1152x864" (width too large for virtual size)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (width too large for virtual size)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1152x864" (width too large for virtual size)
(II) R128(0): Not using default mode "576x432" (hsync out of range)
(II) R128(0): Not using default mode "1360x768" (width too large for virtual size)
(II) R128(0): Not using default mode "1360x768" (width too large for virtual size)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1440x900" (width too large for virtual size)
(II) R128(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "840x525" (hsync out of range)
(II) R128(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) R128(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "960x600" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using driver mode "1280x1024" (width too large for virtual size)
(--) R128(0): Virtual size is 1024x768 (pitch 1024)
(**) R128(0): *Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) R128(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) R128(0): *Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) R128(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) R128(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) R128(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) R128(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) R128(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) R128(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) R128(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) R128(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) R128(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) R128(0): *Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) R128(0): Modeline "1024x768"x86.9   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(**) R128(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) R128(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) R128(0): *Driver mode "800x600": 56.2 MHz, 53.7 kHz, 85.1 Hz
(II) R128(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) R128(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) R128(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) R128(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) R128(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) R128(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) R128(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) R128(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) R128(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) R128(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) R128(0): *Default mode "840x525": 73.1 MHz, 65.3 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "840x525"x60.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz)
(**) R128(0): *Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
(**) R128(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
(**) R128(0): *Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
(II) R128(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
(**) R128(0): *Driver mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) R128(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) R128(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) R128(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) R128(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) R128(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) R128(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) R128(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) R128(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) R128(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) R128(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) R128(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) R128(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) R128(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) R128(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) R128(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) R128(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) R128(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) R128(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) R128(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) R128(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
(**) R128(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
(II) R128(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
(**) R128(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) R128(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
(**) R128(0): *Default mode "576x432": 52.5 MHz, 67.6 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "576x432"x75.0   52.49  576 612 676 776  432 432 434 451 doublescan -hsync +vsync (67.6 kHz)
(**) R128(0): *Default mode "576x432": 48.4 MHz, 63.0 kHz, 70.0 Hz (D)
(II) R128(0): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450 doublescan -hsync +vsync (63.0 kHz)
(**) R128(0): *Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
(**) R128(0): *Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) R128(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(**) R128(0): *Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) R128(0): Modeline "512x384"x85.0   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync (68.7 kHz)
(**) R128(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) R128(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) R128(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) R128(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) R128(0): *Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) R128(0): Modeline "512x384"x86.6   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync (35.5 kHz)
(**) R128(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) R128(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) R128(0): *Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) R128(0): Modeline "400x300"x85.3   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync (53.7 kHz)
(**) R128(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) R128(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
(**) R128(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) R128(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(**) R128(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) R128(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) R128(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) R128(0): *Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) R128(0): Modeline "320x240"x85.2   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync (43.3 kHz)
(**) R128(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
(**) R128(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) R128(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
(**) R128(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(**) R128(0): *Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) R128(0): Modeline "360x200"x85.0   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) R128(0): Modeline "320x200"x85.3   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) R128(0): Modeline "320x175"x85.3   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync (37.9 kHz)
(**) R128(0): Display dimensions: (320, 240) mm
(**) R128(0): DPI set to (81, 81)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4.901, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.6.4.901, module version = 1.2.1
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules//libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
    compiled for 1.6.4.901, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) R128(0): Page flipping disabled
(!!) R128(0): For information on using the multimedia capabilities
    of this adapter, please see http://gatos.sf.net.
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) R128(0): [drm] Using the DRM lock SAREA also for drawables.
(II) R128(0): [drm] framebuffer handle = 0xd8000000
(II) R128(0): [drm] added 1 reserved context for kernel
(II) R128(0): X context handle = 0x1
(II) R128(0): [drm] installed DRM signal handler
(II) R128(0): [agp] Mode 0x1f000201 [AGP 0x1106/0x3116; Card 0x1002/0x5046]
(II) R128(0): [agp] 8192 kB allocated with handle 0x00000001
(II) R128(0): [agp] ring handle = 0xd0000000
(II) R128(0): [agp] Ring mapped at 0xb713f000
(II) R128(0): [agp] ring read ptr handle = 0xd0101000
(II) R128(0): [agp] Ring read ptr mapped at 0xb713e000
(II) R128(0): [agp] vertex/indirect buffers handle = 0xd0102000
(II) R128(0): [agp] Vertex/indirect buffers mapped at 0xb5e4e000
(II) R128(0): [agp] AGP texture map handle = 0xd0302000
(II) R128(0): [agp] AGP Texture map mapped at 0xb596e000
(II) R128(0): [drm] register handle = 0xdd000000
(II) R128(0): [dri] Visual configs initialized
(II) R128(0): CCE in BM mode
(II) R128(0): Using 8 MB AGP aperture
(II) R128(0): Using 1 MB for the ring buffer
(II) R128(0): Using 2 MB for vertex/indirect buffers
(II) R128(0): Using 5 MB for AGP textures
(II) R128(0): Memory manager initialized to (0,0) (1024,3072)
(II) R128(0): Reserved area from (0,768) to (1024,770)
(II) R128(0): Largest offscreen area available: 1024 x 2302
(II) R128(0): Reserved back buffer from (0,770) to (1024,1538)
(II) R128(0): Reserved depth buffer from (0,1538) to (1024,2307)
(II) R128(0): Reserved depth span from (0,2306) offset 0x902000
(II) R128(0): Reserved 4096 kb for textures at offset 0xc00000
(II) R128(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Dashed Lines
    Setting up tile and stipple cache:
        20 128x128 slots
        5 256x256 slots
(II) R128(0): Acceleration enabled
(==) R128(0): Backing store disabled
(==) R128(0): Silken mouse enabled
(II) R128(0): Using hardware cursor (scanline 9228)
(II) R128(0): Largest offscreen area available: 1024 x 763
(II) R128(0): DPMS enabled
(II) R128(0): [DRI] installation complete
(II) R128(0): [drm] Added 128 16384 byte vertex/indirect buffers
(II) R128(0): [drm] Mapped 128 vertex/indirect buffers
(II) R128(0): [drm] dma control initialized, using IRQ 16
(II) R128(0): Direct rendering enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: Loaded and initialized /usr/lib/dri/r128_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4.901, module version = 2.2.99
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device ImExPS/2 Logitech Wheel Mouse
(**) ImExPS/2 Logitech Wheel Mouse: always reports core events
(**) ImExPS/2 Logitech Wheel Mouse: Device: "/dev/input/event5"
(II) ImExPS/2 Logitech Wheel Mouse: Found 9 mouse buttons
(II) ImExPS/2 Logitech Wheel Mouse: found relative axes
(II) ImExPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImExPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
(II) ImExPS/2 Logitech Wheel Mouse: Configuring as mouse
(**) ImExPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImExPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImExPS/2 Logitech Wheel Mouse" (type: MOUSE)
(**) ImExPS/2 Logitech Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImExPS/2 Logitech Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImExPS/2 Logitech Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImExPS/2 Logitech Wheel Mouse: (accel) set acceleration profile 0
(II) ImExPS/2 Logitech Wheel Mouse: initialized for relative axes.
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
```

---

### Post by MaindotC on 2009-11-06
Sorry for running you through this whole process but I just realized your card is not going to work on Jaunty and above.  After 8.10, there are certain requirements for installing the ATI driver that are only prevalent in editions after 8.10.  I have the same issue with my ATI x850 - the only driver (that I know of) that will work for 3d support will only install on 8.10 and below.  If you notice, try downloading the driver from the ATI site for Linux (if they have one - I couldn't find it) and installing it - it will stop saying you don't have the proper version of whatever (I think it's freedesktop).

You're only getting 2D support unless you use Ibex and below.

---

### Post by ghostcoil on 2009-11-07
Oh well. Thanks for taking the time to walk me through all that stuff - guess I'll wait 'til I get a new video card!

---

### Post by MaindotC on 2009-11-07
> **ghostcoil said:**
> Oh well. Thanks for taking the time to walk me through all that stuff - guess I'll wait 'til I get a new video card!

Check out slickdeals.net - great prices and the users on those forums typically find special coupon codes and combine it with Bing cash back or Paypal for even more savings.  Their search engine is pretty good: [http://is.gd/4PDAs](http://is.gd/4PDAs) But also check out the front page or subscribe to their twitter so you don't lose out on a deal because they go quickly.

---

### Post by ghostcoil on 2009-11-07
I might actually have a deal on an ATI 9250... looks like there was a bug (  [https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI](https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI) ) in the driver... is it likely that, as there was a fix for it in Edgy and Feisty that the fix is now incorporated into the regular driver set?

---

### Post by tormod on 2010-02-24
The assertion error message is reported in Lucid in bug 515846 and seems to affects all free, non-DRI2 drivers since mesa 7.7 was introduced. You were running a mesa 7.7 (or beta) version from xorg-edgers, right?

---

### Post by ghostcoil on 2010-03-04
i'm not sure what mesa version i was running, and i've got a nvidia geforce card now that's working great so i've shelved the old ati card...

cheers!

---

