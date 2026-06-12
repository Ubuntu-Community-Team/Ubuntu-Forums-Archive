---
title: "Clevo P170EM - installation of nvidia/bumbelbee breaks"
date: 2012-07-15
forum: Hardware
---

### Post by denied on 2012-07-15
Alright so im not 100% sure whats going on but the nvidia modles dont get made with DKMS, no matter what i try they wont make. Im not sure if its because the Quirks fail to recognize my laptop?

Its a custom build laptop from Clevo called: P170EM / 17" FHD Glossy 90% Color Gamut / Core I7 3820QM 2,7-3,7 Ghz / GTX 675M 2 GB GDDR5 / 32GB Crosair Vengeance DDR3 1600 MHz / Intel 520 Series 240GB SSD / 750GB 7200RPM Seagate Second Drive / Intel Centrino Advanced 6230 / IC Diamond 7

I've tried to install bumbelbee and what not but still cant get this to work. When i make the xorg.conf file by typing nvidia-xconfig and reboot, i get a prompt thats 640xVery small and its not working.

Here are the results, please if you want some more info to be able to help me resolve this just ask and ill supply:

```
octodur@mainframe:/usr/bin$ sudo apt-get install --reinstall nvidia-current && sudo dpkg-reconfigure nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/58.8 MB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 168518 files and directories currently installed.)
Preparing to replace nvidia-current 302.17-0ubuntu1~precise~xup1 (using .../nvidia-current_302.17-0ubuntu1~precise~xup1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Setting up nvidia-current (302.17-0ubuntu1~precise~xup1) ...
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match CLEVO with Dell Inc.
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match CLEVO with LENOVO
DEBUG:Quirk doesn't match
Loading new nvidia-current-302.17 DKMS files...
Building only for 3.2.0-26-generic
Building for architecture x86_64
Building initial module for 3.2.0-26-generic
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod....

DKMS: install completed.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Removing all DKMS Modules
Done.
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match CLEVO with Dell Inc.
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match CLEVO with LENOVO
DEBUG:Quirk doesn't match
Loading new nvidia-current-302.17 DKMS files...
Building only for 3.2.0-26-generic
Building for architecture x86_64
Building initial module for 3.2.0-26-generic
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod....

DKMS: install completed.
```

Any help or hints is most welcome, i've been trying to resolve this issue for a week now =/

Also:

```
octodur@mainframe:/usr/bin$ sudo modprobe nvidia
FATAL: Module nvidia not found.

octodur@mainframe:/usr/bin$ lspci -vnn | grep '\''[030[02]\]'
00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1212] (rev a1) (prog-if 00 [VGA controller])



```

---

### Post by denied on 2012-07-16
So no thoughts on this?

---

### Post by typhoon_tip on 2012-07-16
Start by posting an...
```
lspci
```

... output first (full).

EDIT: you may try to update your Kernel to 3.4 first (there is a PPA for this !), as Ivy Bridge chipset may be problematic with current Kernel.

---

### Post by denied on 2012-07-16
> octodur@mainframe:~$ lspci
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1212 (rev ff)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
03:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 0a)
04:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230 (rev 34)
05:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (rev 30)


Cheers mate, i'll see to that PPA and upgrade the kernel.


EDIT:
After reading the comments bellow on that site im not sure this was the right way to upgrade the kernel =)
[http://www.upubuntu.com/2012/05/how-to-install-kernel-340-stable-on.html](http://www.upubuntu.com/2012/05/how-to-install-kernel-340-stable-on.html)
Anyhow, i'll revert to the old one if this totaly screws up the system. [http://www.thelinuxgeeks.info/how-to-install-linux-3-4-rc6-kernel-in-ubuntu-12-04/4/](http://www.thelinuxgeeks.info/how-to-install-linux-3-4-rc6-kernel-in-ubuntu-12-04/4/) that would have been better to do, but yeah, lets hope for luck =)

---

### Post by typhoon_tip on 2012-07-17
No wait, don't use that way !! Is horrible ! There is a single PPA to add to the system, I find it for you:

```
sudo add-apt-repository ppa:kernel-ppa/pre-proposed
sudo apt-get update
sudo apt-get dist-upgrade
```

If it doesn't work, press SHIFT during boot and a menu will pop up, allowing you to select the previous Kernel, so you can uninstall this one.

Referenced in this thread:
[http://ubuntuforums.org/archive/index.php/t-2006316.html](http://ubuntuforums.org/archive/index.php/t-2006316.html)

:P

---

### Post by denied on 2012-07-19
Thanks mate! I already did that weird upgrade, must say it was a very strange way to upgrade just the kernel =)

Ill try your method now =)

Thanks


OOPS: octodur@mainframe:~$ sudo add-apt-repository ppa:kernel-ppa/pre-proposed
sudo: add-apt-repository: command not found

guess ill do a reinstall later, cant be hustled with that crapy "update" i did.

---

