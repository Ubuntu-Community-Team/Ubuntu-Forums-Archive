---
title: "problems with laptop running nvidia 9650m gt"
date: 2009-10-25
forum: Hardware
---

### Post by rico1986 on 2009-10-25
Hy, 

here is a pict of my problem

[[IMG]http://img97.imageshack.us/img97/9319/nvidia9659m.th.png[/IMG]]("http://gama.us/up1/up/slike/nvidia_9659m.png")
I've installed the 185 drivers using system->administration->hardware drivers menu

i get that's noise or sometimes just freeze of whole desktop till i restart the computer after 5-10minutes of using the laptop.

I really think thats software issue, cause before i have vista installed and everything work  ok.

I have asus m70vn laptop.

I've tried the 173 drivers and everything seems to be ok, except that desktop applications works really slow sometimes.

i have no fancy things enabled, just clean install of ubuntu 9.10 beta and nvidia drivers.

---

### Post by rico1986 on 2009-10-26
i found that, [http://forums.nvidia.com/index.php?s=&showtopic=102344&view=findpost&p=590031](http://forums.nvidia.com/index.php?s=&showtopic=102344&view=findpost&p=590031)
 
i'll try it later this day and post the results

---

### Post by rico1986 on 2009-10-27
that didn;t work
neither didn't work the hack to run nce nvidia-settings -q all > /dev/null every 30 seconds to keep power level at 3. 
:/
can anyone solve the mystery ?

---

### Post by askysoft on 2009-10-28
well I have this card too and so far , from what I have read online no driver after the 180 series will work on linux. Also there is the same issue on windows too. i guess nvidia screwed up and has not fixed it for a looooooong time now.

if you're using windows then try dox 185 series drivers, they work. I'm using them on windows 7 and everything works perfectly.

I installed Ubuntu 9.10 and the 173 driver while not allowing fancy desktop effects does make linux work on my system so i am happy!

let me know if you find a solution :)

---

### Post by pxxc on 2009-10-30
Hi,

I've been using the 185 drivers in 9.04 without any problems.
Unfortunately, today I've decided to upgrade to 9.10 and I'm having the same problem....

---

### Post by askysoft on 2009-10-30
OK Guys, I MAY Have found a solution.

Try these drivers :
> [ftp://download.nvidia.com/XFree86/Linux-x86/173.14.20/](ftp://download.nvidia.com/XFree86/Linux-x86/173.14.20/)

I do not remember which one i installed ( pkg0 or pkg1) but yea did that and everything works smoothly, desktop effects also works!!

Let me know.

---

### Post by SimpleSeb on 2009-11-01
Hi, 
I'm using ubuntu 9.10 on my Asus m70vn laptop too and i ran into the same graphic problems. 
To solve this problem just visit the nvidia website, go to Downloads, select your hardware (i.e. GeForce 9650m GT) and Download the driver(190.42). This driver works fine.

Have a nice day,
Seb

---

### Post by ephman on 2009-11-04
whew!  i can confirm that my asus m70vn with its nvidia 9650m gt video card works just fine with this driver!  wow, that was a long time coming.  believe it or not i sent my machine in thinking it was a hardware issue, and they replaced the vga card.  but ha ha software was the culprit.  lets just hope that all is fine in a month from now :)

thanks for the bandwidth,

ephman

---

### Post by SimpleSeb on 2009-11-04
Hi,
> **SimpleSeb said:**
> 
I'm using ubuntu 9.10 on my Asus m70vn laptop too and i ran into the same graphic problems. 
To solve this problem just visit the nvidia website, go to Downloads, select your hardware (i.e. GeForce 9650m GT) and Download the driver(190.42). This driver works fine.


after three days using 9.10 i switched back to 9.04. 9.10 has massive problems with the nvidia driver. Neither the old 185 nor the new 190.42 driver works. So my advice is deprecated now.

Have a nice day,
Seb

---

### Post by ephman on 2009-11-04
ok CrAsH.  took a few hours and the whole system halted.  what i've done now is set the PowerMizer setting to Perfer Maximum  Performance.  so if you hear back from me you'll know that the setting change didn't work for me.  fingers crossed!  if this doesn't work i'm going to sell the asus.  their customer service is a joke anyways.

---

### Post by SimpleSeb on 2009-11-05
Hi, 
I think i found a(or better: the :D) solution. I tested it for round about 6 hours now and everything works fine.

At first you have to add the nvidia ppa:
```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
```Update your sources list:
```
sudo apt-get update
```At least install the drivers:
```
sudo apt-get install nvidia-190-modaliases nvidia-glx-190  nvidia-settings-190
```Read more at [http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)

Happy hacking, 
Seb

EDIT: This does NOT fix the problem with the white flickering neither...  Probably getting rid of the damn asus is the best solution...

---

### Post by askysoft on 2009-11-07
> **askysoft said:**
> OK Guys, I MAY Have found a solution.

Try these drivers :


I do not remember which one i installed ( pkg0 or pkg1) but yea did that and everything works smoothly, desktop effects also works!!

Let me know.

DId you guys try this out ? This driver is working perfectly for me!

---

### Post by SimpleSeb on 2009-11-09
> **askysoft said:**
> DId you guys try this out ? This driver is working perfectly for me!
Hi,
this driver is quite old, it's 173.XX . It's not running fluent on my system. -.-

---

### Post by xwang on 2009-12-29
Hi to all,
I've a pro5av asus notebook (aka n50) with the nvidia 9650m gt video card (with 1 gb video ram).
This is the output of lspci --vv:

01:00.0 VGA compatible controller: nVidia Corporation Device 064c (rev a1)
        Subsystem: ASUSTeK Computer Inc. Device 1912                      
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Latency: 0                                                                                           
        Interrupt: pin A routed to IRQ 16                                                                    
        Region 0: Memory at fc000000 (32-bit, non-prefetchable) [size=16M]                                   
        Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]                                      
        Region 3: Memory at fa000000 (64-bit, non-prefetchable) [size=32M]                                   
        Region 5: I/O ports at cc00 [size=128]                                                               
        [virtual] Expansion ROM at fd000000 [disabled] [size=512K]                                           
        Capabilities: <access denied>                                                                        
        Kernel driver in use: nvidia                                                                         
        Kernel modules: nvidia, nvidiafb 
   
