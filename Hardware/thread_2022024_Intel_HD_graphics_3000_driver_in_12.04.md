---
title: "Intel HD graphics 3000 driver in 12.04"
date: 2012-07-10
forum: Hardware
---

### Post by emagar on 2012-07-10
I have a battery consumption issue in a dell xps 13 i5 running 64-bit ubuntu 12.04. Jupiter is installed. If I only use a text editor and an open console, battery reports 6.5 hours. Opening chrome web browser, however, drops expected duration to 2+ hours only. 

I suspect a video card driver problem. A friend pointed to [this]("http://askubuntu.com/questions/151157/how-do-i-install-hd3000-drivers-on-ubuntu-12-04") thread, which suggests a partial solution. He also suggested that I may need to update the video card driver ([here]("http://intellinuxgraphics.org/index.htm") is info from Intel), which seems far from self-evident from my Linux newbie perspective.

Has anyone done this?

Some info that ought to be useful to diagnose my problem:

```
eric@eric-xps13:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation QS67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230 (rev 34)
03:00.0 USB controller: Fresco Logic Device 1009 (rev 02)

```

Thank you in advance.

---

### Post by Ubun2to on 2012-07-10
Do you have the latest drivers?
Go to the Additional Drivers program to see if Intel has proprietary drivers.
If they don't, go here:
[http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Processor+graphics&ProductProduct=2nd+Generation+Intel%C2%AE+Core%E2%84%A2+Processors+with+Intel%C2%AE+HD+Graphics+3000%2f2000](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Processor+graphics&ProductProduct=2nd+Generation+Intel%C2%AE+Core%E2%84%A2+Processors+with+Intel%C2%AE+HD+Graphics+3000%2f2000)
Go to the bottom of the list of supported OSs-there are Linux drivers.

---

### Post by QIII on 2012-07-10
Ubuntu already has the Intel driver by default, as do many Linux distros.

The XPS appears to come with a number of video card options.  Does you machine include hybrid graphics.  That is, Intel/NVIDIA switchable graphics?

---

### Post by emagar on 2012-07-10
Thank [Ubun2to]("http://ubuntuforums.org/member.php?u=1579962") for the reply. I have no proprietary drivers listed in additional drivers. The intel site does list a driver that looks like what I need. But there are also several  warnings about the difficulty of the task ahead in order to  compile drivers from scratch... Has anyone done this and written about it?

---

### Post by emagar on 2012-07-10
> **QIII said:**
> Ubuntu already has the Intel driver by default, as do many Linux distros.

The XPS appears to come with a number of video card options.  Does you machine include hybrid graphics.  That is, Intel/NVIDIA switchable graphics?

Thanks Qlll for the help. I'll stop attemting to upgrade the intel driver. I am not aware of an option to switch graphics... system settings offers no option of this nature. Where should I look for this? 

Sorry for the ignorance, I am rather new in Linux.

Thanks again.

---

### Post by Sylslay on 2012-07-10
Becouse browser (with flash plugin) will use more power then any text editor.

and for sure if You start watching move at VLC,
than batery performacne will drop to 90 min. 
Plese chesk the CPU load in system monitor.

I think that there is no intel drivers issue at all
if You install brand new drivers total performance will be better about max 5%,

The times You posted are much greater than 5%.):P

Check firefox without any plugins on. (will be almost idle)

And as they said, intel drivers are allready build in kernel,
and the better one (edge) You maight found in PPA repos.

Spec of laptop.
I hasn't any nvidia video chip:



    Design
    Tech Specs
    Customer Ratings
    Ultrabooks

Processor Help Me Choose

    Intel® Core&#8482; i5-2467M processor (1.60 GHz with Turbo Boost 2.0 up to 2.30 GHz)

Memory

    4096MB 1333MHz Single Channel DDR3 SDRAM [1x4096]

Chipset

    Intel® QS67

Video CardHelp Me Choose

    Intel HD Graphics 3000

---

### Post by Ubun2to on 2012-07-10
> **emagar said:**
> Thanks Qlll for the help. I'll stop attemting to upgrade the intel driver. I am not aware of an option to switch graphics... system settings offers no option of this nature. Where should I look for this? 

Sorry for the ignorance, I am rather new in Linux.

Thanks again.

What version of the kernel are you using? I have heard of reports of stuff going weird if the kernel isn't updated. Type the following command into terminal:
```
uname -a
```
This is my output:
```
Linux ubuntu 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```
If your kernel is outdated, that could explain a lot.
If it isn't the same as mine (3.2.0-26) or higher, go to the update manager and attempt to install updates-it could be that it was never updated (maybe the updater somehow missed it) or didn't update properly (although that is unlikely, it is possible).
Also, here is another test to determine if it's the OS that is the problem or if it is within the actual hardware:
1. Create a live CD.
2. Boot into the live CD.
3. If the display turns bad again, there is a good chance that the hardware is going screwy. If not, it is most likely the OS itself.
Edit: I found another thing that may help you determine what is going wrong. I have found a list of glitches with hardware relating to the current kernel. The list can be found here:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop/#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Kernel](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop/#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Kernel)

