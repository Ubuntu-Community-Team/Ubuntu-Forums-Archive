---
title: "problems with dell vostro 3350"
date: 2011-07-08
forum: Hardware
---

### Post by AlexValex on 2011-07-08
Hello

I'm absolute beginner in Linux (experience with ubuntu for three days) and just a regular user of Windows XP. 
I recently bought an Dell Vostro 3350: [http://www.dell.com/sg/business/p/vostro-3350/pd](http://www.dell.com/sg/business/p/vostro-3350/pd)
Intel I5 2410M processor.

I have two problems: 
1. with AMD/ATI video card:

>                                   lspci | grep VGA 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) 
 01:00.0 VGA compatible controller: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M] 
 alex@DeLLu:~$  
 Well, the additional driver utility identifies the Radeon VGA, installs the driver (is this proper linuxese?) but when I restart the system I'm informed that no ATI VGA is identified on my computer (I'm trasnlating from Romanian, so maybe in English it's not exact this phrasing, but you get the idea, methinks). Without the ATI driver, Ubuntu works quite fine, displaying that nice apple-wise, win7-wise interface. It probably works with a proper driver for the Intel Integrated VGA .

2. with the fingerprint reader - It is identified in the test (it simply exists), but I have no interface whatsoever to putting it to use.

I'm using Ubuntu 11.04. 32 bit, installed on an ext3 partition, on a dual system (with windows XP). I had some problems with the instalation, but I managed to solve them with the GParted Live CD.

Anyway, my problems with Ubuntu are quite small compared with those in WinXP. I can't find any drivers for XP, whatsoever -  Dell is providing drivers only for Windows 7and I bought the system without any OS.

Sorry for my English, I can only hope that I made myself clear.

---

### Post by AlexValex on 2011-07-09
I tried to solve the problem of the VGA and I think I'm pretty close, but my lack of knowledge of Linux is hindering me.
I have found on the AMD support site ([http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)) a driver which is quite recent (6/15/2011). I have downloaded and tried to install it according to the instruction here: [http://www2.ati.com/relnotes/Catalyst_11.6_Linux_Installer.pdf](http://www2.ati.com/relnotes/Catalyst_11.6_Linux_Installer.pdf)
But, when in terminal, I didn't get to a point where a visual interface would lunch, as presented in that tutorial. Instead, this is what appears:
> alex@DeLLu:~$ cd ATI
alex@DeLLu:~/ATI$ sh ./ati-driver-installer-11-6-x86.x86_64.run
Created directory fglrx-install.QWnDHd
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.861.................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
[COLOR=Red]=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================[/COLOR]
Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 6.9 or later
See /usr/share/ati/fglrx-install.log for installation details.
Removing temporary directory: fglrx-install.QWnDHd

I cannot find the log file, nor the ATI directory in the usr/share.
What do I do wrong?
I'm using Gnome as a terminal.

---

### Post by AlexValex on 2011-07-11
New problems with Ubuntu on the Dell Vostro 3350.
A. I've updated the bios from the manufacturer's website from A03 to A04. After installing this update I systematically cannot load the Ubuntu. It's always blocking somewhere in the process. I guess this update is the problem (I cannot find other possible explanation, but I might be wrong). According to the manufacturer's website, this update:
1. Improved BIOS password function.
2. Added TI USB 3.0 Host Controller support. 
 
I've updated the bios from windows. 

B. I have an option in bios for HD: ATA vs. AHCI. None of my systems work with AHCI.

Suggestions, anyone?

---

### Post by AlexValex on 2011-07-14
I'm thinking to quit linux, although I hate it. After several installations it seemed to work fine, but after only a few restarts, it started again to stop somewhere in the process.
When I'm booting in recovery mode, it stops everytime here:  
> 
21.161894] ppdev: user parallel port driver
21.195338] type=1400 audit (1310656183.989.2): apparmor="STATUS" operation="profile load" name="/usrlib/cups/backend/cups-pdf" pid=835 comm="apparmor_parser"
21.196919] type=1400 audit (1310656183.989.3): apparmor="STATUS" operation="profile  load" name="/usrlib/cups" pid=835  comm="apparmor_parser"


It stays on screen for about three minutes and after that the screen is  going to standby.
What does this mean?
I don't even know what more frustrating: that for my laptop (bought without any OS) Dell is providing drivers only for Windows 7, or that I don't have any cue whatsoever why Linux is not working on this laptop.
Are there any chances that other dstro would work better?

---

### Post by AlexValex on 2011-07-15
The problem seems to be generated by the dual VGA card (Intel HD, associated with the I5 processor and the ATI/Radeon). Somebody showed me how to deactivate de gfx-thing during boot and it load without any problems.

I do it this way:
1. when in GRUB (I have a dual boot system) I select the OS and press E
2. in the third line of the menu - 
> set gfxpayload=$linux_gfx_mode I put a "#" in front of this line;
3. Press F10 and it boots properly, but with the ATI/Radeo deactivated.

Obviously, this is not a satisfying solution, but it works for the moment. I'm curious if and how could I save this modification (with the #), so I don't have to enter this menu every time I boot.

---

### Post by qwertyas on 2011-12-03
After installing the 11.10 version of Ubuntu, still no solution to the problem.
I can install the driver coming from the package, but not its updated version. Yet, when launching Catalist, I'm informed that no ATI/AMD card is installed.

---

### Post by crey84 on 2011-12-09
I am about to buy one, and reading around the graphics to be sure they will working I found this thread that should be useful for you: [http://askubuntu.com/questions/86221/does-ubuntu-support-radeon-hd-6750m-or-6490m](http://askubuntu.com/questions/86221/does-ubuntu-support-radeon-hd-6750m-or-6490m)

Specially this website for dowloading AMD / ATI drivers: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Good luck

---

### Post by crey84 on 2011-12-09
As for the fingerprints reader it seem that Dell is working with Validity Sensors that are still unsupported by the fprint project [http://www.freedesktop.org/wiki/Software/fprint/libfprint/Unsupported%20devices](http://www.freedesktop.org/wiki/Software/fprint/libfprint/Unsupported%20devices)

Apart form these two issues any good news from the 3350?

---