Actually I'm using kubuntu 9.04 amd64 with nvidia driver 180 with absolutely no problem.
Yesterday I've tried to update the system, but I've had the same issue as you both with driver 185, 190 and 195. I've also try to do a clean install with the same problem. 
I would like to know:
1) if you have managed to solve the problem
2) if the same problem happens in 9.04 installing the 185 drivers (meaning it is only a nvidia bug)
3) if, instead, it happens only in 9.10 with driver >180 (meaning it is an interaction between 9.10 and nvidia)
4) if someone has already opened a bug in ubuntu or nvidia (link please)
5) if the same issue happens in other distros with the same driver
Thank you,
Xwang

---

### Post by xwang on 2009-12-29
I've also opened this thread on the nvidia linux forum.
[http://www.nvnews.net/vbulletin/showthread.php?p=2153262#post2153262](http://www.nvnews.net/vbulletin/showthread.php?p=2153262#post2153262)
If you can add your experience and data, maybe nvidia will solve the problem.
Xwang

---

### Post by ephman on 2009-12-29
ok for the past monthish or so i've had the latest driver (see a prior reply from me in this thread) working just fine.  it's a bit of a pain though.  i need to put the "powermizer" function to full blast every time i login.  and all works no problem, not a single crash :)  wish there was a way to set that function by default.

---

### Post by xwang on 2009-12-29
Here:
[http://forums.nvidia.com/index.php?showtopic=102344&st=0](http://forums.nvidia.com/index.php?showtopic=102344&st=0)
snake4d suggests (post #13)
to use this command:
modprobe nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222" 

Have you ever tried it?
Is it possible to modify some system configuration file so that nvidia module is always loaded with such option?
Thank you,
Xwang

---

### Post by SeePU on 2009-12-29
Did you guys solve your Nvidia driver problems yet? 

I like to think I could help.  You guys are trying to do it the manual method and if you do ONE thing wrong or forget a step, it will NOT work.  It's very frustrating but it does work if you do it correctly which means 'certain' steps.

I have another way but I want to see if anyone is reading my post.

Post back or pm me and I will help you get it working.

I have installed the Nvidia drivers on four different distros although three have been Debian based (one rpm-based - Fedora).  

I have done it the manual method (I just call it that) and an easier script method.  You should use newer drivers, too.  Your hardware is recent enough that you should have support with few issues.

---

### Post by Kozay9 on 2010-01-03
I've been trying for the graphics card to work, and got it! :P

Follow the following steps:

CTRL + ALT + F1

sudo su
mkdir / nvidia
cd / nvidia
wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/190.53/NVIDIA-Linux-x86_64-190.53-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/190.53/NVIDIA-Linux-x86_64-190.53-pkg2.run)
chmod + x NVIDIA-Linux-x86_64-190.53-pkg2.run
stop gdm

# Installs the driver, you should keep the executable to be easier to remove if necessary.

./NVIDIA-Linux-x86_64-190.53-pkg2.run
cp / etc/X11/xorg.conf gedit / etc/X11/xorg.conf.backup

# Editing the file / etc/X11/xorg.conf
nano / etc/X11/xorg.conf

# And replace:

Section "Device"
    Identifier "Device0"
        Driver "nvidia"
        VendorName "NVIDIA Corporation"
EndSection

# For

Section "Device"
        Identifier "Device0"
        Driver "nvidia"
         Option "RegistryDwords" PowerMizerEnable = 0x1; PowerMizerDefault = 0x3; PowerMizerDefaultAC = 0x0; PowerMizerLeve "
        VendorName "NVIDIA Corporation"
EndSection

# Values for PowerMizerDefault and PowerMizerDefaultAC:
# 0x0 - Maximum Performance
# 0x1 - Maximum Energy Savings
# 0x2 - Medium Energy saving
# 0x3 - Low Energy saving, save more than 0x0

start gdm
have fun, :lolflag:

---

### Post by xwang on 2010-01-03
> **Kozay9 said:**
> I've been trying for the graphics card to work, and got it! :P

Follow the following steps:

CTRL + ALT + F1

sudo su
mkdir / nvidia
cd / nvidia
wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/190.53/NVIDIA-Linux-x86_64-190.53-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/190.53/NVIDIA-Linux-x86_64-190.53-pkg2.run)
chmod + x NVIDIA-Linux-x86_64-190.53-pkg2.run
stop gdm