### Post by typhoon_tip on 2012-07-19
> **denied said:**
> Thanks mate! I already did that weird upgrade, must say it was a very strange way to upgrade just the kernel =)

Ill try your method now =)

Thanks


OOPS: octodur@mainframe:~$ sudo add-apt-repository ppa:kernel-ppa/pre-proposed
sudo: add-apt-repository: command not found

guess ill do a reinstall later, cant be hustled with that crapy "update" i did.

Copy/paste without check (me), correct is **apt-add-repository** ! Sorry.

---

### Post by denied on 2012-07-23
Thanks mate! I've re-installed ubuntu now and upgrading the kernel by your method here. I'll let you know how it goes =) Thanks for helping me! =)


EDIT: Hmm did the commands, did the dist upgrade but still on kernel 3.2 =/

octodur@mainframe:~$ uname -a
Linux mainframe 3.2.0-28-generic #44~pre201207180400-Ubuntu SMP Wed Jul 18 12:46:05 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux


anything else i need to do? There are no updates on the software center either so...? =)

EDIT2: Did the manual upgrade instead and now im on 3.4, lets see how this will do =) For others reading this here is the instructions:
[http://ubuntuforums.org/showpost.php?p=12035647&postcount=16](http://ubuntuforums.org/showpost.php?p=12035647&postcount=16)

> $ cd ~/Downloads/

Then use dpkg command to install the packages, for example, here I assume the 32-bit versions of the packages. Run the following commands one by one and type the password for sudo access when prompted.

For linux-headers (of the 3 files, this one is not architecture specific):

$ sudo dpkg -i linux-headers-3.4.0-030400_3.4.0-030400.201205210521_all.deb

For linux-headers-generic (is architecture specific):

$ sudo dpkg -i linux-headers-3.4.0-030400-generic_3.4.0-030400.201205210521_i386.deb

For linux-image-generic (is architecture specific):

$ sudo dpkg -i linux-image-3.4.0-030400-generic_3.4.0-030400.201205210521_i386.deb


---

### Post by denied on 2012-07-23
still doesnt work =(

> **octodur@mainframe:~$ optirun firefox**
[ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to assign any connected display devices to X screen 0

[ERROR]Aborting because fallback start is disabled.
**octodur@mainframe:~$ sudo dpkg-reconfigure nvidia-current**
Removing all DKMS Modules
Done.
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match CLEVO with LENOVO
DEBUG:Quirk doesn't match
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match CLEVO with Dell Inc.
DEBUG:Quirk doesn't match
Loading new nvidia-current-302.17 DKMS files...
Building only for 3.4.0-030400-generic
Building for architecture x86_64
Building initial module for 3.4.0-030400-generic
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.4.0-030400-generic/updates/dkms/

depmod....

DKMS: install completed.
**octodur@mainframe:~$ sudo modprobe nvidia**
FATAL: Module nvidia not found.
octodur@mainframe:~$ 



Bleh im soon giving up the whole linux experience for good. Been strugling with this for years now, both times the gfx card has been the problem. Last laptop had AMD radeon that caused the comp to hand because of clocksource needed to be changed to =jiffies (took 3 years to fix that problem). Now i buy a new laptop with nvidia card hoping i wouldnt have to deal with issues. Instead im forced again to go down this rabbit hole due to hybrid graphics. Just makes me sick of all these problems =(

---

### Post by denied on 2012-07-24
okey so i installed the ppa xorg-edgers and did the upgrade. Now im on kernel 3.5 with the latest drivers. Though still when i run nvidia-xconfig i still get the 640xsomething display. Though i notice something new:

> **octodur@mainframe:~$ optirun glxspheres**
[ERROR]Cannot access secondary GPU - error: Could not load GPU driver

[ERROR]Aborting because fallback start is disabled.

**octodur@mainframe:~$ modprobe nvidia**
WARNING: Not loading blacklisted module nvidia_current
FATAL: Module nvidia not found.

though i cant find that the nvidia_current is blacklisted in /etc/modprobe.d/blacklist.conf


> **octodur@mainframe:/etc/modprobe.d$ ls -la**
total 68
drwxr-xr-x 2 root root 4096 Jul 23 22:32 .
drwxr-xr-x 134 root root 12288 Jul 23 23:08 ..
-rw-r--r-- 1 root root 2507 Feb 16 04:03 alsa-base.conf
-rw-r--r-- 1 root root 325 Mar 18 2011 blacklist-ath_pci.conf
-rw-r--r-- 1 root root 1603 Mar 18 2011 blacklist.conf
-rw-r--r-- 1 root root 108 May 23 15:35 blacklist-cups-usblp.conf
-rw-r--r-- 1 root root 210 Mar 18 2011 blacklist-firewire.conf
-rw-r--r-- 1 root root 661 Nov 20 2011 blacklist-framebuffer.conf
-rw-r--r-- 1 root root 156 Feb 16 04:03 blacklist-modem.conf
lrwxrwxrwx 1 root root 41 Jul 23 12:29 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root 583 Mar 18 2011 blacklist-rare-network.conf
-rw-r--r-- 1 root root 1077 Mar 18 2011 blacklist-watchdog.conf
-rw-r--r-- 1 root root 349 Apr 30 16:50 bumblebee.conf
-rw-r--r-- 1 root root 127 Apr 22 09:31 dkms.conf
-rw-r--r-- 1 root root 157 Jun 18 00:15 nvidia-current_hybrid.conf
lrwxrwxrwx 1 root root 49 Jul 23 21:25 nvidia-graphics-drivers.conf -> /etc/alternatives/x86_64-linux-gnu_nvidia_modconf
-rw-r--r-- 1 root root 30 May 18 10:03 vmwgfx-fbdev.conf

so where is the nvidia_current being blacklisted? anyone have a clue?

---

### Post by typhoon_tip on 2012-07-24
It can be any of those files in modprobe.d ! Have a look.

---

### Post by denied on 2012-07-24
Found these:

blacklist nvidiafb <--- blacklist-framebuffer.conf

And also this is weird: in **bumblebee.conf**

> # installed by bumblebee-nvidia

# do not automatically load nouveau as it may prevent nvidia from loading
blacklist nouveau
# do not automatically load nvidia as it's unloaded anyway when bumblebeed
# starts and may fail bumblebeed to disable the card in a race condition.
blacklist nvidia
blacklist nvidia-current
blacklist nvidia-current-updates

shall i remove all this? why is it blacklisted in there? =)


EDIT: saw this in dmesg:

> [    5.316197] bbswitch: version 0.4.2
[    5.316205] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    5.316213] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
[    5.316322] bbswitch: detected an Optimus _DSM function
[    5.316328] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[    5.319011] init: alsa-restore main process (1077) terminated with status 19
[    5.319319] init: bumblebeed main process (1079) terminated with status 1
[    5.319346] init: bumblebeed main process ended, respawning
[    5.324728] init: bumblebeed main process (1159) terminated with status 1
[    5.324744] init: bumblebeed main process ended, respawning
[    5.328182] init: bumblebeed main process (1171) terminated with status 1
[    5.328200] init: bumblebeed main process ended, respawning
[    5.331716] init: bumblebeed main process (1175) terminated with status 1
[    5.331735] init: bumblebeed main process ended, respawning
[    5.334589] init: bumblebeed main process (1185) terminated with status 1
[    5.334607] init: bumblebeed main process ended, respawning
[    5.337470] init: bumblebeed main process (1190) terminated with status 1
[    5.337483] init: bumblebeed main process ended, respawning
[    5.340431] init: bumblebeed main process (1194) terminated with status 1
[    5.340444] init: bumblebeed main process ended, respawning
[    5.343113] init: bumblebeed main process (1202) terminated with status 1
[    5.343127] init: bumblebeed main process ended, respawning
[    5.345937] init: bumblebeed main process (1212) terminated with status 1
[    5.345951] init: bumblebeed main process ended, respawning
[    5.348753] init: bumblebeed main process (1224) terminated with status 1
[    5.348767] init: bumblebeed main process ended, respawning
[    5.351864] init: bumblebeed main process (1236) terminated with status 1
[    5.351877] init: bumblebeed respawning too fast, stopped


doesnt look very good =/

also:

> octodur@mainframe:~$ grep bumblebeed /var/log/syslog
Jul 24 07:42:51 mainframe bumblebeed[1094]: Module 'nvidia-current' is not found.
Jul 24 07:42:51 mainframe bumblebeed[1181]: Module 'nvidia-current' is not found.


EDiT:

So i went into **/etc/bumblebee/bumblebee.conf** and changed this line:

**KernelDriver=nvidia-current**
to
**KernelDriver=nvidia**

rebooted and now at least i can start glxspheres with optirun and its working.
Not sure if this is a proper fix but its working for now (though im still missing the icons to the left in ubuntu)

---

### Post by tenmoi on 2012-07-24
I think you should remove the xorg-edgers ppa for now. On my machine the left panel loses all icons if it runs kernel 3.5.from the xorg-egders ppa.

First install ppa-purge
$sudo apt-get install ppa-purge
then:
$sudo ppa-purge ppa:xorg-edgers/ppa

What you want is this more stable ppa: ppa:ubuntu-x-swat/x-updates

$sudo **add**-apt-repository ppa:ubuntu-x-swat/x-updates
$sudo apt-get update
$sudo apt-get upgrade

Um. How did you install bumblebee in the first place?

P.S
This is my bumblebee.conf for your reference.
> 
cat /etc/bumblebee/bumblebee.conf 
# Configuration file for Bumblebee. Values should **not** be put between quotes

## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=

## Client options. Will take effect on the next optirun executed.
[optirun]
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false


# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# [https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods](https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods)

## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-current
Module=nvidia
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-current:/usr/lib32/nvidia-current
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia

## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau


---