---

### Post by emagar on 2012-07-10
Thanks [Sylslay]("http://ubuntuforums.org/member.php?u=739078") for the elaborate reply. Your suggestion seems reasonable: instead of tweaking the drivers, I'll use minimalist firefox whenever I can. I'll experiment with this route and report back in a couple of days. 

Cheers!

---

### Post by emagar on 2012-07-10
> **Ubun2to said:**
> What version of the kernel are you using? I have heard of reports of stuff going weird if the kernel isn't updated. Type the following command into terminal:
```
uname -a
```This is my output:
```
Linux ubuntu 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```If your kernel is outdated, that could explain a lot.
If it isn't the same as mine (3.2.0-26) or higher, go to the update manager and attempt to install updates-it could be that it was never updated (maybe the updater somehow missed it) or didn't update properly (although that is unlikely, it is possible).
Also, here is another test to determine if it's the OS that is the problem or if it is within the actual hardware:
1. Create a live CD.
2. Boot into the live CD.
3. If the display turns bad again, there is a good chance that the hardware is going screwy. If not, it is most likely the OS itself.

Here's mine
```
Linux eric-xps13 3.2.0-27-generic #43+kamal5~DellXPS-Ubuntu SMP Fri Jul 6 23:01:01 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```
it does not look outdated... the problem appears to be elsewhere. 
Thanks for the help.

---

### Post by emagar on 2012-07-10
> **Ubun2to said:**
> Edit: I found another thing that may help you determine what is going wrong. I have found a list of glitches with hardware relating to the current kernel. The list can be found here:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop/#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Kernel](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop/#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Kernel)

Thanks for this. I'll keep browsing the list, but so far have been unable to find anything related to my problem... Patience is indeed a virtue.

---

### Post by mastablasta on 2012-07-11
install htop and then run it in terminal post the result here when you have the CPU load again. so we can see what take up your CPU.
 
inte drivers are there if you want to compile the kernel yourself. -27 kernel is strange as mine is also at -26. are you using some development version of kernel? or maybe there way a new update again...
 
anyway xorg edgers PPA will give development version of drivers, but it doesn't look like they are the ones causing the issue.

---

### Post by Ubun2to on 2012-07-11
> **emagar said:**
> Here's mine
```
Linux eric-xps13 3.2.0-27-generic #43+kamal5~DellXPS-Ubuntu SMP Fri Jul 6 23:01:01 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```
it does not look outdated... the problem appears to be elsewhere. 
Thanks for the help.

That's weird. Your kernel is more recent then mine. However, that is a start.
When you boot, if you don't get options for recovery mode or previous versions, press shift. If it gets to the login screen, you need to try again.
Once you get to the Grub boot menu, go to "Previous Linux Versions".
Select the 3.2.0-26 kernel. See if that works. If so, it would be a problem with the kernel. If not, I am stumped. That is the only thing I can think of right now.

---

### Post by 1c3d0g on 2012-07-13
Type in chrome:

```
about:flags
```

Disable AT LEAST the following:

```
GPU compositing on all pages 
Disable accelerated 2D canvas
Disable deferred 2D canvas
Disable accelerated CSS animations
GPU Accelerated SVG Filters 
Disable WebGL
```

See if that helps. :)

---

### Post by emagar on 2012-07-20
> **1c3d0g said:**
> Type in chrome:

```
about:flags
```

Disable AT LEAST the following:

```
GPU compositing on all pages 
Disable accelerated 2D canvas
Disable deferred 2D canvas
Disable accelerated CSS animations
GPU Accelerated SVG Filters 
Disable WebGL
```

See if that helps. :)

Thanks for the reply. The 2nd and 3rd are not listed. All others were already disabled...

---

### Post by emagar on 2012-07-20
> **mastablasta said:**
> install htop and then run it in terminal post the result here when you have the CPU load again. so we can see what take up your CPU.
 
inte drivers are there if you want to compile the kernel yourself. -27 kernel is strange as mine is also at -26. are you using some development version of kernel? or maybe there way a new update again...
 
anyway xorg edgers PPA will give development version of drivers, but it doesn't look like they are the ones causing the issue.

Thanks for the reply and sorry for the week-long absence. I found no way of copying htop's info. So I sorted the processes by CPU% and saved the following screen-picture:

---