# Installs the driver, you should keep the executable to be easier to remove if necessary.

./NVIDIA-Linux-x86_64-190.53-pkg2.run
cp / etc/X11/xorg.conf gedit / etc/X11/xorg.conf.backup

# Editing the file / etc/X11/xorg.conf
nano / etc/X11/xorg.conf

# And replace:

Section "Device"
    Identifier "Device0"
        Driver "nvidia"
        VendorName "NVIDIA Corporation"
EndSection

# For

Section "Device"
        Identifier "Device0"
        Driver "nvidia"
         Option "RegistryDwords" PowerMizerEnable = 0x1; PowerMizerDefault = 0x3; PowerMizerDefaultAC = 0x0; PowerMizerLeve "
        VendorName "NVIDIA Corporation"
EndSection

# Values for PowerMizerDefault and PowerMizerDefaultAC:
# 0x0 - Maximum Performance
# 0x1 - Maximum Energy Savings
# 0x2 - Medium Energy saving
# 0x3 - Low Energy saving, save more than 0x0

start gdm
have fun, :lolflag:

If I'm not wrong it is the same that to disable the PowerMizer as suggested previously. Why do you need to install the driver from nvidia? The same thing should work from 185or above driver installed from repository, do you agree?
Xwang

---

### Post by pistacoppu on 2010-01-03
Hi i have an asus n50vn with a 9650m gt that worked perfectly with 185 on karmic.
I tried to install 190 or 195 with ppa but i get an error, is ppa upadater working for you?

that is the error i get after i type: sudo apt-get install nvidia-190-modaliases nvidia-glx-190:

The following extra packages will be installed:
  nvidia-190-kernel-source
The following packages will be REMOVED:
  nvidia-185-kernel-source nvidia-glx-185
The following NEW packages will be installed:
  nvidia-190-kernel-source nvidia-glx-190
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B/22.9MB of archives.
After this operation, 3,846kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 221026 files and directories currently installed.)
Removing nvidia-glx-185 ...
Removing nvidia-185-kernel-source ...
Removing all DKMS Modules
Done.
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package nvidia-190-kernel-source.
(Reading database ... 220798 files and directories currently installed.)
Unpacking nvidia-190-kernel-source (from .../nvidia-190-kernel-source_190.53-0ubuntu1~karmic~nvidiavdpauppa8_i386.deb) ...
Unpacking nvidia-glx-190 (from .../nvidia-glx-190_190.53-0ubuntu1~karmic~nvidiavdpauppa8_i386.deb) ...
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-190' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-185'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-190_190.53-0ubuntu1~karmic~nvidiavdpauppa8_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-190_190.53-0ubuntu1~karmic~nvidiavdpauppa8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by xwang on 2010-01-03
> **pistacoppu said:**
> Hi i have an asus n50vn with a 9650m gt that worked perfectly with 185 on karmic.
I tried to install 190 or 195 with ppa but i get an error, is ppa upadater working for you?

that is the error i get after i type: sudo apt-get install nvidia-190-modaliases nvidia-glx-190:

The following extra packages will be installed:
  nvidia-190-kernel-source
The following packages will be REMOVED:
  nvidia-185-kernel-source nvidia-glx-185
