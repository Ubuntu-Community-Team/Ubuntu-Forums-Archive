---
title: "Anyone have experience with Dell Vostro 3750"
date: 2011-04-17
forum: Hardware
---

### Post by Petrik on 2011-04-17
Just while I am waiting for this machine to arrive I wonder if anyone here has had any experience getting Ubuntu installed on this model.

[http://www.dell.com/nz/business/p/vostro-3750/pd?oc=u5203d4nz&model_id=vostro-3750](http://www.dell.com/nz/business/p/vostro-3750/pd?oc=u5203d4nz&model_id=vostro-3750)

I will be giving it a go when it shows up in about two weeks time. I am hoping that 11.04 will be up to the job.

---

### Post by Imago Maeror on 2011-04-20
Hi there!

Sorry, but i have to tell you that it doesn't seem to work. I got my Vostro 3750 (i52nd gen, 8GB RAM, NVidia Grafics) about a week ago. The first thing I tried was to install Ubuntu. I tried three different Versions, but none of them worked. I'm not that experienced in ubuntu. I worked for a half year now with it, but i think i already learned a few things.

At first I tried Ubuntu 10.10 64-Bit The Problem ist to get the Live-CD started. The machine boots until the screen with the dots appears. Then it gets stuck. Pressing a key to see the console shows up an error like "(process:384): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)       
                                stdin: error 0
chroot: can't execute 'mktemp': input/output error"
when i open the cd-tray i get a bunch of input/output errors for different files....

So my hope was that the 11.04BetaI 64-Bit will work. I tried it but i got the error: "stdin: error 0" at the same point of booting. Same effect by ejecting the disc, a bunch of i/o errors....

My last try was Ubuntu 11.04BetaII 64-Bit. But same here: "stdin error 0    chroot: can't execute 'mktemp': Input/output error"

I don't exactly know what the problem is, but maybe the kernel isn't ready for the new chipset or something like that. I even tried to modify the booting options (F8) but it still doesn't work.

Well I hope that the 11.04 Final will work properly. I would be very disappointed if there is no way to get Ubuntu running on this machine. 

Whatever, maybe you'll have more luck ;-)

best wishes,
Imago

---

### Post by mario_7 on 2011-04-20
Did you try to run Live session from USB drive? 
Maybe there is something wrong with dvd drive.

---

### Post by Imago Maeror on 2011-04-23
Hello!

Thank you for this advice, i will give it a try. I only tested via CD drive. I hope it works with the live USB.

Well, i will let you know what happened ;-)

---

### Post by mörgæs on 2011-04-23
Post 176 in this thread
[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)
tells how to solve the Glib-problem. It is not related to Dell.

10.10 can shed a lot of repeated error messages about I/O right after the installation. Most often they are harmless; just boot the machine and see for yourself if anything is wrong. 

If a 64 bit install does not work, the 32 bit version should be your next step.

---

### Post by JRV on 2011-04-23
There is also an issue with some newer Dell machines that dual boot installing and working fine until Windows is booted. Then the grub2 boot loader is erased, and the machine will only run Windows.

This link, and the link in the first post explain the problem:

