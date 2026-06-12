---
title: "Want to switch to Ryzen"
date: 2017-02-19
forum: Hardware
---

### Post by laserburn2 on 2017-02-19
My Phenom II X4  CPU is showing it's age and I want to replace it with a new AMD Ryzen processor once it becomes available. For that, I'll need to change the motherboard, CPU and RAM. I'm running Ubuntu 16.04, current kernel installed is vmlinuz-4.4.8-040408-generic.

Now, I know that Linux kernel is modular, but I'm not sure that it could handle such a big change as replacing mobo and CPU without having to reinstall the system. Has anyone tried something like that and what were the experiences?

Second of all, I'm not even sure how aging Ubuntu 16.04 is going to handle the sparkling new CPU family. Can we rely on Canonical to upgrade the kernel in the official 16.04 repository to the version that supports Ryzen? Will we have to add external repository? I really want to stay on LTS Ubuntu, upgrading to something like 17.04 doesn't appeal to me.

---

### Post by oldrocker99 on 2017-02-19
The Linux kernel developers are constantly receiving new hardware for which to study and write drivers for the kernel. It's not unlikely that the new(?) chipset will be supported at release. I'm looking forward to the Ryzen myself.

---

### Post by Yellow Pasque on 2017-02-20
That's probably the best answer you'll get for now: [http://www.phoronix.com/scan.php?page=news_item&px=AMD-Zen-Ryzen17h-Patches](http://www.phoronix.com/scan.php?page=news_item&px=AMD-Zen-Ryzen17h-Patches)

If Linux 4.10 is what's needed, then that kernel will come to Ubuntu 16.04.3, which is set to be released in August. I'm not sure if the kernel will be available to 16.04 users before then, but even if it's not, you can always use a mainline kernel.

---

### Post by cariboo on 2017-02-20
With newer bleeding edge hardware, you're probably going have to wait for 18.04 if you want to use an LTS releaase. If you don't mind reinstalling every six months you could probably get away with using 17.04 - 17.10 until 18.04 is released.

---

### Post by daniell59 on 2017-02-22
It was fortunate that I read this thread. I too am considering a Ryzen build. It would be quite upsetting to have invested in the hardware, only to learn later that it would not be supported.

---

### Post by quantumbb on 2017-03-04
Now that the Ryzen processors are available, any new info about them?

---

### Post by quantumbb on 2017-03-04
which kernel, if any, will be needed to use a Ryzen processor?

---

### Post by Perfect Storm on 2017-03-04
You could properly install kernel 4.10 in ubuntu 16.04 to get it working.
I was thinking to make the switch my self in a couple of month.

---

### Post by sczhg on 2017-03-04
This page tells how to get full support of ryzen.
[https://www.servethehome.com/amd-ryzen-with-ubuntu-here-is-what-you-have-to-do-to-fix-constant-crashes/](https://www.servethehome.com/amd-ryzen-with-ubuntu-here-is-what-you-have-to-do-to-fix-constant-crashes/)
Just update to kernel 4.10.1

---

### Post by quantumbb on 2017-03-05
thanks

---

### Post by quantumbb on 2017-03-05
> **sczhg said:**
> This page tells how to get full support of ryzen.
[https://www.servethehome.com/amd-ryzen-with-ubuntu-here-is-what-you-have-to-do-to-fix-constant-crashes/](https://www.servethehome.com/amd-ryzen-with-ubuntu-here-is-what-you-have-to-do-to-fix-constant-crashes/)
Just update to kernel 4.10.1

thanks, just finished.

---

### Post by vishalrao on 2017-03-08
FYI, interestingly, I have a Ryzen 1700 with ASUS Prime B350 Plus motherboard and AMD RX460 graphics card.

I was able to boot and install "stock" ubuntu 16.04 LTS based elementary OS (which has kernel 4.4) - the only dmesg line of interest was something like "coreperf - missing empty info - unknown hardware" but /proc/cpuinfo seemed OK (I am not an expert though).

I installed the 4.8 HWE kernel and Xorg stack because I needed support for my RX460 GPU.

I ran multiple times kernel compile (v4.10.1 git source) with various thread counts and one time there was a kernel stack dump in dmesg and filesystem error and desktop hang - i can't say if this is due to kernel lacking support or some other hardware/software glitch.

I tried same with Fedora 25 with latest 4.9.13 kernel which apparently has a backported Zen CPU topology fix but that was similar performance result and in it's dmesg a lot of "AMD Vi - IO Page Fault" error lines.

Will try installing latest 4.10.x kernel and see if anything different.

---

### Post by vishalrao on 2017-03-09
So I installed mainline kernel 4.10.1 using UKUU tool and the "AMD-Vi IO Page Fault" log lines still occur but the "coreperf missing empty info unknown hardware" message went away. Probably BIOS updates for my ASUS B350 board should resolve things hopefully they release more updates soon.

---

### Post by rsandru on 2017-03-09
Lucky you :)

I still haven't managed a proper installation so far: 16.04 and 16.10 both fail to get me very far on my Gigabyte GA-AX370 and 1700X...  Now downloading 17.04 beta to see if I can get any further in the process.

---

### Post by QIII on 2017-03-09
If you are intrepid, you may [try installing the 4.11 rc1 kernel]("https://ubuntuforums.org/showthread.php?t=2354851&p=13617987#post13617987").

I was testing it for AMDGPU-PRO compatibility last night (it works!) and I realized that it may have support for the Ryzen.

Be advised, however, that such a radical test is at your own risk.

I'm contacting vendors to see if I can get components for a test system so I can provide help here and write a few blog articles.  We'll see if they are interested in providing promo items to a pip-squeak like me!

---

### Post by rsandru on 2017-03-09
> **QIII said:**
> If you are intrepid, you may [try installing the 4.11 rc1 kernel]("https://ubuntuforums.org/showthread.php?t=2354851&p=13617987#post13617987").

I was testing it for AMDGPU-PRO compatibility last night (it works!) and I realized that it may have support for the Ryzen.

Be advised, however, that such a radical test is at your own risk.

I'm contacting vendors to see if I can get components for a test system so I can provide help here and write a few blog articles.  We'll see if they are interested in providing promo items to a pip-squeak like me!

Well, unless I can fix the installation image I don't think I can do much. All versions from 16.04 to 17.04 beta are unable to even get started with the installation. Since this computer had no previous OS at all I'm completely stuck at the moment. :(

---

### Post by vishalrao on 2017-03-09
@rsandru - Try playing around with grub kernel boot options like "acpi=off" to see if you can boot and install???

@QIII - "If you are intrepid" hah was that a pun intended? :D

Good luck to get some parts for testing with ubuntu!

---

### Post by QIII on 2017-03-10
> **rsandru said:**
> Well, unless I can fix the installation image I don't think I can do much. All versions from 16.04 to 17.04 beta are unable to even get started with the installation. Since this computer had no previous OS at all I'm completely stuck at the moment. :(

Install Ubuntu on a different machine, without any proprietary drivers. Upgrade the kernel.

Swap the drive into the new machine as the boot drive.

---

### Post by P-I H on 2017-03-12
I upgraded my AMD 8120 Bulldozer system with a new motherboard, MSI-B350-Tomahawk, and the Ryzen 7 1700 CPU. Used two SSD:s, one with Ubuntu 16.04.2 and one from my test system with Ubuntu zesty.
Both the zesty system and the Ubuntu 16.04.2 booted OK. First boot with took some time over a minute.
```

**Computer**
Processor    16x AMD Ryzen 7 1700 Eight-Core Processor
Memory    16446MB (2069MB used)
Operating System    Ubuntu Zesty Zapus (development branch)
User Name    p-i (P-I H)
Date/Time    sön 12 mar 2017 07:24:18
Display
Resolution    1920x1200 pixels
OpenGL Renderer    Gallium 0.4 on AMD TONGA (DRM 3.9.0 / 4.10.0-11-generic, LLVM 3.9.1)
X11 Vendor    The X.Org Foundation
Multimedia
Audio Adapter    AV200 - Xonar D2X
Audio Adapter    USB-Audio - USB Device 0x46d
Audio Adapter    HDA-Intel - HDA ATI HDMI
Audio Adapter    HDA-Intel - HD-Audio Generic
Input Devices
Power Button    
Power Button    
Logitech HID compliant keyboard    
Logitech USB Optical Mouse    
Logitech HID compliant keyboard    
UVC Camera (046d:0804)    
HDA ATI HDMI HDMI/DP,pcm    3=
HDA ATI HDMI HDMI/DP,pcm    7=
HDA ATI HDMI HDMI/DP,pcm    8=
HDA ATI HDMI HDMI/DP,pcm    9=
HDA ATI HDMI HDMI/DP,pcm    10=
HDA ATI HDMI HDMI/DP,pcm    11=
HD-Audio Generic Front Mic    
HD-Audio Generic Rear Mic    
HD-Audio Generic Line    
HD-Audio Generic Line Out Front    
HD-Audio Generic Line Out Surround    
HD-Audio Generic Line Out CLFE    
HD-Audio Generic Line Out Side    
HD-Audio Generic Front Headphone    
Printers (CUPS)
HL3140CW    Default
SCSI Disks
ATA SanDisk Ultra II    
ATA KINGSTON SV300S3    
**Operating System**
Version
Kernel    Linux 4.10.0-11-generic (x86_64)
Compiled    #13-Ubuntu SMP Wed Mar 1 21:27:28 UTC 2017
C Library    GNU C Library version (Ubuntu GLIBC 2.24-7ubuntu2) 2.24 (unstable)
Default C Compiler    GNU C Compiler version 6.3.0 20170221 (Ubuntu 6.3.0-8ubuntu1)
Distribution    Ubuntu Zesty Zapus (development branch)
Current Session
Computer Name    pi-MSI-B350-Tomahawk-Kingstone
User Name    p-i (P-I H)
Home Directory    /home/p-i
Desktop Environment    Unity:Unity7 (ubuntu)
**DMI**
BIOS
Date    02/15/2017
Vendor    American Megatrends Inc. (www.ami.com)
Version    1.00
Board
Name    B350 TOMAHAWK (MS-7A34)
Vendor    Micro-Star International Co., Ltd

```

---

### Post by laserburn2 on 2017-05-04
Well, it's time for me, the thread starter, to update you on my situation. Bought Ryzen 1600 and ASUS Prime B350 Plus motherboard, made a switch in the case today and computer booted normally. I've put the 4.10.12 kernel using Ukuu.

The only issue I have is that every few seconds HDD LED on the case lights up for no apparent reason. As I had SSD die on me before, this scares me quite a bit. I don't know if this is some sort of problem with BTRFS I use.

---