The following NEW packages will be installed:
  nvidia-190-kernel-source nvidia-glx-190
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B/22.9MB of archives.
After this operation, 3,846kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 221026 files and directories currently installed.)
Removing nvidia-glx-185 ...
Removing nvidia-185-kernel-source ...
Removing all DKMS Modules
Done.
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package nvidia-190-kernel-source.
(Reading database ... 220798 files and directories currently installed.)
Unpacking nvidia-190-kernel-source (from .../nvidia-190-kernel-source_190.53-0ubuntu1~karmic~nvidiavdpauppa8_i386.deb) ...
Unpacking nvidia-glx-190 (from .../nvidia-glx-190_190.53-0ubuntu1~karmic~nvidiavdpauppa8_i386.deb) ...
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-190' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-185'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-190_190.53-0ubuntu1~karmic~nvidiavdpauppa8_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-190_190.53-0ubuntu1~karmic~nvidiavdpauppa8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Uhm, so you have the same laptop as I and you don't have any issue with 185? 
If I use 185, after a while (< 20 minutes ) the screen begins to get corrupted (if you move or resize windows) and I've to restart X (if it meanwhile does not hang).
Is Powermizer active?
Can you plese tell me what are you bios and video card firmware versins? 
Have you made some particular configuration?
Thank you,
Xwang

---

### Post by pistacoppu on 2010-01-03
- I have no particular setting
- BIOS version: 62.94.75.00.07
- poewrmizer is active
- firmware version:don't know.. i'll search and tell you. i have to reinstall 185 now, cause i've so many troubles installing 195 or 190 with ppa.

---

### Post by pistacoppu on 2010-01-03
I have no particular settings, and powermizer is active.
All the infos of my card are in the screen of xsetting.

---

### Post by xwang on 2010-01-03
> **pistacoppu said:**
> I have no particular settings, and powermizer is active.
All the infos of my card are in the screen of xsetting.

Can you please tell me also the BIOS version (the notebook one not the video card one)?
Thank you,
Xwang

---

### Post by pistacoppu on 2010-01-04
bios: 211

---

### Post by xwang on 2010-01-04
> **pistacoppu said:**
> bios: 211

Thank you!
I've upgraded the bios from 204 to 212 and now the Video BIOS is the same as you. So I've reinstalled the 185 drivers and I'm testing them.
Thank you,
Xwang

PS I will post tests results in the ext days to be sure the problem has gone away

---

### Post by pistacoppu on 2010-01-04
xwang if you have some time, can you please try to install 195 or 190 drivers via ppa, and tell me if gives you any error.
tnk

---

### Post by xwang on 2010-01-04
> **pistacoppu said:**
> xwang if you have some time, can you please try to install 195 or 190 drivers via ppa, and tell me if gives you any error.
tnk

I generally prefer not installing driver from external repositories.
I have had the same problem when I tried ppa driver some days ago. I my case, I managed to install 195 driver but since then I was not able to go back to 173 ones any more with the same error. So I've reinstalled the disk image created some days before.
Xwang

---

### Post by xwang on 2010-01-04
x pistacoppu:

look here:
[http://blog.mymediasystem.net/uncategorized/the-nvidia-glx-180-opengl3-divert-problem/](http://blog.mymediasystem.net/uncategorized/the-nvidia-glx-180-opengl3-divert-problem/)
maybe it is the solution to your problem.
Xwang

---

### Post by sistja on 2010-01-06
> **pistacoppu said:**
> xwang if you have some time, can you please try to install 195 or 190 drivers via ppa, and tell me if gives you any error.
tnk

Hi, 
I have the M50V laptop (M/B version M50VN) running Ubuntu 9.04 with NVIDIA
GeForce 9650M GT card. I have experienced same quite serious problems with recent Nvidia drivers - image flickering, random freezing after some time spent in Xorg. Strange enough, I have never experienced any problems with an external monitor. These problem always appeared only on the laptop screen.
Two days ago, I have tried the BIOS update described in this thread (to version 212 downloaded from the ASUS website).
And so far, it really seems that it had resolved my troubles.
I am now running the 190.53 NVIDIA driver from NVIDIA website.

If the behaviour finally changed, I will let you know, but so far so good!

Jakub

---

### Post by jitendrasnv on 2010-01-06
hello !!!!

I don't think so that this problem is due to the 185 driver as this can happen with the virus attack.so i thing you can restore your laptop for some previous session.

Thanks

---

### Post by wickstopher on 2010-05-20
bump.

I've had all sorts of problems with drivers for this card since Karmic.  The last time it worked well for me was in Jaunty using the 180 drivers.  I've been trying to install the 180 drivers in Lucid.  They're in the repos, I have them installed, but I can't activate them for some reason.  I'm still stuck with the 173 drivers for any sort of 3D functionality, and they're kinda slow for some reason, and also cause random freezes when playing openGL games like World of Goo.  Any help would be greatly appreciated!  Maybe we need to petition nVidia for better support of this card?  Lots of Asus laptops (and presumably others) in the past 2 years shipped with this one.

---

### Post by ephman on 2010-06-04
virus? no idea what that is.  ha ha ha...

---