[http://ubuntuforums.org/showthread.php?t=1670010](http://ubuntuforums.org/showthread.php?t=1670010)

---

### Post by Imago Maeror on 2011-04-24
Alright, first i tried the installation with live-usb from ubuntu 11.04Beta2 64-Bit. The procedure failed, the system hang up after the screen which looked like "Linux Kernel xyz by Name". But thanks again for this hint anyway. 

After that i tried the way mörgæs described. I downloaded a minimal iso of Ubuntu 10.10 64-Bit ([http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-amd64/current/images/netboot/mini.iso) ). This worked for me fine for the process of installation. Ubuntu is now installed at a separated partition.

The first boot was no problem and i set up the password for the drive encryption. After that i installed the NVIDIA drivers. Ubuntu requested a reboot. After that Grub started and showed me the list. I chose start Ubuntu xx.xxx - generic. After that the system booted, but only in console-mode. There is a prompt for my Username and password, after that i can use the regular command-line linux. But i don't know why it doesn't start GNOME.

I have to try the solution for dual-boot from JRV, too. I want to use the preinstalled win7 as well as ubuntu. So is it possible after the steps you described JRV?

---

### Post by mörgæs on 2011-04-24
It sounds like you need to add boot options. They are described  here:

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by JRV on 2011-04-24
> **Imago Maeror said:**
> 
I have to try the solution for dual-boot from JRV, too. I want to use the preinstalled win7 as well as ubuntu. So is it possible after the steps you described JRV?

All you can do is try it, after installing Ubuntu everything appears to work.  If your machine has the problem I mentioned it will run Ubuntu as expected until you run Windows.  Then it will only run Windows from that point on.  In my post, in the thread I linked, I tell how I re-installed grub2.  After that I deleted Windows and my friend quit Windows and switched to Ubuntu.

---

### Post by Imago Maeror on 2011-04-25
> **JRV said:**
> All you can do is try it, after installing Ubuntu everything appears to work.  If your machine has the problem I mentioned it will run Ubuntu as expected until you run Windows.  Then it will only run Windows from that point on.  In my post, in the thread I linked, I tell how I re-installed grub2.  After that I deleted Windows and my friend quit Windows and switched to Ubuntu.

Okay, I see. Sorry I misunderstood you. I thought you described some kind of a "workaround" or something like that. I tested it and luckily it seems that *this problem doesn't affect me on this machine*. I can boot both OS's from GRUB.


After a bit of "trial-and-error" I found a problem with gdm. After the booting process of Ubuntu I got the tty1-console. I googled how to get from this point into gdm. So I logged in and typed "gdm". I got this error:
```

** (gdm-binary:1836): WARNING ** : Failed to aquire org.gnome.DisplayManager: Connection ":1.23" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file.

``` My first idea is to reinstall gdm. Maybe it will work after that. The first time the problem appeared it worked by reinstalling gdm. Now it doesn't. I tried to boot with different bootoptions like "xforcevesa" and "nouveau.modeset=0" but it still won't work. What does it mean and how can I fix that?
[B]
[/B]
---- ***Current Status:*** **Fixing the System again...**

Now I'm gonna *configuring* the system. I started the internal Hardwaretest of Ubuntu to test the system and I think there are a few things which don't work properly at the moment.

1. **Wireless-LAN:** 
I think the system doesn't recognize the WLAN device correctly, i can only connect to the internet via cable (like i did for the installation-process)
- Okay, first I will try to fix this one. A Googlesearch gave me some answers. First I checked if the system even recognizes the hardware by typing "iwconfig" into gnome-terminal the result was:
```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```so I think that the system doesn't recognize the card yet. I will try the steps described here: [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access")

Okay I found out, that this Notebook uses a Intel Network chipset.
```
sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f2a00000-f2a01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: 14:fe:b5:a1:cd:6d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.180 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:45 ioport:3000(size=256) memory:f1804000-f1804fff memory:f1800000-f1803fff
``````
lspci | grep Network
02:00.0 Network controller: Intel Corporation Device 008a (rev 34)

```I found a thread for another Notbook with the same PCI-Card (here: [http://forum.ubuntuusers.de/topic/intel-centrino-1030-kann-nicht-aktiviert-werde/]("http://wiki.ubuntuusers.de/WLAN/Linux-backports-modules")) and it seems that I have to install the Backport-drivers. ([http://wiki.ubuntuusers.de/WLAN/Linux-backports-modules](http://wiki.ubuntuusers.de/WLAN/Linux-backports-modules)) 

I will give this a try by installing "linux-backports-modules-compat-wireless-2.6.37-maverick-generic" from universe

This is it! The Wifi works now!  *--solved*


2. **Fingerprintreader:**
I don't know if the Fingerprintreader even works under Ubuntu. A short look into the Software-center didn't help me. Are there any Programs to get it running?
I took a look at "fingerprint-gui"-Project. I installed it but it doesn't recognize the scanner.

3. **internal microphone:**
I can't hear the recordings during the test. I installed the ALSA-Mixer for this reason, I think it works now. *--solved*

this is what I found for now...

---

### Post by Imago Maeror on 2011-05-01
Well, new Version of Ubuntu is out for approximately a week!

The System works much better with natty (Ubuntu 11.04). Most problems were solved and the most things worked "out-of-the-box". The Live-CD worked as well, so I didn't need to go the way with minimal.iso.

But actually there is a problem with the NVIDIA-Current driver or jockey. The Geforce GT 525M doesn't work at the moment. But the internal Intel Chipset works fine, so i will use it until they fixed the Nvidia driver.

And I couldn't find a solution for the fingerprint reader.

---

### Post by vivek456 on 2011-05-05
Hi, I also just bought Vostro 3750. There is a big discussion/frustrations going around the web about people not able to use their nVidia card.

I wanted to know if you are able get the intel card to work, atleast? Or are you using the Vesa driver? Can you confirm please? Also pls post your 'lspci |grep VGA'

Mine is:

00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1)

Thanks,
Vivek.

---

### Post by Imago Maeror on 2011-05-05
> **vivek456 said:**
>  I wanted to know if you are able get the intel card to work, atleast? Or are you using the Vesa driver? Can you confirm please? Also pls post your 'lspci |grep VGA'
  Yes the Intel Chipset works fine, even with unity support. I just uninstalled the nvidia driver and now use the default one (I think it is vesa)  My lspci is: ```
 lspci |grep VGA 00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) 01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1) 
```

---

### Post by vivek456 on 2011-05-06
Ok, Thanks.

Mine works with Vesa too. But not with intel drivers. So I am only getting a resolution of 1024x768 though the native resolution is 1600x900.

---

### Post by townsend92 on 2011-05-06
I've had my 3750 for about a month. I used 10.10 for only a couple of months on another dell laptop without issue. At first I installed 10.10 using the 32bit iso that I already had. This worked, but i think I installed the Nvidia drivers and now the screen is blank when booted.

I downloaded the new 11.04 32bit and 64bit and would like to reinstall with those, but when booting from the CD I also experience boot issues before the GUI is displayed. Did anyone install from the CD? or do I have to install from the other minimal iso first that is described previously?

Thanks

---

### Post by vivek456 on 2011-05-06
I just burnt a Ubuntu 11.04 and tried to boot with it but was not able to. 

I also use Debian on Vostro 3750 and none of the newer kernels work - 2.6.38 and 2.6.39 does not work. I get a blank screen and no control over the keyboard. Only kernel that works is 2.6.32 :(

So am trying Knoppix 6.4.4 now.

---

### Post by vivek456 on 2011-05-06
Knoppix also failed at boot. But it did lot of things and it failed while bringing the X up. This is the same problem as before. It uses the kernel - 2.6.37. So it detects that I have an intel graphics card and it loads up the intel xorg driver which doesn't work. I also tried with the latest intel driver compiled from the CVS (as of yest) and it throws 'No devices detected'. So I am out of option now, other than to try out the latest xorg driver from the CVS everyday.

---

### Post by townsend92 on 2011-05-09
I did get the alternative iso to install (64bit). After installation and reboot, I was again faced with a blank screen. I edited the recovery GRUB entry to add the nomodeset option to allow the GUI to display. 

This gives a working install, but the graphics need to be a little better to be usable. (Also, a warning popped up saying I can't use Unity.)

---

### Post by vivek456 on 2011-05-11
Hi townsend92, I have created a bug report over at freedesktop.org to get the intel KMS and xorg driver to work in Vostro 3750. Can you please go through the bug report and if possible replicate the issue at your end and add comments there too?

[https://bugs.freedesktop.org/show_bug.cgi?id=37029](https://bugs.freedesktop.org/show_bug.cgi?id=37029)

Thanks,
Vivek.

---

### Post by townsend92 on 2011-05-13
I read through the report. I don't know the inner workings of Linux yet, so it may take me some time to replicate the problems in the report.

---

### Post by sanova on 2011-05-17
I would like to know how do you run Ubuntu (in graphic mode) using the intel graphic card. I have tried to run every distro i can, without positive results (Debian testing and sid, opensuse, fedora, and ubuntu 11.04). The last one freezes at start up, debian can run only in "shell mode". 

So can you tell me how can i exec X server with no error and freeze with Ubuntu?

Thank you

---

### Post by vivek456 on 2011-05-18
Maybe it's trying to bring up the X server and not able to do that. There is a problem with Intel's kernel module 'i915' as outlined in the bug report I posted before. 

You can try to boot the kernel with 'nomodeset', that will disable the kernel's intel module not to do KMS. 

This way atleast, you can get the Xorg's Vesa driver to run.

---

### Post by sanova on 2011-05-18
I'm trying opensuse at the moment, and the "failsafe" mode has got that option in boot kernel option yet, but it does not work.

The kernel stops running at following load point (with opensuse as ubuntu as debian):

[Firmware Bug] ACPI(PEGP) defines _DOD but not _DOS

Anyway i have read that someone can load x server and uses also intel drivers in one of last posts of this thread.
Didn't i understand?

---

### Post by vivek456 on 2011-05-19
Ok. I think you have the exact same intel's VGA adaptor as mine.

Right now, the intel kernel driver as well as the xorg driver doesn't work. You should stop the kernel from loading the driver 'i915'. Any kernel >= 2.6.38 doesn't work. But xorg's Vesa driver will work but without the native resolution. I am able to install debian successfully. You need to get to the command prompt and blacklist i915 driver so that kernel doesn't load it at boot time.

I have created a bug report over here: [https://bugs.freedesktop.org/show_bug.cgi?id=37029](https://bugs.freedesktop.org/show_bug.cgi?id=37029) . So if you can visit this site and confirm that you too are getting the same error, we might be able to see some support soon

---

### Post by sanova on 2011-05-20
I posted in that section as you suggested. But i don't think this bug will be solved in the next time. May be no support will come for our intel graphic card for a long long time.

If we could switch to nvidia card (disabling intel card with acpi_call and switcheroo) we probably could use nouveau or nvidia proprietary driver. Don't you think?
Unluckily acpi_call could not recognized the "switch mode" used by two cards, so i could not set nvidia card as default card.

---

### Post by vivek456 on 2011-05-20
Yes, I saw your post. Thank you! If more people report the issue on different models, then maybe they will consider fixing it soon.

I did try out acpi_call from hybrid graphics. The max I was able to do is to switch off the nVidia card. 

I think we need to get intel driver working for that. Even so, I am not sure if we can completely start using nVidia in place of Intel. You can definitely get 3D apps running using the nVidia card, but what about the X itself? Can it run in nVidia card with native resolution? I would love that but I don't think it's possible. :(

---

### Post by sanova on 2011-05-21
At the moment, but also for the future, 3D is last purpose (On my desktop i use nouveau without 3D and i could install nvidia proprietary driver to have it). I would like to run system with its native resolution and nothing else, using one of both two cards. it's not important for me wich of both. 

So i hope we will have support for at least one of them :o

We will see...

I'm trying Arch.. :D . I know it will not solve our problem but... it's just another attempt.

---

### Post by sanova on 2011-05-22
As other distro it works only with vesa at 1024x768 resolution :(

Vesa works not so bad, but 1024x768 is too low.

If vesa gave the opportunity to set the max resolution it should be great.

---

### Post by vivek456 on 2011-05-23
Yes. I also use 1024x768. It's not so bad.

---

### Post by sanova on 2011-05-24
as i read in the bug report, it seems that our intel graphic card is the unique exception!! :( .. we are very unlucky! all graphic intel cards of same family are perfectly supported.
it is a bug..so we can only wait and hope this bug will be solved as soon as possible. :(

vivek, but has kernel 2.6.32 (32 and 64 bit) same bug too? or not? or kernel 2.6.35 ?

---

### Post by vivek456 on 2011-05-24
Yes, it seems that way.

The i915 of 2.6.32 loads without any errors. But it doesn't do anything else too. Haven't tried 2.6.35.

---

### Post by sanova on 2011-05-28
Yes, it's as you wrote. I have tried ubuntu 10.004. It loads i915 without any errors but then unloads it and set vesa driver.

---

### Post by sanova on 2011-05-28
Bad new is that no new replay in bug report opened by you :( . So it can mean nobody is interested to solve bug of our card. May be there are few users running it so is not so important as other bugs :( .

I suppose that the problem is coused by a conflict between firmware and driver.

Anyway, for now, i'm re-installing windows 7 on pc and it is very horrible..

---

### Post by vivek456 on 2011-05-28
I believe they need the hardware to fix it. So first they have to get it before going on further. Not sure how long it will take.

Switching to windows is not an option for me, I have everything in linux. I am ok with vesa for now. It's pity that I can't use nVidia I paid for and it adds to the injury that I can't use intel either.

---

### Post by vivek456 on 2011-05-28
>  I suppose that the problem is coused by a conflict between firmware and driver.


Check this link out. This person is getting the exact same error but he was able to proceed further. Like that bug report states, there is some problem in LVDS linking.

[https://lists.launchpad.net/hybrid-graphics-linux/msg00864.html](https://lists.launchpad.net/hybrid-graphics-linux/msg00864.html)

---

### Post by sanova on 2011-05-30
[   16.165764] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0

That kernel module appears everywhere. Anyway acpi_call is not the best way to try switching to nvidia card, also because the nvidia is directly connected to intel. Intel is like a bridge between nvidia and monitor. For this reason intel has to run also when nvidia card is used. 
A better solution could be "bumblebee", that gives the opportunity for using nvidia card when needed, but not without the intel properly working.

Today i have called to dell support to have some more informations about this problem. He told me that 10.10 should have support for our 3750. They have tested it and should properly work.

---

### Post by vivek456 on 2011-06-10
Sanova, The i915 in kernel 2.6.39-rc7 is correctly setting the mode without any panics. And the xorg driver is correctly setting the native resolutions on both laptop's monitor as well as the external monitor. I am not sure what got fixed but just wish I had tried this kernel earlier. :)

---

### Post by kirandulo on 2011-06-20
> **vivek456 said:**
> ...i915 in kernel 2.6.39-rc7 is correctly setting the mode without any panics. And the xorg driver is correctly setting the native resolutions on both laptop's monitor as well as the external monitor...
Vivek, is this done natively when installing a fresh Debian or Ubuntu 10.10? Or should kernel 2.6.39-rc7 be installed / build manually?
(Do I need to worry about native resolution any at all on Vostro 3750 laptop when I do fresh install of Debian? Or i915 module and xorg driver will work properly out of the box? Thanks, Greg

---

### Post by JGSD on 2011-07-01
> **vivek456 said:**
> Sanova, The i915 in kernel 2.6.39-rc7 is correctly setting the mode without any panics. And the xorg driver is correctly setting the native resolutions on both laptop's monitor as well as the external monitor. I am not sure what got fixed but just wish I had tried this kernel earlier. :)

If I sit and wait patiently, will 2.6.39 (or above) eventually come to my 11.04 as part of a regular update (I'm on 2.6.38-8-generic at the moment) or is it going to be a case of waiting for 11.10 or installing the kernel manually?

Also, Vivek, is WiFi working out of the box on the Vostro 3750 with the new kernel? Someone a few months ago mentioned it still wasn't and that a workaround was needed.

---

### Post by vivek456 on 2011-07-03
> **kirandulo said:**
> Vivek, is this done natively when installing a fresh Debian or Ubuntu 10.10? Or should kernel 2.6.39-rc7 be installed / build manually?
(Do I need to worry about native resolution any at all on Vostro 3750 laptop when I do fresh install of Debian? Or i915 module and xorg driver will work properly out of the box? Thanks, Greg

I did have a weird story. In the beginning, none of the kernel worked. But after it worked in kernel 2.6.39-rc7, other kernels started working too. For example, Knoppix which has Kernel 2.6.37 didn't work first, but it's now working. So I can't really say which kernel it works. 2.6.32 doesn't work at all, that I can say for sure. So my theory is the something changed the intel's registry and it started working from there on in.

I think you will have some problems getting it to work. It doesn't work out of the box.

What happens when you 'modprobe i915'?

As per Sanova, above, unlike my case, his USB optimal mouse was hindering the loading of i915. So I would suggest you remove all the USB connections and then try loading the driver.

---

### Post by vivek456 on 2011-07-03
> **JGSD said:**
> If I sit and wait patiently, will 2.6.39 (or above) eventually come to my 11.04 as part of a regular update (I'm on 2.6.38-8-generic at the moment) or is it going to be a case of waiting for 11.10 or installing the kernel manually? 

You could try the latest from edgers or something similiar?

>  Also, Vivek, is WiFi working out of the box on the Vostro 3750 with the new kernel? Someone a few months ago mentioned it still wasn't and that a workaround was needed.

Wifi works out of the box on Vostro 3750.

---

### Post by bummi on 2011-07-08
Hi all,

i suffer the same problem having the vostro 3350. Only diff is, i have the ATI card instead of the nVidia. But the problems with the HD3000 is the same.

Did anyone use the drivers from [http://intellinuxgraphics.org/documentation.html?](http://intellinuxgraphics.org/documentation.html?)  i'm not so much experienced wit linux, but wonder to give it a try. Any suggestion or experiences yet with that drivers? The "supported Hardware" list mentiones the "Sandybridge 	Intel® HD Graphics 2000/3000 (used in 2nd Generation Intel® Core&#8482; i7/i5/i3 processor family)"

---

### Post by vivek456 on 2011-07-08
You would need the entire stack of xorg drivers + drm + kernel module. So your best bet would be to try ubuntu's xorg-edgers repository, that has the latest of the above mentioned packages.

What error do you get when you 'modprobe i915'?

---

### Post by bummi on 2011-07-09
dont know. i just killed the ubuntu-partition. My Work arround is now Win7 with a VirtualBox and Ubuntu inside. I will make another try when the problem is fixed out of the box.

---

### Post by Imago Maeror on 2011-07-10
I'm using the computer now for a few months. The "grafics-problem" isn't still solved totally, but i'm able to use the NVIDIA card.  I'm using the X-Update source and from there the Binary NVIDIA X-Org Driver 185. This works.  Only thing its a bit slow when i use cairo-dock in opengl mode... althogh i'm able to use Unity and other opengl applications.

---

### Post by neandr on 2011-09-02
.. yes some more  experience with Dell Vostro 3750 .. see my thread on the German 
**[Ubuntuuser.de]("http://forum.ubuntuusers.de/topic/ubuntu-11-04-laeuft-nicht-auf-neuem-laptop/")**

That's a long story of only a few busy days with good feedback by bowman and mcvoicex. And also some hint from the German Dell support line. Finally -- at least at this moment -- no sucess.

During the process I had to completly reinstall WIN7, have used very different ISO's (Ubuntu, Knoppix) and finally used the mini.ISO which did an succesful Ubuntu 10.10 ... tty mode only!

Booting from CD/DVD still has the same problem (discussed also with this thread), using ESC during power on to get the Ubuntu Grub menu is OK, I can use F6 to set "nomodeset" (Dell support line suggestion) ... NOK, another "forcevesa" couldn't be used (question of my experience?).

So the final point seems to be: no possibility to do a dual boot WIN7/Ubuntu with graphic UI. And I expect Ubuntu with graphic UI will NOT work at all with current software.

I learned it's the specific graphic devices .. but don't see a solution, not even on an interim basis .. before Ubuntu or someone else has a general fix for this Dell Vostro 3750. It's a shame, the machine seems to be a good one. But not with Linux/graphical UI.
  
:guitar: Is there anyone out there ... to have an idee .. solution ..

---

### Post by petr_voinov on 2011-09-03
Just bought Dell Vostro 3750, i5-2410m, GT525M.

Spent a lot time before finally make Ubuntu work fine.
I found that **install from flash drive doesn't works well**, most probably because once bootable flash drive is in one-only USB2.0 port (upper on right side of notebook) BIOS doesn't recognize flash drive correctly and can't boot from that in some reason, even after BIOS update. Though it can boot from other USB3.0 port - but with errors. Most probably those errors are because there are special driver needed to recognize those ports by linux on kernel load (even windows require special driver before make those ports work correctly). I tried 10.10, 11.04 (32 and 64) and 11.10 64 beta with no luck from flash drive.

What i did:
1. **burnt CD with 11.04 amd64 - and install worked great**!!!
2. issue: no compiz support during and after install (unity?)
3. tried nvidia-xconfig - no success, restored /etc/X11/xorg.conf from .backup
4. **removed nvidia from "additional drivers" tool**, probably it was installed and activated because i selected third-party addons on install
5. And now, compiz/unity finally works as needed, TADAAa!

It was a long day with timbrel, hope this will help somebody!

---

### Post by neandr on 2011-09-04
@petr_voinov

Congratulation! 
When my Vostro arrived I was able to install Ubuntu 11.04 aside with Win7. The problem was after some switching the OS, finally under Ubuntu I had to restart the machine to get it running.

But now I can't start the Ubuntu cd/DVD (and also other distro's) anymore!
With one of my last installation test I recognize a  firmware error!

So I hope you have more luck.

---

### Post by petr_voinov on 2011-09-05
@neandr

Sorry, just to make it clear:
1. you are trying to load from **physical CD/DVD**, not their images from flash drive;
2. just for in case, did you **updated BIOS**? might be found on DELL site [http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&SystemID=VOS_N_3750&os=W764&osl=en&catid=-1&impid=-1&dateid=-1&typeid=-1&formatid=-1&source=-1]("http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&SystemID=VOS_N_3750&os=W764&osl=en&catid=-1&impid=-1&dateid=-1&typeid=-1&formatid=-1&source=-1");
3. You are using default drive **AHCI option** (**enabled**, not ATA) at BIOS? ... though if you are switching that back or forth your windows might become unbootable (need to return that to the value used on win install as i imagine).

---

### Post by shafiee01 on 2012-02-04
Dear friends, 
I finally managed to solve this issue.
The problem is exactly in the kernel and it has been resolved in the 3.0.0-15!!
You can simply upgrade to the new kernel by adding ppa:
```
sudo apt-add-repository ppa:kernel-ppa/ppa
sudo apt-get update
```and then install "linux-image-generic-lts-backport-oneiric" from synaptics or terminal.
Hope this helps.

P.S if you want install a linux with kernerl >= 2.6.38 you need to disable ACPI. For example you can install latest Ubuntu but just enter these two parameters in the kernel boot options:
```
acpi=noacpi 
pci=noacpi
```

---

### Post by kshchepanovskyi on 2012-08-05
Graphics works fine on 12.04 (using nouveau driver).
But I can't configure second monitor on HDMI port.

---

